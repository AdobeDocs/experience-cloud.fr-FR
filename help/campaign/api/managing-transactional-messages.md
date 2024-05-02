---
title: Gestion des messages transactionnels
description: Découvrez comment gérer les messages transactionnels avec les API.
audience: developing
content-type: reference
topic-tags: campaign-standard-apis
hidefromtoc: true
hide: true
role: Data Engineer
level: Experienced
badge: label="DISPONIBILITÉ LIMITÉE" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Limité aux utilisateurs migrés Campaign Standard"
exl-id: 00d39438-a232-49f1-ae5e-1e98c73397e3
source-git-commit: 3f4400f24b75e8e435610afbe49e9d9444dbf563
workflow-type: tm+mt
source-wordcount: '661'
ht-degree: 93%

---

# Gestion des messages transactionnels {#managing-transactional-messages}

Une fois que vous avez créé et publié un événement transactionnel, vous devez intégrer le déclenchement de cet événement dans votre site Web.

Par exemple, vous souhaitez qu’un événement de type « Abandon de panier » soit déclenché lorsque l’un de vos clients quitte votre site Web avant d’avoir acheté les produits de son panier. Pour ce faire, le développeur Web de votre site doit se servir de l’API REST des messages transactionnels.

1. Il exécute une requête selon la méthode POST, qui déclenche l’[envoi de l’événement transactionnel](#sending-a-transactional-event).
1. La réponse à la requête POST contient une clé primaire, qui permet au développeur d’exécuter une ou plusieurs requêtes par le biais d’une requête GET. Vous pouvez ensuite obtenir le [statut de l’événement](#transactional-event-status).

## Envoi d’un événement transactionnel {#sending-a-transactional-event}

L’événement transactionnel est envoyé via une requête POST avec la structure d’URL suivante :

```
POST https://mc.adobe.io/<ORGANIZATION>/campaign/<transactionalAPI>/<eventID>
```

* **&lt;ORGANIZATION>** : votre ORGANIZATION ID personnel. Reportez-vous à [cette section](must-read.md).

* **&lt;transactionalAPI>** : les points d’entrée (endPoints) de l’API des messages transactionnels.

  Le nom du point d’entrée de l’API des messages transactionnels dépend de la configuration de votre instance. Il correspond à la valeur &quot;mc&quot; suivie de votre identifiant d’organisation personnel. Prenons l’exemple de la société Geometrixx, dont l’identifiant d’organisation est &quot;geometrixx&quot;. Dans ce cas, la requête POST serait la suivante :

  `POST https://mc.adobe.io/geometrixx/campaign/mcgeometrixx/<eventID>`

  Notez que le point d’entrée de l’API des messages transactionnels est également visible pendant l’aperçu de l’API.

* **&lt;eventID>** : type d’événement à envoyer. Cet identifiant est généré lors de la création de la configuration de l’événement.

### En-tête de requête POST

La requête doit contenir un en-tête &quot;Content-Type: application/json&quot;.

Vous devez ajouter un jeu de caractères, par exemple **utf-8**. Cette valeur dépend de l’application REST utilisée.

```
-X POST \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>' \
-H 'Content-Type: application/json;charset=utf-8' \
-H 'Content-Length:79' \
```

### Corps de requête POST

Les données d’événement sont contenues dans le corps JSON POST. La structure de l’événement dépend de sa définition. Le bouton d’aperçu de l’API dans l’écran de définition des ressources fournit un exemple de requête.

Il est possible d’ajouter les paramètres facultatifs suivants au contenu de l’événement pour gérer l’envoi de messages transactionnels liés à cet événement :

* **expiration** (facultatif) : après cette date, l’envoi de l’événement transactionnel sera annulé.
* **scheduled** (facultatif) : à partir de cette date, l’événement transactionnel sera traité et le message transactionnel sera envoyé.

>[!NOTE]
>
>Les valeurs des paramètres &quot;expiration&quot; et &quot;scheduled&quot; suivent le format ISO 8601. Ce format spécifie l’utilisation de la lettre majuscule &quot;T&quot; pour séparer la date et l’heure. Il peut toutefois être supprimé de l’entrée ou de la sortie pour une meilleure lisibilité.

### Réponse à la requête POST

La réponse POST renvoie l’état de l’événement transactionnel au moment de sa création. Pour récupérer son état actuel (données de l’événement, statut de l’événement...), utilisez la clé primaire renvoyée par la réponse POST dans une requête GET :

`GET https://mc.adobe.io/<ORGANIZATION>/campaign/<transactionalAPI>/<eventID>/`

<br/>

***Exemple de requête***

Requête POST pour envoyer l’événement.

```
-X POST https://mc.adobe.io/<ORGANIZATION>/campaign/mcAdobe/EVTcartAbandonment \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>' \
-H 'Content-Type: application/json;charset=utf-8' \
-H 'Content-Length:79'

{
  "email":"test@example.com",
  "scheduled":"2017-12-01 08:00:00.768Z",
  "expiration":"2017-12-31 08:00:00.768Z",
  "ctx":
  {
    "cartAmount": "$ 125",
    "lastProduct": "Leather motorbike jacket",
    "firstName": "Jack"
  }
}
```

Réponse à la requête POST.

```
{
  "PKey":"<PKEY>",
  "ctx":
  {
    "cartAmount": "",
    "lastProduct": "",
    "firstName": ""
  }
  "email":"",
  "scheduled":"2017-12-01 08:00:00.768Z",
  "expiration":"2017-12-31 08:00:00.768Z",
  "href": "mcAdobe/EVTcartAbandonment/<PKEY>",
  "serverUrl":" https://myserver.com ",
  "status":"pending",
  "type":""
}
```

### Statut de l’événement transactionnel {#transactional-event-status}

Dans la réponse, le champ &quot;status&quot; vous permet de savoir si l’événement a été traité ou non :

* **pending** : l’événement est en attente ; il se trouve dans cet état lorsqu’il vient d’être déclenché.
* **processing** : l’événement est en attente de diffusion ; il est transformé en message et ce message est envoyé.
* **paused** : le processus d’événement est en pause. Il n’est plus traité, mais il est conservé dans une file d’attente dans la base de données Adobe Campaign.
* **processed** : l’événement a été traité et le message a bien été envoyé.
* **ignored** : l’événement a été ignoré par la diffusion, généralement lorsqu’une adresse est en quarantaine.
* **deliveryFailed** : une erreur de diffusion s’est produite pendant le traitement de l’événement.
* **routageFailed** : la phase de routage a échoué ; cette situation peut se produire, par exemple, lorsque le type d’événement spécifié est introuvable.
* **tooOld** : l’événement a expiré avant d’être traité ; cette situation peut se produire pour diverses raisons, par exemple lorsqu’un envoi échoue à plusieurs reprises (l’événement n’est plus à jour) ou lorsque le serveur ne peut plus traiter les événements après une surcharge.
* **targetingFailed** : Campaign Standard n&#39;a pas pu enrichir un lien utilisé pour le ciblage des messages.
