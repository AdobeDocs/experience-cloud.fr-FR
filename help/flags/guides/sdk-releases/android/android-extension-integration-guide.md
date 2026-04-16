---
title: Guide d’intégration de l’extension Experience Rollout pour Android
description: Découvrez comment intégrer l’extension Experience Rollout à Adobe Experience Platform Mobile SDK sur Android.
hide: true
exl-id: 683ef4d4-e637-4b7b-b694-689c7e65a99e
source-git-commit: b3e13a42c19eb7b8b7d5d402bf9a56f89f573044
workflow-type: tm+mt
source-wordcount: '934'
ht-degree: 8%

---

# Extension Experience Rollout pour Android {#android-extension-integration-guide}

Ce guide décrit comment intégrer l’extension Experience Rollout à Adobe Experience Platform Mobile SDK sur Android.

## Conditions préalables {#prerequisites}

Avant de mettre en œuvre l’extension Déploiement d’expérience , vérifiez que vous disposez des éléments suivants :

* Propriété mobile configurée dans la collecte de données Adobe Experience Platform [](https://experience.adobe.com/#/data-collection)
* Extension Experience Rollout installée et configurée dans votre propriété mobile
* Un identifiant d’organisation Adobe Experience Cloud
* SDK minimale : API 21 (Android 5.0 Lollipop)

## Dépendances d’extension {#extension-dependencies}

L’extension Experience Rollout requiert les extensions Adobe Experience Platform suivantes :

| Extension | Description | Obligatoire |
|---|---|---|
| Mobile Core | Fournit des fonctionnalités de base, notamment la configuration et le traitement des événements | Oui |
| Cycle de vie | Collecte les données de session et de cycle de vie des applications pour Mobile SDK | Oui |
| Edge Network | Permet la communication avec Adobe Experience Platform Edge Network. | Oui |
| Identité Edge | Gère l’identité de l’utilisateur pour Edge Network | Oui |

Assurez-vous que ces extensions sont installées dans votre propriété mobile de collecte de données et incluses dans vos dépendances d’application.

## Configurer l’extension de déploiement d’expérience dans la collecte de données {#configure}

### Installation l’extension {#install-extension}

1. Connectez-vous à [Collecte de données ](https://experience.adobe.com/#/data-collection).
1. Sélectionnez l’onglet **Balises** et choisissez votre propriété mobile.
1. Accédez à **Extensions** > **Catalogue**.
1. Recherchez **Extension du déploiement d’expérience** et sélectionnez **Installer**.
1. Configurez les paramètres d’extension :

   | Paramètre | Description |
   |---|---|
   | Sandbox | Le sandbox Adobe Experience Platform contenant votre configuration de déploiement d’expérience |
   | ID de l’application | Identifiant unique de votre application dans le déploiement d’expérience |
   | Identifiant du jeu de données | Identifiant du jeu de données Adobe Experience Platform pour les données d’événement Analytics |

1. Sélectionnez **Enregistrer**.
1. Suivez le [processus de publication](https://experienceleague.adobe.com/en/docs/experience-platform/tags/publish/overview) pour mettre à jour votre configuration.

### Obtention de l’identifiant du fichier d’environnement {#environment-file-id}

1. Dans votre propriété mobile, accédez à **Environnements**.
1. Sélectionnez l’icône en forme de boîte sous la colonne **Installer** pour votre environnement.
1. Dans la boîte de dialogue **Instructions d’installation mobile**, copiez le **ID du fichier d’environnement**.

## Ajout de l’extension Experience Rollout à votre application {#add-to-app}

### Ajouter des dépendances {#add-dependencies}

Ajoutez les dépendances Mobile SDK à votre projet. L’extension Experience Rollout nécessite Mobile Core et les extensions associées à Edge répertoriées ci-dessous.

#### Utilisation de Gradle avec la nomenclature (recommandé) {#gradle-bom}

Ajoutez les dépendances suivantes au fichier `build.gradle.kts` de votre application :

```kotlin
dependencies {
    // Adobe Experience Platform Mobile SDK BOM
    implementation(platform("com.adobe.marketing.mobile:sdk-bom:3.+"))

    // Required extensions
    implementation("com.adobe.marketing.mobile:core")
    implementation("com.adobe.marketing.mobile:lifecycle")
    implementation("com.adobe.marketing.mobile:edge")
    implementation("com.adobe.marketing.mobile:edgeidentity")

    // Experience Rollout extension
    implementation("com.adobe.marketing.mobile:rollout")
}
```

#### Utilisation de Gradle (Groovy) {#gradle-groovy}

```groovy
dependencies {
    // Adobe Experience Platform Mobile SDK BOM
    implementation platform('com.adobe.marketing.mobile:sdk-bom:3.+')

    // Required extensions
    implementation 'com.adobe.marketing.mobile:core'
    implementation 'com.adobe.marketing.mobile:lifecycle'
    implementation 'com.adobe.marketing.mobile:edge'
    implementation 'com.adobe.marketing.mobile:edgeidentity'

    // Experience Rollout extension
    implementation 'com.adobe.marketing.mobile:rollout'
}
```

>[!IMPORTANT]
>
>Pour les applications de production, Adobe recommande d’utiliser des numéros de version explicites plutôt que des versions dynamiques. Voir [ Gestion des dépendances Gradle ](https://docs.gradle.org/current/userguide/dependency_management.html) pour plus d’informations.

### Ajout d’autorisations {#add-permissions}

Ajoutez les autorisations suivantes à votre fichier `AndroidManifest.xml` :

```xml
<uses-permission android:name="android.permission.INTERNET" />
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
```

### Initialiser le SDK {#initialize-sdk}

Initialisez Mobile SDK dans votre classe `Application` avant d’appeler les API d’extension de déploiement d’expérience. Utilisez l’identifiant du fichier d’environnement de votre propriété mobile avec `MobileCore.initialize` afin que l’application récupère les paramètres de déploiement que vous avez publiés dans la collecte de données.

#### Utilisation de MobileCore.initialize {#mobile-core-initialize}

Disponible à partir de la version 3.8.0 d&#39;Android BOM, cette API enregistre automatiquement les extensions et permet le suivi du cycle de vie.

>[!IMPORTANT]
>
>Pour les applications de production, utilisez `LoggingMode.ERROR` uniquement. N’utilisez ni `DEBUG` ni `VERBOSE` dans les builds de version.

**Kotlin**

```kotlin
import android.app.Application
import com.adobe.marketing.mobile.LoggingMode
import com.adobe.marketing.mobile.MobileCore

class MainApplication : Application() {

    override fun onCreate() {
        super.onCreate()

        MobileCore.setLogLevel(LoggingMode.ERROR)

        // Initialize with your Environment File ID from Data Collection
        MobileCore.initialize(this, "YOUR_ENVIRONMENT_FILE_ID")
    }
}
```

**Java**

```java
import android.app.Application;
import com.adobe.marketing.mobile.LoggingMode;
import com.adobe.marketing.mobile.MobileCore;

public class MainApplication extends Application {

    @Override
    public void onCreate() {
        super.onCreate();

        MobileCore.setLogLevel(LoggingMode.ERROR);

        // Initialize with your Environment File ID from Data Collection
        MobileCore.initialize(this, "YOUR_ENVIRONMENT_FILE_ID", null);
    }
}
```

### Enregistrer la classe d’application {#register-application}

Enregistrez votre classe `Application` dans `AndroidManifest.xml` :

```xml
<application
    android:name=".MainApplication"
    ... >
</application>
```

## Contexte d’évaluation {#evaluation-context}

`FeatureEvaluationContext` inclut les attributs de ciblage (utilisés pour la correspondance des règles de déploiement) et l’identité facultative (utilisée pour les analyses).

| Méthode | Obligatoire | Description |
|---|---|---|
| `withIdentity(namespace, id)` | Non | Premier argument : espace de noms d’identité (voir [Espaces de noms d’identité ](https://experienceleague.adobe.com/fr/docs/experience-platform/identity/features/namespaces)). Deuxième argument : valeur de l&#39;identité. Incluez-le lorsque vous souhaitez que cet espace de noms et cet identifiant soient représentés dans Analytics pour cette évaluation. S’il n’est pas fourni, Analytics utilise ECID par défaut. Cela n’est pas utilisé pour prendre des décisions d’activation de fonctionnalités. |
| `withAttributes(map)` | Non | `Map<String, List<String>>`. Clé est le nom de l’attribut de contexte utilisé par vos règles de déploiement (par exemple, `locale`, `platform`, `appVersion`, `deviceType`). Valeur est la liste des valeurs d’attribut candidates pour cette clé pour l’utilisateur/la session en cours (par exemple `["en_US"]` ou `["phone"]`). |

**Kotlin**

```kotlin
import com.adobe.marketing.mobile.rollout.FeatureEvaluationContext

val attrs = mapOf(
    "locale" to listOf("en_US"),
    "platform" to listOf("ANDROID"),
    "appVersion" to listOf("3.0.0")
)

val ctx = FeatureEvaluationContext.builder()
    .withIdentity("Email", "customer@example.com")
    .withAttributes(attrs)
    .build()
```

**Java**

```java
import com.adobe.marketing.mobile.rollout.FeatureEvaluationContext;
import java.util.Arrays;
import java.util.HashMap;
import java.util.List;
import java.util.Map;

Map<String, List<String>> attrs = new HashMap<>();
attrs.put("locale", Arrays.asList("en_US"));
attrs.put("platform", Arrays.asList("ANDROID"));
attrs.put("appVersion", Arrays.asList("3.0.0"));

FeatureEvaluationContext ctx = FeatureEvaluationContext.builder()
        .withIdentity("Email", "customer@example.com")
        .withAttributes(attrs)
        .build();
```

### Exemples d’attributs de ciblage {#sample-attributes}

| Attribut | Description | Exemples de valeurs |
|---|---|---|
| `locale` | Paramètres régionaux/langue de l’utilisateur | `["en_US"]`, `["fr_FR"]` |
| `platform` | Identifiant de plateforme | `["ANDROID"]` |
| `appVersion` | Version de l’application | `["3.0.0"]` |
| `deviceType` | Type d’appareil | `["phone"]`, `["tablet"]` |

## Référence d’API {#api-reference}

### isFeatureEnabled {#is-feature-enabled}

`isFeatureEnabled` indique si la fonction Déploiement d’expérience est activée ou désactivée pour le contexte donné. Transmettez des `featureKey`, un `FeatureEvaluationContext` (attributs de ciblage facultatifs et identité facultative pour Analytics) et un rappel. Voir [ Contexte d’évaluation ](#evaluation-context).

**Signature**

*Kotlin*

```kotlin
Rollout.isFeatureEnabled(
    featureKey: String,
    evaluationContext: FeatureEvaluationContext,
    callback: AdobeCallback<Boolean>
)
```

*Java*

```java
Rollout.isFeatureEnabled(
    String featureKey,
    FeatureEvaluationContext evaluationContext,
    AdobeCallback<Boolean> callback);
```

**Paramètres**

| Paramètre | Type | Description |
|---|---|---|
| `featureKey` | Chaîne | Clé de fonctionnalité à évaluer dans le déploiement d’expérience |
| `evaluationContext` | FeatureEvaluationContext | Ajoutez des attributs de ciblage et une identité facultative pour les analyses, au besoin ; utilisez `FeatureEvaluationContext.builder().build()` pour un contexte vide. Voir [ Contexte d’évaluation ](#evaluation-context). |
| `callback` | AdobeCallback&lt;Boolean> | Appelée avec `true` si la fonctionnalité est activée, `false` dans le cas contraire. Vous pouvez également transmettre des `AdobeCallbackWithError<Boolean>` pour gérer les `fail(...)`. |

**Exemples**

*Kotlin*

```kotlin
import com.adobe.marketing.mobile.AdobeCallback
import com.adobe.marketing.mobile.rollout.Rollout

Rollout.isFeatureEnabled(
    "new-checkout-experience",
    ctx,
    object : AdobeCallback<Boolean> {
        override fun call(isEnabled: Boolean?) {
            if (isEnabled == true) {
                showNewCheckout()
            } else {
                showDefaultCheckout()
            }
        }
    }
)
```

*Java*

```java
import com.adobe.marketing.mobile.AdobeCallback;
import com.adobe.marketing.mobile.rollout.Rollout;

Rollout.isFeatureEnabled(
    "new-checkout-experience",
    ctx,
    new AdobeCallback<Boolean>() {
        @Override
        public void call(Boolean isEnabled) {
            if (Boolean.TRUE.equals(isEnabled)) {
                showNewCheckout();
            } else {
                showDefaultCheckout();
            }
        }
    }
);
```

### getFeature {#get-feature}

`getFeature` renvoie la payload de fonction évaluée pour le contexte fourni. Utilisez cette API lorsque vous avez besoin de plus que activés/désactivés et que vous souhaitez obtenir des métadonnées ou des valeurs de fonctionnalités.

**Signature**

*Kotlin*

```kotlin
Rollout.getFeature(
    featureKey: String,
    evaluationContext: FeatureEvaluationContext,
    callback: AdobeCallback<FeatureEvaluationResult>
)
```

*Java*

```java
Rollout.getFeature(
    String featureKey,
    FeatureEvaluationContext evaluationContext,
    AdobeCallback<FeatureEvaluationResult> callback);
```

**Paramètres**

| Paramètre | Type | Description |
|---|---|---|
| `featureKey` | Chaîne | Clé de fonctionnalité à évaluer dans le déploiement d’expérience |
| `evaluationContext` | FeatureEvaluationContext | Ajoutez des attributs de ciblage et une identité facultative pour les analyses, au besoin ; utilisez `FeatureEvaluationContext.builder().build()` pour un contexte vide. Voir [ Contexte d’évaluation ](#evaluation-context). |
| `callback` | AdobeCallback&lt;FeatureEvaluationResult> | Appelée avec la payload de la fonctionnalité évaluée ; peut être `null` lorsque la fonctionnalité est introuvable. Vous pouvez également transmettre des `AdobeCallbackWithError<FeatureEvaluationResult>` pour gérer les `fail(...)`. |

**Réponse**

*FeatureEvaluationResult*

| Champ | Type | Description |
|---|---|---|
| `id` | Int | Identifiant numérique de la caractéristique |
| `key` | Chaîne | Clé de fonctionnalité |
| `releaseKey` | Chaîne ? | Clé de mise à jour de cette fonctionnalité lorsqu’elle est disponible |
| `meta` | Chaîne ? | Métadonnées sous forme de chaîne JSON, le cas échéant |
| `analyticsParam` | AnalyticsParam ? | Détails Analytics pour la fonctionnalité évaluée |

*AnalyticsParam*

| Champ | Type | Description |
|---|---|---|
| `releaseId` | Int | Identifiant numérique de version |
| `featureId` | Int | Identifiant numérique de la caractéristique |
| `variantId` | Chaîne ? | Identifiant de la variante |

**Exemples**

*Kotlin*

```kotlin
import com.adobe.marketing.mobile.AdobeCallback
import com.adobe.marketing.mobile.rollout.FeatureEvaluationResult
import com.adobe.marketing.mobile.rollout.Rollout

Rollout.getFeature(
    "new-checkout-experience",
    ctx,
    object : AdobeCallback<FeatureEvaluationResult> {
        override fun call(feature: FeatureEvaluationResult?) {
            val meta = feature?.meta
            if (!meta.isNullOrEmpty()) {
                applyMetaDrivenExperience(meta)
            } else {
                showFallbackExperience()
            }
        }
    }
)
```

*Java*

```java
import com.adobe.marketing.mobile.AdobeCallback;
import com.adobe.marketing.mobile.rollout.FeatureEvaluationResult;
import com.adobe.marketing.mobile.rollout.Rollout;

Rollout.getFeature(
    "new-checkout-experience",
    ctx,
    new AdobeCallback<FeatureEvaluationResult>() {
        @Override
        public void call(FeatureEvaluationResult feature) {
            String meta = feature != null ? feature.getMeta() : null;
            if (meta != null && !meta.isEmpty()) {
                applyMetaDrivenExperience(meta);
            } else {
                showFallbackExperience();
            }
        }
    }
);
```

### refreshCache {#refresh-cache}

Par défaut, l’extension Experience Rollout synchronise régulièrement les dernières règles et fonctionnalités de déploiement du serveur selon un planning que vous pouvez configurer. Si vous avez besoin d’une mise à jour avant la prochaine synchronisation planifiée, appelez `refreshCache` pour forcer une actualisation. Les cas types incluent après la connexion ou lorsque l’état de l’application change d’une manière qui doit affecter le ciblage.

**Syntaxe**

*Kotlin*

```kotlin
Rollout.refreshCache()
```

*Java*

```java
Rollout.refreshCache();
```

### extensionVersion {#extension-version}

Renvoie la chaîne de version de l’extension Experience Rollout.

**Syntaxe**

```kotlin
Rollout.extensionVersion(): String
```

**Exemple**

*Kotlin*

```kotlin
val version = Rollout.extensionVersion()
```

*Java*

```java
String version = Rollout.extensionVersion();
```

## Résumé des API {#api-summary}

| API | Retours |
|---|---|
| `isFeatureEnabled(featureKey, evaluationContext, callback)`. `FeatureEvaluationContext` transporte les attributs de ciblage pour les règles et l’identité facultative pour les analyses. Voir [Évaluation des fonctionnalités](#is-feature-enabled). | Booléen via le rappel |
| `getFeature(featureKey, evaluationContext, callback)`. Renvoie la payload de fonction évaluée pour le contexte donné. Voir [getFeature](#get-feature). | FeatureEvaluationResult via le rappel |
| `refreshCache()` | vide |
| `extensionVersion()` | Chaîne |

## Voir également {#see-also}

* [Applications mobiles](../../integrate/mobile-applications.md)
* [Étapes d’intégration](../../integrate/integration-steps.md)
* [SDK](../../integrate/sdks.md)

<!-- -->
