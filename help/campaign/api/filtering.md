---
title: Filtrage
description: Découvrez comment effectuer des opérations de filtrage.
audience: developing
content-type: reference
topic-tags: campaign-standard-apis
role: Data Engineer
level: Experienced
badge: label="DISPONIBILITÉ LIMITÉE" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Limité aux utilisateurs migrés Campaign Standard"
exl-id: cdb050b7-d327-42f7-b534-d32d988c8ffb
source-git-commit: 3f4400f24b75e8e435610afbe49e9d9444dbf563
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 97%

---

# Filtrage {#filtering}

## Récupérer les métadonnées des filtres

Des filtres sont disponibles pour chaque ressource. Pour identifier les filtres associés à une ressource, vous devez exécuter une requête GET sur les métadonnées de la ressource. Cette requête renvoie l’URL dans laquelle tous les filtres sont définis pour une ressource donnée. Pour plus d’informations sur les métadonnées, voir [cette section](metadata-mechanism.md).

Pour identifier les métadonnées d’un filtre et déterminer comment l’utiliser, vous devez exécuter une requête GET sur l’URL précédemment renvoyée.

<br/>

***Exemple de requête***

Les exemples de payloads ci-dessous montrent comment récupérer les métadonnées de filtre « byText » pour la ressource « profile ». Commencez par exécuter une requête GET sur les métadonnées de la ressource « profile ».

```
-X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/resourceType/profile \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

Elle renvoie l’URL où les filtres sont décrits.

```
{
"filters": {
        "href": "https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/resourceType/<PKEY>/filters/"
    }
  }
```

Exécutez une requête GET sur l’URL. Elle renvoie la liste des filtres pour la ressource « profile », avec les métadonnées associées à chaque filtre.

```
{
"birthday": {
        "PKey": "@FL-CbDFXbnHbXcVpeCGWL46VXJLn1LqxLMPagt2vz8sCxQ52lvB15KiUaxXkxJYQw-tZXYrgUWG6K8QcB4gxVY9RKoba5bRFY3294YFshDmorRr8",
        "category": "0150_profile",
        "condition": ...,
        "data": "https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/birthday?type=$value&precision=$value&operator=$value&day=$value&month=$value&includeStart=$value&endDay=$value&endMonth=$value&includeEnd=$value&relativeValue=$value&nextUnitsValue=$value&previousUnitsValue=$value",
        "formType": "webPage",
        "fragmentName": "",
        "label": "Birthday",
}
```

## Structure des métadonnées des filtres

Chaque filtre possède la même structure de métadonnées :

* Les champs **@formType** et **@webPage** sont techniques.
* Le champ **data** donne un exemple d’utilisation du filtre.
* Le nœud **metadata** décrit les paramètres du filtre.
* Le nœud **condition** décrit ce que le filtre est censé faire. Les paramètres de filtre décrits dans le nœud « metadata » sont utilisés pour créer des conditions de filtre. Pour chaque condition de filtre, si **enabledIf** est vrai, le contenu **expr** est appliqué.

<br/>

Exemple de structure de métadonnées de filtre :

```
"byText": {
        "PKey": "...",
        "category": "99_none",
        "condition": ...,
        "data": "/profileAndServices/profile/byText?text=$value",
        "formType": "none",
        "fragmentName": "",
        "label": "By name or email",
    }
```

## Utilisation de l’élément filters

Le filtrage est appliqué avec la requête suivante :

`GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/<resourceName>/by<filterName>?<filterParam>=<filterValue>`

Il est possible de combiner plusieurs filtres dans une seule requête :

`GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/<resourceName>/<filter1name>/<filter2name>?<filter1param>=<filter1value>&<filter2param>=<filter2value>`

<br/>

***Exemples de demande***

* Exemple de requête GET pour récupérer les ressources « service » avec le type « email ».

  ```
  -X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/service/byChannel?channel=email \
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
              "created": "2019-09-25 23:20:35.000Z",
              "href": "https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/service/@I_FIiDush4OQPc0mbOVR9USoh36Tt5CsD35lATvQjdWlXrYc0lFkvle2XIwZUbD8GqTVvSp8AfWFUvjkGMe1fPe5nok",
              "label": "Marketing Newsletter",
              "lastModified": "2019-09-25 23:20:35.000Z",
              "limitedDuration": false,
              "messageType": "email",
              "mode": "newsletter",
              ...
          },
          ...
      ],
      ...
  }
  ```

* Exemple de requête GET pour récupérer les ressources &quot;profile&quot; contenant &quot;Doe&quot; dans
les champs email ou nom (le filtre byText effectue une recherche dans les champs email et nom).

  ```
  -X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/byText?text=Doe \
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
          }
          ...
      ],
      ...
  }
  ```

* Exemple de requête GET pour récupérer les ressources « service » avec le type « email » et le libellé « sport ».

  ```
  -X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/service/byChannel/byText?channel=email&text=sport \
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
              "created": "2019-09-26 09:36:01.014Z",
              "href": "https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/service/<PKEY>",
              "label": "sport",
              "lastModified": "2019-09-26 09:36:01.014Z",
              "limitedDuration": false,
              "messageType": "email",
              "mode": "newsletter",
              "name": "SVC13",
              ...
          }
      ],
      ...
  }
  ```

## Filtres personnalisés

Si vous souhaitez utiliser un filtre personnalisé, vous devez le créer et le personnaliser dans l’interface d’Adobe Campaign Standard. Le filtre personnalisé aura alors le même comportement que les filtres prêts à l’emploi :

`GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServicesExt/<resourceName>/by<customFilterName>?<customFilterparam>=<customFilterValue>`

Pour plus d’informations à ce sujet, consultez la documentation relative à Campaign Standard :

* [Configuration de la définition des filtres](https://helpx.adobe.com/fr/campaign/standard/developing/using/configuring-filter-definition.html).
* [Cas pratique : appel d’une ressource à l’aide d’une clé d’identification composite](https://experienceleague.adobe.com/docs/campaign-standard/using/developing/adding-or-extending-a-resource/uc-calling-resource-id-key.html?lang=fr).

<br/>

***Exemple de requête***

Exemple de requête GET pour récupérer les ressources « profile » comportant des montants de transactions de 100 $ ou plus. Notez que le filtre « byAmount » a d’abord été défini dans l’interface Adobe Campaign Standard et lié à la table personnalisées « Transaction ».

```
-X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServicesExt/profile/byAmount?amount_parameter=100 \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

<!--
Response to the request.

```

{
    "content": [
        {
            "PKey": "<PKEY>",
            "builtIn": false,
            "created": "2019-09-26 09:36:01.014Z",
            "desc": "",
            "end": "",
            "href": "https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/<PKEY>",
            ...
        }
    ],
}

```

-->

<!-- exemple à vérifier de bout en bout-->

<!--+category = query editor
privacy ?
displayFOrmat ?
pour faire un POST sur une enum, il faut lui passer le @name décrit dans le noeud values, chaque @name a une correspondance en format = au format définit par le resType
-->





<!--
 if link ou collection.* resName +
* resTarget tout ca, ca va ensemble : le système de lien, resTarget va donner la ressource targetée par le lien. type
resType = type technique (long..) resType = link alors unbound='false' ou 'true'
If type = enumeration alors champ "values" rajouté et les valeurs sont dans values
pour faire un POST sur une enum, il faut lui passer le @name décrit dans le noeud values, chaque @name a une correspondance en format = au format définit par le resType
ail faut que la valeur poster soit conforme ,elle doit valider la dataPolicy . La dataPolicy peut soit controler la valeur (email invalide), soit transformé (cas du smartCase par exemple)
type dans les metadata = type de haut-niveau (nombre, text)
-->
