---
title: Prise en main des rapports dynamiques
description: En savoir plus sur le contrat d’utilisation des rapports dynamiques
level: Beginner
badge: label="DISPONIBILITÉ LIMITÉE" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Limité aux utilisateurs migrés Campaign Standard"
audience: end-user
source-git-commit: c6a6cb7da640c9c29af71487e468f38ebf51d4f6
workflow-type: tm+mt
source-wordcount: '523'
ht-degree: 59%

---


# Accord sur l&#39;utilisation des rapports dynamiques {#pii-agreement}

L’accord sur l’utilisation des rapports dynamiques fonctionne comme un consentement pop-up pour le traitement des données. Par défaut, le contrat n&#39;est visible que par les utilisateurs auxquels des droits d&#39;administration ont été attribués, et ne peut être accepté ou refusé que s&#39;ils le souhaitent.

Pour accéder au contrat d’utilisation des rapports dynamiques, sélectionnez **[!UICONTROL Outils]** > **[!UICONTROL Avancé]** > **[!UICONTROL Assistant de déploiement]**.

![](assets/pii-agreement.png)

Trois options sont disponibles :

* **[!UICONTROL Me demander plus tard]** : tant que vous n’avez pas accepté ou refusé le contrat, les dimensions de profil n’apparaîtront pas dans vos rapports et les Informations personnelles d’identification de vos clients ne seront pas collectées ni envoyées.
* **[!UICONTROL Accepter]** : lorsque vous acceptez les termes de cet accord, vous autorisez Adobe Campaign à collecter les PII de vos clients et à les transférer au centre de données ou de reporting.
* **[!UICONTROL Refuser]** : lorsque vous refusez les termes de l&#39;accord, les dimensions de profil ne s&#39;affichent pas dans vos rapports et les PII de vos clients ne sont pas collectées ni envoyées. Notez que dans ce cas, externalID sera toujours collecté et utilisé pour identifier les utilisateurs finaux.

Le tableau ci-dessous indique ce qui se passe après l&#39;acceptation de cet accord selon votre zone géographique.

|  | Rapports dynamiques | Connecteur Microsoft Dynamics 365 |
|---|---|---|
| Amériques et Asie-Pacifique | **Fonctionnalité disponible**. <br>Toutes les informations de profil personnalisées et d&#39;usine (ville, pays/région, état, genre et segments selon l&#39;âge) sont transmises au centre de reporting des Etats-Unis. | **Fonctionnalité disponible**. <br> Tous les champs de profil personnalisés et d&#39;usine, ainsi que les champs d&#39;événement Adobe Campaign, sont traités dans le centre de données des États-Unis. |
| EMEA (Europe, Moyen-Orient et Afrique) | **Fonctionnalité disponible**. <br>Toutes les informations de profil personnalisées et d&#39;usine (ville, pays/région, état, genre et segments selon l&#39;âge) sont transmises au centre de reporting EMEA. | **Fonctionnalité disponible.** <br>Tous les champs de profil personnalisés et d&#39;usine, ainsi que les champs d&#39;événement Adobe Campaign traités dans le centre de données EMEA. Les <br>**[!UICONTROL données de contrôle ]**qui contiennent les données d&#39;enregistrement Adobe I/O et les identifiants des événements utilisateur des clients sont envoyés et stockés dans le centre de données des Etats-Unis. |

Le tableau ci-dessous indique ce qui se passe après le refus de cet accord selon votre zone géographique. Notez que même si vous refusez cet accord, le reporting sur les diffusions et l&#39;intégration de Microsoft Dynamics 365 sera toujours disponible.

| Région | Rapports dynamiques | Connecteur Microsoft Dynamics 365 |
|---|---|---|
| Amériques et Asie-Pacifique | **Fonctionnalité disponible**. <br> Aucune information de profil personnalisée et d&#39;usine n&#39;est transmise au centre de reporting des Etats-Unis, à l&#39;exception d&#39;ExternalID. | **Fonctionnalité disponible**. <br>Aucun champ de profil personnalisé et d&#39;usine n&#39;est envoyé au centre de données des Etats-Unis, à l&#39;exception des champs Identifiant externe et Identifiant du destinataire. <br> Tous les champs d&#39;événement Adobe Campaign sont traités dans le centre de données des États-Unis, à l&#39;exception de l&#39;ID de la page miroir. |
| EMEA (Europe, Moyen-Orient et Afrique) | **Fonctionnalité disponible**. <br>Aucune information de profil personnalisée et d&#39;usine n&#39;est transmise au centre de reporting EMEA, à l&#39;exception d&#39;ExternalID. | **Fonctionnalité disponible.** <br>Aucun champ de profil personnalisé et d&#39;usine n&#39;est envoyé au centre de données EMEA, à l&#39;exception des champs Identifiant externe et Identifiant du destinataire. <br>Tous les champs d&#39;événement Adobe Campaign sont traités dans le centre de données EMEA, à l&#39;exception de l&#39;ID de la page miroir. |

Ce choix n&#39;est pas définitif. Vous pouvez toujours le modifier en sélectionnant l&#39;option **[!UICONTROL realtimeReporting_collectPII]** dans **[!UICONTROL Administration]** > **[!UICONTROL Plateforme]** > **[!UICONTROL Options]**.

La valeur peut être modifiée à tout moment. La valeur 1 correspond à **[!UICONTROL Me demander plus tard]**, 2 à **[!UICONTROL Refuser]** et 3 à **[!UICONTROL Accepter]**.
