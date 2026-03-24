---
title: Versions et groupes de fonctionnalités interéquipes
description: Découvrez la différence entre les versions et les groupes de fonctionnalités inter-équipes dans les déploiements d’Adobe Experience et quand les utiliser pour des déploiements multi-équipes coordonnés.
source-git-commit: d311efb995b20ffc17370d68d57dd84a8605896c
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 2%

---


# Versions et groupes de fonctionnalités interéquipes {#releases-and-cross-team}

Les versions et les groupes de fonctionnalités interéquipes prennent en charge le déploiement coordonné entre plusieurs équipes et applications. Le bon choix dépend de vos exigences de mise en cache, de vos besoins en matière de ciblage des audiences et du contrôle que vous souhaitez exercer sur le processus.

## Groupes de fonctionnalités multi-équipes {#cross-team-feature-groups}

Un groupe de fonctionnalités multi-équipes vous permet de regrouper des indicateurs de fonctionnalités provenant d’applications détenues par différentes équipes et de les gérer avec des critères d’audience riches.

Caractéristiques principales :

* **Libre-service** — Aucune demande d&#39;assistance requise pour en créer une
* **Ciblage d’audience riche** — Prend en charge l’ensemble complet des critères d’audience (attributs de profil, variables contextuelles, déploiement en pourcentage)
* **Aucune limite** sur le nombre que vous pouvez créer
* **Pas de mise en cache** — Les évaluations des indicateurs de fonctionnalité nécessitent un appel API ; la mise en cache au niveau du SDK n’est pas prise en charge

Pour obtenir des instructions détaillées sur la création d&#39;un groupe de fonctionnalités [Création d&#39;un groupe de fonctionnalités interéquipes](create-cross-team-feature-group.md).

## Versions {#releases}

Une version est conçue pour les lancements volumineux et coordonnés où la mise en cache au niveau du SDK est requise. Les versions utilisent le ciblage d’audience basé sur les jetons d’authentification.

Caractéristiques principales :

* **Nécessite une demande d’assistance** — Les versions ne sont pas entièrement en libre-service ; contactez l’assistance des déploiements d’expérience pour en créer une
* **Mise en cache de SDK** — Toutes les données de version sont mises en cache localement dans le SDK du serveur, ce qui réduit les appels API
* **Critères d’audience limités** — Les règles d’audience sont basées sur des jetons d’authentification (pays, e-mail, ID utilisateur, pourcentage, etc.)
* **Rejets actifs limités** — Un nombre fini de rejets actifs peut exister à la fois ; prévoyez de fermer les rejets ou les rejets de référence dans les trois mois

## Comparaison {#comparison}

| | Groupe de fonctionnalités multi-équipes | Libération |
|---|---|---|
| Libre-service | ✓ | Demande d’assistance requise |
| Critères d’audience riches | ✓ | Limité |
| Tests A/B | ✗ | ✗ |
| Mise en cache du SDK | ✗ | ✓ |
| Limite active | Aucune limite | Limité |

## Recommandation {#recommendation}

Si votre cas d’utilisation implique un ciblage d’audience riche et une gestion en libre-service, utilisez un **groupe de fonctionnalités multi-équipes**. Si vos services principaux nécessitent une mise en cache au niveau du SDK et que les critères d’audience plus simples des versions sont suffisants, utilisez une **version**.

## Voir également {#see-also}

* [Fonctionnalités, groupes de fonctionnalités et versions](features-feature-groups-releases.md)
* [Créer un groupe de fonctionnalités multi-équipes](create-cross-team-feature-group.md)
* [Demander une version](request-a-release.md)
