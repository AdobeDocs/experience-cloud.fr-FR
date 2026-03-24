---
title: Audience dans les indicateurs de fonctionnalité et les groupes de fonctionnalités
description: Découvrez comment définir des critères d’audience pour les indicateurs de fonctionnalités et les groupes de fonctionnalités dans les déploiements d’Adobe Experience à l’aide des attributs de profil, des segments et du calculateur d’audience.
source-git-commit: 3f3f7145b3c58dc721cbeb850e9e8571e3255bb1
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---


# Audience dans les indicateurs de fonctionnalité et les groupes de fonctionnalités {#audience-overview}

Déploiements d’expérience fournit un ciblage d’audience riche pour les indicateurs de fonctionnalité et les groupes de fonctionnalités. Vous pouvez combiner des attributs de profil, des variables contextuelles et des segments d’audience pour contrôler précisément quels utilisateurs bénéficient d’une fonctionnalité.

## Règles de profil {#profile-rules}

Les règles de profil vous permettent de cibler les utilisateurs en fonction d’attributs tels que le pays, le domaine de messagerie, le type de compte, l’identifiant utilisateur, etc. Vous pouvez combiner plusieurs attributs à l’aide d’opérateurs ET/OU et créer une logique imbriquée pour des scénarios de ciblage complexes.

Pour ajouter des règles de profil, accédez à l’onglet **Audience** d’un indicateur de fonctionnalité ou d’un groupe de fonctionnalités et ajoutez des conditions sous **Profil**.

Vous pouvez enregistrer un ensemble de règles d’audience en tant qu’**Audience** réutilisable à utiliser avec plusieurs indicateurs et groupes.

Pour le ciblage basé sur le contexte (par exemple, le ciblage par langue principale ou type de client de l’utilisateur ou de l’utilisatrice), consultez [Utilisation du contexte dans les règles d’audience](using-context-in-audience-rules.md).

## Segments {#segments}

Les indicateurs de fonctionnalité et les groupes de fonctionnalités prennent en charge les segments d’audience. Les segments vous permettent de :

* Utilisez une définition d’audience prédéfinie unique pour plusieurs indicateurs et groupes de fonctionnalités
* Incluez des **critères basés sur un événement** dans le ciblage de votre audience, ce qui est impossible avec les règles de profil uniquement

Pour utiliser un segment, accédez à l’onglet **Audience** et sélectionnez un ou plusieurs segments dans la liste. Vous pouvez combiner plusieurs segments à l’aide d’opérateurs ET/OU et ajouter des filtres de profil ou de contexte supplémentaires à côté d’eux.

>[!NOTE]
>
>Vous avez besoin du rôle **Gestionnaire de tests** ou d’un rôle supérieur pour créer des segments d’audience.

## Calculateur d’audience {#audience-calculator}

Après avoir défini vos critères d’audience, sélectionnez **Calculer** dans la barre inférieure pour obtenir une estimation du nombre d’utilisateurs qui remplissent les critères. Cela vous permet de valider la portée de votre ciblage avant d’activer la fonctionnalité.

>[!NOTE]
>
>Le calculateur d’audience ne renvoie pas de valeur lorsque des variables contextuelles sont incluses dans les critères, car les valeurs contextuelles sont déterminées au moment de l’exécution et ne peuvent pas être prédites à l’avance.

## Voir également {#see-also}

* [Utilisation du contexte dans les règles d’audience](using-context-in-audience-rules.md)
* [Ajouter des règles de pourcentage dans les critères d’audience](adding-percentage-rules.md)
* [Règles d’audience complexes](complex-rules.md)
* [Créer votre premier indicateur de fonctionnalité](../feature-flags/create-your-first-feature-flag.md)
