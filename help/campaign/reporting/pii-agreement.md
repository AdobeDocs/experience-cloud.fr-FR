---
title: Commencer avec les rapports dynamiques
description: En savoir plus sur l’accord relatif à l’utilisation des rapports dynamiques
level: Beginner
badge: label="DISPONIBILITÉ LIMITÉE" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Restrictions aux utilisateurs ayant migré vers Campaign Standard"
audience: end-user
exl-id: 9fcef466-f306-480e-b42e-d18daa8bcf06
TQID: https://experienceleague.adobe.com/AGXqq-XOQU8SmHobDIA-nZqw3eNSa2THnw2jQQP54YA
product_v2: id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
feature_v2: id: fdbb8fc9-ffa3-4b86-88fe-aa4c5a3e1bc6
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
level_v2: id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2: id: aa2f3246-cb95-4b30-8899-fdf7d73550ccid: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: ad84694f2f6f45e4ee30fc51379106835ac302be
workflow-type: tm+mt
source-wordcount: 549
ht-degree: 95%

---

# Accord sur l&#39;utilisation des rapports dynamiques {#pii-agreement}

L’accord sur l’utilisation des rapports dynamiques fonctionne comme un consentement pop-up pour le traitement des données. Par défaut, seuls les utilisateurs et utilisatrices auxquels sont affectés des droits d’administration peuvent afficher et accepter ou refuser cet accord.

Pour accéder à l’accord sur l’utilisation des rapports dynamiques, sélectionnez **[!UICONTROL Outils]** > **[!UICONTROL Avancé]** > **[!UICONTROL Assistant de déploiement]**.

![](assets/pii-agreement.png)

Trois options sont disponibles :

* **[!UICONTROL Me demander plus tard]** : tant que vous n’avez pas accepté ou refusé l’accord, les dimensions de profil ne s’affichent pas dans vos rapports et les PII de vos clientes et clients ne sont pas collectées ni envoyées.
* **[!UICONTROL Accepter]** : lorsque vous acceptez les termes de cet accord, vous autorisez Adobe Campaign à collecter les PII de vos clients et à les transférer au centre de données ou de reporting.
* **[!UICONTROL Refuser]** : lorsque vous refusez les termes de l&#39;accord, les dimensions de profil ne s&#39;affichent pas dans vos rapports et les PII de vos clients ne sont pas collectées ni envoyées. Notez que dans ce cas, externalID sera toujours collecté et utilisé pour identifier les utilisateurs finaux.

Le tableau ci-dessous indique ce qui se passe après l’acceptation de cet accord selon votre zone géographique.

|  | Rapports dynamiques | Connecteur Microsoft Dynamics 365 |
|---|---|---|
| Amériques et Asie-Pacifique | **Fonctionnalité disponible**. <br>Toutes les informations de profil personnalisées et prêtes à l’emploi (c’est-à-dire ville, pays/région, État, genre et segments selon l’âge) sont transmises au centre de reporting des États-Unis. | **Fonctionnalité disponible**. <br>Tous les champs de profil personnalisés et prêts à l’emploi, ainsi que les champs d’événement Adobe Campaign, sont traités dans le centre de données des États-Unis. |
| EMEA (Europe, Moyen-Orient et Afrique) | **Fonctionnalité disponible**. <br>Toutes les informations de profil personnalisées et prêtes à l’emploi (c’est-à-dire ville, pays/région, État, genre et segments selon l’âge) sont transmises au centre de reporting EMEA. | **Fonctionnalité disponible.** <br>Tous les champs de profil personnalisés et d’usine, ainsi que les champs d’événement Adobe Campaign, sont traités dans le centre de données EMEA. Les <br>**[!UICONTROL données de contrôle ]**qui contiennent les données d&#39;enregistrement Adobe I/O et les identifiants des événements utilisateur des clients sont envoyés et stockés dans le centre de données des Etats-Unis. |

Le tableau ci-dessous indique ce qui se passe après le refus de cet accord selon votre zone géographique. Notez que même si vous refusez cet accord, le reporting sur les diffusions et l&#39;intégration de Microsoft Dynamics 365 sera toujours disponible.

| Région | Rapports dynamiques | Connecteur Microsoft Dynamics 365 |
|---|---|---|
| Amériques et Asie-Pacifique | **Fonctionnalité disponible**. <br> Aucune information de profil personnalisée ni d’usine n’est transmise au centre de reporting de la région États-Unis, à l’exception d’ExternalID. | **Fonctionnalité disponible**. <br>Aucun champ de profil personnalisé et d&#39;usine n&#39;est envoyé au centre de données des Etats-Unis, à l&#39;exception des champs Identifiant externe et Identifiant du destinataire. <br>Tous les champs d’événement Adobe Campaign sont traités dans le centre de données des États-Unis, à l’exception de l’ID de la page miroir. |
| EMEA (Europe, Moyen-Orient et Afrique) | **Fonctionnalité disponible**. <br>Aucune information de profil personnalisée et d&#39;usine n&#39;est transmise au centre de reporting EMEA, à l&#39;exception d&#39;ExternalID. | **Fonctionnalité disponible.** <br>Aucun champ de profil personnalisé ni d’usine n’est envoyé au centre de données EMEA, à l’exception des champs Identifiant externe et Identifiant du destinataire. <br>Tous les champs d’événement Adobe Campaign sont traités dans le centre de données EMEA, à l’exception de l’ID de la page miroir. |

Ce choix n’est pas définitif, vous pouvez toujours le modifier en sélectionnant l’option **[!UICONTROL realtimeReporting_collectPII]** dans **[!UICONTROL Administration]** > **[!UICONTROL Plateforme]** > **[!UICONTROL Options]**.

La valeur peut être modifiée à tout moment. La valeur 1 correspond à **[!UICONTROL Me demander plus tard]**, 2 à **[!UICONTROL Refuser]** et 3 à **[!UICONTROL Accepter]**.
