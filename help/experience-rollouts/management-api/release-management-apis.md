---
title: API Release Management
description: Référence d’API pour les API de gestion des versions des déploiements d’expérience, y compris les points d’entrée pour obtenir, créer et modifier des versions et des groupes de fonctionnalités interéquipes.
exl-id: e8d1d025-0645-4cf2-921f-d94c9f71282d
source-git-commit: 454b5c719a5f8be82d1ed835da58bfca6316def2
workflow-type: tm+mt
source-wordcount: '490'
ht-degree: 15%

---

# API Release Management {#release-management-apis}

Les API Release Management vous permettent de récupérer, créer et modifier des versions et des groupes de fonctionnalités interéquipes (CTFG) par programmation. Ces API utilisent le point d’entrée de gestion v2.

**Chemin de base :** `/m/api/v2/mgmt/release`

Toutes les requêtes nécessitent les en-têtes décrits dans la section [exigences communes](feature-management-apis-overview.md#common-requirements), ainsi que l’en-tête supplémentaire répertorié ci-dessous.

## En-tête supplémentaire obligatoire {#additional-header}

| Header | Description | Obligatoire |
|---|---|---|
| `x-user-context-org` | Identifiant numérique d’équipe pour votre organisation. Cette valeur se trouve dans la console Déploiements d’expérience sous les paramètres de votre équipe. | Oui |

## Obtenir la version par ID {#get-release}

Récupère une version unique ou un groupe de fonctionnalités inter-équipes par son identifiant numérique.

| | |
|---|---|
| **Point d’entrée** | `GET /m/api/v2/mgmt/release/{id}` |
| **Méthode** | GET |

### Paramètres de requête {#get-query-params}

| Paramètre | Type | Description | Par défaut |
|---|---|---|---|
| `includePermissions` | Booléen | Incluez des autorisations de mise à jour ou de suppression de cette version. | `true` |
| `includeOrg` | Booléen | Incluez les informations sur l’organisation pour cette version. | `true` |
| `includeAnalyzeInfo` | Booléen | Incluez les informations d’analyse. | `false` |

### Réponse {#get-response}

| État | Description |
|---|---|
| `200` | Réussite. Le corps de la réponse est un objet de libération. Voir [Référence de l&#39;objet de libération](#release-object). |
| `400` | ID de version non valide ou requête incorrecte. |

## Créer une version {#create-release}

Crée une nouvelle version ou un groupe de fonctionnalités interéquipes.

| | |
|---|---|
| **Point d’entrée** | `POST /m/api/v2/mgmt/release` |
| **Méthode** | POST |

### Corps de la requête {#create-request-body}

Le corps de la requête utilise l’[objet Release](#release-object). Pour la création, `status` doit être défini sur `"SAVED"` pour les groupes de fonctionnalités inter-équipes (type `CROSS_TEAM_FEATURE_GROUP`) ou `"DRAFT"` pour les versions standard (type `RELEASE`).

**Exemple — créer un groupe de fonctionnalités inter-équipes :**

```json
{
  "params": {
    "rolloutType": "manual",
    "cohortingType": "guid",
    "tags": [],
    "canContextOverridePUP": false,
    "label": "my-cross-team-group"
  },
  "status": "SAVED",
  "type": "CROSS_TEAM_FEATURE_GROUP",
  "name": "my-cross-team-group",
  "description": null,
  "meta": "",
  "variations": [{ "variantPercentage": 100, "variantName": "Variant 1", "features": [] }],
  "audience": [{}],
  "clients": [],
  "pollInterval": 300,
  "org": { "id": "95" },
  "comment": ""
}
```

### Réponse {#create-response}

| État | Description |
|---|---|
| `200` | Réussite. Le corps de la réponse est l’objet de version créé. |
| `400` | Payload non valide. |

## Modifier la version {#edit-release}

Met à jour une version existante ou un groupe de fonctionnalités interéquipes. Transmettez l’objet de version complète, y compris le champ `id`.

| | |
|---|---|
| **Point d’entrée** | `PUT /m/api/v2/mgmt/release/{id}` |
| **Méthode** | PUT |

### Réponse {#edit-response}

| État | Description |
|---|---|
| `200` | Réussite. Le corps de la réponse est l’objet de version mis à jour. |
| `417` | Conflit de mise à jour simultanée. La version a été modifiée entre vos appels GET et PUT. Récupérez la version actuelle et réessayez. |

## Référence d’objet de version {#release-object}

| Champ | Type | Description | Obligatoire |
|---|---|---|---|
| `id` | Entier | ID de version. Requis uniquement pour les appels de mise à jour. | Conditionnel |
| `name` | Chaîne | Nom de la version. 50 caractères max. Modèle : `^[a-zA-Z0-9_ ,.:()-]*$`. Doit être unique. | Oui |
| `description` | Chaîne | Description facultative. 255 caractères maximum. | Non |
| `type` | Chaîne | `"RELEASE"` pour les versions standard ; `"CROSS_TEAM_FEATURE_GROUP"` pour les groupes de fonctionnalités interéquipes. | Oui |
| `status` | Chaîne | État de la version. Pour IMS : `"DRAFT"` à la création ; `"DRAFT"`, `"SAVED"`, `"PUBLISHED"` à la mise à jour. Pour CTFG : `"SAVED"` à la création ; `"SAVED"`, `"PUBLISHED"` à la mise à jour. | Oui |
| `clients` | Tableau | Applications associées à cette version. Chaque entrée nécessite `id` (numérique) et `imsClientId` (chaîne). | Non |
| `audience` | Tableau | Liste des règles d’audience. Voir [Objet de condition](feature-flags-management-api.md#condition-object). | Non |
| `variations` | Tableau | Liste des variations. Une seule variation est prise en charge lors de l’envoi. | Requis pour l’envoi |
| `params` | Objet | Paramètres de version. Voir [Champs de paramètres pris en charge](#supported-params). | Requis pour l’envoi |
| `org` | Objet | Objet Organisation. Doit inclure `id`. | Non |

### Champs de paramètres pris en charge {#supported-params}

| Champ | Type | Description | Obligatoire |
|---|---|---|---|
| `label` | Chaîne | Nom d’affichage. 50 caractères max. | Oui |
| `tags` | Tableau\&lt;Chaîne\> | Balises facultatives. 50 caractères maximum chacun. | Non |
| `canContextOverridePUP` | Booléen | Si `true`, les règles de contexte remplacent les règles de profil. Valeur par défaut : `false`. | Oui |
| `isBetaRelease` | Booléen | Si `true`, le marque comme version bêta. Valeur par défaut : `false`. | Non |

### Objet de variation {#variation-object}

| Champ | Type | Description | Obligatoire |
|---|---|---|---|
| `id` | Entier | ID de variation. Requis uniquement pour les appels de mise à jour. | Conditionnel |
| `variantName` | Chaîne | Nom de la variante. 50 caractères max. | Oui |
| `variantPercentage` | Double | Pourcentage de l’audience recevant cette variante. Plage : [0, 100]. | Oui |
| `features` | Tableau | Fonctionnalités incluses dans cette variation. Chaque entrée doit inclure `id`, `name`, `clientId` et `state`. | Non |

## Voir également {#see-also}

* [Présentation des API de gestion des fonctionnalités](feature-management-apis-overview.md)
* [API Feature flags management](feature-flags-management-api.md)
* [API Feature group Management](feature-group-management-api.md)
