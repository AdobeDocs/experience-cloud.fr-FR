---
title: Création d’une dimension de profil
description: Découvrez comment créer une dimension de profil à partir des données de profil.
audience: reporting
content-type: reference
level: Intermediate
exl-id: a12dc772-13c7-45ff-9fbf-3dfdd3801eae
TQID: https://experienceleague.adobe.com/eru99ME-JlrcRl074heBXwVhBLgeQJaQdiJkM-QT2SY
product_v2:
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
feature_v2:
  - id: fdbb8fc9-ffa3-4b86-88fe-aa4c5a3e1bc6
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: ad84694f2f6f45e4ee30fc51379106835ac302be
workflow-type: tm+mt
source-wordcount: 517
ht-degree: 97%

---

# Création d’une dimension de profil{#creating-a-custom-profile-dimension}

Les rapports peuvent également être créés et gérés en fonction des données de profil créées lors de l’extension du schéma des personnes destinataires.

* [Étape 1 : étendre votre schéma des personnes destinataires](##extend-schema)
* [Étape 2 : lier votre nouveau champ personnalisé](#link-custom)
* [Étape 3 : créer un rapport dynamique pour filtrer les personnes destinataires avec la dimension de profil](#create-report)

## Étape 1 : étendre votre schéma des personnes destinataires {#extend-schema}

Pour ajouter un nouveau champ de profil, vous devez étendre votre schéma. Procédez comme suit :

1. Accédez au dossier **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Schémas de données]** dans l’explorateur.

   ![](assets/custom_field_1.png)

1. Identifiez votre schéma des personnes destinataires personnalisé et sélectionnez-le. Si vous n&#39;avez pas encore étendu le schéma nms:recipient intégré, reportez-vous à [cette procédure](https://experienceleague.adobe.com/fr/docs/campaign/campaign-v8/developer/shemas-forms/extend-schema).

1. Ajoutez votre champ personnalisé à l’éditeur de schéma.

   Par exemple, pour ajouter un champ personnalisé Fidélité dans votre schéma des personnes destinataires, procédez comme suit :

   ```
   <attribute label="Loyalty" name="loyalty" type="string"/>
   ```

   ![](assets/custom_field_2.png)

1. Cliquez sur **[!UICONTROL Enregistrer]**.

1. Ensuite, identifiez votre schéma broadLogRcp personnalisé et sélectionnez-le. Si vous n’avez pas encore étendu le schéma intégré des logs de diffusion, reportez-vous à [cette procédure](https://experienceleague.adobe.com/fr/docs/campaign/campaign-v8/developer/shemas-forms/extend-schema).

1. Ajoutez le même champ personnalisé que votre schéma des personnes destinataires à l’éditeur de schéma.

   ![](assets/custom_field_3.png)

1. Cliquez sur **[!UICONTROL Enregistrer]**.

1. Pour appliquer les modifications apportées aux schémas, lancez l’assistant de mise à jour de la base de données via **[!UICONTROL Outils]** > **[!UICONTROL Avancé]** > **[!UICONTROL Mettre à jour la structure de la base de données]** et exécutez la commande Mettre à jour la structure de la base de données. [En savoir plus](https://experienceleague.adobe.com/fr/docs/campaign/campaign-v8/developer/shemas-forms/update-database-structure)

   ![](assets/custom_field_4.png)

Votre nouveau champ de profil est maintenant prêt à être utilisé et sélectionné par vos destinataires.

## Étape 2 : lier votre nouveau champ personnalisé {#link-custom}

>[!NOTE]
>
> Vous pouvez seulement ajouter jusqu’à 20 champs personnalisés au rapport dynamique.

Maintenant que votre champ de profil est créé, nous devons le lier à la dimension de rapport dynamique correspondante.

Avant d’étendre le log avec notre champ de profil, veillez à ce que la fenêtre des PII ait été acceptée afin de pouvoir envoyer des données de PII vers le rapport dynamique. Pour en savoir plus à ce sujet, consultez cette [page](pii-agreement.md).

1. Accédez au dossier **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Schémas de données]** > **[!UICONTROL Champ de rapport supplémentaire]** dans l’explorateur.

   ![](assets/custom_field_5.png)

1. Cliquez sur **[!UICONTROL Nouveau]** pour créer la dimension de rapport dynamique correspondante.

1. Sélectionnez **[!UICONTROL Modifier l’expression]** et parcourez le schéma des personnes destinataires pour trouver le champ de profil précédemment créé.

   ![](assets/custom_field_6.png)

1. Cliquez sur **[!UICONTROL Terminer]**.

1. Saisissez votre **[!UICONTROL Libellé]** de dimension, visible dans les rapports dynamiques, puis cliquez sur **[!UICONTROL Enregistrer]**.

   ![](assets/custom_field_7.png)

Votre champ de profil est maintenant disponible en tant que dimension de profil dans vos rapports. Pour supprimer votre dimension de profil, vous pouvez la sélectionner et cliquer sur l’icône **[!UICONTROL Supprimer]**.

Maintenant que le schéma des destinataires a été étendu avec ce champ de profil et que votre dimension personnalisée a été créée, vous pouvez commencer à cibler les destinataires dans les diffusions.

## Étape 3 : créer un rapport dynamique pour filtrer les personnes destinataires avec la dimension de profil {#create-report}

Après l’envoi de votre diffusion, vous pouvez répartir les rapports à l’aide de votre dimension de profil.

1. Depuis l&#39;onglet **[!UICONTROL Rapports]**, sélectionnez un rapport aux paramètres d&#39;usine et cliquez sur le bouton **[!UICONTROL Créer]** pour en lancer un à partir de zéro.

   ![](assets/custom_field_8.png)

1. Dans la catégorie **[!UICONTROL Dimensions]**, cliquez sur **[!UICONTROL Profil]**, puis faites glisser et déposez votre dimension de profil sur votre tableau à structure libre.

   ![](assets/custom_field_9.png)

1. Faites glisser et déposez des mesures pour commencer à filtrer vos données.

1. Faites glisser et déposez une visualisation dans votre espace de travail, le cas échéant.

