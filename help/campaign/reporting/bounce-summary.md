---
title: Synthèse des rebonds (Bounce summary)
description: Grâce au rapport d'usine Synthèse des rebonds (Bounce summary), découvrez le statut des campagnes envoyées et les erreurs qu'elles ont peut-être rencontrées.
audience: end-user
level: Intermediate
badge: label="DISPONIBILITÉ LIMITÉE" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Limité aux utilisateurs migrés Campaign Standard"
source-git-commit: 3f4400f24b75e8e435610afbe49e9d9444dbf563
workflow-type: tm+mt
source-wordcount: '295'
ht-degree: 96%

---

# Synthèse des rebonds (Bounce summary){#bounce-summary}

Ce rapport présente l&#39;ensemble des statistiques d&#39;erreurs hard et soft survenues lors des diffusions ainsi que le traitement automatique des retours.

![](assets/campaign_reports_bounces.png)

Chaque tableau est représenté par des nombres et des graphiques de synthèse. Vous pouvez modifier le mode d&#39;affichage des détails dans leurs paramètres de visualisation respectifs.

**Flop 5 des répartitions** liste les cinq diffusions présentant le plus grand nombre de mises en quarantaine :

Le tableau **Raisons de bounce** contient les données disponibles pour les types d&#39;erreur ayant causé des bounces pour chaque diffusion :

* **[!UICONTROL Utilisateur inconnu]** : type d&#39;erreur générée lors de l&#39;envoi d&#39;une diffusion indiquant que l&#39;adresse email est invalide.
* **[!UICONTROL Domaine invalide]** : type d&#39;erreur générée lors de l&#39;envoi d&#39;une diffusion indiquant que le domaine de l&#39;adresse email est erroné ou n&#39;existe plus.
* **[!UICONTROL Inatteignable]** : type d’erreur rencontrée dans la chaîne de diffusion des messages, par exemple en cas de domaine temporairement inatteignable.
* **[!UICONTROL Compte désactivé]** : type d&#39;erreur générée lors de l&#39;envoi d&#39;une diffusion indiquant que l&#39;adresse n&#39;existe plus.
* **[!UICONTROL Boîte pleine]** : type d&#39;erreur générée lorsque la boîte de réception du destinataire est pleine. Il y a cinq tentatives d&#39;envoi du message avant que cette erreur soit générée.
* **[!UICONTROL Non connecté]** : type d&#39;erreur générée lorsque le téléphone portable du destinataire est éteint ou n&#39;est pas connecté au réseau au moment de l&#39;envoi du message.

  >[!NOTE]
  >
  >Ce type d&#39;envoi ne concerne que les diffusions sur les canaux mobiles.

* **[!UICONTROL Refusé]** : type d&#39;erreur générée lorsqu&#39;une adresse est refusée par le fournisseur d&#39;accès Internet (FAI). Par exemple, lorsqu&#39;une règle de sécurité a été appliquée par un logiciel anti-spam.

Le tableau **Répartition des domaines** affiche les problèmes généraux survenus au cours des diffusions, en fonction du domaine du destinataire.
