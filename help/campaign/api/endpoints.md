---
title: Points d’entrée
description: En savoir plus sur les points d’entrée des API.
audience: developing
content-type: reference
topic-tags: campaign-standard-apis
role: Data Engineer
level: Experienced
badge: label="DISPONIBILITÉ LIMITÉE" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Limité aux utilisateurs migrés Campaign Standard"
source-git-commit: 84b72258789ba61016deb813e93bdca0ea142712
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 95%

---

# Points d’entrée {#endpoints}

Points d’entrée disponibles des API REST d’Adobe Campaign :

* **/profileAndServices** : permet d’interagir avec les champs d’usine. Les champs étendus ne sont pas accessibles par ce point d’entrée.
* **/profileAndServicesExt** : permet d’interagir avec les champs personnalisés ajoutés lors de l’extension des ressources personnalisées Profile ou Services. Pour plus d’informations sur les ressources personnalisées, reportez-vous à [cette section](custom-resources.md).
* **/&lt;transactionalAPI>** : permet d’interagir avec l’API des messages transactionnels (le nom du point d’entrée de l’API des messages transactionnels dépend de la configuration de votre instance). Voir à ce propos [cette section](managing-transactional-messages.md).
* **/workflow/exécution** : permet d’interagir avec les workflows. Voir à ce propos [cette section](controlling-a-workflow.md).

Par défaut, les principales ressources disponibles pour les API **profileAndServices** et **profileAndServicesExt** sont les suivantes :

* **/profile** : permet d’interagir avec les profils issus de la base de données Campaign. Pour ajouter des profils à un service, utilisez le point d’entrée **/service**. Pour plus d’informations sur les profils dans Campaign, reportez-vous à la [documentation de Campaign](https://helpx.adobe.com/fr/campaign/standard/audiences/using/about-profiles.html).
* **/service** : permet de gérer les services d’abonnement. Pour plus d’informations sur les services dans Campaign, reportez-vous à la [documentation de Campaign](https://helpx.adobe.com/fr/campaign/standard/audiences/using/creating-a-service.html).

>[!NOTE]
>
>Toutes les autres ressources étendues ou créées sont exclusivement disponibles via l’API **ProfileAndServicesExt**. Elles doivent être liées à la ressource **Profile** pour être accessibles.
