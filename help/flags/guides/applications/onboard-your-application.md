---
title: Intégration de votre application
description: Découvrez comment intégrer une nouvelle application aux indicateurs afin de pouvoir commencer à créer et gérer des indicateurs de fonctionnalités.
hide: true
exl-id: d88c27a5-f490-4504-9764-5e4ce98fdf20
source-git-commit: b3e13a42c19eb7b8b7d5d402bf9a56f89f573044
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 3%

---

# Intégration de votre application {#onboard-your-application}

Vous devez disposer du rôle **Admin** pour ajouter une nouvelle application. Contactez votre administrateur si vous avez besoin de vérifier ou de mettre à jour votre rôle.

## Ajouter une nouvelle application {#add-application}

1. Connectez-vous à la console Indicateurs et accédez à **Déploiement d’expérience > Applications**.

   >[!NOTE]
   >
   >Si le bouton **Nouvelle application** n’est pas visible, vérifiez que vous disposez du rôle **Administrateur Floodgate**.

2. Sélectionnez **Nouvelle application**.

3. Sélectionnez la **plateforme** correspondant à votre type d’application (web ou mobile).

4. Fournissez les informations suivantes :

   | Champ | Description |
   |---|---|
   | **ID de l’application** | Identifiant unique utilisé lors de l’appel des indicateurs à partir de votre code. Utilisez l’identifiant client de votre application. |
   | **TTL** | Intervalle d’interrogation (en secondes) pour l’actualisation du cache par application. S’applique uniquement aux SDK côté serveur. |

5. Sélectionnez **Ajouter**. Votre application est maintenant enregistrée et prête pour la configuration des indicateurs de fonctionnalité.

## Et après ? {#next-steps}

Une fois votre application intégrée, vous pouvez commencer à créer des indicateurs de fonctionnalité :

* [Créer votre premier indicateur de fonctionnalité](../feature-flags/create-your-first-feature-flag.md)
* [Intégration d’indicateurs dans l’application](../integrate/integrating-in-your-app.md)

## Voir également {#see-also}

* [Gestion des applications](manage-applications.md)
* [Connexion à la console](../console/log-in-to-the-console.md)

<!-- -->
