---
title: Pourquoi utiliser les API de Campaign Standard ?
description: Découvrez les API de Campaign Standard et pourquoi les utiliser.
audience: developing
content-type: reference
topic-tags: campaign-standard-apis
role: Data Engineer
level: Experienced
badge: label="DISPONIBILITÉ LIMITÉE" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Limité aux utilisateurs migrés Campaign Standard"
exl-id: ef045e5d-cd02-44a0-9a1e-d468483a38d9
source-git-commit: 3f4400f24b75e8e435610afbe49e9d9444dbf563
workflow-type: tm+mt
source-wordcount: '481'
ht-degree: 98%

---

# Pourquoi utiliser les API de Campaign Standard ?  {#why-using-campaign-standard-apis}

Adobe Campaign Standard fournit des API qui permettent aux systèmes existants de s’intégrer à la plateforme Campaign pour résoudre des problèmes concrets en temps réel.

Les sites web publics, comme les pages d’opt-in ou d&#39;opt-out, doivent se connecter aux systèmes principaux pour stocker les informations de profil. Les systèmes principaux tels qu’Adobe Campaign offrent la souplesse et la puissance nécessaires pour ingérer les données de profil et leur appliquer des opérations personnalisées.

Voici quelques exemples :

* Inscription en ligne de prospects.
* Gestion des profils de clients existants et des préférences en matière de communication marketing.
* Déclenchement de communications transactionnelles à partir d’événements - confirmation de commande, itinéraire de réservation, réinitialisation du mot de passe, etc.
* Communication par email en cas d’abandon d’un panier d’achat.

Les landing pages d’inscription permettent aux clients ou aux prospects d’enregistrer leur nom et leur adresse email. Une fois les informations de profil et de préférences recueillies par Campaign Standard, il est possible d’envoyer des messages personnalisés en fonction des centres d’intérêt de la personne concernée.

Ces messages sont élaborés à l’aide des éléments suivants :

1. Formulaire d’enregistrement avec des écouteurs (listeners) d’API Campaign.

   ![texte alternatif](assets/apis_uc1.png)

1. Actions personnalisées à effectuer en fonction des cases à cocher. Contrairement au processus normal d’inscription, un client qui choisit « Offres spéciales par email » recevra un nouvel email personnalisé assorti d’un bon-cadeau.

   ![texte alternatif](assets/apis_uc2.png)

1. Il est possible de modifier les informations d’un profil si le destinataire clique sur le lien « Mettre à jour les informations » dans l’email. Ce profil est affiché dans la page « Mettre à jour vos informations de profil et de préférences ». Pour effectuer l’opération, les informations de profil (Pkey) sont transmises au serveur Campaign et le profil est récupéré et représenté. Une fois que le profil a cliqué sur le bouton « Mettre à jour », les informations sont mises à jour dans le système (via une commande PATCH).

   ![texte alternatif](assets/apis_uc3.png)

Un ensemble de requêtes est disponible pour mieux vous familiariser avec les requêtes d’API Campaign Standard. Cet ensemble au format JSON met à votre disposition des requêtes d’API prédéfinies représentant des cas pratiques courants.

Les étapes ci-dessous décrivent un cas pratique détaillé. Vous pourrez ainsi importer et utiliser l’ensemble de requêtes pour créer un profil dans la base de données Campaign Standard.

>[!NOTE]
>
>Notre exemple utilise Postman. Cependant, n’hésitez pas à utiliser votre client REST préféré.

1. Téléchargez la collection JSON en cliquant [ici](https://helpx.adobe.com/content/dam/help/en/campaign/kb/working-with-acs-api/_jcr_content/main-pars/download_section/download-1/KB_postman_collection.json.zip).

1. Ouvrez Postman, puis sélectionnez le menu **Fichier** / **Importer** .

1. Faites glisser et déposez le fichier téléchargé dans la fenêtre. Les requêtes d’API prédéfinies s’affichent, prêtes à être utilisées.

   ![texte alternatif](assets/postman_collection.png)

1. Sélectionnez la requête **Créer un profil**, puis mettez à jour la requête POST et l’onglet **En-têtes** avec vos propres informations (&lt;ORGANIZATION>, &lt;API_KEY>, &lt;ACCESS_TOKEN>). Voir à ce propos [cette section](setting-up-api-access.md).

   ![texte alternatif](assets/postman_uc1.png)

1. Renseignez l’onglet **Corps** avec les informations que vous souhaitez ajouter au nouveau profil, puis cliquez sur le bouton **Envoyer** pour exécuter la requête.

   ![texte alternatif](assets/postman_uc2.png)

1. Une fois un objet créé, une clé primaire (PKey) lui est associée. Elle est visible dans la réponse à la requête, ainsi que d’autres attributs.

   ![texte alternatif](assets/postman_uc3.png)

1. Ouvrez votre instance Campaign Standard, puis vérifiez que le profil est créé, avec toutes les informations issues de la payload.

   ![Texte alternatif](assets/postman_uc4.png)
