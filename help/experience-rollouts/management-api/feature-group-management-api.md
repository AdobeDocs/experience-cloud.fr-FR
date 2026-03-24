---
title: API Feature group Management
description: Référence d’API pour l’API de gestion des groupes de fonctionnalités des déploiements d’expérience, y compris les points d’entrée pour obtenir, créer, mettre à jour, supprimer et contrôler les plans de déploiement pour les groupes de fonctionnalités.
source-git-commit: 8a92b7a3e8c52da8bb2474f52c831e159420b878
workflow-type: tm+mt
source-wordcount: '614'
ht-degree: 16%

---


# API Feature group Management {#feature-group-management-api}

L’API de gestion des groupes de fonctionnalités vous permet de créer, lire, mettre à jour et supprimer des groupes de fonctionnalités par programmation dans les déploiements d’expérience, y compris les plans de déploiement de tests A/B et automatisés.

**Chemin de base :** `/m/api/v1/mgmt/group`

Toutes les requêtes nécessitent les en-têtes décrits dans la [exigences communes](feature-management-apis-overview.md#common-requirements).

## Obtenir tous les groupes de fonctionnalités {#get-all-groups}

Récupère tous les groupes de fonctionnalités de votre organisation.

| | |
|---|---|
| **Point d’entrée** | `GET /m/api/v1/mgmt/group` |
| **Méthode** | GET |

### Paramètres de requête {#get-all-query-params}

| Paramètre | Type | Description | Obligatoire |
|---|---|---|---|
| `myOrg` | Booléen | Définissez sur `true` pour inclure les informations sur l’organisation. | Oui |
| `includeClientInfo` | Booléen | Définissez cette valeur sur `true` afin d’inclure les informations d’application pour chaque groupe. | Oui |

### Réponse {#get-all-response}

| État | Description |
|---|---|
| `200` | Réussite. Le corps de la réponse est un tableau d&#39;objets de groupe de fonctionnalités. |

## Obtenir le groupe de fonctionnalités par ID {#get-group-by-id}

Récupère un seul groupe de fonctionnalités par son identifiant numérique.

| | |
|---|---|
| **Point d’entrée** | `GET /m/api/v1/mgmt/group/{groupId}` |
| **Méthode** | GET |
| **Paramètre de requête** | `includeAnalyzeInfo=true` (facultatif — ajoute les données d’analyse à la réponse) |

### Réponse {#get-by-id-response}

| État | Description |
|---|---|
| `200` | Réussite. Le corps de la réponse est un objet de groupe de fonctionnalités. |
| `400` | Identifiant de groupe de fonctionnalités non valide. |

## Créer un groupe de fonctionnalités {#create-group}

Crée un groupe de fonctionnalités avec un type de déploiement de test A/B manuel, automatisé ou .

| | |
|---|---|
| **Point d’entrée** | `POST /m/api/v1/mgmt/group` |
| **Méthode** | POST |

### Corps de la requête {#create-request-body}

Le corps de la requête utilise l’objet [groupe de fonctionnalités](#feature-group-object). La `rolloutType` à l’intérieur de `params` est obligatoire et détermine la structure de la payload.

**Exemple — déploiement manuel :**

```json
{
  "params": {
    "rolloutType": "manual",
    "label": "my-feature-group",
    "tags": [],
    "canContextOverridePUP": false
  },
  "status": "SAVED",
  "type": "group",
  "name": "my.feature.group",
  "description": "A manual feature group",
  "variations": [{ "variantPercentage": 100, "variantName": "Variant 1", "features": [] }],
  "audience": [{ "criteria": { "and": [{ "operator": "EQ", "attr": "COUNTRY", "val": "US", "ruleId": 1, "category": "default" }] } }],
  "clients": [],
  "org": { "id": 95 }
}
```

**Exemple — déploiement automatisé :**

```json
{
  "params": { "rolloutType": "automated", "label": "my-automated-group", "tags": [] },
  "status": "SAVED",
  "type": "group",
  "name": "my.automated.group",
  "variations": [{ "variantPercentage": 100, "variantName": "Variant 1", "features": [] }],
  "phaseRollOutPlan": {
    "phaseRollOutBlocks": [
      { "isPhaseBlock": true, "phaseRule": { "audience": [] }, "waitRule": null, "blockId": 1, "blockName": "", "isBlockActivated": false },
      { "isPhaseBlock": false, "phaseRule": null, "waitRule": { "waitDuration": { "val": "2", "unit": "HOURS" } }, "blockId": 2, "blockName": "", "isBlockActivated": false },
      { "isPhaseBlock": true, "phaseRule": { "audience": [] }, "waitRule": null, "blockId": 3, "blockName": "", "isBlockActivated": false }
    ],
    "rollOutPlanState": "DRAFT"
  },
  "clients": [],
  "org": { "id": 95 }
}
```

### Réponse {#create-response}

| État | Description |
|---|---|
| `200` | Réussite. Le corps de la réponse est l&#39;objet du groupe de fonctionnalités créé. |
| `400` | Payload non valide : voir [messages d’erreur](#error-messages) pour plus de détails. |
| `403` | Autorisations insuffisantes. |

## Mettre à jour le groupe de fonctionnalités {#update-group}

Met à jour un groupe de fonctionnalités existant. Transmettez la même structure que le corps de la requête de création, y compris le champ `id`.

| | |
|---|---|
| **Point d’entrée** | `PUT /m/api/v1/mgmt/group` |
| **Méthode** | PUT |

### Réponse {#update-response}

| État | Description |
|---|---|
| `200` | Réussite. Le corps de la réponse est l&#39;objet du groupe de fonctionnalités mis à jour. |
| `400` | Payload non valide. |
| `403` | Autorisations insuffisantes. |

## Suspendre, reprendre ou abandonner un plan de déploiement {#pause-resume-abort}

Contrôle l’exécution d’un plan de déploiement de tests A/B ou automatisés en cours.

| Action | Point d’entrée |
|---|---|
| **Reprendre** | `POST /m/api/v1/mgmt/phaserollout/resume` |
| **Pause** | `POST /m/api/v1/mgmt/phaserollout/pause` |
| **Abandon** | `POST /m/api/v1/mgmt/phaserollout/abort` |

### Corps de la requête {#control-request-body}

```json
{
  "entityId": 10282,
  "fgEntityType": "GROUP"
}
```

### Réponse {#control-response}

Renvoie `true` en cas de succès.

## Supprimer le groupe de fonctionnalités {#delete-group}

Supprime un groupe de caractéristiques par son identifiant numérique.

| | |
|---|---|
| **Point d’entrée** | `DELETE /m/api/v1/mgmt/group/{groupId}` |
| **Méthode** | DELETE |

### Réponse {#delete-response}

| État | Description |
|---|---|
| `204` | Réussite. Pas de corps de réponse. |
| `403` | Autorisations insuffisantes. |

## Référence d’objet de groupe de fonctionnalités {#feature-group-object}

| Champ | Type | Description | Obligatoire |
|---|---|---|---|
| `id` | Entier | Identifiant du groupe de fonctionnalités. Requis uniquement pour les appels de mise à jour. | Conditionnel |
| `name` | Chaîne | Clé du groupe de fonctionnalités. 50 caractères max. Modèle : `^[a-zA-Z0-9_.-]*$` | Oui (créer) |
| `clients` | Tableau | Applications associées au groupe. Chaque entrée doit inclure `id` et `imsClientId`. | Oui |
| `status` | Chaîne | `"SAVED"` ou `"PUBLISHED"`. | Oui |
| `type` | Chaîne | Toujours `"group"` pour les groupes de fonctionnalités. | Oui |
| `org` | Objet | Détails de l’organisation. Doit inclure `id`. | Oui |
| `params` | Objet | Paramètres du groupe. `rolloutType` est obligatoire (`"manual"`, `"automated"` ou `"ab-testing"`). Prend également en charge `label` et `tags`. | Oui |
| `audience` | Tableau | Règles d’audience pour les types de déploiement manuels. | Non |
| `variations` | Tableau | Liste des variantes. Voir [Objet FeatureGroupVariation](#featuregroupvariation-object). | Non |
| `phaseRollOutPlan` | Objet | Plan de déploiement de la phase. Requis pour les types de tests A/B et automatisés. Voir [Objet PhaseRollOutPlan](#phaserolloutplan-object). | Conditionnel |
| `description` | Chaîne | Description d’affichage facultative. 225 caractères maximum. | Non |

### Objet FeatureGroupVariation {#featuregroupvariation-object}

| Champ | Type | Description | Obligatoire |
|---|---|---|---|
| `id` | Entier | ID de variation. Requis uniquement pour les appels de mise à jour. | Conditionnel |
| `variantName` | Chaîne | Nom de la variante. Codé en dur pour `"Variant 1"`. | Oui |
| `variantPercentage` | Décimal | Pourcentage de l’audience recevant cette variante. Doit être supérieur à 0 et ne pas dépasser 100. | Oui |

### Objet PhaseRollOutPlan {#phaserolloutplan-object}

| Champ | Type | Description | Obligatoire |
|---|---|---|---|
| `phaseRollOutBlocks` | Tableau | Liste ordonnée des blocs de phase et des blocs d’attente. Le dernier bloc doit être un bloc de phase. | Oui |
| `rollOutPlanState` | Chaîne | `"DRAFT"`, `"RUNNING"`, `"PAUSED"` ou `"ABORTED"` | Oui |

Chaque bloc dans `phaseRollOutBlocks` est soit un **bloc de phase** (`isPhaseBlock: true`) contenant un `phaseRule` avec des critères d’audience, soit un **bloc d’attente** (`isPhaseBlock: false`) contenant un `waitRule` avec un `waitDuration` (relatif) ou `executionDate` (horodatage fixe).

## Messages d’erreur {#error-messages}

| Condition | Statut | Message d’erreur |
|---|---|---|
| Nom non valide ou vide | 400 | `Error: Invalid value for release name.` |
| Critères d’audience vides | 400 | `Error: Release is not valid` |
| Variantes multiples pour le type automatisé | 400 | `Error: Feature variation is not valid. Variation name should be unique across variations` |
| Groupe publié sans clients | 400 | `Error: At least one client must be associated with enabled feature group.` |
| Le dernier bloc du plan n&#39;est pas un bloc de phases | 400 | `Error: The last block in the Phase Rollout plan should be phase block` |
| Délais de bloc d&#39;attente dans le désordre | 400 | `Error: Wait block timings are not in order in the phase rollout plan` |
| Types de blocs d’attente incohérents | 400 | `Error: Wait block should be of same type.` |
| Edition d&#39;un bloc de phase activé | 400 | `Error: Activated phase block should not be changed` |
| Type de déploiement vide | 400 | `Error: Rollout type cannot be empty while feature group creation` |
| Plan de phase réussi avec le type manuel | 400 | `Error: PhaseRollOutPlan can't be added with manual rollout type while feature group creation` |
| Planning transmis avec statut PUBLIÉ | 400 | `Error: Schedule can't be added in published state while release/group creation` |

## Voir également {#see-also}

* [Présentation des API de gestion des fonctionnalités](feature-management-apis-overview.md)
* [API Feature flags management](feature-flags-management-api.md)
* [API de correctif de gestion](management-patch-api.md)
* [Créer un déploiement automatisé](../guides/automated-rollouts/create-automated-rollout.md)
