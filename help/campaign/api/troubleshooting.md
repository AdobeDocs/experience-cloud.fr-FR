---
title: Résolution des problèmes d’API
description: Découvrez les problèmes courants liés aux API Campaign Standard
role: Data Engineer
level: Experienced
badge: label="DISPONIBILITÉ LIMITÉE" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Limité aux utilisateurs migrés Campaign Standard"
exl-id: 404356cd-021f-4739-a88f-b8b1b79e19bc
source-git-commit: 3f4400f24b75e8e435610afbe49e9d9444dbf563
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 97%

---

# Résolution des problèmes d’API {#troubleshooting}

* **Lorsque vous accédez à la console Adobe.io, l’erreur suivante s’affiche : « La console Adobe I/O est uniquement disponible pour sélectionner les membres des comptes d’entreprise. Si vous pensez que vous devriez y avoir accès, contactez votre administrateur système. »**

Vous ne pouvez créer des clés d’API que pour les organisations dont vous êtes administrateur. Si ce message s’affiche et que vous souhaitez créer des clés d’API, demandez à l’un des administrateurs de l’organisation.

* **Lors de l’exécution d’une requête sur Adobe.io, vous obtenez {&quot;error_code&quot;:&quot;403023&quot;,&quot;message&quot;:&quot;Profil non valide&quot;}.**

Cela signifie qu’il existe un problème avec l’approvisionnement IMS de votre produit Campaign spécifique : l’équipe IMS doit le résoudre.

Pour plus de détails, vous pouvez appeler l’API IMS avec votre jeton pour voir à quoi ressemble votre profil IMS : pour qu’Adobe.io puisse acheminer votre requête, vous devez disposer d’un prodCtx possédant un identifiant id_organization identique à celui inséré dans l’URL.
S’il manque, l’approvisionnement IMS doit être corrigé.

```
-X GET https://mc.adobe.io/{ORGANIZATION}/campaign/profileAndServices/profile \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

La requête renvoie l’erreur suivante.

```
{"error_code":"403023","message":"Profile is not valid"}
```

Vérifiez votre profil IMS avec cette requête.

```
-X GET https://ims-na1.adobelogin.com/ims/profile/v1 \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

Dans la réponse, la valeur ORGANIZATION_ID doit être la même que dans votre première requête GET.

```
{
  "countryCode": "FR",
  "mrktPermEmail": null,
  "projectedProductContext": [
    {
    "prodCtx": {
      "statusCode": "ACTIVE",
      "ident": "ZQ9FRQK7BF09YXAESFY9DDQP1G",
      "modDts": 1448307260000,
      "organization_id": "actest",
      "owningEntity": "6096892F54B5819E0A4C98A2@AdobeOrg",
      "serviceCode": "dma_tartan",
      "label": "Adobe Marketing Cloud",
      "serviceLevel": "standard",
      "createDts": 1421181343000,
      "deal_id": " "
      }
    }
  ]
}
```

* **Lors d’une requête sur Adobe.io, vous obtenez {&quot;code&quot;:500, &quot;message&quot;:&quot; Une erreur s’est produite. Vérifiez votre URI et réessayez.&quot;}**

Adobe.io déclare votre URI comme non valide : l’URI que vous demandez n’est probablement pas valide. Sur Adobe.io, lorsque vous sélectionnez le service Campaign, vous obtenez un sélecteur avec une liste des valeurs organization_ids possibles. Vous devez vérifier que celui choisi est celui que vous avez inséré dans votre URL.

* **Lors de l’exécution d’une requête sur Adobe.io, vous obtenez {&quot;error_code&quot;:&quot;401013&quot;,&quot;message&quot;:&quot;Le jeton Oauth n’est pas valide&quot;}.**

Votre jeton n’est pas valide (appel IMS incorrect utilisé pour générer un jeton) ou votre jeton a expiré.

* **Je ne vois pas mon profil après la création**

Selon la configuration de l’instance, le profil créé doit être associé à un **orgUnit**. Pour comprendre comment ajouter ce champ à votre création, consultez [cette section](creating-profiles-api.md).

<!-- * (error duplicate key : quand tu crées un profile qui existe déjà , il faut faire un patch pour updater le profile plutôt qu’un POST)

With Curl
List all profiles

Create a profile

Update the mobilePhone attribute of a profile

API Calls on Service

GET the list of services

-->

<!--

How to find and use a filter?
Error codes:

* PAtch sur Age = message d'erreur :
500
Cannot update the 'age' property that is read-only
'age' property is not valid for the 'profile' resource.
-->

<!--
How to filter a list of subscribed profiles with available profile filters ? by date (by les filtres dispo sur la ressource) ?

Pattern classique :

recupérer la liste des subscriptions filtrées d'un profile
1) get sur profile
2) recup PKey
3) get sur PKey
4) get sur href des subscriptions

Comment savoir quel filtre appliquer ?

1) get sur metadata de profile
2) retourne description de la collection subscription
3) get sur la valeur du champ resTarget
4) get sur le href dans filters
5) retourne les filtres applicables sur l'url des data.

-->
