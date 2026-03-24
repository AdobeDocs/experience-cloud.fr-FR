---
title: Guide d’intégration de Java SDK
description: Découvrez comment intégrer Java SDK à des déploiements d’expérience dans votre service principal pour récupérer et évaluer les indicateurs de fonctionnalité.
source-git-commit: 9bfe0e55e89c1d7fbd77cde63831a6a186820e24
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 2%

---


# Guide d’intégration de Java SDK {#java-sdk-integration-guide}

La SDK Java des déploiements d’expérience est une bibliothèque côté serveur qui met en cache les données des indicateurs de fonctionnalité localement et évalue les indicateurs sans appel API synchrone à chaque requête. Ce guide couvre le SDK actuel (4.x).

## Conditions préalables {#prerequisites}

Avant d’intégrer Java SDK, vérifiez les points suivants :

* JDK 11 ou version ultérieure (requis à partir de la version 3.0.0 de SDK ; les versions antérieures prennent en charge JDK 8+)
* Un système de création basé sur Maven
* Une **clé API** et un **jeton de service** identifiant client de votre projet Adobe Developer Console ; voir [S’abonner à l’application API](../../integrate/subscribe-to-api-application.md)
* Votre **ID de client de l’application** enregistré dans la console Déploiements d’expérience ; voir [Intégration de votre application](../../applications/onboard-your-application.md)

## Ajoutez la dépendance Maven . {#maven-dependency}

Ajoutez le SDK Java de déploiements d’expérience au `pom.xml` de votre projet :

```xml
<dependency>
  <groupId>com.adobe.cloudtech</groupId>
  <artifactId>fg-client-sdk</artifactId>
  <version>4.0.6</version>
</dependency>
```

## Initialiser le SDK {#initialize}

Le SDK est initialisé une seule fois au démarrage de l’application à l’aide de `FloodgateClient.createInstance()`. La méthode prend un objet `FloodgateConfiguration` que vous créez avec le créateur de configurations.

### Implémenter le rappel du jeton de service {#service-token-callback}

Le SDK utilise une interface de rappel pour récupérer un nouveau jeton de service au moment de l’exécution :

```java
private class FgConfigCallBack implements FGConfigBaseCallBack {

  @Override
  public String getIMSServiceToken() {
    // Fetch and return a valid service token
  }

  @Override
  public boolean isAnalyticsEnabled() {
    return false; // Set to true to enable analytics
  }
}
```

### Création de l’objet de configuration {#configuration}

Utilisez le créateur de configurations pour configurer le SDK :

```java
FloodgateConfiguration configuration = FloodgateConfiguration.FloodgateConfigurationBuilder
    .aFloodgateConfiguration(
        FgEnv.PRD,                   // Use FgEnv.STG for Stage
        "<YOUR_API_KEY>",
        Set.of("<CLIENT_ID_1>", "<CLIENT_ID_2>"),
        new FgConfigCallBack(),
        CallType.ASYNC
    )
    .withRetryPolicy(retryPolicy)    // Optional: defaults to 5 retries, 10s interval
    .build();
```

Utilisez `FgEnv.STG` pour l’environnement d’évaluation et `FgEnv.PRD` pour la production.

### Création de l’instance cliente {#client-instance}

```java
FloodgateClient fgClient = FloodgateClient.createInstance(configuration);
```

## Récupération des indicateurs de fonctionnalité {#retrieve-features}

### Utilisateur authentifié {#authenticated-user}

Utilisez un jeton d’accès IMS pour récupérer les indicateurs de fonctionnalité de l’utilisateur actuel :

```java
GetFeatureRequest request = GetFeatureRequestBuilder
    .aGetFeatureRequest("<CLIENT_ID>")
    .withAccessToken("<USER_ACCESS_TOKEN>")
    .withContext(context)
    .build();

FeaturesResponse[] features = fgClient.getFeatures(request);
```

### Utilisateur anonyme {#anonymous-user}

Pour les utilisateurs non authentifiés, transmettez un identifiant visiteur et votre jeton de service :

```java
GetFeatureRequest request = GetFeatureRequestBuilder
    .aGetFeatureRequest("<CLIENT_ID>")
    .withServiceToken("<SERVICE_TOKEN>")
    .withVisitorId("<VISITOR_ID>")
    .withContext(context)
    .build();

FeaturesResponse[] features = fgClient.getFeatures(request);
```

### Récupération d’un indicateur de fonctionnalité ou d’une version spécifique {#specific-feature}

Pour récupérer un indicateur de fonctionnalité unique par clé :

```java
GetFeatureRequest request = GetFeatureRequestBuilder
    .aGetFeatureRequest("<CLIENT_ID>")
    .withAccessToken("<ACCESS_TOKEN>")
    .withFeatureKey("<FEATURE_KEY>")
    .build();
```

Pour récupérer par clé de version, remplacez `.withFeatureKey()` par `.withReleaseKey()`.

## Vérifier si une fonctionnalité est activée {#check-feature}

```java
boolean isEnabled = FloodgateClient.isFeatureEnabled(features, "MY_FEATURE_FLAG");

if (isEnabled) {
  // Serve the new experience
} else {
  // Serve the default experience
}
```

Pour les contrôles basés sur les versions :

```java
boolean isEnabled = FloodgateClient.isFeatureEnabled(features, "MY_RELEASE", "MY_FEATURE_FLAG");
```

## Gestion du cache {#cache-management}

Le SDK met en cache les données d’indicateur de fonctionnalité et les actualise selon un intervalle d’interrogation défini par application dans la console. Pour déclencher une actualisation du cache à la demande :

```java
fgClient.refreshClientCache("<CLIENT_ID>");
```

### Clients non pouvant être mis en cache {#non-cacheable}

Pour les clients non pouvant être mis en cache, `getFeature()` effectue un appel API en direct à chaque fois. Le SDK poursuit l’interrogation en arrière-plan et bascule vers la diffusion en cache lorsque le client peut être mis en cache. Pris en charge à partir de SDK version 0.8.

## Options de configuration {#configuration-options}

Les méthodes de configuration facultatives suivantes sont disponibles dans le créateur :

| Option | Méthode | Description |
|---|---|---|
| Toujours utiliser le cache | `.alwaysCache()` | Contourne la réponse de mise en cache de l’API ; utilise pour les indicateurs sans règles d’audience. |
| Désactiver la mise en cache | `.neverCache()` | Désactive la mise en cache par défaut ; utile pour la logique d’actualisation personnalisée du cache |
| Client HTTP personnalisé | `.withHttpClient(client)` | Utiliser votre propre client HTTP |
| Exécuteur personnalisé | `.withScheduledExecutorService(executor)` | Utiliser votre propre exécuteur planifié pour l’interrogation en arrière-plan |
| Inclure la population témoin | `.includeControlGroup()` | Renvoie les données de la population témoin dans la réponse de la fonction |

## Gérer les erreurs {#error-handling}

Enveloppez les appels `getFeatures()` pour capturer les exceptions SDK :

```java
try {
  features = fgClient.getFeatures(request);
} catch (FgClientException e) {
  int statusCode = e.getStatusCode();
  // Handle error and serve default experience
} catch (FgInitException e) {
  e.printStackTrace();
}
```

## Voir également {#see-also}

* [Notes de mise à jour de Java SDK](java-sdk-release-notes.md)
* [SDK](../../integrate/sdks.md)
* [S’abonner à l’application API](../../integrate/subscribe-to-api-application.md)
* [Étapes d’intégration](../../integrate/integration-steps.md)
