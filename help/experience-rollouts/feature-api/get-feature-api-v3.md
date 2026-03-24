---
title: API de fonctionnalités GET V3
description: Référence d’API pour l’API de fonctionnalité Déploiements d’expérience V3, utilisée pour récupérer les indicateurs de fonctionnalité pour les applications web et mobiles.
source-git-commit: 6ecedbfc6c7de392f214f3f8f2e71aa18e1bacb9
workflow-type: tm+mt
source-wordcount: '679'
ht-degree: 9%

---


# API de fonctionnalités GET V3 {#get-feature-api-v3}

L’API Feature V3 est le point d’entrée principal pour la récupération des indicateurs de fonctionnalité dans les applications web et mobiles. Elle renvoie les fonctionnalités et les publications auxquelles un utilisateur est éligible, en fonction de son identité et des règles d’audience configurées dans la console.

**Endpoint:** `GET {HOST}/fg/api/v3/feature`

Utilisez `https://p13-stage.adobe.io` pour l’évaluation et `https://p13n.adobe.io` pour la production.

## Requête {#request}

### En-têtes de requête {#request-headers}

| Header | Type | Description | Obligatoire |
|---|---|---|---|
| `x-api-key` | Chaîne | Clé API de votre application à partir du Adobe Developer Console. Doit être configuré séparément pour l’évaluation et la production. | Oui |
| `Authorization` | Chaîne | **Non requis** pour les scénarios non authentifiés. Utilisez `Bearer <AccessToken>` pour les utilisateurs authentifiés. Utilisez `Bearer <ServiceToken>` pour les scénarios de mise en cache du SDK côté serveur. | Non |
| `x-adobe-uuid` | Chaîne | Identifiant visiteur ou appareil unique. Utilisé pour prendre en charge le déploiement en pourcentage pour les utilisateurs non authentifiés et pour maintenir la fidélité entre les sessions et les transitions non authentifié à authentifié. | Non |

### Paramètres de requête {#query-parameters}

| Paramètre | Type | Description | Obligatoire |
|---|---|---|---|
| `clientId` | Chaîne | Identifiant client de votre application, tel qu’intégré dans la console Déploiements d’expérience. | Oui |
| `ignore_rf` | Booléen | Si `true`, les indicateurs de version sont ignorés et toutes les versions pour le client sont renvoyées. Valeur par défaut : `false`. | Non |
| `rf` | Chaîne | Indicateur de version. Utilisé uniquement lorsque `ignore_rf` est `false`. | Non |
| `meta` | Booléen | Si `true`, les métadonnées de chaque fonctionnalité sont incluses dans la réponse, renvoyées sous la forme d’une paire clé-valeur où la valeur est codée en Base64. Valeur par défaut : `false`. | Non |
| `userId` | Chaîne | Nécessite un jeton de service. GUID de l’utilisateur pour lequel vous souhaitez récupérer les indicateurs de fonctionnalité. | Non |
| *Paramètres contextuels* | S.O. | Tout paramètre de requête qui ne figure pas ci-dessus est traité comme une variable contextuelle et utilisé pour évaluer les règles d’audience. Transmettez plusieurs valeurs en tant que `?key1=val1&key2=val2`. Exemple : `?clientLanguage=ja_JP&contractCurrency=JPY`. | Non |

## Réponse {#response}

### Codes d’état de réponse {#response-status}

| Code d’état | Description |
|---|---|
| `200 OK` | Les données d’indicateur de fonctionnalité sont renvoyées dans le corps de la réponse. |
| `304 Not Modified` | L’ETag transmis par le client correspond au dernier état du serveur. Traiter ceci comme une opération nulle - aucune modification à appliquer. |
| `400 Bad Request` | Le `clientId` n’a pas été intégré ou la requête est incorrecte. |
| `403 Forbidden` | Clé API non valide ou l’application n’est pas abonnée à l’API de déploiements d’expérience dans Adobe Developer Console. |

### En-têtes de réponse {#response-headers}

| Header | Description |
|---|---|
| `x-request-id` | Identifiant de requête unique pour le débogage. Incluez-le dans toute demande d’assistance. |
| `ETag` | Jeton représentant l’état actuel du serveur pour les fonctionnalités de cet utilisateur. Transmettez cette valeur comme `If-None-Match` dans les requêtes suivantes. Si l’état n’a pas changé, l’API renvoie `304`. |
| `x-adobe-fg-poll-interval` | Durée de vie (en secondes) du cache local du client. Rappelez l’API uniquement après cet intervalle. |

### Corps de réponse {#response-body}

La réponse est un objet JSON avec les champs de niveau supérieur suivants :

| Champ | Type | Description |
|---|---|---|
| `api_version` | Chaîne | Version de l’API. Champ interne : aucun traitement requis. |
| `json_version` | Chaîne | Version du schéma JSON. Champ interne : aucun traitement requis. |
| `ttl` | Entier | TTL de cache en secondes. Même valeur que l’en-tête de réponse `x-adobe-fg-poll-interval`. Valeur par défaut : 300. |
| `caching_enabled` | Booléen | Si `true`, l’évaluation des fonctionnalités se produit localement sur le client. Si `false`, l’évaluation se produit côté serveur sur chaque requête. |
| `client_analytics_params` | Objet | Configuration Analytics pour l’application. Voir [champs client_analytics_params](#client-analytics-params) ci-dessous. |
| `releases` | Tableau | Liste des versions et indicateurs de fonctionnalité auxquels l’utilisateur est éligible. Voir [champs de versions](#releases-fields) ci-dessous. |

#### champs client_analytics_params {#client-analytics-params}

| Champ | Description |
|---|---|
| `app_id` | Identifiant numérique de l’application. |
| `safe_event_required` | `true` si les événements de reciblage sont activés pour ce client. |
| `analytics_required` | Toujours `false` dans les réponses V3. |

#### champs des versions {#releases-fields}

| Champ | Description |
|---|---|
| `release_name` | Nom de la version ou du groupe de fonctionnalités auquel l&#39;utilisateur est éligible. |
| `bit_index` | Index du bit de libération. Les valeurs négatives indiquent un état de déploiement complet. |
| `features` | Tableau de clés d’indicateur de fonctionnalité auxquelles l’utilisateur est éligible. Une clé de fonctionnalité est renvoyée uniquement si l’utilisateur est éligible et que l’indicateur est à l’état activé. Il s’agit du champ principal autour duquel votre logique d’application doit être créée. |
| `meta` | Métadonnées codées en Base64 facultatives associées à la fonctionnalité. Décoder avant utilisation. |
| `release_analytics_params` | Tableau d’objets de métadonnées Analytics pour chaque fonctionnalité éligible. Voir les champs [release_analytics_params](#release-analytics-params) ci-dessous. Dans les scénarios de la population témoin, `features` est vide. |

#### champs release_analytics_params {#release-analytics-params}

| Champ | Type | Description |
|---|---|---|
| `app_id` | Entier | ID de l’application. |
| `release_id` | Entier | ID de version. |
| `bit_index` | Entier | Libérer l’index binaire. Obsolète. |
| `variant_id` | Entier | `0` si l’utilisateur se trouve dans la population témoin ; différent de zéro dans le cas contraire. |
| `feature_id` | Entier | Identifiant interne de la fonctionnalité. |
| `f_key` | Chaîne | Clé de l’indicateur de fonctionnalité. |

## Exemple de requête et de réponse {#sample}

### Exemple de requête {#sample-request}

```http
GET /fg/api/v3/feature?clientId=MyWebApp&meta=true HTTP/1.1
Host: p13n.adobe.io
Authorization: Bearer <ACCESS_TOKEN>
x-api-key: <YOUR_API_KEY>
If-None-Match: <ETAG>
```

### Exemple de réponse — utilisateur dans le groupe de test {#sample-response-test}

```json
{
  "api_version": "0.1",
  "json_version": "0.1",
  "clients": {
    "MyWebApp": {
      "analyticsVersion": "2.0",
      "client_analytics_params": {
        "app_id": 1378,
        "safe_event_required": false,
        "analytics_required": false
      },
      "releases": [
        {
          "bit_index": -160,
          "release_name": "||features||",
          "features": ["ff1", "ff2", "ff3"],
          "release_analytics_params": [
            {
              "app_id": 1378,
              "release_id": -1,
              "bit_index": -160,
              "variant_id": 10040476,
              "feature_id": 26059,
              "f_key": "ff1",
              "analytics_required": true
            }
          ]
        }
      ]
    }
  },
  "ttl": 60
}
```

### Exemple de réponse — utilisateur dans la population témoin {#sample-response-control}

Lorsqu’un utilisateur se trouve dans la population témoin, le tableau `features` est vide et `variant_id` est `0` :

```json
{
  "api_version": "0.1",
  "json_version": "0.1",
  "clients": {
    "MyWebApp": {
      "releases": [
        {
          "bit_index": -160,
          "release_name": "||features||",
          "features": [],
          "release_analytics_params": [
            {
              "app_id": 1378,
              "release_id": -1,
              "bit_index": -160,
              "variant_id": 0,
              "feature_id": 26059,
              "f_key": "ff1"
            }
          ]
        }
      ]
    }
  },
  "ttl": 60
}
```

## Voir également {#see-also}

* [API de fonctionnalités GET V2](get-feature-api-v2.md)
* [Des applications web](../guides/integrate/web-applications.md)
* [Applications mobiles](../guides/integrate/mobile-applications.md)
* [Étapes d’intégration](../guides/integrate/integration-steps.md)
