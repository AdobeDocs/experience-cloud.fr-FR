---
title: API de fonctionnalités GET V2
description: Référence d’API pour l’API de fonctionnalité Déploiements d’expérience V2, utilisée pour récupérer les indicateurs de fonctionnalité pour les applications de bureau.
source-git-commit: 6ecedbfc6c7de392f214f3f8f2e71aa18e1bacb9
workflow-type: tm+mt
source-wordcount: '525'
ht-degree: 12%

---


# API de fonctionnalités GET V2 {#get-feature-api-v2}

L’API Feature V2 est conçue pour l’intégration d’applications de bureau. Il récupère les indicateurs de fonctionnalité et les données de version de l’utilisateur authentifié, le code de produit et la version du produit pris en charge comme identifiant de l’application en plus d’un identifiant client standard.

**Endpoint:** `GET {HOST}/fg/api/v2/feature`

Utilisez `https://p13-stage.adobe.io` pour l’évaluation et `https://p13n.adobe.io` pour la production.

## Requête {#request}

### En-têtes de requête {#request-headers}

| Header | Type | Description | Obligatoire |
|---|---|---|---|
| `x-api-key` | Chaîne | Clé API de votre application à partir du Adobe Developer Console. Doit être configuré séparément pour l’évaluation et la production. | Oui |
| `Authorization` | Chaîne | `Bearer <AccessToken>` ou `Bearer <ServiceToken>`. | Oui |
| `x-adobe-uuid` | Chaîne | Identifiant visiteur ou appareil unique. Utilisé pour le déploiement en pourcentage dans les scénarios non authentifiés et pour maintenir la fidélité de la session. | Non |

### Paramètres de requête {#query-parameters}

| Paramètre | Type | Description | Obligatoire |
|---|---|---|---|
| `clientId` | Chaîne | Identifiant client de l’application, tel qu’intégré dans la console Déploiements d’expérience. Plusieurs valeurs peuvent être transmises : `clientId=C1&clientId=C2`. | Non |
| `p` | Chaîne | Produit, version, plateforme, chaîne de paramètres régionaux (format PVPL). Exemple : `PHSP:17.0:WIN:en_US`. Plusieurs valeurs peuvent être transmises : `p=PHSP:17.0:WIN:en_US&p=PPRO:8:WIN:en_US`. Seuls le code et la version du produit sont utilisés dans l’évaluation. | Non |
| `meta` | Booléen | Si `true`, des métadonnées codées en Base64 sont renvoyées pour chaque fonctionnalité. Valeur par défaut : `false`. | Non |
| *Paramètres contextuels* | S.O. | Toute paire clé-valeur supplémentaire est traitée comme une variable contextuelle pour l’évaluation des règles d’audience. Exemple : `clientLanguage=ja_JP&contractCurrency=JPY`. | Non |

>[!NOTE]
>
>Au moins l’un des `clientId` ou `p` est requis pour identifier l’application.

## Réponse {#response}

### Codes d’état de réponse {#response-status}

| Code d’état | Description |
|---|---|
| `200 OK` | Les données d’indicateur de fonctionnalité sont renvoyées dans le corps de la réponse. |
| `304 Not Modified` | L’ETag correspond à l’état actuel du serveur. Traiter comme un no-op : aucune modification à appliquer. |
| `401 Unauthorized` | Le jeton d’autorisation est non valide. |

### En-têtes de réponse {#response-headers}

| Header | Description |
|---|---|
| `x-request-id` | Identifiant de requête unique pour le débogage. Incluez-le dans toute demande d’assistance. |
| `ETag` | Jeton représentant l’état actuel de la fonctionnalité pour l’utilisateur. Transmettez comme `If-None-Match` dans les requêtes suivantes. Renvoie `304` si inchangé. |
| `x-adobe-fg-poll-interval` | Durée de vie en secondes du cache local du client. Rappelez l’API uniquement après la fin de cet intervalle. |

### Corps de réponse {#response-body}

La réponse est un objet JSON avec les champs de niveau supérieur suivants :

| Champ | Type | Description |
|---|---|---|
| `api_version` | Chaîne | Version de l’API. Champ interne : aucun traitement requis. |
| `json_version` | Chaîne | Version du schéma JSON. Champ interne : aucun traitement requis. |
| `ttl` | Entier | TTL de cache en secondes. Valeur par défaut : 300. |
| `clients` | Objet | Mappage des identifiants client (ou chaînes PVPL) à leurs données de version. Chaque clé contient les champs décrits ci-dessous. |

#### Champs de réponse par client {#per-client-fields}

| Champ | Description |
|---|---|
| `releases` | Tableau des versions auxquelles l’utilisateur est éligible. Voir [champs de versions](#releases-fields) ci-dessous. |
| `client_analytics_params` | Objet de configuration Analytics. Voir [champs client_analytics_params](#analytics-fields) ci-dessous. |

#### champs des versions {#releases-fields}

| Champ | Description |
|---|---|
| `release_name` | Nom de la version ou du groupe de fonctionnalités. |
| `bit_index` | Libérer l’index binaire. Obsolète. Peut être `null` ou négatif selon l’état de libération. |
| `features` | Tableau de clés d’indicateur de fonctionnalité auxquelles l’utilisateur est éligible. Une clé de fonction ne s’affiche que si l’utilisateur est éligible et que l’indicateur est activé. |
| `meta` | Métadonnées codées en Base64 facultatives. Décoder avant utilisation. |
| `release_analytics_params` | Métadonnées Analytics pour les fonctionnalités éligibles. Dans les scénarios de la population témoin, `features` est vide. |

#### champs release_analytics_params {#release-analytics-params}

| Champ | Type | Description |
|---|---|---|
| `app_id` | Entier | ID de l’application. |
| `release_id` | Entier | ID de version. |
| `bit_index` | Entier | Obsolète. |
| `variant_id` | Entier | `0` si population témoin ; différent de zéro dans le cas contraire. |
| `feature_id` | Entier | Identifiant interne de la fonctionnalité. |
| `f_key` | Chaîne | Clé de l’indicateur de fonctionnalité. |

#### champs client_analytics_params {#analytics-fields}

| Champ | Type | Description |
|---|---|---|
| `app_id` | Entier | ID de l’application. |
| `safe_event_required` | Booléen | `true` si les événements de reciblage sont activés. |
| `analytics_required` | Booléen | `false` si Analytics est désactivé ou sur le flux par défaut ; `true` si le flux Kinesis est activé. |

## Exemple de requête et de réponse {#sample}

### Exemple de requête {#sample-request}

```http
GET /fg/api/v2/feature?clientId=MyDesktopApp&p=PHSP:17.0:WIN:en_US&meta=true HTTP/1.1
Host: p13n.adobe.io
Authorization: Bearer <ACCESS_TOKEN>
x-api-key: <YOUR_API_KEY>
If-None-Match: <ETAG>
```

### Exemple de réponse {#sample-response}

```json
{
  "api_version": "0.1",
  "json_version": "0.1",
  "clients": {
    "PHSP:17.0:WIN:en_US": {
      "analyticsVersion": "1.0",
      "releases": []
    },
    "MyDesktopApp": {
      "analyticsVersion": "1.0",
      "client_analytics_params": {
        "app_id": 388,
        "safe_event_required": false,
        "analytics_required": false
      },
      "releases": [
        {
          "bit_index": 160,
          "release_name": "||features||",
          "features": ["feature_a", "feature_b"],
          "release_analytics_params": [
            {
              "app_id": 388,
              "release_id": -1,
              "bit_index": 160,
              "variant_id": 10031741,
              "feature_id": 2918,
              "f_key": "feature_a"
            }
          ],
          "meta": []
        }
      ]
    }
  },
  "ttl": 300
}
```

## Voir également {#see-also}

* [API de fonctionnalités GET V3](get-feature-api-v3.md)
* [Applications de bureau](../guides/integrate/desktop-applications.md)
* [Étapes d’intégration](../guides/integrate/integration-steps.md)
