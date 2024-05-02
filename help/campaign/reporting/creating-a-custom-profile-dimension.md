---
title: Création d'une dimension de profil personnalisé
description: Découvrez comment créer une dimension de profil personnalisé à partir des données de profil personnalisé.
audience: reporting
content-type: reference
level: Intermediate
source-git-commit: 5a7337c44d6ca5ee4403d9fe0b65246b629afacd
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 22%

---

# Création d&#39;une dimension de profil personnalisé{#creating-a-custom-profile-dimension}

Les rapports peuvent également être créés et gérés en fonction des données de profil personnalisées créées lors de l&#39;extension du schéma des destinataires.

* [Etape 1 : Etendre le schéma de vos destinataires](##extend-schema)
* [Étape 2 : lier votre nouveau champ personnalisé](#link-custom)
* [Étape 3 : Création d&#39;un rapport dynamique pour filtrer les destinataires avec la dimension de profil personnalisé](#create-report)

## Etape 1 : Etendre le schéma de vos destinataires {#extend-schema}

Pour ajouter un nouveau champ de profil, vous devez étendre votre schéma, procédez comme suit :

1. Accédez au **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Schémas de données]** dans l’Explorateur.

   ![](assets/custom_field_1.png)

1. Identifiez votre schéma de destinataire personnalisé et sélectionnez-le. Si vous n&#39;avez pas encore étendu le schéma nms:recipient intégré, reportez-vous à la section [cette procédure](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/developer/shemas-forms/extend-schema).

1. Ajoutez votre champ personnalisé à l’éditeur de schéma.

   Par exemple, pour ajouter un champ personnalisé Loyalty dans votre schéma de destinataire :

   ```
   <attribute label="Loyalty" name="loyalty" type="string"/>
   ```

   ![](assets/custom_field_2.png)

1. Cliquez sur **[!UICONTROL Enregistrer]**.

1. Identifiez ensuite votre schéma broadLogRcp personnalisé et sélectionnez-le. Si vous n&#39;avez pas encore étendu le schéma de log de diffusion intégré, reportez-vous à la section [cette procédure](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/developer/shemas-forms/extend-schema).

1. Ajoutez le même champ personnalisé que votre schéma Destinataire dans l’éditeur de schéma.

   ![](assets/custom_field_3.png)

1. Cliquez sur **[!UICONTROL Enregistrer]**.

1. Pour appliquer les modifications apportées aux schémas, lancez l&#39;assistant Mise à jour de la base via **[!UICONTROL Outils]** > **[!UICONTROL Avancé]** > **[!UICONTROL Mettre à jour la structure de la base de données]** et exécutez le workflow Mise à jour de la structure de la base de données. [En savoir plus](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/developer/shemas-forms/update-database-structure)

   ![](assets/custom_field_4.png)

Votre nouveau champ de profil est maintenant prêt à être utilisé et sélectionné par vos destinataires.

## Étape 2 : lier votre nouveau champ personnalisé {#link-custom}

>[!NOTE]
>
> Vous pouvez uniquement ajouter jusqu’à 20 champs personnalisés au rapport dynamique.

Maintenant que votre champ de profil est créé, nous devons le lier à la dimension de reporting dynamique correspondante.

1. Accédez au **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Schémas de données]** > **[!UICONTROL Champ de création de rapports supplémentaire]** dans l’Explorateur.

   ![](assets/custom_field_5.png)

1. Cliquez sur **[!UICONTROL Nouveau]** pour créer la dimension de création de rapports dynamiques correspondante.

1. Sélectionner **[!UICONTROL Expression d’édition]** et parcourez le schéma Destinataire pour trouver le champ de profil personnalisé que vous avez créé précédemment.

   ![](assets/custom_field_6.png)

1. Cliquez sur **[!UICONTROL Terminer]**.

1. Saisissez votre dimension **[!UICONTROL Libellé]**, visible dans les rapports dynamiques, puis cliquez sur **[!UICONTROL Enregistrer]**.

   ![](assets/custom_field_7.png)

Votre champ de profil personnalisé est désormais disponible en tant que dimension de profil personnalisé dans vos rapports. Pour supprimer la dimension de votre profil personnalisé, vous pouvez la sélectionner et cliquer sur le bouton **[!UICONTROL Supprimer]** Icône

Maintenant que le schéma des destinataires a été étendu avec ce champ de profil et votre dimension personnalisée créée, vous pouvez commencer à cibler les destinataires dans les diffusions.

## Étape 3 : Création d&#39;un rapport dynamique pour filtrer les destinataires avec la dimension de profil personnalisé {#create-report}

Une fois votre diffusion envoyée, vous pouvez ventiler les rapports à l’aide de la dimension de votre profil personnalisé.

1. Depuis l&#39;onglet **[!UICONTROL Rapports]**, sélectionnez un rapport aux paramètres d&#39;usine et cliquez sur le bouton **[!UICONTROL Créer]** pour en lancer un à partir de zéro.

   ![](assets/custom_field_8.png)

1. Dans le **[!UICONTROL Dimensions]** catégorie, cliquez sur **[!UICONTROL Profil]** puis faites glisser et déposez votre dimension de profil personnalisé dans votre tableau à structure libre.

   ![](assets/custom_field_9.png)

1. Faites glisser et déposez des mesures pour commencer à filtrer vos données.

1. Faites glisser et déposez une visualisation dans votre espace de travail, le cas échéant.
