---
title: Obtenir les critères d’audience souhaités
description: Découvrez comment générer la structure JSON des critères d’audience appropriée à utiliser dans les API de gestion des déploiements d’expérience à l’aide de la console et de l’API de fonctionnalité GET.
source-git-commit: 6ecedbfc6c7de392f214f3f8f2e71aa18e1bacb9
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 1%

---


# Obtenir les critères d’audience souhaités {#get-audience-criteria}

Le champ Critères d’audience dans les API de gestion utilise un format JSON structuré qui peut être complexe à écrire manuellement. L’approche recommandée consiste à créer l’audience souhaitée à l’aide de la console, puis à récupérer sa représentation JSON via l’API.

## Étapes {#steps}

Pour obtenir le fichier JSON pour un critère d’audience souhaité, procédez comme suit :

1. Dans la console Déploiements d’expérience , créez un indicateur de fonctionnalité temporaire avec les critères d’audience que vous souhaitez utiliser dans votre appel API.
2. Après l’enregistrement, notez l’identifiant de l’indicateur de fonctionnalité dans l’URL du navigateur. L’ID apparaît dans l’URL après l’ID client. Par exemple, dans `.../feature-flags/1191/22080`, l’ID de la fonctionnalité est `22080`.
3. Appelez le point d’entrée [Get Feature by ID](feature-flags-management-api.md#get-feature-by-id) avec cet identifiant de fonctionnalité.
4. Dans le fichier JSON de réponse, recherchez le champ `audience` . Contient la structure exacte des critères d’audience dont vous avez besoin.
5. Copiez la valeur `audience`, en supprimant l’attribut `id` de chaque objet de règle. Utilisez-le dans votre appel API de fonction Créer ou Mettre à jour .

## Exemple {#example}

Après avoir appelé GET `/m/api/v1/mgmt/feature/22080`, la réponse inclut :

```json
{
  "audience": [
    {
      "id": 10034665,
      "criteria": {
        "and": [
          {
            "operator": "EQ",
            "attr": "LOCALE",
            "val": "EN",
            "ruleId": 1,
            "category": "default"
          }
        ]
      }
    }
  ]
}
```

Pour l’utiliser dans un appel de création de fonction, supprimez le champ `id` de l’objet audience :

```json
{
  "audience": [
    {
      "criteria": {
        "and": [
          {
            "operator": "EQ",
            "attr": "LOCALE",
            "val": "EN",
            "ruleId": 1,
            "category": "default"
          }
        ]
      }
    }
  ]
}
```

## Voir également {#see-also}

* [API Feature flags management](feature-flags-management-api.md)
* [Obtention de l’identifiant client pour une application](get-client-id.md)
* [API de correctif de gestion](management-patch-api.md)
