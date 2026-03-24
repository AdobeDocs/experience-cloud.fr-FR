---
title: Surveiller et modifier un plan de déploiement
description: Découvrez comment suivre la progression d’un plan de déploiement automatisé dans les déploiements d’Adobe Experience et comment suspendre, reprendre ou abandonner un plan en cours.
source-git-commit: d824d85c6701edc9be314713bb8e9624b183e2d2
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 0%

---


# Surveiller et modifier un plan de déploiement {#monitor-edit-rollout-plan}

Une fois qu’un déploiement automatisé est actif, vous pouvez suivre sa progression et intervenir si nécessaire. Cette page décrit comment lire l&#39;indicateur de progression, mettre en pause et reprendre un plan, puis l&#39;abandonner si nécessaire.

Cette page suppose que vous avez déjà créé et publié un plan de déploiement. Voir [Créer un déploiement automatisé](create-automated-rollout.md) si vous n’en avez pas encore configuré un.

## Afficher la progression du déploiement {#view-progress}

Une fois que l’exécution du plan de déploiement a commencé, ouvrez l’onglet **Audience** de la fonctionnalité pour afficher l’état actuel du plan. Le plan affiche un indicateur de progression qui signale le bloc de phase actuellement actif.

Utilisez l’indicateur de progression pour comprendre les éléments suivants :

* **Blocs terminés** — Tous les blocs de phase et d&#39;attente au-dessus de l&#39;indicateur ont été exécutés. Ces blocs sont verrouillés et ne peuvent pas être modifiés.
* **Bloc actuel** — Le bloc actuellement mis en surbrillance est la phase active ou la période d&#39;attente.
* **Blocs à venir** — Tous les blocs de phase et d&#39;attente situés sous l&#39;indicateur ne sont pas encore exécutés. Ils peuvent toujours être modifiés.

## Suspendre un plan de déploiement {#pause}

Pour suspendre le déploiement à tout moment pendant qu’il est en cours, sélectionnez **Pause du déploiement** dans la console.

Lorsque le plan est suspendu :

* L’audience du dernier bloc de phase terminé reste active. Les utilisateurs et utilisatrices de cette audience continuent à recevoir la fonctionnalité.
* L&#39;indicateur de fonction, le groupe de fonctions ou le groupe de fonctions interéquipes reste dans son état actuel activé ou publié. Il continue à proposer la fonctionnalité à l’audience active actuelle.
* La phase à venir et les blocs d’attente restent modifiables.

Pour reprendre une planification en pause, sélectionnez **Reprendre le déploiement**. Le plan se poursuit là où il s&#39;est arrêté.

## Abandon d’un plan de déploiement {#abort}

Pour arrêter définitivement le plan de déploiement, sélectionnez **Abandonner le déploiement** dans la console.

Lorsque le plan est abandonné :

* L’audience du dernier bloc de phase terminé reste active et la fonctionnalité continue d’être diffusée à cette audience.
* La fonction elle-même n&#39;est pas désactivée : si vous voulez arrêter complètement la diffusion de la fonction, vous devez abandonner séparément la publication ou désactiver l&#39;indicateur ou le groupe de fonction.
* La phase à venir et les blocs d’attente ne peuvent plus être modifiés.
* Un plan abandonné ne peut pas être repris.

>[!IMPORTANT]
>
>L’abandon d’une procédure de déploiement ne désactive pas automatiquement la fonction. Effectuez une action distincte sur l’état de la fonctionnalité si vous souhaitez arrêter sa diffusion aux utilisateurs.

## Modifier les blocs de phase à venir {#edit-upcoming}

Pendant que le plan est en cours (ou en pause), vous pouvez toujours modifier toute phase ou tout bloc d’attente qui n’a pas encore été exécuté :

* Ajustez les règles ou le pourcentage d’audience pour un bloc de phase à venir.
* Modifier la durée ou la date fixe d&#39;un bloc d&#39;attente à venir.

Les blocs terminés sont verrouillés et ne peuvent pas être modifiés.

## Voir également {#see-also}

* [Créer un déploiement automatisé](create-automated-rollout.md)
* [Concept de déploiement automatisé](automated-rollout-concept.md)
* [États de la version](../feature-flags/release-states.md)
