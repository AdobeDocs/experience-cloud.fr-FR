---
title: Interface utilisateur web d’Adobe Campaign
description: Tables 64 bits
badge: label="DISPONIBILITÉ LIMITÉE" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Limité aux utilisateurs migrés Campaign Standard"
exl-id: ab5f01fd-4ad5-46e9-b132-011fe0f7bbd2
source-git-commit: 34c6f8a137a9085b26c0ea8f78930cff6192cfc9
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 7%

---

# Schémas 64 bits {#64-bit-tables}

Afin de faciliter la transition de Campaign Standard vers Campaign v8, plusieurs tables sont passées de 32 à 64 bits. En effet, Campaign Standard prend en charge le PK 64 bits dans plusieurs schémas d’usine, tandis que Campaign v8 prend en charge le PK 32 bits dans la plupart des schémas.

## Limites

* Cette modification technique s’applique uniquement aux clients effectuant la migration depuis Campaign Standard.
* Le schéma et l’extension broadlog ne sont pas pris en charge dans 64 bits. Il restera en 32 bits.
* Les logs relatifs aux diffusions envoyées aux utilisateurs techniques ne seront pas disponibles dans Campaign v8.
* Seul PostgreSQL est pris en charge.

## Schémas modifiés

Voici la liste des schémas modifiés en 64 bits et leurs attributs modifiés.

| Nom du schéma | Nom de l’attribut |
|--- |--- |
| nms:broadLogRcp | identifiant |
| nms:trackingLogRcp | identifiant |
| nms:excludeLogRcp | identifiant |
| nms:broadLogVisitor | identifiant |
| nms:trackingLogVisitor | identifiant |
| nms:propositionRcp | interactionId |
| nms:propositionVisitor | interactionId |
| nms:webTrackingLog | identifiant |
| nms:tmpBroadcast | message-id |
| nms:tmpMarketingPressure | message-id |
| nms:tmpBroadcastExclusion | message-id |
| nms:tmpBroadcastPaper | message-id |
| nms:broadLogAppSubRcp | identifiant |
| nms:trackingLogAppSubRcp | identifiant |
| nms:excludeLogAppSubRcp | identifiant |
| nms:webEvent | broadLogSrc-id, broadLogRemkt-id |
| nms:broadLogMid | mktBroadLogId |
| nms:mirrorPageSearch | remoteMessageId |
