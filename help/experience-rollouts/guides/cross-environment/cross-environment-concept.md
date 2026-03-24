---
title: Concept inter-environnements
description: Découvrez comment les fonctionnalités inter-environnements dans les déploiements d’Adobe Experience Platform vous permettent de lier des applications entre des environnements et de gérer les indicateurs de fonctionnalités de manière cohérente, du développement à la production.
source-git-commit: 5c99061a7f2aaaad98190166ea6fd79b7eb26dec
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 0%

---


# Concept inter-environnements {#cross-environment-concept}

Les fonctionnalités inter-environnements vous permettent de lier vos instances d’application à différents environnements de déploiement (tels que l’assurance qualité, l’évaluation et la production) et de gérer les indicateurs de fonctionnalité de manière cohérente sur tous ces environnements à partir des déploiements d’expérience.

## Le problème inter-environnement est résolu {#problem}

Sans liaison entre environnements, chaque instance d’application dans les déploiements d’expériences est complètement indépendante de ses homologues dans d’autres environnements. Cela crée plusieurs points de friction :

* Une application nommée `my-app` dans l’environnement intermédiaire n’a aucune relation avec les `my-app` en production. Elles sont traitées comme des applications distinctes non liées.
* Vous ne pouvez pas afficher le statut d’un indicateur de fonctionnalité dans l’environnement intermédiaire lorsque vous travaillez en production. Vous devez changer d’environnement manuellement pour comparer les états d’indicateur.
* L&#39;importation d&#39;une configuration d&#39;indicateur de fonctionnalité d&#39;un environnement inférieur vers un environnement supérieur nécessite une recréation manuelle.

## Ce que permet l’interenvironnement {#what-it-enables}

En liant les instances d’application entre les environnements, votre équipe peut :

* Définissez quels environnements de déploiement de votre application mappent à quels environnements de déploiement d’expérience
* Utilisez des libellés d’environnement personnalisés (par exemple, `Dev`, `Staging`, `Prod`) qui correspondent aux conventions de nommage de votre équipe
* Affichage de l’état d’un indicateur de fonctionnalité dans tous les environnements liés à partir d’une seule vue
* Importez les indicateurs de fonctionnalité d’un environnement inférieur dans un environnement supérieur en quelques clics, sans les recréer manuellement

## La structure des environnements {#environment-structure}

Les déploiements d’expériences comportent deux environnements de plateforme : **Évaluation** et **Production**. Cependant, votre application peut avoir d’autres environnements, par exemple, le contrôle qualité, l’évaluation et la production. La liaison entre environnements vous permet de décider de l’emplacement de chacun des environnements de votre application :

* Les environnements d’assurance qualité et d’évaluation peuvent être hébergés dans l’environnement d’évaluation ou de production des déploiements d’expérience.
* Les environnements de production doivent être hébergés dans l’environnement de production Déploiements d’expérience .

Cette flexibilité signifie que vous n’êtes pas contraint à un mappage unique.

## Étapes suivantes {#next-steps}

* [Associer des environnements à une application](associate-environments.md) — Configurer les liens entre les instances de votre application
* [Affichage des indicateurs de fonctionnalité dans les environnements](view-feature-flags-across-environments.md) — Surveillance de l’état des indicateurs dans tous les environnements liés
* [Importer des indicateurs de fonctionnalité](import-feature-flags.md) — promouvoir les indicateurs de fonctionnalité des environnements inférieurs aux environnements supérieurs
