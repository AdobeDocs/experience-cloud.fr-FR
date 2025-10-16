---
title: Interface utilisateur web d’Adobe Campaign
description: tableaux 64 bits
badge: label="DISPONIBILITÉ LIMITÉE" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Restrictions aux utilisateurs ayant migré vers Campaign Standard"
exl-id: ab5f01fd-4ad5-46e9-b132-011fe0f7bbd2
source-git-commit: 11c49b273164b632bcffb7de01890c6f9d7ae9c2
workflow-type: tm+mt
source-wordcount: '163'
ht-degree: 18%

---

# Schémas 64 bits {#sixty-four-bit-tables}

Afin de faciliter la transition de Campaign Standard vers Campaign v8, plusieurs tables ont été modifiées de 32 à 64 bits. En effet, Campaign Standard prend en charge la pharmacocinétique 64 bits dans plusieurs schémas prêts à l’emploi, tandis que Campaign v8 prend en charge la pharmacocinétique 32 bits dans la plupart des schémas.

## Limites

* Cette modification technique s’applique uniquement aux clients effectuant la migration depuis Campaign Standard.
* L’extension de schéma et broadlog n’est pas prise en charge en 64 bits. Il restera en 32 bits.
* Les journaux liés aux diffusions envoyés aux utilisateurs techniques ne seront pas disponibles dans Campaign v8.
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
| nms:webEvent | broadLogSrc-id, broadLogRemote-id |
| nms:broadLogMid | mktBroadLogId |
| nms:mirrorPageSearch | remoteMessageId |
