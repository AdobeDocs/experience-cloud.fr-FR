---
title: Fonctionnalités et groupes de fonctionnalités
description: Découvrez les différences entre les indicateurs de fonctionnalité et les groupes de fonctionnalités dans les déploiements d’Adobe Experience et quand les utiliser.
source-git-commit: c654ca1507abcefcff84cef9f99830042939805d
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 5%

---


# Fonctionnalités et groupes de fonctionnalités {#features-feature-groups}

Déploiements d’expérience fournit deux artefacts pour la gestion des déploiements de fonctionnalités. Le choix de la bonne dépend de la portée de votre déploiement et du nombre de fonctionnalités impliquées.

## Les deux artefacts {#artifacts}

**Indicateur de fonctionnalité**
Unité la plus atomique. Contrôle une fonctionnalité unique pour une application unique. Peut être activé ou désactivé pour une audience définie.

**Groupe de fonctionnalités**
Ensemble d&#39;indicateurs de fonctionnalités appartenant à la même équipe. Permet de gérer plusieurs indicateurs dans plusieurs applications en une seule unité.

## Comparaison {#comparison}

| | Indicateur de fonctionnalité | Groupe de fonctionnalités |
|---|---|---|
| **Rôle requis pour gérer l’audience** | Propriétaire de la version de produit | Propriétaire de la version de produit |
| **Applications** | Célibataire | Multiple (même équipe) |
| **Critères d’audience riches** | ✓ | ✓ |
| **Pourcentage de déploiement** | Combiné avec n’importe quel critère d’audience | Combiné avec n’importe quel critère d’audience |
| **Tests AB** | ✓ | ✓ |
| **Libre-service** | ✓ | ✓ |
| **Journal d’audit** | ✓ | ✓ |

## Quand utiliser chaque {#when-to-use}

| Scénario | Utilisation |
|---|---|
| Test ou déploiement d’une fonctionnalité unique pour une application | **Indicateur de fonctionnalité** |
| Coordination de plusieurs fonctionnalités au sein d’une même équipe, activation en même temps | **Groupe de fonctionnalités** |

## Voir également {#see-also}

* [Créer votre premier indicateur de fonctionnalité](create-your-first-feature-flag.md)
* [Créer un groupe de fonctionnalités](create-a-feature-group.md)
