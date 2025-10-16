---
title: Configuration de l’accès aux API
description: Découvrez comment configurer l’accès aux API de Campaign Standard.
audience: developing
content-type: reference
topic-tags: campaign-standard-apis
role: Developer
level: Experienced
badge: label="DISPONIBILITÉ LIMITÉE" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Restrictions aux utilisateurs ayant migré vers Campaign Standard"
exl-id: efbbd0cd-9c56-4ad0-8bcb-efba4b63c28b
source-git-commit: 11c49b273164b632bcffb7de01890c6f9d7ae9c2
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 95%

---

# Configuration de l’accès aux API {#setting-up-api-access}

Pour configurer l’accès aux API d’Adobe Campaign Standard, procédez comme suit. Chacune de ces étapes est détaillée dans la [documentation Adobe Developer](https://developer.adobe.com/developer-console/docs/guides/#!AdobeDocs/adobeio-auth/master/AuthenticationOverview/ServiceAccountIntegration.md).

>[!IMPORTANT]
>
>Pour gérer les certificats dans [Adobe Developer](https://developer.adobe.com/), assurez-vous de disposer des droits d’**administrateur système** sur l’organisation ou d’un [compte de développeur](https://helpx.adobe.com/fr/enterprise/using/manage-developers.html) dans Admin Console.

1. **Vérifiez que vous disposez d’un certificat numérique**, ou créez-en un si nécessaire. Les clés publique et privée fournies avec le certificat sont nécessaires dans les étapes suivantes.
1. **Créez une nouvelle intégration avec Adobe Campaign Service** dans [Adobe Developer](https://developer.adobe.com/) et configurez-la. Vos informations d’identification seront alors générées (clé d’API, secret client...).
1. **Créez des informations d’identification de serveur à serveur OAuth** en suivant ces [étapes d’implémentation](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation/)

   >[!IMPORTANT]
   >
   >JWT (JSON Web Tokens) est actuellement en voie de devenir obsolète et sera remplacé par OAuth. La transition se fera progressivement dans les prochaines versions de Campaign. Bien que les informations d’identification du compte de service (JWT) aient été marquées comme obsolètes, elles continueront de fonctionner jusqu’au 27 janvier 2025. Par conséquent, vous devez migrer votre application ou intégration pour utiliser les nouvelles informations d’identification OAuth serveur à serveur avant le 27 janvier 2025. L’authentification OAuth est préférable. Vous trouverez tous les éléments à migrer de l’authentification JWT vers l’authentification OAuth sur ces pages :
   >* [Migration](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/)
   >* [Mise en œuvre](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation/)
   >* [Questions fréquentes sur l’obsolescence de JWT](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/faqs/)

Pour établir une session d’API Adobe I/O de service à service sécurisée, chaque requête adressée à un service Adobe doit inclure les informations ci-dessous dans l’en-tête d’autorisation.

```
-X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

* **&lt;ORGANIZATION>** : il s’agit de votre ORGANIZATION ID personnel, fourni par Adobe pour chacune de vos instances :

   * &lt;ORGANIZATION> : votre instance de production,
   * &lt;ORGANIZATION-mkt-stage> : votre instance d’évaluation.

  Pour obtenir votre valeur ORGANIZATION ID, contactez votre administrateur ou votre administratrice ou votre contact technique Adobe. Vous pouvez également la récupérer dans Adobe I/O lors de la création d’une nouvelle intégration, dans la liste des licences (voir la <a href="https://developer.adobe.com/developer-console/docs/guides/authentication/">documentation Adobe Developer</a>).

* **&lt;ACCESS_TOKEN>** : votre jeton d’accès personnel, récupéré lors de l’échange de votre jeton Web JSON par le biais d’une requête POST.

* **&lt;API_KEY>** : votre clé d’API personnelle. Elle est fournie dans Adobe I/O après la création d’une nouvelle intégration avec Adobe Campaign Service.

  ![texte alternatif](assets/tenant.png)

## Résolution des problèmes

Lors de l’intégration d’Adobe IO, si l’erreur suivante s’affiche :

```
{ 
"code": 502, 
"message": "Oops. Something went wrong. Check your URI and try again." 
}
```


Pour vérifier si le paramètre CNAME est correctement créé, contactez votre administrateur ou votre contact technique Adobe.
