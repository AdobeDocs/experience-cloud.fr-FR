---
title: Marques
description: Découvrez comment attribuer votre marque
audience: administration
context-tags: branding,overview;branding,main
role: Admin
level: Experienced
badge: label="DISPONIBILITÉ LIMITÉE" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Limité aux utilisateurs migrés Campaign Standard"
source-git-commit: 51abadc86b97097d13824651d8c50d4ddd014a51
workflow-type: tm+mt
source-wordcount: '481'
ht-degree: 20%

---

# Attribuer votre marque {#branding-assign}

>[!IMPORTANT]
>
>Les options de branding sont actuellement limitées aux diffusions email et push.

## Associer une marque à un modèle {#linking-a-brand-to-a-template}

Pour utiliser les paramètres définis pour une marque, elle doit être liée à un modèle de diffusion. Pour ce faire, vous devez créer, ou éditer, un modèle.

Votre modèle sera associé à la marque. Dans l&#39;éditeur d&#39;email, les éléments comme l&#39;**adresse email de l&#39;expéditeur par défaut**, le **nom de l&#39;expéditeur par défaut** ou le **logo** utiliseront les données paramétrées de la marque.

>[!BEGINTABS]

>[!TAB Adobe Campaign V8]

Pour créer un modèle de diffusion, vous pouvez dupliquer un modèle intégré, convertir une diffusion existante en modèle ou créer entièrement un modèle de diffusion. [En savoir plus](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/create-templates)

Une fois votre modèle créé, vous pouvez le lier à une marque. Pour ce faire :

1. Accédez à **[!UICONTROL Ressources]** `>` **[!UICONTROL Modèles]** `>` **[!UICONTROL Modèles de diffusion]** dans l’explorateur Adobe Campaign.

1. Sélectionnez un modèle de diffusion ou dupliquez-en un existant.

   ![](assets/branding_assign_V8_1.png)

1. Accédez au **[!UICONTROL Propriétés]** de votre modèle de diffusion sélectionné.

   ![](assets/branding_assign_V8_2.png)

1. Dans la **[!UICONTROL Général]** , sélectionnez votre marque dans la **[!UICONTROL Marques]** menu déroulant.

   ![](assets/branding_assign_V8_3.png)

1. Une fois la configuration effectuée, sélectionnez **OK**.

Vous pouvez maintenant utiliser ce modèle pour envoyer vos diffusions.

>[!TAB Adobe Campaign Web]

Pour créer un modèle de diffusion, vous pouvez dupliquer un modèle intégré, convertir une diffusion existante en modèle ou créer entièrement un modèle de diffusion. [En savoir plus](https://experienceleague.adobe.com/en/docs/campaign-web/v8/msg/delivery-template)

Une fois votre modèle créé, vous pouvez le lier à une marque. Pour ce faire :

1. Accédez au **[!UICONTROL Modèles]** , depuis l’onglet **[!UICONTROL Diffusions]** et sélectionnez un modèle de diffusion.

   ![](assets/branding_assign_web_1.png)

1. Cliquez sur **[!UICONTROL Paramètres]**.

   ![](assets/branding_assign_web_2.png)

1. Dans la **[!UICONTROL Diffusion]** , accédez à la **[!UICONTROL Marques]** et sélectionnez la marque que vous souhaitez lier au modèle.

   ![](assets/branding_assign_web_3.png)

1. Validez votre sélection et enregistrez votre modèle.

Vous pouvez maintenant utiliser ce modèle pour envoyer vos diffusions.

>[!ENDTABS]

## Attribuer une marque à votre diffusion {#assigning-a-brand-to-an-email}

>[!BEGINTABS]

>[!TAB Adobe Campaign V8]

Pour créer une diffusion autonome, procédez comme suit.

1. Pour créer une diffusion, accédez au **[!UICONTROL Campagnes]** .

1. Cliquez sur **[!UICONTROL Diffusions]** et cliquez sur le bouton **[!UICONTROL Créer]** au-dessus de la liste des diffusions existantes.

   ![](assets/branding_assign_V8_4.png)

1. Sélectionnez un modèle de diffusion.

1. Accédez au **[!UICONTROL Propriétés]** de votre modèle de diffusion sélectionné.

   ![](assets/branding_assign_V8_5.png)

1. Dans la **[!UICONTROL Général]** , sélectionnez votre marque dans la **[!UICONTROL Marques]** menu déroulant.

   ![](assets/branding_assign_V8_6.png)

1. Une fois la configuration effectuée, sélectionnez **OK**.

1. personnaliser davantage vos diffusions ; Pour plus d’informations sur la création d’un email, reportez-vous à la section [Concevoir et envoyer des emails](https://experienceleague.adobe.com/en/docs/campaign-web/v8/msg/email/create-email) .

>[!TAB Adobe Campaign Web]

Pour créer une diffusion autonome, procédez comme suit.

1. Accédez au **[!UICONTROL Diffusions]** sur le rail de gauche, puis cliquez sur le **[!UICONTROL Créer une diffusion]** bouton .

   ![](assets/branding_assign_web_4.png)

1. Sélectionnez Email ou Notification push comme canal et choisissez un modèle de diffusion dans la liste.

1. Cliquez sur le bouton **[!UICONTROL Créer une diffusion]** pour confirmer.

1. Dans la **[!UICONTROL Propriétés]** page, cliquez sur **[!UICONTROL Paramètres]**.

   ![](assets/branding_assign_web_5.png)

1. Dans la **[!UICONTROL Diffusion]** , accédez à la **[!UICONTROL Marques]** champ .

   ![](assets/branding_assign_web_6.png)

1. Sélectionnez la marque que vous souhaitez lier au modèle.

   ![](assets/branding_assign_web_7.png)

1. personnaliser davantage vos diffusions ; Pour plus d’informations sur la création d’un email, reportez-vous à la section [Créer votre premier email](https://experienceleague.adobe.com/en/docs/campaign-web/v8/msg/email/create-email) .

>[!ENDTABS]
