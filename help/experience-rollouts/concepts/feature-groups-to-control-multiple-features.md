---
title: Groupes de fonctionnalités pour contrôler plusieurs fonctionnalités
description: Découvrez comment les groupes de fonctionnalités dans les déploiements d’expérience vous permettent de regrouper et de gérer les indicateurs de fonctionnalité associés dans les applications en une seule entité.
source-git-commit: 1c8fd9b42d08f657b4e6b16efae86faa04d15565
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 1%

---


# Groupes de fonctionnalités pour contrôler plusieurs fonctionnalités {#feature-groups}

Un indicateur [fonctionnalité](what-is-a-feature-flag.md) contrôle une seule fonctionnalité. Lorsque vous devez gérer plusieurs indicateurs de fonctionnalité associés ensemble (et vous assurer qu’ils atteignent la même audience), vous utilisez un **groupe de fonctionnalités**.

## Fonctionnement d&#39;un groupe de fonctionnalités {#what-it-does}

Un groupe de fonctionnalités regroupe plusieurs indicateurs de fonctionnalité et vous permet d’appliquer une seule règle d’audience à tous en même temps. Cela s’avère utile lorsqu’une seule fonctionnalité face à l’utilisateur ou à l’utilisatrice couvre plusieurs applications ou services.

Prenons l’exemple d’une fonctionnalité de collaboration qui implique des modifications sur une application de bureau, une application mobile et un service principal. En créant un groupe de fonctionnalités avec des indicateurs des trois applications, vous pouvez ouvrir la fonctionnalité à 1 % des utilisateurs, et vous assurer que ces utilisateurs bénéficient d&#39;une expérience cohérente sur les trois surfaces simultanément.

## Regroupement de plusieurs applications {#cross-application}

Les groupes de fonctionnalités prennent en charge la gestion de fonctionnalités entre applications à condition que les indicateurs appartiennent à la **même équipe** dans les déploiements d’expérience. Une équipe peut posséder plusieurs applications, de sorte que les indicateurs associés à ces applications peuvent être regroupés.

## Groupes de fonctionnalités et versions {#vs-releases}

| | Groupe de fonctionnalités | Libération |
|---|---|---|
| Portée | Au sein d’une seule équipe | À travers plusieurs équipes |
| Cas d’utilisation | Coordination des indicateurs au sein de votre équipe | Coordination de lancement à grande échelle et à plusieurs équipes |
| Privilèges requis | Team-level | Supérieur (gestionnaire de version) |

Si les indicateurs de fonctionnalité que vous souhaitez regrouper appartiennent à des applications appartenant à différentes équipes, utilisez une version [release](release-management.md) au lieu d’un groupe de fonctionnalités.
