---
title: Définir une fonctionnalité à déployer progressivement
description: Découvrez comment configurer un déploiement progressif en fonction d’un pourcentage pour un indicateur de fonctionnalité dans les déploiements d’Adobe Experience.
source-git-commit: 9bfe0e55e89c1d7fbd77cde63831a6a186820e24
workflow-type: tm+mt
source-wordcount: '148'
ht-degree: 3%

---


# Définir une fonctionnalité à déployer progressivement {#gradual-rollout-feature}

Le pourcentage de déploiement d’un indicateur de fonctionnalité est configuré dans l’onglet **Détails de base**. Vous pouvez ajuster cette valeur à la hausse ou à la baisse à tout moment au fur et à mesure du déploiement.

## Fonctionnement {#how-it-works}

Lorsque vous définissez un pourcentage de déploiement, par exemple 25 %, ce pourcentage de l’audience définie est exposé à la fonctionnalité. Le pourcentage restant est placé dans la **population témoin**, qui reçoit l’expérience par défaut.

Vous pouvez augmenter ou réduire le pourcentage au fil du temps pour développer ou réduire le déploiement. La réduction du pourcentage à 0 % désactive la fonctionnalité pour tous les membres de l’audience sans supprimer l’indicateur.

## Voir également {#see-also}

* [Déploiement graduel](../../concepts/gradual-rollout.md)
* [Définir un groupe de fonctionnalités à déployer progressivement](set-feature-group-gradual-rollout.md)
* [Créer votre premier indicateur de fonctionnalité](create-your-first-feature-flag.md)
