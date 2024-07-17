---
title: Synthèse des rebonds
description: Grâce au rapport prêt à l’emploi Synthèse des rebonds, découvrez le statut des campagnes envoyées et les erreurs qu’elles ont peut-être rencontrées.
audience: end-user
level: Intermediate
badge: label="DISPONIBILITÉ LIMITÉE" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Limité aux utilisateurs migrés Campaign Standard"
exl-id: b341edad-aa82-43d8-a5a1-b33a19973a1a
source-git-commit: 34c6f8a137a9085b26c0ea8f78930cff6192cfc9
workflow-type: tm+mt
source-wordcount: '295'
ht-degree: 86%

---

# Synthèse des rebonds{#bounce-summary}

Ce rapport présente l’ensemble des erreurs relatives aux rebonds définitifs et temporaires survenues lors des diffusions ainsi que le traitement automatique des rebonds.

![](assets/campaign_reports_bounces.png)

Chaque tableau est représenté par des nombres et des graphiques de synthèse. Vous pouvez modifier le mode d&#39;affichage des détails dans leurs paramètres de visualisation respectifs.

**Flop 5 repartition** liste les cinq diffusions ayant le plus grand nombre de mises en quarantaine :

Le tableau **Raisons des rebonds** contient les données disponibles pour les types d’erreur ayant causé des rebonds pour chaque diffusion :

* **[!UICONTROL Utilisateur inconnu]** : type d’erreur générée lors de l’envoi d’une diffusion indiquant que l’adresse email est invalide.
* **[!UICONTROL Domaine invalide]** : type d’erreur générée lors de l’envoi d’une diffusion indiquant que le domaine de l’adresse email est erroné ou n’existe plus.
* **[!UICONTROL Inatteignable]** : type d’erreur rencontrée dans la chaîne de diffusion des messages, par exemple en cas de domaine temporairement inatteignable.
* **[!UICONTROL Compte désactivé]** : type d’erreur générée lors de l’envoi d’une diffusion indiquant que l’adresse n’existe plus.
* **[!UICONTROL Boîte pleine]** : type d’erreur générée lorsque la boîte de réception du destinataire est pleine. Il y a cinq tentatives d’envoi du message avant que cette erreur soit générée.
* **[!UICONTROL Non connecté]** : type d’erreur générée lorsque le téléphone portable du destinataire est éteint ou n’est pas connecté au réseau au moment de l’envoi du message.

  >[!NOTE]
  >
  >Ce type d’envoi ne concerne que les diffusions sur les canaux mobiles.

* **[!UICONTROL Refusé]** : type d’erreur générée lorsqu’une adresse est refusée par le fournisseur d’accès Internet (FAI). Par exemple, lorsqu’une règle de sécurité a été appliquée par un logiciel anti-spam.

La table **Répartition de domaine** affiche les problèmes généraux rencontrés lors des diffusions en fonction du domaine du destinataire.
