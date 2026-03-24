---
title: Fonctionnalités, groupes de fonctionnalités et versions
description: Découvrez les différences entre les indicateurs de fonctionnalité, les groupes de fonctionnalités, les groupes de fonctionnalités inter-équipes et les versions dans les déploiements d’Adobe Experience et quand utiliser chacun d’eux.
source-git-commit: d311efb995b20ffc17370d68d57dd84a8605896c
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 2%

---


# Fonctionnalités, groupes de fonctionnalités et versions {#features-feature-groups-releases}

Les déploiements d’expérience fournissent quatre artefacts pour la gestion des déploiements de fonctionnalités. Le choix de la bonne dépend de la portée de votre déploiement, du nombre d’équipes impliquées et des fonctionnalités de ciblage d’audience dont vous avez besoin.

## Les quatre artefacts {#artifacts}

**Indicateur de fonctionnalité**
Unité la plus atomique. Contrôle une fonctionnalité unique pour une application unique, détenue par une seule équipe. Peut être activé ou désactivé pour une audience définie.

**Groupe de fonctionnalités**
Ensemble d&#39;indicateurs de fonctionnalités appartenant à la même équipe. Permet de gérer plusieurs indicateurs dans plusieurs applications d&#39;une même équipe en tant qu&#39;unité unique.

**Groupe de fonctionnalités multi-équipes**
Étend les fonctionnalités du groupe de fonctionnalités à plusieurs équipes et applications. Se sert lui-même et prend en charge les critères d’audience enrichis, mais ne prend pas en charge la mise en cache.

**Version**
Conçu pour les déploiements importants et coordonnés entre plusieurs équipes et applications. Utilise le ciblage d’audience basé sur les jetons d’authentification. Prend en charge la mise en cache sur le serveur SDK.

## Comparaison {#comparison}

| | Indicateur de fonctionnalité | Groupe de fonctionnalités | Groupe de fonctionnalités multi-équipes | Libération |
|---|---|---|---|---|
| **Rôle requis pour gérer l’audience** | Propriétaire de la version de produit | Propriétaire de la version de produit | Administrateur de fonctionnalités | Gestionnaire de version |
| **Applications** | Célibataire | Multiple (même équipe) | Multiple (cross-team) | Multiple (cross-team) |
| **Équipes** | Célibataire | Célibataire | Équipe croisée | Équipe croisée |
| **Critères d’audience riches** | ✓ | ✓ | ✓ | Limité |
| **Pourcentage de déploiement** | Combiné avec n’importe quel critère d’audience | Combiné avec n’importe quel critère d’audience | Combiné avec n’importe quel critère d’audience | Combiné avec des critères d’audience fixes |
| **Tests AB** | ✓ | ✓ | ✗ | ✗ |
| **Mise en cache dans le SDK du serveur** | Indicateurs on/off par défaut uniquement | Pas de mise en cache | Pas de mise en cache | Toutes les versions sont mises en cache localement |
| **Libre-service** | ✓ | ✓ | ✓ | Demande d’assistance requise |
| **Journal d’audit** | ✓ | ✓ | ✓ | ✓ |

## Quand utiliser chaque {#when-to-use}

| Scénario | Utilisation |
|---|---|
| Test ou déploiement d’une fonctionnalité unique pour une application | **Indicateur de fonctionnalité** |
| Coordination de plusieurs fonctionnalités au sein d’une même équipe, activation en même temps | **Groupe de fonctionnalités** |
| Coordination des fonctionnalités entre les applications de différentes équipes, avec un ciblage riche | **Groupe de fonctionnalités multi-équipes** |
| Mise à jour coordonnée à grande échelle entre plusieurs équipes, avec mise en cache au niveau du SDK | **Version** |

## Voir également {#see-also}

* [Créer votre premier indicateur de fonctionnalité](create-your-first-feature-flag.md)
* [Créer un groupe de fonctionnalités](create-a-feature-group.md)
* [Créer un groupe de fonctionnalités multi-équipes](create-cross-team-feature-group.md)
* [Versions et groupes de fonctionnalités interéquipes](releases-and-cross-team-feature-groups.md)
