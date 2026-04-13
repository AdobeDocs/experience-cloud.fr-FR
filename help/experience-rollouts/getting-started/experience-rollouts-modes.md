---
title: Modes de déploiement d’expérience
description: Découvrez les deux modes de ciblage des fonctionnalités dans les déploiements d’Adobe Experience , le ciblage au niveau de l’utilisateur et le ciblage au niveau de l’organisation, ainsi que le moment d’utiliser chacun d’eux.
hide: true
exl-id: 0fdfa429-d9bd-4990-8f96-cd9deb273aa0
source-git-commit: 12032cbed45e694a3f25f16afe80308b3eb82924
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 3%

---

# Modes de déploiement d’expérience {#modes}

Les déploiements d’expérience fournissent deux modes de ciblage des fonctionnalités distincts. Chacun a un objectif de contrôle de libération différent et est conçu pour un type spécifique d’application ou de cas d’utilisation.

>[!TIP]
>
>Choisissez le mode en fonction de ce que vous contrôlez : sessions d’utilisateurs individuelles ou portée de l’organisation et de l’environnement.

## Ciblage au niveau de l’utilisateur {#user-level}

### Vue d’ensemble {#user-level-overview}

Le ciblage au niveau de l’utilisateur permet de déployer des fonctionnalités au niveau de chaque utilisateur. Il prend en charge le ciblage précis d’utilisateurs et utilisatrices spécifiques, les testeurs et testeuses internes, les utilisateurs et utilisatrices de canaris et les déploiements progressifs en fonction du pourcentage.

Ce mode est mieux adapté aux applications qui doivent varier l’expérience en fonction de la personne connectée.

### Quand l’utiliser {#user-level-when}

Utilisez le ciblage au niveau de l’utilisateur pour :

* Activation d’une fonctionnalité pour des utilisateurs spécifiques
* Exécuter des expériences A/B
* Effectuez des tests canariens avec un petit groupe avant un déploiement plus large.
* Déploiement progressif d’une fonctionnalité par pourcentage d’utilisateurs
* Ajustez l’expérience en fonction des attributs d’utilisateur individuels (tels que le domaine de l’e-mail ou les données de profil)

### Limites {#user-level-limitations}

Le ciblage au niveau de l’utilisateur n’est pas conçu pour les scénarios suivants :

* Ne contrôle pas les fonctionnalités au niveau de l&#39;organisation, de l&#39;environnement ou de la région
* Non destiné à l’activation des fonctionnalités à l’échelle du client ou au point de contrôle des droits

## Ciblage au niveau de l’organisation et de l’environnement {#org-level}

### Vue d’ensemble {#org-level-overview}

Le ciblage au niveau de l’organisation permet le déploiement de fonctionnalités au niveau de l’organisation, de l’environnement et de la région. Il contrôle la disponibilité des fonctionnalités dans des organisations entières ou des environnements de déploiement spécifiques, plutôt que pour des utilisateurs individuels.

Ce mode est conçu pour les points de contrôle de fonctionnalité au niveau de l’entreprise et les déploiements spécifiques à un environnement.

### Quand l’utiliser {#org-level-when}

Utilisez le ciblage au niveau de l’organisation lorsque vous souhaitez :

* Activation d’une fonctionnalité pour l’ensemble de l’organisation
* Contrôler la disponibilité des fonctionnalités par environnement (par exemple, évaluation ou production)
* Effectuer un déploiement régional
* Fonctionnalités de point de contrôle en fonction du droit ou du niveau d’abonnement

### Limites {#org-level-limitations}

Le ciblage au niveau de l’organisation et de l’environnement n’est pas conçu pour les scénarios suivants :

* Ne prend pas en charge le ciblage basé sur les profils d’utilisateurs enrichis
* ne prend pas en charge le déploiement en pourcentage au niveau de chaque utilisateur ;
* Non destiné à l’expérimentation ou aux tests A/B

## Comparaison {#comparison}

| Dimension | Ciblage au niveau de l’utilisateur | Ciblage au niveau de l’organisation et de l’environnement |
|---|---|---|
| Portée du contrôle | Utilisateur individuel | Organisation, environnement, région |
| Base de ciblage | Profil utilisateur et attributs | Contexte d’organisation et d’environnement |
| Déploiement en pourcentage | Oui | Non |
| Tests A/B | Oui | Non |
| Entrée d’entreprise | Non | Oui |

## Choisir le bon mode {#choosing}

* Si votre question est *« Quels utilisateurs doivent voir cette fonctionnalité ? »* → Utiliser le **ciblage au niveau de l’utilisateur**
* Si votre question est *« Quelles organisations ou quels environnements doivent disposer de cette fonctionnalité ? »* → Utiliser le ciblage **au niveau de l’organisation et de l’environnement**

<!-- -->
