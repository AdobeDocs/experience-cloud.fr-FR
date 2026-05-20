---
title: Synthèse des rebonds
description: Grâce au rapport prêt à l’emploi Synthèse des rebonds, découvrez le statut des campagnes envoyées et les erreurs qu’elles ont peut-être rencontrées.
audience: end-user
level: Intermediate
badge: label="DISPONIBILITÉ LIMITÉE" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Restrictions aux utilisateurs ayant migré vers Campaign Standard"
exl-id: b341edad-aa82-43d8-a5a1-b33a19973a1a
TQID: https://experienceleague.adobe.com/gfOXWpdQvONw72sdpnGehwpXcgte16B6dLiWV2LZXOc
product_v2: id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2: id: aa2f3246-cb95-4b30-8899-fdf7d73550ccid: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: ad84694f2f6f45e4ee30fc51379106835ac302be
workflow-type: tm+mt
source-wordcount: 298
ht-degree: 97%

---

# Synthèse des rebonds{#bounce-summary}

Ce rapport présente l’ensemble des erreurs relatives aux rebonds définitifs et temporaires survenues lors des diffusions ainsi que le traitement automatique des rebonds.

![](assets/campaign_reports_bounces.png)

Chaque tableau est représenté par des nombres et des graphiques de synthèse. Vous pouvez modifier le mode d&#39;affichage des détails dans leurs paramètres de visualisation respectifs.

**Flop 5 des répartitions** liste les cinq diffusions présentant le plus grand nombre de mises en quarantaine :

Le tableau **Raisons des rebonds** contient les données disponibles pour les types d’erreur ayant causé des rebonds pour chaque diffusion :

* **[!UICONTROL Utilisateur inconnu]** : type d’erreur générée lors de l’envoi d’une diffusion indiquant que l’adresse email est invalide.
* **[!UICONTROL Domaine invalide]** : type d’erreur générée lors de l’envoi d’une diffusion indiquant que le domaine de l’adresse email est erroné ou n’existe plus.
* **[!UICONTROL Inatteignable]** : type d’erreur rencontrée dans la chaîne de diffusion des messages, par exemple en cas de domaine temporairement inatteignable.
* **[!UICONTROL Compte désactivé]** : type d’erreur générée lors de l’envoi d’une diffusion indiquant que l’adresse n’existe plus.
* **[!UICONTROL Boîte pleine]** : type d’erreur générée lorsque la boîte de réception du destinataire est pleine. Il y a cinq tentatives d’envoi du message avant que cette erreur soit générée.
* **[!UICONTROL Non connecté]** : type d’erreur générée lorsque le téléphone portable du destinataire est éteint ou n’est pas connecté au réseau au moment de l’envoi du message.

  >[!NOTE]
  >
  >Ce type d’erreur ne concerne que les diffusions sur les canaux mobiles.

* **[!UICONTROL Refusé]** : type d’erreur générée lorsqu’une adresse est refusée par le fournisseur d’accès Internet (FAI). Par exemple, lorsqu’une règle de sécurité a été appliquée par un logiciel anti-spam.

Le tableau **Répartition des domaines** affiche les problèmes généraux survenus au cours des diffusions, en fonction du domaine du destinataire.
