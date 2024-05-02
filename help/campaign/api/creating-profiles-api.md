---
title: Créer des profils à l'aide des API
description: En savoir plus sur la façon de créer des profils à l'aide des API.
audience: developing
content-type: reference
topic-tags: campaign-standard-apis
role: Data Engineer
level: Experienced
badge: label="DISPONIBILITÉ LIMITÉE" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Limité aux utilisateurs migrés Campaign Standard"
exl-id: 69e8d034-6bdd-4b82-bcd7-1ef4be0a59b3
source-git-commit: 3f4400f24b75e8e435610afbe49e9d9444dbf563
workflow-type: tm+mt
source-wordcount: '110'
ht-degree: 91%

---

# Créer des profils à l&#39;aide des API {#creating-profiles-api}

La création de profils est effectuée avec une requête **POST** sur la ressource de profil.

>[!CAUTION]
>
>Si vous souhaitez associer un <b>orgUnit</b> au profil créé, vous devez étendre la ressource de profil à ce champ et, après la publication de l’extension, effectuer une requête POST sur le point d’entrée <b>ProfileAndServicesExt</b>.
>
>Pour plus d’informations sur l’extension de ressource du profil, consultez la <a href="https://helpx.adobe.com/fr/campaign/standard/administration/using/organizational-units.html#partitioning-profiles">documentation de Campaign</a>.

<br/>

***Exemple de requête***

Exemple de requête POST pour créer un profil avec le message « john.doe@mail.com ».

```
-X POST https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>' \
-i
-d '{"email":"john.doe@mail.com"}'
```

Elle renvoie le profil créé, avec l’adresse email « john.doe@mail.com ».

```
{
    "PKey": "<PKEY>",
    "firstName": "John",
    "lastName":"Doe",
    "birthDate": "1980-10-24",
    "email": "john.doe@mail.com",
    ...
}
```
