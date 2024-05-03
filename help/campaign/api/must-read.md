---
title: À lire absolument
description: À lire absolument avant d’utiliser les API.
audience: developing
content-type: reference
topic-tags: campaign-standard-apis
role: Data Engineer
level: Experienced
badge: label="DISPONIBILITÉ LIMITÉE" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Limité aux utilisateurs migrés Campaign Standard"
source-git-commit: 84b72258789ba61016deb813e93bdca0ea142712
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 97%

---

# À lire absolument {#must-read}

## Exigences techniques

* Les API d’Adobe Campaign ne doivent être utilisées que de serveur à serveur.
* Vérifiez systématiquement avec votre contact technique Adobe si le cas pratique que vous souhaitez mettre en œuvre est conforme à l’échelle autorisée par les API Adobe Campaign.
* La configuration d’un accès AdobeIO nécessite des autorisations spécifiques. Contactez le support technique d’Adobe pour tout problème.

## Droits et accès

* Par défaut, les API Adobe Campaign utilisent le contexte administrateur et les entités organisationnelles et rôles ne s’appliquent donc pas.
* Les API Adobe Campaign sont exclues du contexte de rôle.
* Si vous souhaitez configurer les API avec une entité organisationnelle ou des rôles, contactez d’abord votre contact technique Adobe.

## Représentation des ressources

Toutes les ressources d’API sont disponibles dans **JSON** avec une extension d’URL ou dans un en-tête HTTP Accept  :

`GET /profileAndServices/<resourceName>.json`

>[!NOTE]
>
>Faute d’extension d’URL, le format par défaut du type de contenu est **json**.

<br/>

***exemple de requête***

```
-X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile.json \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

## Clé primaire et URL

* N’essayez pas de créer d’URL par vous-même. Toutes les URL sont renvoyées par l’API. Cependant, il est possible de créer une URL basée sur le nom de ressource de niveau supérieur.

* Les valeurs de clé primaire automatique (PKey) qui illustrent les exemples ne sont pas destinées à fonctionner dans un autre déploiement spécifique. Elles sont produites par l’API Adobe Campaign.

* Les valeurs de clé primaire automatique générées par Adobe Campaign ne doivent jamais être stockées dans une base de données ou un site web externe. Vous devez générer des champs de clés spécifiques dans la définition de votre base de données et les utiliser lors de vos développements.

## Clés personnalisées {#custom-keys}

Si la ressource de profil a été étendue avec un champ de clé personnalisé, vous pouvez utiliser ce champ comme clé au lieu de la clé primaire automatique générée par Adobe Campaign :

`GET /.../profileAndServicesExt/profile/<customKey>`

Les clés personnalisées ne peuvent pas être modifiées à l’aide d’une opération PATCH si la valeur de la clé est différente de celle de la clé d’origine ou si vous utilisez votre propre clé d’entreprise comme URI au lieu de celle fournie par Adobe.

Utilisez une clé personnalisée uniquement pour les **ressources de profil de niveau supérieur**. Les URL sont renvoyées par l’API et ne doivent jamais être créées par vous-même.

<br/>

***Exemple de requête***

Pour récupérer les abonnements d’un profil à l’aide d’une clé personnalisée, effectuez une opération GET sur la clé personnalisée.

```
-X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServicesExt/profile/<customKey> \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

Exécutez une requête GET sur l’URL des abonnements renvoyée.

```
-X GET <SUBSCRIPTION_URL> \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

Elle renvoie la liste des abonnements du profil.

```
"service": {
"PKey": "<PKEY>",
"href": "https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/service/<PKEY>",
"label": "Sport Newsletter",
"name": "SVC1",
"title": "Sport Newsletter (SVC1)"
}
```
