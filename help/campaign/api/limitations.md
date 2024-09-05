---
title: Recommendations et limitations
description: Recommendations et limites lors de la migration vers les API REST de Campaign v8.
audience: developing
content-type: reference
topic-tags: campaign-standard-apis
role: Data Engineer
level: Experienced
mini-toc-levels: 1
badge: label="DISPONIBILITÉ LIMITÉE" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Limité aux utilisateurs migrés Campaign Standard"
exl-id: 45acebb1-9325-4e26-8fe9-cc73f745d801
source-git-commit: 6e4e214731b9772014d01dde89b3f80e4c4e93a6
workflow-type: tm+mt
source-wordcount: '1063'
ht-degree: 1%

---

# Recommendations et limitations {#limitations}

## Autorisations et sécurité {#permissions}

### Mappage des profils de produit

Dans Campaign Standard, un accès aux API avec un rôle d’administrateur élevé vous a été accordé, quel que soit votre profil de produit attribué. Campaign v8 introduit un ensemble différent de profils de produit, nécessitant un mappage de Campaign Standard aux profils de produit Campaign v8.

Avec la migration, deux profils de produit sont ajoutés à vos comptes techniques existants ou précréés : Administrateur et Message Center (pour l’accès aux API transactionnelles). Passez en revue le mappage de profil de produit et attribuez le profil de produit nécessaire si vous ne souhaitez pas que le profil de produit administrateur soit mappé à votre compte technique.

### Identifiant du client

Après la migration, pour les intégrations futures, il est recommandé d’utiliser votre **ID de tenant Campaign v8** dans les URL REST, en remplaçant votre identifiant de client Campaign Standard précédent.

### Utilisation des clés

La gestion des valeurs PKey diffère entre Campaign Standard et Campaign v8. Si vous stockiez des PKeys avec Campaign Standard, assurez-vous que votre mise en oeuvre forme dynamiquement les appels d’API suivants à l’aide de PKeys ou de hrefs obtenus à partir d’appels d’API précédents.

## API disponibles {#deprecated}

Pour l’instant, les API REST répertoriées ci-dessous sont disponibles :

* **Profils**
* **Services et abonnements**
* **Ressources personnalisées**
* **Workflows**

>[!AVAILABILITY]
>
>Pour l’instant, l’API REST **Messages transactionnels** n’est pas disponible.
>
>Les API REST répertoriées ci-dessous sont obsolètes et ne sont pas disponibles :
>* Historique marketing
>* Entités organisationnelles
>* Gestion de la confidentialité

## Filtrage

* Pour utiliser vos filtres dans les payloads de l’API REST, vous devez les modifier dans Campaign v8 et donner un nom à utiliser dans les payloads. Pour ce faire, accédez aux paramètres supplémentaires du filtre à partir de l’onglet **[!UICONTROL Paramètres]** et indiquez le nom de votre choix dans le champ **[!UICONTROL Nom du filtre dans l’API REST]**.

  ![](assets/api-filtering.png)


* Le préfixe &quot;by&quot; requis pour utiliser des filtres personnalisés n’est plus nécessaire. Le nom du filtre doit être utilisé tel quel dans vos requêtes.

  Exemple :

  `GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServicesExt/<resourceName>/<customFilterName>?<customFilterparam>=<customFilterValue>`

## Champs de base de données supprimés

Certains champs de la base de données sont supprimés lors de la migration. Lors de l’utilisation d’un champ déposé, les API REST renvoient des valeurs vides. À l’avenir, tous les champs déposés seront abandonnés et supprimés.

## POST avec ressources liées

Lors de l’utilisation du format de corps de requête suivant, avec &quot;véhiculeOwner&quot; représentant le lien vers &quot;nms:recipient&quot; :

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

Les informations sur le lien sont ignorées. Par conséquent, un nouvel enregistrement est généré sous &quot;cusVehicle&quot; contenant uniquement les valeurs &quot;véhiculeNumber&quot; et &quot;véhiculeName&quot;. Cependant, le lien reste nul, ce qui entraîne la définition de &quot;véhiculeOwner&quot; sur null.

Dans Campaign v8, lorsque la même structure de corps de requête est utilisée et que le &quot;véhicule&quot; est lié à un profil, une erreur se produit. Cette erreur se produit car la propriété &quot;firstName&quot; n’est pas reconnue comme valide pour &quot;cusVehicle&quot;. Cependant, un corps de requête comprenant uniquement les attributs sans fonctions de lien ne présente aucun problème.

## Opérations PATCH

* Campaign v8 ne prend pas en charge le PATCH avec un corps de requête vide : il renvoie un état 204 No Content .
* Bien que Campaign Standard prenne en charge le PATCH sur les éléments/attributs d’un schéma, notez que les opérations de PATCH à l’emplacement ne sont pas prises en charge dans Campaign v8. La tentative d’un PATCH sur l’emplacement entraînera une erreur interne 500 du serveur avec un message d’erreur indiquant que la propriété &#39;zipCode&#39; n’est pas valide pour la ressource &#39;profile&#39;.

## Réponses REST

La section ci-dessous répertorie les différences mineures entre les réponses REST Campaign Standard et v8.

* Pour les enregistrements de GET unique, la réponse inclut le href dans la réponse.
* Lors de l’interrogation de l’attribut , Campaign v8 fournit le décompte et la pagination dans la réponse.
* Après les opérations de POST, les valeurs des ressources liées sont renvoyées dans la réponse.

## Codes d’erreur et messages

La section ci-dessous répertorie les différences entre les codes et les messages d’erreur de Campaign Standard et de Campaign v8.

| Scénario | Campaign Standard | Campaign v8 |
|  ---  |  ---  |  ---  |
| Utiliser une clé PKey non valide dans le corps de la requête | 500 - Attribut &#39;O5iRp40EGA&#39; inconnu (voir définition du schéma &#39;Profils (nms:recipient)&#39;). XTK-170036 Impossible d&#39;analyser l&#39;expression &#39;@id = @O5iRp40EGA&#39;. | 404 - Impossible de déchiffrer la clé PKey. (PKey=@jksad) |
| Utilisation d’une clé PKey non valide dans l’URI | 500 - Attribut &#39;O5iRp40EGA&#39; inconnu (voir définition du schéma &#39;Profils (nms:recipient)&#39;). XTK-170036 Impossible d&#39;analyser l&#39;expression &#39;@id = @O5iRp40EGA&#39;. | 404 - Impossible de déchiffrer la clé PKey. (PKey=@jksad) Point de terminaison non pris en charge. (endpoint=rest/profileAndServices/profile/@jksad) |
| Utilisation de deux Pkeys bruts différents dans l’URI et le corps de la requête | 500 - RST-360011 Une erreur s&#39;est produite - contactez votre administrateur. RST-360012 Opération incohérente sur la ressource &quot;service&quot; - Impossible de mettre à jour la clé &quot;SVC3&quot; en &quot;SVC4&quot;. | 500 - Une erreur s’est produite - contactez votre administrateur. |
| Utilisation de PKey dans l’URI et d’une autre clé PKey brute dans le corps de la requête | 500 - Un &quot;Service&quot; avec la même clé &quot;SVC4&quot; existe déjà. Erreur PGS-220000 PostgreSQL : ERREUR : la valeur de clé en double viole la contrainte unique &quot;nmsservice_name&quot; DETAIL: Key (sname)=(SVC4) existe déjà. | 500 - Une erreur s’est produite - contactez votre administrateur. |
| Utilisation d’un raw-id non existant dans l’URI | 404 - RST-360011 Une erreur s&#39;est produite - contactez votre administrateur. Impossible de trouver le document avec le chemin &quot;Service&quot; à partir de la clé &quot;adobe_nl:0&quot; (document avec le schéma &quot;service&quot; et le nom &quot;adobe_nl&quot;) | 404 - Impossible de trouver le document avec le chemin &#39;Service&#39; à partir de la clé &#39;adobe_nl&#39; (document avec le schéma &#39;service&#39; et le nom &#39;adobe_nl&#39;) |
| Utilisation d’un identifiant brut non existant dans le corps de la requête | 404 - RST-360011 Une erreur s&#39;est produite - contactez votre administrateur. Impossible de trouver le document avec le chemin &quot;Service&quot; à partir de la clé &quot;adobe_nl&quot; (document avec le schéma &quot;service&quot; et le nom &quot;adobe_nl&quot;) | 404 - Impossible de trouver le document avec le chemin &#39;Service&#39; à partir de la clé &#39;adobe_nl&#39; (document avec le schéma &#39;service&#39; et le nom &#39;adobe_nl&#39;) |
| - | 500 - RST-360011 Une erreur s&#39;est produite - contactez votre administrateur. | 500 - Une erreur s’est produite - contactez votre administrateur. |
| Insérer un profil/service avec une valeur d’énumération de genre non valide (ou autre) | 500 - RST-360011 Une erreur s&#39;est produite - contactez votre administrateur. La valeur &#39;invalid&#39; n&#39;est pas valide pour l&#39;énumération &#39;nms:recipient:gender&#39; du champ &#39;@gender&#39; | 500 - Une erreur s’est produite - contactez votre administrateur. |

## Profil - Fuseau horaire

Avec Campaign Standard, le fuseau horaire s’affiche dans le cadre de la réponse JSON des appels d’API REST **profileAndServices/profile**.

Avec Campaign v8, le fuseau horaire s’affiche uniquement pour l’utilisateur dans le cadre des appels d’API REST **profileAndServicesExt/profile**. Il ne fait pas partie des appels d’API REST **profileAndServices/profile** puisqu’il est ajouté à un schéma étendu.

## Workflows - Déclenchement de signaux externes

L’API Campaign Standard Workflow GET renvoie les noms des paramètres tels que les variables d’instance de workflow et leurs types de données (booléen, chaîne, etc.). Il est utilisé pour créer le corps de requête JSON correctement formaté lors du déclenchement du signal via un appel API de POST.

Campaign v8 ne prend pas en charge les variables d’instance de workflow publicitaire, mais attend des développeurs qu’ils sachent ce qu’elles sont. Par conséquent, les informations de paramètres post-migration dans le corps de la requête du POST devront être construites sans la disponibilité des informations de paramètres dans la réponse de l’API GET.

<!--## Transactional messages

* With Campaign Standard, a POST request returns empty fields for elements and attributes in the request body. With Campaign v8, the response returns values that match the ones in the request body instead.

* When publishing an event configuration, the API preview panel displays the REST URL alongside the request body syntax.

    Since Campaign v8 does not support event configuration fields definition (event creation is just adding a value to eventType enumeration), there is no API preview panel when adding an event type. The REST URL is displayed  in the transactional message user interface once an event transactional message is published.-->
