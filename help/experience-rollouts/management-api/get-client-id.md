---
title: Obtention de l’identifiant client pour une application
description: Découvrez comment trouver l’identifiant client numérique pour une application dans la console Déploiements d’expérience, ce qui est nécessaire lors de l’appel des API de gestion.
source-git-commit: 6ecedbfc6c7de392f214f3f8f2e71aa18e1bacb9
workflow-type: tm+mt
source-wordcount: '193'
ht-degree: 1%

---


# Obtention de l’identifiant client pour une application {#get-client-id}

Les indicateurs de fonctionnalité et les API de gestion des groupes de fonctionnalités nécessitent un `clientId` numérique pour identifier l’application à laquelle la fonctionnalité appartient. Il est différent de l’identifiant client IMS basé sur une chaîne utilisé pour l’authentification de l’API.

Pour trouver l’identifiant client numérique d’une application, procédez comme suit.

## Étapes {#steps}

Pour rechercher l’identifiant client numérique d’une application, procédez comme suit :

1. Connectez-vous à la console Déploiements d’expérience .
2. Accédez à **Fonctionnalités et versions**.
3. Sélectionnez l’onglet **Indicateurs de fonctionnalité**.
4. Ouvrez la liste déroulante **Application** et sélectionnez l’application dont vous avez besoin comme identifiant client.
5. Examinez l’URL dans la barre d’adresse de votre navigateur. Après `feature-flags/`, le nombre affiché est l’identifiant client numérique pour cette application.

Par exemple, si l’URL se termine par `.../feature-flags/1191/...`, l’identifiant du client est `1191`.

## Utiliser l’identifiant client dans les appels API {#use-in-api}

Transmettez cette valeur en tant que paramètre `clientId` dans les requêtes d’API de gestion. Par exemple, lors de la création d&#39;un indicateur de fonctionnalité :

```json
{
  "name": "my-feature-flag",
  "clientId": 1191,
  "state": "disabled"
}
```

## Voir également {#see-also}

* [API Feature flags management](feature-flags-management-api.md)
* [API Feature group Management](feature-group-management-api.md)
* [Obtenir les critères d’audience souhaités](get-audience-criteria.md)
