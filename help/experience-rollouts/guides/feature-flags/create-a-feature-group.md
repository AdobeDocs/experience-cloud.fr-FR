---
title: Créer un groupe de fonctionnalités
description: Découvrez comment créer un groupe de fonctionnalités dans les déploiements d’Adobe Experience afin de gérer plusieurs indicateurs de fonctionnalités dans les applications de votre équipe en une seule entité.
source-git-commit: 9bfe0e55e89c1d7fbd77cde63831a6a186820e24
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 0%

---


# Créer un groupe de fonctionnalités {#create-feature-group}

## Conditions préalables {#prerequisites}

Avant de créer un groupe de fonctionnalités, effectuez les opérations suivantes :

* Vous avez accès à la console Déploiements d’expérience ; voir [ Connexion à la console ](../console/log-in-to-the-console.md)
* Vous appartenez à une équipe. Voir [Gérer les équipes](../teams/manage-teams.md)
* Votre application est intégrée : consultez la section [Intégration de votre application](../applications/onboard-your-application.md)
* Vous disposez du rôle **Développeur** ou **Propriétaire de la version du produit** voir [Rôles utilisateur](../teams/user-roles.md)
* Vous avez créé les indicateurs de fonctionnalité que vous souhaitez ajouter au groupe. Voir [Créer votre premier indicateur de fonctionnalité](create-your-first-feature-flag.md)

Pour une présentation des groupes de fonctions, voir [Groupes de fonctions pour contrôler plusieurs fonctions](../../concepts/feature-groups-to-control-multiple-features.md).

## Étape 1 : créer le groupe de fonctionnalités {#create}

Ouvrez la console et démarrez un nouveau groupe de fonctionnalités :

1. Connectez-vous à la console Déploiements d’expérience et accédez à **Tests de fonctionnalités > Groupes de fonctionnalités**.
2. Sélectionnez **Nouveau groupe de fonctionnalités**.

## Étape 2 : détails de base {#basic-details}

Configurez les paramètres généraux du groupe de fonctionnalités :

1. Fournissez un titre, une clé, une description et, éventuellement, une balise .
2. Définissez un **pourcentage de déploiement** pour le groupe de fonctionnalités.
3. Si vous souhaitez exécuter un test A/B, sélectionnez plusieurs variantes. Sinon, laissez-la sur une variante. [ Pour plus d’informations](a-b-testing.md) voir Tests A/B avec indicateurs de fonctionnalité .

## Étape 3 : Audience {#audience}

Définissez qui recevra les fonctionnalités de ce groupe :

1. Dans l’onglet **Audience**, ajoutez des critères d’audience pour définir quels utilisateurs bénéficient de la fonctionnalité.
2. Sous **Applications**, ajoutez une ou plusieurs applications de votre équipe. Les groupes de fonctionnalités peuvent s’étendre sur plusieurs applications, à condition qu’ils appartiennent tous à la même équipe.

>[!NOTE]
>
>Le rôle **Développeur** est en sandbox. Ajoutez votre propre ID utilisateur sous **Audience > Profil > ID utilisateur** pour effectuer des tests en privé. Pour cibler des utilisateurs externes, vous devez disposer du rôle **Propriétaire de la version de produit**.

## Étape 4 : fonctionnalités {#features}

Attribuez les indicateurs de fonctionnalité qui seront contrôlés par ce groupe :

1. Sous l’onglet **Fonctions**, une boîte s’affiche pour chaque application sélectionnée.
2. Ajoutez des indicateurs de fonctionnalité pour chaque application.
3. Si vous avez sélectionné plusieurs variantes (pour les tests A/B), vous voyez des onglets pour chaque variante. Ajoutez les indicateurs de fonctionnalité appropriés à chaque élément.

>[!IMPORTANT]
>
>Un indicateur de fonctionnalité ne peut être diffusé que par une méthode, soit directement en tant qu&#39;indicateur de fonctionnalité, soit par l&#39;intermédiaire d&#39;un groupe de fonctionnalités, soit par l&#39;intermédiaire d&#39;une version. Lorsque vous ajoutez un indicateur de fonctionnalité à un groupe de fonctionnalités, toute audience ou pourcentage de déploiement défini sur l’indicateur est supprimé. Les indicateurs de fonctionnalité déjà affectés à une autre version ou à un autre groupe de fonctionnalités n&#39;apparaissent pas dans la liste.

## Étape 5 : Planifier (facultatif) {#schedule}

Vous pouvez planifier l&#39;activation du groupe de fonctionnalités à une date et une heure ultérieures. Voir [Planification](schedule.md) pour plus de détails.

## Voir également {#see-also}

* [Définir un groupe de fonctionnalités à déployer progressivement](set-feature-group-gradual-rollout.md)
* [Test A/B avec indicateurs de fonctionnalité](a-b-testing.md)
* [Groupes de fonctionnalités pour contrôler plusieurs fonctionnalités](../../concepts/feature-groups-to-control-multiple-features.md)
