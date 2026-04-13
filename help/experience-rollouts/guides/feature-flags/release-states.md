---
title: États de la version
description: Découvrez les états de cycle de vie d’une version dans les déploiements d’Adobe Experience, y compris la signification de chaque état et les transitions autorisées.
hide: true
exl-id: c1311353-9c36-43c5-8e75-3b3ee225da41
source-git-commit: 12032cbed45e694a3f25f16afe80308b3eb82924
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 3%

---

# États de la version {#release-states}

Un gestionnaire de versions peut mettre à jour l’état d’une version directement à partir de la barre de navigation de la console. L’état contrôle si la version est active, limitée aux tests, entièrement déployée ou fermée.

## États disponibles {#states}

| # | État | Description | Modifications autorisées |
|---|---|---|---|
| 1 | **Brouillon** | La version est enregistrée dans le système, mais n’est pas encore active. Aucune règle d’audience n’est appliquée. | Toutes les modifications autorisées (version, fonctionnalités, audience). |
| 2 | **enregistré** | La version est enregistrée et un emplacement lui est attribué. La version n’est pas encore visible pour les utilisateurs et utilisatrices. | Toutes les modifications sont autorisées. |
| 3 | **Publié** | La version est active pour l’audience spécifiée. Les utilisateurs répondant aux critères d’audience reçoivent les fonctionnalités. | Toutes les modifications sont autorisées. |
| 4 | **Déploiement complet** | La version est disponible pour tous les utilisateurs et utilisatrices, quelles que soient les règles d’audience. Toutes les règles d’audience sont supprimées. | Modifications de fonctionnalités autorisées. L’audience ne peut pas être modifiée. |
| 5 | **En ligne de base** | Tous les utilisateurs disposent désormais des fonctionnalités de cette version comme comportement par défaut. Le code conditionnel peut être supprimé. L&#39;emplacement de libération est libéré. | Aucune modification n’est autorisée. |
| 6 | **Abandonné** | La publication a été arrêtée. Aucun utilisateur ne reçoit de fonctionnalités de cette version. L&#39;emplacement de libération est libéré. | Aucune modification n’est autorisée. |

## Transitions autorisées {#transitions}

Toutes les transitions d’état ne sont pas autorisées. Comprendre les chemins autorisés vous permet de planifier votre déploiement et d’éviter les erreurs lors de la gestion des changements d’état :

* Une version peut passer d’un statut à l’autre : Brouillon → Enregistré → Publié → Déploiement complet → Déploiement de référence
* Une version peut être Abandonnée du brouillon, Enregistrée, Publiée ou Déploiement complet
* Une fois défini comme référence ou abandonné, aucune autre modification n&#39;est autorisée

## Capacité de publication {#capacity}

Le nombre de versions actives (enregistrées ou publiées) à tout moment est limité. Pour libérer de la capacité :

* Déplacez les versions terminées vers **Version de référence** une fois que toutes les applications participantes ont supprimé leur code conditionnel.
* **Abandon** versions qui ont échoué et ne seront pas poursuivies.

Planifiez la création ou l’abandon de vos versions dans les trois mois.

## Voir également {#see-also}

* [Demander une version](request-a-release.md)
* [Workflow de publication complet](release-workflow-end-to-end.md)
* [Mise à jour des règles d’audience de version](update-release-audience-rules.md)

<!-- -->
