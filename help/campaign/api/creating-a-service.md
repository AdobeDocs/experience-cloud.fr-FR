---
title: Créer un service à l’aide des API
description: Découvrez comment créer un service à l’aide des API
role: Data Engineer
level: Experienced
badge: label="DISPONIBILITÉ LIMITÉE" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Limité aux utilisateurs migrés Campaign Standard"
exl-id: 91bbce9e-a618-4be2-840b-c7d021271f4e
source-git-commit: 14d8cf78192bcad7b89cc70827f5672bd6e07f4a
workflow-type: tm+mt
source-wordcount: '86'
ht-degree: 89%

---

# Créer un service à l’aide des API{#creating-a-service-api}

La création de services est effectuée avec une requête **POST** sur la ressource de service.

Si vous souhaitez créer le service avec des attributs spécifiques, ajoutez-les à la payload. Sinon, le nouveau service sera créé avec les services par défaut.

<br/>

***Exemple de requête***

Exemple de requête POST pour créer un service avec des attributs spécifiques.

```
-X POST https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/service/ \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
-i
-d {
-d "label": "My newsletter",
-d "messageType": "email",
-d "name": "email_newsletter",
-d "start": "2019-10-06"
-d }
```

Elle renvoie le service qui vient d’être créé avec les attributs mis à jour.

```
{
    "PKey": "<PKEY>",
    "builtIn": false,
    "created": "2019-09-26 12:00:37.005Z",
    "href": "https://mc.adobe.io/<ORGANIZATION>/profileAndServices/service/@NLscZuVHxdVu9rPftvrMWFfR1zRIxQGswSOmGLrK09JTF_iWhB0JCUHEndA_vvy__k9mzOYa5NVkcWDcrK8qGh0wygahX9kRcD44kiWWSEceShn3",
    "label": "My newsletter",
    ...
}
```
