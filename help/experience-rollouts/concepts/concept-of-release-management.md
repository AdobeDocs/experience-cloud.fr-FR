---
title: Concept de gestion des versions
description: Découvrez comment la gestion des versions dans les déploiements d’expérience permet de coordonner les déploiements de fonctionnalités importants entre les équipes grâce aux indicateurs de fonctionnalité.
source-git-commit: 1c8fd9b42d08f657b4e6b16efae86faa04d15565
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 0%

---


# Concept de gestion des versions {#concept-of-release-management}

Les versions volumineuses partagent quelques défis communs : plusieurs équipes sont impliquées, les planifications sont en conflit et les dépendances sont difficiles à coordonner. La gestion des versions résout ces problèmes en fournissant un moyen structuré de déployer les modifications en douceur.

## Signification de la gestion des versions {#what-it-means}

La gestion des versions couvre la coordination d’une version de bout en bout, à partir du moment où les équipes commencent à se développer derrière les indicateurs de fonctionnalité jusqu’au moment où la fonctionnalité est entièrement disponible pour tous les utilisateurs et utilisatrices.

Il permet aux équipes de :

* Déployer indépendamment en production, à leur propre rythme, sans révéler de fonctionnalités aux utilisateurs finaux
* Activer uniquement lorsque toutes les équipes participantes sont prêtes
* Déployez progressivement la version sur un sous-ensemble d’utilisateurs avant sa disponibilité complète.

## Fonctionnement dans les déploiements d’expérience {#how-it-works}

La gestion des versions dans les déploiements d’expérience s’appuie sur le concept de [indicateurs de fonctionnalité](what-is-a-feature-flag.md). Chaque équipe déploie son code en production derrière un indicateur de fonctionnalité. Une version consiste alors en un **ensemble d’indicateurs de fonctionnalité définis dans plusieurs applications et équipes**.

Lorsque toutes les équipes sont prêtes, la version peut être activée en une seule opération ou déployée progressivement, sans qu’aucune équipe individuelle n’ait besoin de redéployer ou de coordonner le calendrier de déploiement.

Cette approche permet d’obtenir les éléments suivants :

* **Déploiement indépendant** — Les équipes effectuent le déploiement selon leur propre calendrier sans affecter les autres équipes ou les utilisateurs finaux.
* **Activation coordonnée** — Tous les indicateurs d&#39;une version sont activés ensemble lorsque la version est activée.
* **Déploiement progressif** — La version peut être ouverte progressivement pour augmenter les pourcentages d’utilisateurs.

Pour plus d’informations sur la configuration des versions dans les déploiements d’expérience, voir [Gestion des versions](release-management.md).
