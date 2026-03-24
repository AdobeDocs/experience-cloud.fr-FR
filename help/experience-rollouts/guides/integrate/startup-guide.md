---
title: Guide de démarrage
description: Pour intégrer votre application aux déploiements d’Adobe Experience, procédez comme suit, de la demande d’accès à la création de votre premier indicateur de fonctionnalité.
source-git-commit: 9bfe0e55e89c1d7fbd77cde63831a6a186820e24
workflow-type: tm+mt
source-wordcount: '309'
ht-degree: 1%

---


# Guide de démarrage {#startup-guide}

Pour intégrer des déploiements d’expérience dans votre application, procédez comme suit.

## Étape 1 : Demander l&#39;accès {#step-1-access}

Demandez l’accès à la console Déploiements d’expérience et rejoignez votre équipe. Consultez [Demande d’accès](../console/request-access.md) pour obtenir des instructions détaillées.

## Étape 2 : intégration de votre application {#step-2-onboard}

Après avoir obtenu l’accès, connectez-vous à la console Déploiements d’expérience et vérifiez que votre application est répertoriée sous votre équipe. Si ce n’est pas le cas, demandez à l’administrateur de votre équipe de l’ajouter. Voir [Intégration de votre application](../applications/onboard-your-application.md).

Avant l’intégration, préparez les éléments suivants :

| Exigence | Détails |
|---|---|
| **ID de l’application** | Identifiant client unique utilisé lors de l’appel des API de déploiements d’expérience. Utilisez l’identifiant client existant de votre application, le cas échéant. |
| **Clients côté serveur** | En cas d’intégration à un SDK côté serveur, vous avez besoin d’un identifiant client d’administration disposant des autorisations appropriées. |
| **Clients de bureau** | Un code de produit et une version de produit peuvent être utilisés à la place d’un identifiant client. |

## Étape 3 : s’abonner à l’API de déploiements d’expérience {#step-3-subscribe}

Abonnez-vous à l’API de déploiements d’expérience via Adobe Developer Console afin que votre application puisse appeler les points d’entrée d’indicateur de fonctionnalité. Voir [S’abonner à l’application API dans Adobe Developer Console](subscribe-to-api-application.md).

>[!NOTE]
>
>Si vous intégrez via un SDK côté serveur, vous avez besoin d’un identifiant client de jeton de service. Contactez l’assistance des déploiements d’expérience pour que votre identifiant client soit placé sur la liste autorisée.

## Étape 4 : intégration à l’aide d’un SDK ou de l’API {#step-4-integrate}

Suivez les [étapes d’intégration](integration-steps.md) pour votre type d’application. Choisissez le chemin d’accès qui correspond à votre pile :

* **Services web** → Java SDK ou Node.js SDK
* **Applications web et mobiles** API de fonctionnalités → V3
* **Applications de bureau** API de fonctionnalités → V2

## Étape 5 : créer et tester votre premier indicateur de fonctionnalité {#step-5-feature-flag}

Une fois l’intégration terminée, créez votre premier indicateur de fonctionnalité dans la console et testez-le :

* [Créer votre premier indicateur de fonctionnalité](../feature-flags/create-your-first-feature-flag.md)

## Voir également {#see-also}

* [Intégration de déploiements d’expérience dans votre application](integrating-in-your-app.md)
* [Étapes d’intégration](integration-steps.md)
* [SDK](sdks.md)
