---
title: API de correctif de gestion
description: Utilisez l'API PATCH des déploiements d'expérience pour mettre à jour les champs individuels d'un indicateur de fonctionnalité, d'un groupe de fonctionnalités ou d'un groupe de fonctionnalités interéquipes sans transmettre l'objet complet.
source-git-commit: 6ecedbfc6c7de392f214f3f8f2e71aa18e1bacb9
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 4%

---


# API de correctif de gestion {#management-patch-api}

L&#39;API PATCH vous permet de mettre à jour des champs spécifiques d&#39;un indicateur de fonctionnalité, d&#39;un groupe de fonctionnalités ou d&#39;un groupe de fonctionnalités inter-équipes sans envoyer l&#39;objet complet dans le corps de la requête. Cela s’avère utile pour les mises à jour ciblées, telles que la modification d’une règle d’audience, le basculement d’état ou l’ajustement d’un pourcentage de variation.

## Indicateur de fonctionnalité PATCH {#feature-flag-patch}

Met à jour un ou plusieurs champs d&#39;un indicateur de fonctionnalité.

| | |
|---|---|
| **Point d’entrée** | `PATCH /m/api/v1/mgmt/feature/{featureFlagId}` |
| **Méthode** | PATCH |

### En-têtes de requête {#ff-request-headers}

Toutes les requêtes nécessitent les en-têtes décrits dans la [exigences communes](feature-management-apis-overview.md#common-requirements).

### Paramètre de chemin {#ff-path-param}

| Paramètre | Type | Description | Obligatoire |
|---|---|---|---|
| `featureFlagId` | Entier | Identifiant numérique de l’indicateur de fonctionnalité à mettre à jour. | Oui |

### Corps de la requête {#ff-request-body}

Transmettez uniquement les champs à mettre à jour. La réponse renvoie toujours l’objet d’indicateur de fonctionnalité mis à jour complet.

**Exemple — mettre à jour la description uniquement :**

```json
{
  "description": "Updated description"
}
```

**Exemple — supprimer une audience existante :**

```json
{
  "audience": null
}
```

**Exemple — ajouter une nouvelle audience alors qu&#39;elle n&#39;existait pas :**

```json
{
  "audience": [
    {
      "criteria": {
        "and": [
          { "operator": "EQ", "attr": "sandboxType", "val": "DEVELOPMENT", "ruleId": 1, "category": "contextual" }
        ]
      }
    }
  ]
}
```

**Exemple — mettre à jour une règle d&#39;audience existante :**

```json
{
  "audience": [
    {
      "id": 10020035,
      "criteria": {
        "and": [
          { "operator": "EQ", "attr": "sandboxType", "val": "PRODUCTION", "ruleId": 1, "category": "contextual" }
        ]
      }
    }
  ]
}
```

**Exemple — état de modification et pourcentage de variation :**

```json
{
  "state": "disabled",
  "variations": [
    {
      "id": 10017188,
      "variantName": "Variation 1",
      "variantPercentage": 80.0
    }
  ]
}
```

>[!NOTE]
>
>Lors de la mise à jour d’une règle d’audience existante, incluez la `id` de la règle (disponible dans la réponse de la fonctionnalité GET) pour la mettre à jour. Lors de la mise à jour des variations, incluez la `id` de la variation pour éviter de créer un doublon.

### Réponse {#ff-response}

| État | Description |
|---|---|
| `200` | Réussite. Le corps de la réponse est l’objet d’indicateur de fonctionnalité complet mis à jour. |
| `400` | Payload non valide. |
| `403` | Autorisations insuffisantes. |
| `417` | Conflit de mise à jour simultanée. Récupérez la fonctionnalité actuelle et réessayez. |

## PATCH du groupe de fonctionnalités {#feature-group-patch}

Met à jour un ou plusieurs champs d&#39;un groupe de fonctionnalités. La structure de la requête et de la réponse est identique à celle de l’indicateur de fonctionnalité PATCH, seul le point d’entrée diffère.

| | |
|---|---|
| **Point d’entrée** | `PATCH /m/api/v1/mgmt/group/{featureGroupId}` |
| **Méthode** | PATCH |

## PATCH du groupe de fonctionnalités multi-équipes {#ctfg-patch}

Met à jour un ou plusieurs champs d&#39;un groupe de fonctionnalités multi-équipes. Utilise le point d’entrée de la version v2.

| | |
|---|---|
| **Point d’entrée** | `PATCH /m/api/v2/mgmt/release/{CTFGId}` |
| **Méthode** | PATCH |

## Voir également {#see-also}

* [API Feature flags management](feature-flags-management-api.md)
* [API Feature group Management](feature-group-management-api.md)
* [API Release Management](release-management-apis.md)
* [Présentation des API de gestion des fonctionnalités](feature-management-apis-overview.md)
