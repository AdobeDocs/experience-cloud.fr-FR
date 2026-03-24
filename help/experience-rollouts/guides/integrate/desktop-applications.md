---
title: Applications de bureau
description: Découvrez comment intégrer des déploiements d’Adobe Experience dans une application de bureau à l’aide de l’API Feature V2.
source-git-commit: b82520eebe0070b5f76e0f7daeb2bb79a4bccca0
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 2%

---


# Applications de bureau {#desktop-applications}

Les applications de bureau s’intègrent aux déploiements d’expérience en effectuant des appels API REST directs. Utilisez l’API **Feature API V2** pour les clients de bureau.

Voir **API de fonctionnalités GET V2** dans la section API de fonctionnalités de ce guide pour la référence complète de l’API.

## Exigences d’intégration {#requirements}

Les clients de bureau doivent :

* **Respectez la valeur de durée de vie** renvoyée dans la réponse de l’API. La TTL définit la durée pendant laquelle le client doit mettre en cache les données d’indicateur de fonctionnalité avant d’appeler à nouveau l’API. Implémentez un cas de test qui valide ce comportement pour s’assurer que les anciennes versions de l’application entrent correctement en veille lorsqu’aucun indicateur de fonctionnalité n’est diffusé.
* **Gérez les scénarios d’erreur HTTP de manière élégante**. Créez un ensemble de fonctionnalités de secours afin que l’application reste fonctionnelle en cas d’indisponibilité temporaire de l’API.
* **Maintenez un plan de test d’intégration détaillé** qui couvre à la fois la durée de vie et les exigences de gestion des erreurs ci-dessus.

## ID de l’application {#app-id}

Les clients de bureau peuvent utiliser un **code de produit et version du produit** comme identifiant de l’application lors de l’appel de l’API, au lieu d’un identifiant client standard.

## Voir également {#see-also}

* [Étapes d’intégration](integration-steps.md)
* [Guide de démarrage](startup-guide.md)
