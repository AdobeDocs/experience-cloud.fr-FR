---
title: Concept de déploiement automatisé
description: Découvrez le fonctionnement des déploiements automatisés dans Adobe Experience Rollouts, notamment les blocs de phase et les blocs d’attente, ainsi que la progression automatique du plan de déploiement.
source-git-commit: d824d85c6701edc9be314713bb8e9624b183e2d2
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 2%

---


# Concept de déploiement automatisé {#automated-rollout-concept}

Le déploiement automatisé vous permet de définir l’ensemble de votre plan de déploiement par phases en une seule fois. Au lieu de revenir manuellement à la console pour étendre votre audience pour chaque phase, vous configurez toutes les phases et leurs planifications au départ, et les déploiements d’expérience progressent automatiquement d’une phase à l’autre.

Les déploiements automatisés sont pris en charge pour les indicateurs de fonctionnalité, les groupes de fonctionnalités et les groupes de fonctionnalités interéquipes.

## Fonctionnement {#how-it-works}

Un plan de déploiement est constitué de **blocs de phase** et **blocs d’attente** exécutés en séquence :

* **Bloc de phase** — Définit les critères d’audience pour une phase du déploiement. Lorsque le plan atteint un bloc de phase, cette audience devient l’audience active de la fonctionnalité.
* **Bloc d&#39;attente** — Définit la pause entre deux blocs de phase. Un bloc d’attente peut être une durée relative (par exemple, « trois jours d’attente ») ou une date et une heure fixes.

Le plan commence lorsque vous publiez la fonction ou que vous la planifiez à une date ultérieure. Les déploiements d’expérience se déplacent automatiquement d’un bloc à l’autre en fonction du planning que vous avez configuré.

## Comportement du bloc de phase {#phase-block-behavior}

Chaque bloc de phase suivant est prérempli avec l’audience de la phase précédente. Il est ainsi plus facile de créer des déploiements à expansion incrémentielle où chaque nouvelle phase inclut tous les groupes d’audience précédents en plus de nouveaux.

>[!IMPORTANT]
>
>Les règles d’audience de chaque bloc de phase sont modifiables. Vous devez donc veiller à ne pas supprimer les critères d’audience des phases précédentes lorsque vous en ajoutez de nouveaux. La réduction de la portée de l’audience en milieu de déploiement peut entraîner une perte inattendue de l’accès à une fonctionnalité.

## États du plan de déploiement {#rollout-plan-states}

Une fois qu’un plan de déploiement est actif, il peut se trouver dans l’un des trois états suivants :

| État | Description |
|---|---|
| **En cours** | Le plan est en cours d’exécution. Un indicateur de progression dans la console indique quel bloc de phase est actuellement actif. Tous les blocs terminés sont verrouillés et ne peuvent pas être modifiés. |
| **En pause** | Le plan est en attente. L’audience du dernier bloc de phase terminé reste active. La phase future et les blocs d’attente peuvent toujours être modifiés alors qu’ils sont en pause. |
| **Abandonné** | Le plan a été arrêté définitivement. L’audience du dernier bloc de phase terminé reste active. Aucune autre modification du plan n’est autorisée. L&#39;abandon du plan ne désactive pas la fonctionnalité — vous devez modifier séparément l&#39;état de la fonctionnalité si vous voulez arrêter sa diffusion. |

## Voir également {#see-also}

* [Créer un déploiement automatisé](create-automated-rollout.md)
* [Surveiller et modifier un plan de déploiement](monitor-edit-rollout-plan.md)
* [Définir une fonctionnalité à déployer progressivement](../feature-flags/set-feature-gradual-rollout.md)
