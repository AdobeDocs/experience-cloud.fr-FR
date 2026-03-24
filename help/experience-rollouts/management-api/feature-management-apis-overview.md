---
title: Présentation des API de gestion des fonctionnalités
description: Présentation des API de gestion des déploiements d’expérience, qui vous permettent de créer, lire, mettre à jour et supprimer des indicateurs de fonctionnalité, des groupes de fonctionnalités et des versions par programmation.
source-git-commit: 6ecedbfc6c7de392f214f3f8f2e71aa18e1bacb9
workflow-type: tm+mt
source-wordcount: '284'
ht-degree: 0%

---


# Présentation des API de gestion des fonctionnalités {#feature-management-apis-overview}

Les API de gestion des déploiements d’expérience vous permettent de gérer les indicateurs de fonctionnalité, les groupes de fonctionnalités et les versions par programmation. Les équipes qui doivent automatiser les workflows ou intégrer des déploiements d’expérience dans des pipelines de déploiement existants peuvent utiliser ces API plutôt que la console.

>[!NOTE]
>
>L’accès aux API de gestion à l’aide d’un jeton de service est accordé sur demande. Contactez l’assistance des déploiements d’expérience et fournissez une justification commerciale pour demander l’accès.

## API de gestion disponibles {#available-apis}

Les API de gestion suivantes sont disponibles :

* [API Feature flags management](feature-flags-management-api.md) — Créez, lisez, mettez à jour et supprimez des indicateurs de fonctionnalité pour une application.
* [API Feature group management](feature-group-management-api.md) — Créez, lisez, mettez à jour, supprimez et contrôlez les plans de déploiement automatisé pour les groupes de fonctionnalités.
* [API Release Management](release-management-apis.md) — Créez et modifiez des groupes de fonctionnalités et des versions interéquipes.

## Exigences communes {#common-requirements}

Tous les appels de l’API de gestion nécessitent les éléments suivants :

* Une **clé API** du Adobe Developer Console — voir [S’abonner à l’application API](../guides/integrate/subscribe-to-api-application.md).
* Un **jeton d’accès utilisateur IMS** ou **jeton de service**, transmis comme `Bearer <token>` dans l’en-tête `Authorization`.
* En-tête `Content-Type: application/json`.

Les clés et jetons API doivent être configurés séparément pour les environnements d’évaluation et de production.

## Guides d’assistance {#helper-guides}

Les guides suivants permettent de créer des payloads d’API correctes :

* [Obtenir l’ID client pour une application](get-client-id.md) — Recherchez l’ID client numérique requis par les indicateurs de fonctionnalité et les API de gestion des groupes de fonctionnalités.
* [Obtenir les critères d’audience souhaités ](get-audience-criteria.md) — Utilisez la console et l’API GET pour générer la structure JSON de critères d’audience appropriée.
* [API Management Patch](management-patch-api.md) — Mettez à jour les champs individuels d&#39;un indicateur de fonctionnalité, d&#39;un groupe de fonctionnalités ou d&#39;un groupe de fonctionnalités interéquipes sans transmettre l&#39;objet complet.

## Voir également {#see-also}

* [API de fonctionnalités GET V3](../feature-api/get-feature-api-v3.md)
* [API de fonctionnalités GET V2](../feature-api/get-feature-api-v2.md)
* [S’abonner à l’application API](../guides/integrate/subscribe-to-api-application.md)
