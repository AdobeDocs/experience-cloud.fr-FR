---
title: Intégration de votre application
description: Découvrez comment intégrer une nouvelle application aux déploiements d’Adobe Experience afin que votre équipe puisse commencer à créer et gérer des indicateurs de fonctionnalité.
source-git-commit: 9bfe0e55e89c1d7fbd77cde63831a6a186820e24
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 2%

---


# Intégration de votre application {#onboard-your-application}

Vous devez disposer du rôle **Admin** pour ajouter une nouvelle application. Voir [Rôles utilisateur](../teams/user-roles.md) si vous devez vérifier votre rôle ou le demander à l’administrateur de votre équipe.

## Ajouter une nouvelle application {#add-application}

1. Connectez-vous à la console Déploiements d’expérience et accédez à **Admin > Applications**.

   >[!NOTE]
   >
   >Si le bouton **Nouvelle application** n’est pas visible, vérifiez que vous vous trouvez dans la bonne équipe et que vous disposez du rôle **Administrateur**.

2. Sélectionnez **Nouvelle application**.

3. Sélectionnez le **canal** qui correspond à votre type d’application (web, mobile, bureau ou service).

4. Fournissez les informations suivantes :

   | Champ | Description |
   |---|---|
   | **ID de l’application** | Identifiant unique utilisé lors de l’appel des déploiements d’expérience à partir de votre code. Utilisez l’identifiant client de votre application. |
   | **TTL** | Intervalle d’interrogation (en secondes) pour l’actualisation du cache par application. S’applique uniquement aux SDK côté serveur. |
   | **Équipe** | Équipe qui possédera et gérera cette application. Seuls les membres de cette équipe peuvent créer et modifier des indicateurs de fonctionnalité pour celle-ci. |

5. Sélectionnez **Ajouter**. Votre application est maintenant enregistrée et prête pour la configuration des indicateurs de fonctionnalité.

## Et après ? {#next-steps}

Une fois votre application intégrée, votre équipe peut commencer à créer des indicateurs de fonctionnalité :

* [Créer votre premier indicateur de fonctionnalité](../feature-flags/create-your-first-feature-flag.md)
* [Intégration de déploiements d’expérience dans votre application](../integrate/integrating-in-your-app.md)

## Voir également {#see-also}

* [Gestion des applications](manage-applications.md)
* [Rôles utilisateur](../teams/user-roles.md)
* [Connexion à la console](../console/log-in-to-the-console.md)
