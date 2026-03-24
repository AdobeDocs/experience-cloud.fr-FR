---
title: Abonnement à l’application API dans Adobe Developer Console
description: Découvrez comment abonner votre application à l’API de déploiements d’expérience via Adobe Developer Console afin de pouvoir appeler les points d’entrée d’indicateur de fonctionnalité.
source-git-commit: 120a2ea34682c878aaf6f6cb75504a8704d10e3d
workflow-type: tm+mt
source-wordcount: '278'
ht-degree: 3%

---


# Abonnement à l’application API dans Adobe Developer Console {#subscribe-to-api}

Pour appeler l’API de déploiements d’expérience à partir de votre application, vous devez vous y abonner via [](https://developer.adobe.com/console). Cela donne à votre application un identifiant client qu’Experience Rollouts utilise pour identifier l’appelant.

## Conditions préalables {#prerequisites}

Avant de vous abonner, vérifiez les points suivants :

* Votre application est intégrée dans la console Déploiements d’expérience. Voir [Intégration de votre application](../applications/onboard-your-application.md).
* Vous avez accès au Adobe Developer Console pour votre organisation

## Abonnement à l’API de déploiements d’expériences {#subscribe}

Pour abonner votre application à l’API de déploiements d’expérience, procédez comme suit :

1. Accédez à [](https://developer.adobe.com/console) et connectez-vous avec les informations d’identification de votre organisation.
2. Sélectionnez votre projet ou créez-en un.
3. Sélectionnez **Ajouter une API**.
4. Recherchez et sélectionnez **API de déploiements d’expérience**.
5. Suivez les invites pour configurer l’API et générer les informations d’identification.
6. Notez l’identifiant **client** généré pour votre projet. Il s’agit de l’identifiant que vous utilisez lors de l’appel de l’API des déploiements d’expérience et de l’intégration de votre application dans la console des déploiements d’expérience.

## Intégrations SDK côté serveur {#server-sdk}

Si vous intégrez à l’aide du SDK Java SDK ou Node.js, vous avez besoin d’un identifiant client **jeton de service** en plus d’une clé API. Le jeton de service permet au SDK d’appeler les API de déploiements d’expérience en arrière-plan.

>[!NOTE]
>
>Les identifiants de client SDK côté serveur doivent être contrôlés par la prise en charge des déploiements d’expérience avant de pouvoir effectuer des appels API. Contactez l’assistance après avoir terminé la configuration de Developer Console.

## Voir également {#see-also}

* [Guide de démarrage](startup-guide.md)
* [SDK](sdks.md)
* [Intégration de votre application](../applications/onboard-your-application.md)
* [Étapes d’intégration](integration-steps.md)
