---
title: Créer un groupe de fonctionnalités multi-équipes
description: Découvrez comment créer un groupe de fonctionnalités interéquipes dans les déploiements d’Adobe Experience afin de coordonner les indicateurs de fonctionnalités entre les applications détenues par différentes équipes.
source-git-commit: db719ba7b9db91aea818d8ef216a28fcedc6aa65
workflow-type: tm+mt
source-wordcount: '594'
ht-degree: 2%

---


# Créer un groupe de fonctionnalités multi-équipes {#create-cross-team-feature-group}

## Conditions préalables {#prerequisites}

Avant de créer un groupe de fonctionnalités multi-équipes, vérifiez les points suivants :

* Vous avez accès à la console ; voir [ Connexion à la console ](../console/log-in-to-the-console.md)
* Vous appartenez à une équipe et votre application est intégrée
* Vous disposez du rôle **Administrateur de fonctionnalités** — voir [Rôles utilisateur](../teams/user-roles.md)
* Vous avez créé les indicateurs de fonctionnalité à inclure. Voir [Créer votre premier indicateur de fonctionnalité](create-your-first-feature-flag.md)

Un groupe de fonctionnalités inter-équipes permet de regrouper des indicateurs de fonctionnalités provenant d’applications dans plusieurs équipes avec un ciblage d’audience riche. Contrairement aux versions , il est entièrement en libre-service et n’a aucune limite sur le nombre que vous pouvez créer. Consultez [Versions et groupes de fonctionnalités inter-équipes](releases-and-cross-team-feature-groups.md) pour une comparaison.

## Étape 1 : créer le groupe de fonctionnalités inter-équipes {#create}

Démarrez le processus de création à partir de la section Versions de la console :

1. Accédez à **Fonctionnalités et versions > Versions** dans la console.
2. Sélectionnez **Nouveau groupe de fonctionnalités (équipe croisée)**.

## Étape 2 : détails de base {#basic-details}

Fournissez un titre, une clé, une description et, éventuellement, une balise . Configurez les options suivantes :

* **Déploiement en pourcentage** — Définissez la proportion de l’audience qui recevra la fonctionnalité.
* **Type de déploiement** — Défini sur Manuel. Le pourcentage est géré étape par étape au fur et à mesure de la progression du déploiement.

>[!NOTE]
>
>Les tests A/B ne sont pas pris en charge pour les groupes de fonctionnalités inter-équipes. Pour exécuter des tests A/B, utilisez un [groupe de fonctionnalités](create-a-feature-group.md) standard (les applications doivent faire partie de la même équipe).

## Étape 3 : Audience {#audience}

Dans l’onglet **Audience**, activez **Règles d’audience** et configurez les éléments suivants :

* **Segments** — Sélectionnez un segment d&#39;audience prédéfini.
* **Filtres supplémentaires** — Ajoutez directement des critères basés sur un profil ou un contexte.
* **Applications** — Sélectionnez une ou plusieurs applications de votre équipe ou d&#39;autres équipes.

>[!IMPORTANT]
>
>L’ajout d’une application d’une autre équipe accorde aux administrateurs de fonctionnalités de cette équipe le droit d’ajouter des indicateurs de fonctionnalité pour leur application à ce groupe de fonctionnalités interéquipes. Vous ne pouvez pas ajouter leurs indicateurs de fonctionnalité vous-même.

## Étape 4 : fonctionnalités {#features}

Sous l’onglet **Fonctionnalités**, une boîte s’affiche pour chaque application incluse :

* Pour les applications de votre propre équipe, vous pouvez ajouter directement des indicateurs de fonctionnalité.
* Pour les applications d’autres équipes, ces zones sont grisées : les administrateurs des fonctionnalités de l’équipe correspondante doivent ajouter leurs indicateurs.

>[!IMPORTANT]
>
>Un indicateur de fonctionnalité ne peut être diffusé que par une seule méthode à la fois. L’ajout d’un indicateur à un groupe de fonctionnalités multi-équipes supprime directement toute audience ou pourcentage de déploiement défini sur l’indicateur. Les indicateurs déjà présents dans une autre version ou un autre groupe de fonctionnalités n’apparaîtront pas.

## Étape 5 : Planifier (facultatif) {#schedule}

Vous pouvez planifier l&#39;activation du groupe de fonctionnalités inter-équipes à une date et une heure ultérieures. Voir [Planification](schedule.md) pour plus de détails.

## Gestion des états {#states}

L’équipe qui crée le groupe de fonctionnalités interéquipes le possède et peut gérer son état. Les membres administrateurs de fonctionnalités de l’équipe propriétaire peuvent passer d’un état à l’autre à l’aide du menu déroulant d’état :

| État | Description |
|---|---|
| **Enregistrer** | Enregistré et non actif. Toutes les modifications sont autorisées. |
| **Publier** | En direct pour l’audience configurée. Les administrateurs peuvent continuer à mettre à jour les critères d’audience et le déploiement en pourcentage. |
| **Déploiement complet** | Disponible pour tous les utilisateurs. Impossible de restreindre davantage l’audience après ce point. |
| **Ligne de base** | Les fonctionnalités sont désormais la valeur par défaut. Le groupe de fonctionnalités inter-équipes est fermé. |
| **Abandon** | Le déploiement est arrêté. Aucun utilisateur ne reçoit de fonctionnalités de ce groupe. |

## Questions fréquentes {#faqs}

**Y a-t-il une limite au nombre de groupes de fonctionnalités inter-équipes ?**
Non. Contrairement aux versions , il n’existe aucune limite. Toutefois, archivez ou désactivez des groupes lorsque vous n’en avez plus besoin.

**Quelle est la différence entre une version et un groupe de fonctionnalités multi-équipes ?**
Voir [Versions et groupes de fonctionnalités inter-équipes](releases-and-cross-team-feature-groups.md) pour une comparaison détaillée.

## Voir également {#see-also}

* [Versions et groupes de fonctionnalités interéquipes](releases-and-cross-team-feature-groups.md)
* [Créer un groupe de fonctionnalités](create-a-feature-group.md)
