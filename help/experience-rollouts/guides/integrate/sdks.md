---
title: SDK
description: Découvrez l’architecture de SDK dans les déploiements d’Adobe Experience et les SDK disponibles pour Java et Node.js.
exl-id: 110a440d-b52a-4e1e-a94f-86f9741a223a
source-git-commit: 2a946868f58e25f8aafbf3ccfcf6571e7d0d8d20
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 2%

---

# SDK {#sdks}

Les déploiements d’expérience fournissent des SDK côté serveur pour l’intégration du service principal. Cette page décrit l’architecture de SDK et les options disponibles.

## Architecture de SDK {#architecture}

Tous les SDK de déploiement d’Experience partagent la même architecture principale :

* **Initialisation** — Le SDK est configuré via un appel `createInstance()` qui renvoie un objet singleton.
* **Récupération de fonctionnalités** — La méthode `getFeatures()` récupère les données d&#39;indicateur de fonctionnalité du SDK.
* **Mise en cache** — Le SDK met en cache les réponses du service de déploiements d’expérience. Un gestionnaire de cache actualise le cache selon un intervalle d’interrogation configurable (TTL).
* **Gestion des erreurs** — Si le service renvoie un 503, le gestionnaire de cache conserve les données mises en cache existantes et continue de fournir des évaluations d’indicateur de fonctionnalité. Si les données n&#39;ont pas changé depuis le dernier appel (304), le cache n&#39;est pas mis à jour.

## Conditions préalables {#prerequisites}

Avant d’intégrer un SDK, vérifiez que vous disposez des éléments suivants :

1. **ID de l’application** — L’ID client pour chaque application intégrée à la console Déploiements d’expérience.
2. **Jeton de service** : utilisé par le SDK pour appeler les API de déploiements d’expérience en arrière-plan.
3. **Clé API** — Utilisé avec le jeton de service pour l&#39;authentification API.

## SDK disponibles {#available-sdks}

### SDK Java {#java-sdk}

Le SDK Java est distribué via Maven. Ajoutez la dépendance au `pom.xml` de votre projet à intégrer. Pour les applications basées sur Spring, la dépendance Maven configure automatiquement le cache de SDK avant que votre application ne se charge complètement.

Spécifications clés pour Java SDK :

* **JDK pris en charge :** JDK 8 et versions ultérieures
* **Clients non pouvant être mis en cache :** pris en charge à partir de la version 0.8 de SDK. Pour les clients qui ne peuvent pas être mis en cache, `getFeature()` effectue un appel API en direct au lieu de lire depuis le cache. Le SDK poursuit l’interrogation en arrière-plan et passe au service basé sur la mise en cache si le client peut être mis en cache.

Pour obtenir des instructions de configuration, consultez le [guide d’intégration de Java SDK](../sdk-releases/java/java-sdk-integration-guide.md).

### Node.js SDK {#nodejs-sdk}

Le SDK Node.js est distribué via npm.

Pour obtenir des instructions de configuration, consultez le [guide d’intégration de SDK Node.js](../sdk-releases/nodejs/nodejs-sdk-integration-guide.md).

## Voir également {#see-also}

* [Services Web](web-services.md)
* [Étapes d’intégration](integration-steps.md)
* [Guide d’intégration de Java SDK](../sdk-releases/java/java-sdk-integration-guide.md)
* [Guide d’intégration de Node.js SDK](../sdk-releases/nodejs/nodejs-sdk-integration-guide.md)
