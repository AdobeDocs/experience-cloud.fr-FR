---
title: Définir un groupe de fonctionnalités à déployer progressivement
description: Découvrez comment configurer un déploiement progressif en fonction d’un pourcentage pour un groupe de fonctionnalités dans les déploiements d’Adobe Experience.
hide: true
exl-id: fcf187f1-2f33-4e3a-b740-985d5bc0bcdc
source-git-commit: 12032cbed45e694a3f25f16afe80308b3eb82924
workflow-type: tm+mt
source-wordcount: '166'
ht-degree: 3%

---

# Définir un groupe de fonctionnalités à déployer progressivement {#gradual-rollout-feature-group}

Le pourcentage de déploiement d’un groupe de fonctionnalités est configuré dans l’onglet **Détails de base**. Vous pouvez ajuster cette valeur à la hausse ou à la baisse à tout moment au fur et à mesure du déploiement.

## Fonctionnement {#how-it-works}

Lorsque vous définissez un pourcentage de déploiement, par exemple 60 %, ce pourcentage de l’audience définie est exposé au groupe de fonctionnalités. Les 40 % restants sont placés dans la **population témoin**, qui reçoit le comportement par défaut.

Si vous avez configuré plusieurs variantes (pour les tests A/B), le pourcentage d’exposition est réparti de manière égale entre les variantes. Par exemple, une exposition de 60 % avec trois variants donne 20 % par variante, dont 40 % dans le groupe témoin.

Vous pouvez augmenter ou réduire le pourcentage à tout moment pour développer, réduire ou suspendre le déploiement.

## Voir également {#see-also}

* [Créer un groupe de fonctionnalités](create-a-feature-group.md)
* [Test A/B avec indicateurs de fonctionnalité](a-b-testing.md)
* [Déploiement graduel](../../concepts/gradual-rollout.md)

<!-- -->
