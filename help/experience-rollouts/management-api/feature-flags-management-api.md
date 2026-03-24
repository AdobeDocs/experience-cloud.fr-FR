---
title: API Feature flags management
description: Référence d’API pour l’API de gestion des indicateurs de fonctionnalité des déploiements d’expérience, y compris les points d’entrée pour obtenir, créer, mettre à jour et supprimer des indicateurs de fonctionnalité pour une application.
source-git-commit: 8a92b7a3e8c52da8bb2474f52c831e159420b878
workflow-type: tm+mt
source-wordcount: '650'
ht-degree: 14%

---


# API Feature flags management {#feature-flags-management-api}

L’API de gestion des indicateurs de fonctionnalité vous permet de créer, lire, mettre à jour et supprimer des indicateurs de fonctionnalité par programmation pour vos applications dans les déploiements d’expérience.

**Chemin de base :** `/m/api/v1/mgmt/feature`

Toutes les requêtes nécessitent les en-têtes décrits dans la [exigences communes](feature-management-apis-overview.md#common-requirements).

## Obtenir tous les indicateurs de fonctionnalités {#get-all-features}

Récupère tous les indicateurs de fonctionnalité pour une application spécifiée.

| | |
|---|---|
| **Point d’entrée** | `GET /m/api/v1/mgmt/feature` |
| **Méthode** | GET |

### Paramètres de requête {#get-all-query-params}

| Paramètre | Type | Description | Obligatoire |
|---|---|---|---|
| `clientId` | Entier | Identifiant numérique de l’application. Voir [Obtention de l’ID client](get-client-id.md). Obligatoire si `imsClientId` n’est pas fourni. | Conditionnel |
| `imsClientId` | Chaîne | Identifiant client au format chaîne de l’application. Obligatoire si `clientId` n’est pas fourni. | Conditionnel |
| `nonReleaseFeature` | Booléen | Définissez cette valeur sur `true` afin d’inclure des indicateurs de fonctionnalités indépendants qui ne sont associés à aucun groupe ou version. Obligatoire pour les workflows basés sur des API. | Oui |

### Réponse {#get-all-response}

| État | Description |
|---|---|
| `200` | Réussite. Le corps de la réponse contient une liste d’objets d’indicateur de fonctionnalité. |

Le corps de la réponse contient un tableau `features`. Chaque élément est un objet d’indicateur de fonctionnalité avec les champs décrits dans la référence d’objet [FeatureDTO](#featuredto-object).

**Exemple de réponse :**

```json
{
  "features": [
    {
      "id": 22079,
      "name": "new.FF.1",
      "clientId": 1191,
      "state": "enabled",
      "description": "first feature flag",
      "release": { "id": 2631, "name": "FF.group", "status": "SAVED" },
      "audience": null,
      "params": { "label": "new FF 1", "rolloutType": "manual" }
    },
    {
      "id": 22080,
      "name": "new.FF.2",
      "clientId": 1191,
      "state": "enabled",
      "description": "second feature flag",
      "audience": [
        {
          "id": 10034665,
          "criteria": { "and": [{ "operator": "EQ", "attr": "LOCALE", "val": "EN" }] }
        }
      ]
    }
  ]
}
```

## Obtenir l’indicateur de fonctionnalité par ID {#get-feature-by-id}

Récupère un indicateur de fonctionnalité unique par son identifiant numérique.

| | |
|---|---|
| **Point d’entrée** | `GET /m/api/v1/mgmt/feature/{featureId}` |
| **Méthode** | GET |

### Réponse {#get-by-id-response}

| État | Description |
|---|---|
| `200` | Réussite. Le corps de la réponse est un seul objet [FeatureDTO](#featuredto-object). |
| `400` | Identifiant de fonctionnalité non valide. |

## Créer un indicateur de fonctionnalité {#create-feature}

Crée un indicateur de fonctionnalité.

| | |
|---|---|
| **Point d’entrée** | `POST /m/api/v1/mgmt/feature` |
| **Méthode** | POST |

### Corps de la requête {#create-request-body}

Le corps de la requête est un objet [FeatureDTO](#featuredto-object). Les champs suivants sont requis pour la création :

| Champ | Obligatoire | Remarques |
|---|---|---|
| `name` | Oui | Clé de l’indicateur de fonctionnalité. 50 caractères maximum. Modèle : `^[a-zA-Z0-9_.-]*$` |
| `clientId` | Oui | Identifiant numérique de l’application. Voir [Obtention de l’ID client](get-client-id.md). |
| `state` | Oui | `"enabled"` ou `"disabled"`. |

### Réponse {#create-response}

| État | Description |
|---|---|
| `200` | Réussite. Le corps de la réponse contient `{ "generatedFeatureId": <id> }`. |
| `400` | Payload non valide. |
| `403` | Autorisations insuffisantes pour ce client ou cette règle d’audience. |
| `417` | Les utilisateurs dotés du rôle Développeur ne peuvent pas enregistrer une fonctionnalité avec une règle publique ; au moins une règle d’audience est requise. |

**Exemple de requête :**

```json
{
  "name": "my-new-feature",
  "clientId": 1191,
  "state": "disabled",
  "description": "A new feature flag",
  "meta": "VGVzdA==",
  "audience": [
    {
      "criteria": {
        "and": [{ "operator": "EQ", "attr": "COUNTRY", "category": "default", "ruleId": 1, "val": "US" }]
      }
    }
  ],
  "variations": [{ "variantPercentage": 100, "variantName": "Variation 1" }],
  "params": { "label": "My New Feature", "tags": [] }
}
```

## Indicateur de fonctionnalité de mise à jour {#update-feature}

Met à jour un indicateur de fonctionnalité existant. Transmettez l’objet [FeatureDTO complet](#featuredto-object) y compris le champ `id`.

| | |
|---|---|
| **Point d’entrée** | `PUT /m/api/v1/mgmt/feature` |
| **Méthode** | PUT |

### Réponse {#update-response}

| État | Description |
|---|---|
| `200` | Réussite. Le corps de la réponse est l’objet FeatureDTO mis à jour. |
| `400` | Payload non valide. |
| `403` | Autorisations insuffisantes. |
| `417` | Conflit de mise à jour simultanée. Récupérez d’abord la fonctionnalité active et réessayez avec la dernière valeur de `version` de `params`. |

## Supprimer l&#39;indicateur de fonctionnalité {#delete-feature}

Supprime un indicateur de fonctionnalité par son identifiant numérique.

| | |
|---|---|
| **Point d’entrée** | `DELETE /m/api/v1/mgmt/feature/{featureId}` |
| **Méthode** | DELETE |

### Réponse {#delete-response}

| État | Description |
|---|---|
| `204` | Réussite. Pas de corps de réponse. |
| `403` | Autorisations insuffisantes. |

## Référence d’objet FeatureDTO {#featuredto-object}

| Champ | Type | Description | Obligatoire |
|---|---|---|---|
| `id` | Entier | Identifiant de l’indicateur de fonctionnalité. Requis uniquement pour les appels de mise à jour. | Conditionnel |
| `name` | Chaîne | Clé de l’indicateur de fonctionnalité (renvoyée dans les réponses de l’API). 50 caractères max. Modèle : `^[a-zA-Z0-9_.-]*$` | Oui (créer) |
| `clientId` | Entier | Identifiant numérique de l’application. | Oui |
| `state` | Chaîne | `"enabled"` ou `"disabled"`. | Oui |
| `meta` | Chaîne | Métadonnées codées en Base64 renvoyées avec la fonctionnalité dans les réponses de l’API. 1 024 caractères max. | Non |
| `description` | Chaîne | Afficher la description. 225 caractères maximum. | Non |
| `audience` | Tableau | Liste des règles d’audience. Voir [Objet FeatureRule](#featurerule-object). Utilisez [Obtenir les critères d’audience souhaités](get-audience-criteria.md) pour générer ceci. | Non |
| `variations` | Tableau | Liste des variantes. 3 max. Voir [Objet FeatureVariation](#featurevariation-object). | Non |
| `params` | Objet | Métadonnées supplémentaires. Clés prises en charge : `label` (nom d’affichage dans l’interface utilisateur), `tags` (tableau de chaînes). | Non |
| `release` | Objet | Association version/groupe. `null` si l’indicateur ne fait pas partie d’un groupe. Lecture seule. | Non |

### Objet FeatureVariation {#featurevariation-object}

| Champ | Type | Description | Obligatoire |
|---|---|---|---|
| `id` | Entier | ID de variation. Requis uniquement pour les appels de mise à jour. | Conditionnel |
| `variantName` | Chaîne | Nom de la variante. Valeurs fixes : `"Variation 1"`, `"Variation 2"`, `"Variation 3"`. | Oui |
| `variantPercentage` | Décimal | Pourcentage de l’audience recevant cette variante. Doit être supérieur à 0 et ne pas dépasser 100, avec jusqu’à 2 décimales. | Oui |

### Objet FeatureRule {#featurerule-object}

| Champ | Type | Description | Obligatoire |
|---|---|---|---|
| `id` | Entier | ID de règle. Requis uniquement pour les appels de mise à jour. Définissez sur `null` lors de l’ajout d’une nouvelle règle. | Conditionnel |
| `criteria` | Objet | Objet de condition définissant la règle d’audience. Voir [Objet de condition](#condition-object). | Oui |

### Objet de condition {#condition-object}

| Champ | Type | Description |
|---|---|---|
| `and` | Tableau\&lt;Condition\> | Toutes les conditions doivent être vraies. |
| `or` | Tableau\&lt;Condition\> | Au moins une condition doit être vraie. |
| `not` | Condition | Cette condition doit être false. |
| `attr` | Chaîne | Attribut utilisateur à évaluer (par exemple, `COUNTRY`, `LOCALE`). |
| `operator` | Chaîne | Opérateur de comparaison (par exemple, `EQ`, `IN`, `LT`). |
| `val` | Chaîne | Valeur par rapport à laquelle comparer. |
| `meta` | Objet | Métadonnées de condition facultatives. `desc` définit le libellé d’affichage dans l’interface utilisateur. |

Chaque condition doit comporter soit `and`, `or` ou `not`, soit une combinaison de `attr`, `operator` et `val`.

## Voir également {#see-also}

* [Présentation des API de gestion des fonctionnalités](feature-management-apis-overview.md)
* [API de correctif de gestion](management-patch-api.md)
* [Obtention de l’identifiant client pour une application](get-client-id.md)
* [Obtenir les critères d’audience souhaités](get-audience-criteria.md)
