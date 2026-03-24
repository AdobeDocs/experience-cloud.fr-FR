---
title: Guide d’intégration de Node.js SDK
description: Découvrez comment intégrer le SDK Node.js de déploiements d’expérience dans votre service principal pour récupérer et évaluer les indicateurs de fonctionnalité.
source-git-commit: 9bfe0e55e89c1d7fbd77cde63831a6a186820e24
workflow-type: tm+mt
source-wordcount: '254'
ht-degree: 2%

---


# Guide d’intégration de Node.js SDK {#nodejs-sdk-integration-guide}

Le SDK Node.js de déploiements d’expérience est une bibliothèque côté serveur destinée aux services Node.js. Il met en cache les données d’indicateur de fonctionnalité localement et évalue les indicateurs sans appel API synchrone à chaque requête.

>[!NOTE]
>
>Le SDK Node.js est conçu pour une utilisation côté serveur uniquement. Pour les applications web côté client, appelez directement le point d’entrée REST V3 de l’API Feature.

## Conditions préalables {#prerequisites}

Avant d’intégrer le SDK Node.js, vérifiez que vous disposez des éléments suivants :

* Une application Node.js côté serveur
* Une **clé API** et un **jeton de service** obtenus via Adobe Developer Console — voir [S’abonner à l’application API](../../integrate/subscribe-to-api-application.md)
* Votre **ID de client de l’application** enregistré dans la console Déploiements d’expérience ; voir [Intégration de votre application](../../applications/onboard-your-application.md)

## Installation du SDK {#install}

Ajoutez le SDK au `package.json` de votre projet :

```json
"@floodgate/fg-client-sdk": "~1.0.10"
```

Ensuite, exigez-le dans votre code :

```javascript
const { floodgateClient } = require('@floodgate/fg-client-sdk');
```

## Initialiser le SDK {#initialize}

Appelez une `createInstance()` fois au démarrage de l’application :

```javascript
floodgateClient.createInstance(
  {
    adobeIoApiKey: "<YOUR_API_KEY>",
    clientIds: ["<CLIENT_ID_1>", "<CLIENT_ID_2>"],
    env: "PRD",    // Use "STG" for Stage
    featureRequestHttpParams: {
      timeout: 60 * 1000  // Optional: request timeout in ms
    },
    ingestAnalyticsHttpParams: {
      timeout: 5 * 1000   // Optional: analytics timeout in ms
    }
  },
  function(cb) {
    // Fetch a fresh service token from IMS and pass it in the callback
    cb(null, SERVICE_TOKEN);
  },
  function() {
    return true;  // Return false to disable analytics
  },
  function(response) {
    // Called when the SDK initializes successfully
    console.log("SDK initialized");
  },
  function(err) {
    // Called if initialization fails
    console.error("SDK init error:", err);
  }
);
```

## Récupération des indicateurs de fonctionnalité {#retrieve-features}

Les indicateurs de fonctionnalité sont renvoyés de manière asynchrone dans un rappel . Choisissez la méthode appropriée en fonction de votre contexte utilisateur.

### Utilisateur authentifié {#authenticated-user}

```javascript
floodgateClient.getFeatures(
  {
    userAccessToken: "<USER_ACCESS_TOKEN>",
    visitorId: "<VISITOR_ID>",
    clientId1: "<CLIENT_ID>",
    meta: true
  },
  function(err, features) {
    if (err) {
      // Handle error and serve default experience
      return;
    }
    const isEnabled = floodgateClient.isFeatureEnabled(features, "MY_FEATURE_FLAG");
    // Serve experience based on isEnabled
  }
);
```

### Utilisateur anonyme {#anonymous-user}

Lorsqu’aucun jeton d’accès utilisateur n’est disponible, utilisez un indicateur de version ou omettez le jeton pour recevoir les versions entièrement déployées :

```javascript
floodgateClient.getFeatures(
  {
    releaseFlag: "<RELEASE_FLAG>",
    visitorId: "<VISITOR_ID>",
    clientId1: "<CLIENT_ID>",
    meta: false
  },
  callback
);
```

### Versions du déploiement complet par défaut {#default-releases}

Lorsqu’aucun jeton d’accès ni indicateur de version n’est fourni, le SDK renvoie les fonctionnalités à l’état **Déploiement complet** ou **Ligne de base** :

```javascript
floodgateClient.getFeatures(
  {
    clientId1: "<CLIENT_ID>",
    visitorId: "<VISITOR_ID>",
    meta: false
  },
  callback
);
```

## Vérifier si une fonctionnalité est activée {#check-feature}

```javascript
const isEnabled = floodgateClient.isFeatureEnabled(features, "MY_FEATURE_FLAG");

if (isEnabled) {
  // Serve the new experience
} else {
  // Serve the default experience
}
```

## Activer la journalisation du débogage {#debug-logging}

Pour activer les journaux SDK détaillés, transmettez une instance d’enregistreur au niveau du débogage lors de l’appel de `createInstance()` :

```javascript
const bunyan = require('bunyan');
const logger = bunyan.createLogger({ name: "fg", sourceType: "SDK", level: "debug" });

floodgateClient.createInstance(
  { ..., log: logger },
  ...
);
```

## Voir également {#see-also}

* [Notes de mise à jour de Node.js SDK](nodejs-sdk-release-notes.md)
* [SDK](../../integrate/sdks.md)
* [S’abonner à l’application API](../../integrate/subscribe-to-api-application.md)
* [Étapes d’intégration](../../integrate/integration-steps.md)
