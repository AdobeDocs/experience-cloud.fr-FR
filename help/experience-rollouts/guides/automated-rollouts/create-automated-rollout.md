---
title: Créer un déploiement automatisé
description: Découvrez comment configurer un plan de déploiement automatisé dans Déploiements d’Adobe Experience avec des blocs de phase et des blocs d’attente afin que votre audience s’étende automatiquement au fil du temps.
source-git-commit: d824d85c6701edc9be314713bb8e9624b183e2d2
workflow-type: tm+mt
source-wordcount: '522'
ht-degree: 0%

---


# Créer un déploiement automatisé {#create-automated-rollout}

Un déploiement automatisé vous permet de définir toutes les phases de déploiement et leurs planifications en une seule session. Les déploiements d’expérience passent automatiquement d’une phase à l’autre, sans que vous ayez à revenir à la console à chaque étape. Consultez [Concept de déploiement automatisé](automated-rollout-concept.md) pour une vue d’ensemble.

Les déploiements automatisés sont pris en charge pour les indicateurs de fonctionnalité, les groupes de fonctionnalités et les groupes de fonctionnalités interéquipes.

## Étape 1 : activer le déploiement automatisé {#enable-automated-rollout}

Lors de la création d&#39;un indicateur de fonctionnalité, d&#39;un groupe de fonctionnalités ou d&#39;un groupe de fonctionnalités interéquipes, ouvrez l&#39;onglet **Détails de base** et recherchez l&#39;option **Sélectionner le type de déploiement**. La valeur par défaut est **Manuel**. Pour activer un plan de déploiement automatisé, sélectionnez **Déploiement automatisé**.

>[!NOTE]
>
>Lorsque vous sélectionnez Déploiement automatisé, le champ Pourcentage de déploiement dans Détails de base est automatiquement défini sur 100 % et devient non modifiable. Vous pouvez contrôler le pourcentage de chaque phase individuellement dans l’onglet Audience .

## Étape 2 : création du plan de déploiement {#build-rollout-plan}

Ouvrez l’onglet **Audience** et activez le bouton (bascule) **Phases**. Cette action active les commandes **Ajouter un bloc de phase** et **Ajouter un bloc d’attente**.

Pour élaborer votre plan de déploiement, ajoutez des blocs de phase et d’attente dans l’ordre dans lequel vous souhaitez qu’ils s’exécutent :

### Ajouter un bloc de phase {#add-phase-block}

Un bloc de phase définit les critères d’audience pour une phase du déploiement. Le premier bloc de phase est configuré à l’aide des critères d’audience déjà sur la page. Pour chaque bloc de phase suivant, l’audience de la phase précédente est préremplie comme point de départ.

Configurez l’audience pour chaque bloc de phase :

* **Pourcentage** — Définissez le pourcentage de l&#39;audience définie qui reçoit la fonction au cours de cette phase.
* **Règles d’audience** — Ajoutez des règles basées sur un profil, un contexte ou un segment pour cibler des utilisateurs spécifiques.

>[!IMPORTANT]
>
>Chaque phase suivante doit développer l’audience de la phase précédente, et non la remplacer. Ne supprimez pas les règles d’audience des phases précédentes lorsque vous configurez des phases ultérieures, car cela peut exclure par inadvertance les utilisateurs qui recevaient déjà la fonctionnalité.

### Ajouter un bloc d’attente {#add-wait-block}

Un bloc d’attente définit la pause entre deux blocs de phase. Après avoir ajouté un bloc d’attente, sélectionnez l’une des options suivantes :

| Option | Description |
|---|---|
| **Attente** | Une durée relative ; par exemple, attendez 2 jours et 4 heures. Une fois cette durée écoulée, les déploiements d’expérience passent au bloc de phase suivant. |
| **Attendre** | Une date et une heure fixes. Les déploiements d’expérience passent au bloc de phase suivant au moment spécifié. |

### Ajouter les blocs de phase suivants {#add-subsequent-phases}

Répétez le processus pour ajouter des blocs de phase supplémentaires et des blocs d’attente jusqu’à ce que votre plan de déploiement complet soit configuré.

## Étape 3 : planifier ou publier le déploiement {#schedule-or-publish}

Une fois le plan de déploiement terminé, choisissez le mode d’activation :

* **Planification** — Définissez une date et une heure futures pour que le déploiement démarre automatiquement. Voir [Planification](../feature-flags/schedule.md) pour plus de détails.
* **Publier manuellement** — Activez l&#39;indicateur de fonctionnalité ou déplacez le groupe de fonctionnalités vers l&#39;état **Publier** pour démarrer immédiatement.

Le plan commence à s’exécuter à partir du premier bloc de phase. Vous pouvez surveiller et modifier le plan actif à tout moment. Voir [Surveiller et modifier un plan de déploiement](monitor-edit-rollout-plan.md).

## Voir également {#see-also}

* [Concept de déploiement automatisé](automated-rollout-concept.md)
* [Surveiller et modifier un plan de déploiement](monitor-edit-rollout-plan.md)
* [Définir une fonctionnalité à déployer progressivement](../feature-flags/set-feature-gradual-rollout.md)
* [Critères d’audience](../audience/audience-in-feature-flags-and-feature-groups.md)
