---
title: Planning
description: Découvrez comment planifier l’activation automatique d’un indicateur de fonctionnalité, d’un groupe de fonctionnalités ou d’un groupe de fonctionnalités interéquipes à une date et une heure ultérieures dans les déploiements d’Adobe Experience.
source-git-commit: d311efb995b20ffc17370d68d57dd84a8605896c
workflow-type: tm+mt
source-wordcount: '289'
ht-degree: 2%

---


# Planning {#schedule}

La planification est une fonction facultative qui vous permet de définir une date et une heure futures pour l&#39;activation automatique d&#39;un indicateur de fonction, d&#39;un groupe de fonctions ou d&#39;un groupe de fonctions interéquipes. L’activation/désactivation manuelle reste disponible et ne doit pas être remplacée par une planification.

La planification est prise en charge pour les éléments suivants :

* Indicateurs de fonctionnalités
* Groupes de fonctionnalités
* Groupes de fonctionnalités multi-équipes (planifie la transition vers l’état **Publication**)

## Étape 1 : définir le planning {#set-schedule}

1. Ouvrez l&#39;indicateur de fonctionnalité, le groupe de fonctionnalités ou le groupe de fonctionnalités interéquipes dans la console.
2. Sélectionnez le bouton **Planifier** sur le côté droit de l’écran.
3. Dans le pop-up, définissez la **date et heure de début** puis sélectionnez le **fuseau horaire**.

## Étape 2 : enregistrer {#save}

Sélectionnez **Définir le planning**, puis enregistrez les paramètres. Le planning ne prend effet que lorsque vous enregistrez.

## Après la définition d’un planning {#after-schedule-set}

Une fois enregistrées, la date et l&#39;heure planifiées apparaissent dans l&#39;indicateur de fonctionnalité ou dans la vue du groupe de fonctionnalités.

Si vous tentez d’activer/désactiver manuellement l’état alors qu’un planning est actif, un avertissement s’affiche vous demandant si vous souhaitez remplacer le planning ou annuler l’action.

## À la date et à l’heure planifiées {#on-schedule}

A l&#39;heure planifiée, l&#39;indicateur de fonctionnalité ou le groupe de fonctionnalités est automatiquement activé (passe à l&#39;état ACTIVÉ). Pour les groupes de fonctionnalités inter-équipes, l’état passe à **Publié**.

Une fois le planning déclenché, le bouton **Planifier** est désactivé. Les planifications ne peuvent être définies que lorsque l&#39;indicateur de fonctionnalité ou le groupe de fonctionnalités est à l&#39;état désactivé (ou enregistré, pour les groupes de fonctionnalités interéquipes).

## Voir également {#see-also}

* [Créer votre premier indicateur de fonctionnalité](create-your-first-feature-flag.md)
* [Créer un groupe de fonctionnalités](create-a-feature-group.md)
* [Créer un groupe de fonctionnalités multi-équipes](create-cross-team-feature-group.md)
