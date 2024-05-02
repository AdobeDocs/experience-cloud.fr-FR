---
title: Pagination
description: Découvrez comment effectuer des opérations de pagination.
audience: developing
content-type: reference
topic-tags: campaign-standard-apis
role: Data Engineer
level: Experienced
badge: label="DISPONIBILITÉ LIMITÉE" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Limité aux utilisateurs migrés Campaign Standard"
exl-id: d6ebce3c-1e84-4b3b-a68d-90df4680af64
source-git-commit: 3f4400f24b75e8e435610afbe49e9d9444dbf563
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 94%

---

# Pagination

Par défaut, 25 ressources sont chargées dans une liste.

Le paramètre **_lineCount** permet de limiter le nombre de ressources répertoriées dans la réponse. Vous pouvez ensuite utiliser le nœud **suivant** pour afficher les résultats suivants.

>[!NOTE]
>
>Utilisez toujours la valeur d’URL renvoyée dans le nœud **suivant** pour effectuer une requête de pagination.
>
>La requête **_lineStart** est calculée et doit toujours être utilisée dans l’URL renvoyée dans le nœud **suivant**.

<br/>

***Exemple de requête***

Exemple de requête GET pour afficher 1 enregistrement de la ressource de profil.

```
-X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile?_lineCount=1 \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

Réponse à la requête, avec le nœud **suivant** pour effectuer la pagination.

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
    ],
    "next": {
        "href": "https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/email?_lineCount=10&_
        lineStart=@Qy2MRJCS67PFf8soTf4BzF7BXsq1Gbkp_e5lLj1TbE7HJKqc"
    }
    ...
}
```

Par défaut, le nœud **suivant** n’est pas disponible lors de l’interaction avec des tableaux contenant une grande quantité de données. Pour pouvoir effectuer une pagination, vous devez ajouter le paramètre **_forcePagination=true** à votre URL d’appel.

```
-X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile?_forcePagination=true \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

>[!NOTE]
>
>Le nombre d’enregistrements au-dessus duquel un tableau est considéré comme volumineux est défini dans l’option **XtkBigTableThreshold** de Campaign Standard. La valeur par défaut est 100 000 enregistrements.
