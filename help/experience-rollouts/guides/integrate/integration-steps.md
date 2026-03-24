---
title: Étapes d’intégration
description: Suivez les étapes d’intégration de votre type d’application pour connecter les déploiements d’Adobe Experience à votre service web, application web ou mobile ou application de bureau.
source-git-commit: b82520eebe0070b5f76e0f7daeb2bb79a4bccca0
workflow-type: tm+mt
source-wordcount: '220'
ht-degree: 3%

---


# Étapes d’intégration {#integration-steps}

Choisissez le chemin d’intégration correspondant à votre type d’application.

## Services Web {#web-services}

Les services principaux s’intègrent à l’aide d’un SDK côté serveur. Choisissez le SDK pour votre pile technologique.

**Java**

Suivez le guide d’intégration [Java SDK](../sdk-releases/java/java-sdk-integration-guide.md) pour la configuration, la configuration des dépendances et l’initialisation.

**Node.js**

Suivez le [guide d’intégration de SDK Node.js](../sdk-releases/nodejs/nodejs-sdk-integration-guide.md) pour la configuration et l’initialisation.

**Autres langues**

Si votre pile n’est pas répertoriée ci-dessus, intégrez directement à la **API de fonctionnalités V3** (voir la section API de fonctionnalités de ce guide). Contactez l’assistance des déploiements d’expérience si vous avez besoin de conseils.

## Applications web et mobiles {#web-mobile}

Les applications web et mobiles appellent la **API de fonctionnalité V3** pour récupérer les indicateurs de fonctionnalité de l’utilisateur actuel et appliquer une logique conditionnelle dans l’application.

Voir **API de fonctionnalités GET V3** dans la section API de fonctionnalités de ce guide pour la référence complète de l’API.

## Applications de bureau {#desktop}

Les applications de bureau appellent la **API de fonctionnalité V2** pour récupérer les indicateurs de fonctionnalité.

Voir **API de fonctionnalités GET V2** dans la section API de fonctionnalités de ce guide pour la référence complète de l’API.

>[!IMPORTANT]
>
>Les clients de bureau doivent respecter la valeur de durée de vie dans la réponse API et implémenter une gestion des erreurs adaptée en cas d’indisponibilité de l’API. Consultez [Applications de bureau](desktop-applications.md) pour connaître la configuration requise.

## Voir également {#see-also}

* [Guide de démarrage](startup-guide.md)
* [SDK](sdks.md)
* [Services Web](web-services.md)
* [Applications de bureau](desktop-applications.md)
