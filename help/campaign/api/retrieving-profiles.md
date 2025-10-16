---
title: Récupérer des profils
description: Découvrez comment récupérer les profils à l’aide des API
role: Developer
level: Experienced
badge: label="DISPONIBILITÉ LIMITÉE" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Restrictions aux utilisateurs ayant migré vers Campaign Standard"
exl-id: 19679804-f728-49fa-b26e-8f31b67c29bf
source-git-commit: 11c49b273164b632bcffb7de01890c6f9d7ae9c2
workflow-type: tm+mt
source-wordcount: '243'
ht-degree: 96%

---

# Récupérer des profils à l’aide des API {#retrieving-profiles}

La récupération des profils est effectuée avec une requête **GET**.

Vous pouvez ensuite affiner votre recherche à l’aide de filtres, de classements et de paginations. Pour plus d&#39;informations, consultez la section [Autres opérations](sorting.md).

En outre, les API Campaign Standard vous permettent de rechercher des profils en fonction de l’un de ces champs : email, prénom, nom ou tout champ personnalisé. Voir à ce propos [cette section](#searching-field).

<br/>

***Exemples de demande***

* Exemple de requête GET pour récupérer tous les profils.

  ```
  -X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile \
  -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer <ACCESS_TOKEN>' \
  -H 'Cache-Control: no-cache' \
  -H 'X-Api-Key: <API_KEY>'
  ```

  Réponse à la requête.

  ```
  {
      "content": [
          {
              "PKey": "<PKEY>",
              "firstName": "John",
              "lastName":"Doe",
              "birthDate": "1980-10-24",
              ...
          },
          ...
  }
  ```

* Exemple de requête GET pour récupérer les 10 premières valeurs d’email.

  ```
  -X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/email?_lineCount=10 \
  -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer <ACCESS_TOKEN>' \
  -H 'Cache-Control: no-cache' \
  -H 'X-Api-Key: <API_KEY>'
  ```

  Réponse à la requête. Le nœud « suivant » renvoie l’URL qui vous donne accès aux 10 valeurs d’email suivantes.

  ```
  {
  "content": [
      "amy.dakota@mail.com",
      "kristen.smith@mail.com",
      "omalley@mail.com",
      "xander.harrys@mail.com",
      "jane.summer@mail.com",
      "gloria.boston@mail.com",
      "edward.snow@mail.com",
      "dorian.simons@mail.com",
      "peter.paolini@mail.com",
      "mingam+test08@adobe.com"
  ],
  "next": {
      "href": "https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/email?_lineCount=10&_
      lineStart=@Qy2MRJCS67PFf8soTf4BzF7BXsq1Gbkp_e5lLj1TbE7HJKqc"
  }
  }
  ```

## Recherche de profils en fonction d&#39;un champ {#searching-field}

Le paramètre **[!UICONTROL filterType]** permet de rechercher des profils en fonction de l’un de ces champs : email, prénom, nom ou tout champ personnalisé qui a été ajouté dans le filtrage avancé lors de l’extension de la ressource de profil.

>[!NOTE]
>
>Les recherches sont sensibles à la casse et effectuées sur les préfixes uniquement. Par exemple, vous ne pourrez pas rechercher un profil en utilisant les dernières lettres de son nom de famille.

***Exemples de demande***

* Exemple de demande de filtrage des profils en fonction du prénom.

  ```
  -X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/byText?text=John&filterType=firstName \
  -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer <ACCESS_TOKEN>' \
  -H 'Cache-Control: no-cache' \
  -H 'X-Api-Key: <API_KEY>'
  ```

* Exemple de demande de filtrage des profils en fonction du nom de famille.

  ```
  -X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/byText?text=Miller&filterType=lastName \
  -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer <ACCESS_TOKEN>' \
  -H 'Cache-Control: no-cache' \
  -H 'X-Api-Key: <API_KEY>'
  ```

* Exemple de demande de filtrage des profils en fonction de l&#39;email.

  ```
  -X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/byText?text=John%40gmail.com&filterType=email \
  -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer <ACCESS_TOKEN>' \
  -H 'Cache-Control: no-cache' \
  -H 'X-Api-Key: <API_KEY>'
  ```

* Exemple de demande de filtrage des profils en fonction du champ personnalisé Hobby.

  ```
  -X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServicesExt/profile/byText?cusHobby=Dancing&filterType=Hobby \
  -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer <ACCESS_TOKEN>' \
  -H 'Cache-Control: no-cache' \
  -H 'X-Api-Key: <API_KEY>'
  ```
