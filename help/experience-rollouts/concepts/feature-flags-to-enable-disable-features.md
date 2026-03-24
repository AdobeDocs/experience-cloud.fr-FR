---
title: Indicateurs de fonctionnalité pour activer et désactiver des fonctionnalités
description: Découvrez comment les indicateurs de fonctionnalité dans les déploiements d’expérience vous permettent de contrôler la disponibilité des fonctionnalités, de gérer les dépendances et de réduire les risques de déploiement.
source-git-commit: 1c8fd9b42d08f657b4e6b16efae86faa04d15565
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 0%

---


# Indicateurs de fonctionnalité pour activer et désactiver des fonctionnalités {#feature-flags}

Les indicateurs de fonctionnalités vous permettent d’activer ou de désactiver des fonctionnalités d’application au moment de l’exécution sans redéployer le code. Ils séparent également les déploiements de code de la disponibilité des fonctionnalités : le nouveau code peut être déployé en production derrière un indicateur et activé uniquement lorsque vous êtes prêt.

Cette pratique réduit considérablement les risques. Les développeurs peuvent développer avec agilité et confiance, tandis que les équipes produit conservent le contrôle sur le timing et l’audience de chaque mise à jour de fonctionnalité.

## Gestion des dépendances pendant le développement {#manage-dependencies}

Les indicateurs de fonctionnalité permettent de gérer les dépendances lors des tests dans des cycles de développement rapides. Les développeurs passent moins de temps à résoudre des conflits de fusion et à refactoriser, et plus de temps à fournir des fonctionnalités.

La disponibilité des fonctionnalités étant contrôlée en dehors du code, plusieurs fonctionnalités peuvent être développées en parallèle, sans ramification complexe. Chaque fonction peut être restaurée indépendamment, sans affecter les autres fonctions en cours.

## Déploiements sombres {#dark-deployments}

Comme les décisions d’activation et de désactivation se trouvent en dehors de la base de code, vous pouvez déployer le code en production tout en gardant la fonctionnalité invisible pour les utilisateurs finaux. Il s’agit d’un **déploiement sombre**.

Les déploiements sombres vous permettent d’envoyer le code en production en toute sécurité, de le tester dans l’environnement en ligne par rapport à des conditions réelles et de le publier lorsque vous le souhaitez, et non lorsque le planning de déploiement vous le force.

## Déploiement graduel {#gradual-rollout}

Lorsque vous êtes prêt à publier, vous pouvez utiliser un indicateur de fonctionnalité pour effectuer un **déploiement progressif** : ouvrez la fonctionnalité à 1 % des utilisateurs, mesurez les commentaires et les performances, puis augmentez progressivement.

Cette approche progressive vous permet de mieux contrôler l’expérience que vous diffusez et d’accélérer la boucle de commentaires avec les utilisateurs réels, afin que vos équipes puissent répondre rapidement avant une publication complète.

## Interrupteur de fermeture {#kill-switch}

Si une version ne se déroule pas comme prévu (retour d’informations défavorable, bug ou problème de performances), vous pouvez désactiver immédiatement la fonctionnalité à l’aide de l’indicateur de fonctionnalité comme **interrupteur**. Aucun changement ou redéploiement de code n’est nécessaire.

## Cycle de vie de l’indicateur de fonctionnalité {#lifecycle}

L’indicateur de fonctionnalité dans les déploiements d’expérience suit ce cycle de vie type :

1. Un développeur crée un indicateur de fonctionnalité et le teste de manière isolée, sans le présenter à d’autres utilisateurs.
2. Un propriétaire de produit associe une audience à l’indicateur , ce qui rend la fonctionnalité visible par un ensemble défini d’utilisateurs externes.
3. L’indicateur est éventuellement ajouté à un [groupe de fonctionnalités](feature-groups-to-control-multiple-features.md) à gérer avec les indicateurs associés.
4. L’indicateur est éventuellement ajouté à une version [release](release-management.md) pour la coordination entre les équipes.
