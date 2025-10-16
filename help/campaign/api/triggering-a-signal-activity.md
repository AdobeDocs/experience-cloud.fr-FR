---
title: Déclenchement d’une activité de signal
description: Découvrez comment déclencher une activité de signal avec les API.
audience: developing
content-type: reference
topic-tags: campaign-standard-apis
role: Developer
level: Experienced
badge: label="DISPONIBILITÉ LIMITÉE" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Restrictions aux utilisateurs ayant migré vers Campaign Standard"
exl-id: 9f94e98f-fe04-4369-8946-1380e02cdece
source-git-commit: 11c49b273164b632bcffb7de01890c6f9d7ae9c2
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 97%

---

# Déclenchement d&#39;une activité de signal {#triggering-a-signal-activity}

Un workflow Adobe Campaign Standard peut comporter une ou plusieurs activités **Signal externe**. Ces activités sont des « écouteurs » (listeners) qui attendent d’être déclenchés.

Les API de Campaign Standard vous permettent de déclencher une activité **Signal externe** pour appeler un workflow. L’appel d’API peut inclure des paramètres à ingérer dans les variables d’événements du workflow (nom de l’audience à cibler, nom du fichier à importer, partie du contenu du message, etc.). De cette façon, vous pouvez facilement intégrer vos automatisations Campaign avec votre système externe.

>[!NOTE]
>
>Les activités de signal externe ne peuvent pas être déclenchées plus souvent que toutes les 10 minutes et le workflow de destination doit être déjà en cours d’exécution.

Pour déclencher un workflow, procédez comme suit :

1. Exécutez une requête **GET** sur le workflow pour récupérer l’URL du déclencheur d’activité Signal externe.

   `GET https://mc.adobe.io/<ORGANIZATION>/campaign/workflow/execution/<workflowID>`

1. Exécutez une requête **POST** sur l’URL renvoyée pour déclencher l’activité de signal, avec le paramètre **&quot;source&quot;** dans la payload. Cet attribut est obligatoire. Il permet d’indiquer la source de la demande de déclenchement.

Si vous souhaitez appeler le processus avec des paramètres, ajoutez-les à la payload avec l’attribut **&quot;parameters&quot;**. La syntaxe se compose du nom du paramètre suivi de sa valeur (les types suivants sont pris en charge : **string**, **number**, **boolean** et **date/time).**

```
  -X POST <TRIGGER_URL>
  -H 'Authorization: Bearer <ACCESS_TOKEN>' \
  -H 'Cache-Control: no-cache' \
  -H 'X-Api-Key: <API_KEY>' \
  -H 'Content-Type: application/json;charset=utf-8' \
  -H 'Content-Length:79' \
  -i
  -d {
  -d    "source":"<SOURCE>",
  -d    "parameters":{
  -d      "<PARAMETER_NAME":"<PARAMETER_VALUE>",
  -d      "<PARAMETER_NAME":"<PARAMETER_VALUE>",
  -d      "<PARAMETER_NAME":"<PARAMETER_VALUE>",  
  -d      "<PARAMETER_NAME":"<PARAMETER_VALUE>"
  -d    }
  -d }
```

>[!NOTE]
>
>Lors de l’ajout d’un paramètre à la payload, assurez-vous que ses valeurs **name** et **type** sont cohérentes avec les informations déclarées dans l’activité Signal externe. De plus, la taille de la payload ne doit pas dépasser 64 Ko.

<br/>

***Exemple de requête***

Exécutez une requête GET sur le workflow.

```
-X GET https://mc.adobe.io/<ORGANIZATION>/campaign/workflow/execution/<workflowID> \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

Elle renvoie l’activité du signal de workflow et l’URL de déclenchement associée.

```
{
"PKey": "<PKEY>",
"activities": {
  "activity": {
    "signal1": {
      ...
      "trigger": {
        "href": "https://mc.adobe.io/<ORGANIZATION>/campaign/workflow/execution/<PKEY>/activities/activity/<PKEY>/trigger/"
        },
        ...
      }
    }
  }
}
```

Pour déclencher une activité de signal, exécutez une requête POST sur l’URL de déclenchement avec la « source ». Ajoutez les attributs « parameters » si vous souhaitez appeler le workflow avec des paramètres.

```
-X POST https://mc.adobe.io/<ORGANIZATION>/campaign/workflow/execution/<PKEY>/activities/activity/<PKEY>/trigger \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>' \
-i
-d '{
-d "source":"API",
-d "parameters":{
-d    "audience":"audience",
-d    "email":"anna.varney@mail.com",
-d    "template":"05",
-d    "contentURL":"http://www.adobe.com",
-d    "test":"true",
-d    "segmentCode":"my segment",
-d    "attribute":"2019-04-03 08:17:19.100Z"}
-d  }'
```

<!-- + réponse -->

Si l’un des paramètres n’est pas déclaré dans l’activité Signal externe, la requête POST renvoie l’erreur ci-dessous, en indiquant le paramètre manquant.

```
RST-360011 An error has occurred - please contact your administrator.
'contentURL' parameter isn't defined in signal activity.
XTK-170006 Unable to parse expression 'HandleTrigger(@name, $(source), $({parameters}))'.
RST-360000 Error while assessing 'HandleTrigger(@name, $(source), $({parameters}))' expression ('xtk:workflow:execution/activities/signal/trigger' resource)
```
