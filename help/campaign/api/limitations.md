---
title: Recommendations et limitations
description: Recommendations et limitations lors de la migration vers les API REST de Campaign v8.
audience: developing
content-type: reference
topic-tags: campaign-standard-apis
role: Data Engineer
level: Experienced
mini-toc-levels: 1
badge: label="DISPONIBILITÉ LIMITÉE" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Restrictions aux utilisateurs migrés par le Campaign Standard"
exl-id: 45acebb1-9325-4e26-8fe9-cc73f745d801
source-git-commit: 952706ffafc1e7cd6a759bfbbb9c9200191544d9
workflow-type: tm+mt
source-wordcount: '1065'
ht-degree: 1%

---

# Recommendations et limitations {#limitations}

## Autorisations et sécurité {#permissions}

### Mappage des profils de produit

En Campaign Standard, le rôle d’administrateur élevé vous a été accordé un accès aux API, quel que soit votre profil de produit attribué. Campaign v8 introduit un ensemble différent de profils de produit, ce qui nécessite de mapper les profils de produits Campaign Standard aux profils de produits Campaign v8.

Avec la migration, deux profils de produit sont ajoutés à vos comptes techniques existants ou précréés : Administrateur et Message Center (pour l’accès aux API transactionnelles). Vérifiez le mappage des profils de produit et attribuez le profil de produit nécessaire si vous ne souhaitez pas que le profil de produit Administrateur soit mappé à votre compte technique.

### ID du client

Après la migration, pour les intégrations futures, il est recommandé d’utiliser votre **identifiant client Campaign v8** dans les URL REST, en remplaçant votre identifiant client de Campaign Standard précédent.

### Utilisation des clés

La gestion des valeurs PKey diffère entre Campaign Standard et Campaign v8. Si vous stockiez des clés PKey avec Campaign Standard, assurez-vous que votre implémentation crée dynamiquement les appels API suivants à l’aide des clés PKey ou hrefs obtenus à partir d’appels API précédents.

## API disponibles {#deprecated}

Pour l’instant, les API REST répertoriées ci-dessous peuvent être utilisées :

* **Profils**
* **Services et abonnements**
* **Ressources personnalisées**
* **Workflows**
* **Messages transactionnels**

>[!AVAILABILITY]
>
>Pour l’instant, l’API REST **Messages transactionnels** n’est pas disponible.
>
>Les API REST répertoriées ci-dessous sont obsolètes et ne peuvent pas être utilisées :
>* Historique marketing
>* Entités organisationnelles
>* Gestion de la confidentialité

## Filtrage

* Pour utiliser vos filtres dans les payloads de l’API REST, vous devez les modifier dans Campaign v8 et fournir un nom à utiliser dans vos payloads. Pour ce faire, accédez aux paramètres supplémentaires du filtre à partir de l’onglet **[!UICONTROL Paramètres]** et indiquez le nom souhaité dans le champ **[!UICONTROL Nom du filtre dans l’API REST]**.

  ![](assets/api-filtering.png)


* Le préfixe « par » requis pour utiliser les filtres personnalisés n’est plus nécessaire. Le nom du filtre doit être utilisé tel quel dans vos requêtes.

  Exemple :

  `GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServicesExt/<resourceName>/<customFilterName>?<customFilterparam>=<customFilterValue>`

## Champs de base de données supprimés

Certains champs de la base de données sont supprimés lors de la migration. Lors de l’utilisation d’un champ déposé, les API REST renverront des valeurs vides. À l’avenir, tous les champs déposés seront abandonnés et supprimés.

## POST avec les ressources associées

Lors de l’utilisation du format de corps de requête suivant, avec « VehicleOwner » représentant le lien vers « nms:recipient » :

```
{
    "vehicleNumber": "20009",
    "vehicleName": "Model E",
    "vehicleOwner":{
        "firstName":"tester 11",
        "lastName":"Smith 11"
    }
}
```

Les informations sur le lien sont ignorées. Par conséquent, un nouvel enregistrement est généré sous « cusVehicle » contenant uniquement les valeurs « VehicleNumber » et « VehicleName ». Cependant, le lien reste nul, ce qui entraîne la définition de « VehicleOwner » sur null.

Dans Campaign v8, lorsque la même structure de corps de requête est utilisée et que le « véhicule » est lié à un profil, une erreur se produit. Cette erreur se produit car la propriété « firstName » n&#39;est pas reconnue comme valide pour « cusVehicle ». Cependant, un corps de requête comprenant uniquement les attributs sans lien fonctionne sans aucun problème.

## Opérations du PATCH

* Campaign v8 ne prend pas en charge les PATCH dont le corps de requête est vide : il renvoie un statut 204 Aucun contenu .
* Bien que Campaign Standard prenne en charge le PATCH sur les éléments/attributs d’un schéma, notez que les opérations de PATCH à l’emplacement ne sont pas prises en charge dans Campaign v8. Toute tentative de PATCH sur l&#39;emplacement entraînera une erreur interne du serveur 500 avec un message d&#39;erreur indiquant que la propriété &#39;zipCode&#39; n&#39;est pas valide pour la ressource &#39;profile&#39;.

## Réponses REST

La section ci-dessous répertorie les différences mineures entre les réponses REST de Campaign Standard et de v8.

* Pour les enregistrements à GET unique, la réponse inclut le href dans la réponse.
* Lorsqu’elle est interrogée avec l’attribut , Campaign v8 fournit Count et Pagination dans la réponse.
* Après des opérations POST, les valeurs des ressources liées sont renvoyées dans la réponse.

## Codes d’erreur et messages

La section ci-dessous répertorie les différences entre les codes d’erreur et les messages de Campaign Standard et de Campaign v8.

| Scénario | Campaign Standard | Campaign v8 |
|  ---  |  ---  |  ---  |
| Utiliser une clé PKey non valide dans le corps de la requête | 500 - Attribut &#39;O5iRp40EGA&#39; inconnu (voir définition du schéma &#39;Profils (nms:recipient)&#39;). XTK-170036 Impossible d&#39;analyser l&#39;expression &#39;@id = @O5iRp40EGA&#39;. | 404 - Impossible de déchiffrer PKey. (PKey=@jksad) |
| Utiliser une clé PKey non valide dans l’URI | 500 - Attribut &#39;O5iRp40EGA&#39; inconnu (voir définition du schéma &#39;Profils (nms:recipient)&#39;). XTK-170036 Impossible d&#39;analyser l&#39;expression &#39;@id = @O5iRp40EGA&#39;. | 404 - Impossible de déchiffrer PKey. (PKey=@jksad) Point d’entrée non pris en charge. (endpoint=rest/profileAndServices/profile/@jksad) |
| Utilisation de deux Pkeys brutes différentes dans l’URI et le corps de la requête | 500 - RST-360011 Une erreur s&#39;est produite. Veuillez contacter votre administrateur. RST-360012 Opération incohérente sur la ressource &#39;service&#39; - Impossible de mettre à jour la clé &#39;SVC3&#39; vers &#39;SVC4&#39;. | 500 - Une erreur s’est produite. Contactez votre administrateur. |
| Utilisation de PKey dans l’URI et d’une PKey brute différente dans le corps de la requête | 500 - Un « Service » avec la même clé « SVC4 » existe déjà. Erreur PGS-220000 PostgreSQL : ERREUR : la valeur de clé dupliquée viole la contrainte unique « nmsservice_name » DÉTAIL : La clé (sname)=(SVC4) existe déjà. | 500 - Une erreur s’est produite. Contactez votre administrateur. |
| Utilisation d’un raw-id non existant dans l’URI | 404 - RST-360011 Une erreur s&#39;est produite. Veuillez contacter votre administrateur. Impossible de trouver le document de chemin &#39;Service&#39; à partir de la clé &#39;adobe_nl:0&#39; (document de schéma &#39;service&#39; et de nom &#39;adobe_nl&#39;) | 404 - Impossible de trouver le document de chemin &#39;Service&#39; à partir de la clé &#39;adobe_nl&#39; (document de schéma &#39;service&#39; et de nom &#39;adobe_nl&#39;) |
| Utilisation d’un raw-id non existant dans le corps de la requête | 404 - RST-360011 Une erreur s&#39;est produite. Veuillez contacter votre administrateur. Impossible de trouver le document de chemin &#39;Service&#39; à partir de la clé &#39;adobe_nl&#39; (document de schéma &#39;service&#39; et de nom &#39;adobe_nl&#39;) | 404 - Impossible de trouver le document de chemin &#39;Service&#39; à partir de la clé &#39;adobe_nl&#39; (document de schéma &#39;service&#39; et de nom &#39;adobe_nl&#39;) |
| - | 500 - RST-360011 Une erreur s&#39;est produite. Veuillez contacter votre administrateur. | 500 - Une erreur s’est produite. Contactez votre administrateur. |
| Insérer un profil/service avec une valeur d’énumération de genre (ou toute autre valeur) non valide | 500 - RST-360011 Une erreur s&#39;est produite. Veuillez contacter votre administrateur. La valeur &#39;invalid&#39; n&#39;est pas valide pour l&#39;énumération &#39;nms:recipient:gender&#39; du champ &#39;@gender&#39; | 500 - Une erreur s’est produite. Contactez votre administrateur. |

## Profil - Fuseau horaire

Avec Campaign Standard, le fuseau horaire s’affiche dans le cadre de la réponse JSON des appels de l’API REST **profileAndServices/profile**.

Avec Campaign v8, le fuseau horaire n’est affiché que dans le cadre des appels API REST **profileAndServicesExt/profile**. Il ne fait pas partie des appels de l’API REST **profileAndServices/profile**, car il est ajouté dans un schéma étendu.

## Workflows - Déclenchement de signal externe

L’API Campaign Standard Workflow GET renvoie des noms de paramètre tels que les variables d’instance de workflow et leurs types de données (booléen, chaîne, etc.). Il est utilisé pour créer un corps de requête JSON formaté approprié lors du déclenchement du signal via un appel API de POST.

Campaign v8 ne prend pas en charge les variables d’instance de workflow publicitaire, mais s’attend à ce que les développeurs et développeuses les connaissent. Ainsi, après la migration, les informations de paramètres dans le corps de la requête du POST doivent être créées sans que les informations de paramètres ne soient disponibles dans la réponse de l’API GET.

<!--## Transactional messages

* With Campaign Standard, a POST request returns empty fields for elements and attributes in the request body. With Campaign v8, the response returns values that match the ones in the request body instead.

* When publishing an event configuration, the API preview panel displays the REST URL alongside the request body syntax.

    Since Campaign v8 does not support event configuration fields definition (event creation is just adding a value to eventType enumeration), there is no API preview panel when adding an event type. The REST URL is displayed  in the transactional message user interface once an event transactional message is published.-->
