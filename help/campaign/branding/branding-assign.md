---
title: Branding
description: Découvrir comment attribuer votre marque
audience: administration
context-tags: branding,overview;branding,main
role: Admin
level: Experienced
badge: label="DISPONIBILITÉ LIMITÉE" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Restrictions aux utilisateurs ayant migré vers Campaign Standard"
exl-id: 8f6a5255-0245-497b-880f-d91ea82ee19e
TQID: https://experienceleague.adobe.com/aL-I6JknWhDoCob136gJB5Ier2a-T0oMiVFn1ZnRw0s
product_v2:
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
feature_v2:
  - id: fdbb8fc9-ffa3-4b86-88fe-aa4c5a3e1bc6
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2:
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: ad84694f2f6f45e4ee30fc51379106835ac302be
workflow-type: tm+mt
source-wordcount: 513
ht-degree: 94%

---

# Attribuer votre marque {#branding-assign}

## Associer une marque à un modèle {#linking-a-brand-to-a-template}

Pour utiliser les paramètres définis pour une marque, elle doit être liée à un modèle de diffusion. Pour ce faire, vous devez créer ou modifier un modèle.

Votre modèle sera lié à la marque. Dans l’éditeur d’e-mail, les éléments comme l’**adresse e-mail de l’expéditeur ou de l’expéditrice par défaut**, le **nom de l’expéditeur ou de l’expéditrice par défaut** ou le **logo** utiliseront les données paramétrées de la marque.

>[!BEGINTABS]

>[!TAB Adobe Campaign V8]

Pour créer un modèle de diffusion, vous pouvez dupliquer un modèle intégré, convertir une diffusion existante en modèle ou créer un modèle de diffusion à partir de zéro. [En savoir plus](https://experienceleague.adobe.com/fr/docs/campaign/campaign-v8/send/create-templates)

Une fois votre modèle créé, vous pouvez le lier à une marque. Pour ce faire :

1. Accédez à **[!UICONTROL Ressources]** `>` **[!UICONTROL Modèles]** `>` **[!UICONTROL Modèles de diffusion]** dans l’explorateur Adobe Campaign.

1. Sélectionnez un modèle de diffusion ou dupliquez un modèle existant.

   ![](assets/branding_assign_V8_1.png)

1. Accédez aux **[!UICONTROL Propriétés]** du modèle de diffusion sélectionné.

   ![](assets/branding_assign_V8_2.png)

1. Dans l’onglet **[!UICONTROL Général]**, sélectionnez votre marque dans le menu déroulant **[!UICONTROL Branding]**.

   ![](assets/branding_assign_V8_3.png)

1. Une fois la configuration effectuée, sélectionnez **OK**.

Vous pouvez maintenant utiliser ce modèle pour envoyer vos diffusions.

>[!TAB Adobe Campaign Web]

Pour créer un modèle de diffusion, vous pouvez dupliquer un modèle intégré, convertir une diffusion existante en modèle ou créer un modèle de diffusion à partir de zéro. [En savoir plus](https://experienceleague.adobe.com/fr/docs/campaign-web/v8/msg/delivery-template)

Une fois votre modèle créé, vous pouvez le lier à une marque. Pour ce faire :

1. Accédez à l’onglet **[!UICONTROL Modèles]** dans le menu de gauche **[!UICONTROL Diffusions]**, puis sélectionnez un modèle de diffusion.

   ![](assets/branding_assign_web_1.png)

1. Cliquez sur **[!UICONTROL Paramètres]**.

   ![](assets/branding_assign_web_2.png)

1. Dans l’onglet **[!UICONTROL Diffusion]**, accédez au champ **[!UICONTROL Branding]** et sélectionnez la marque que vous souhaitez lier au modèle.

   ![](assets/branding_assign_web_3.png)

1. Validez votre sélection et enregistrez votre modèle.

Vous pouvez maintenant utiliser ce modèle pour envoyer vos diffusions.

>[!ENDTABS]

## Attribuer une marque à votre diffusion {#assigning-a-brand-to-an-email}

>[!BEGINTABS]

>[!TAB Adobe Campaign V8]

Pour créer une diffusion autonome, procédez comme suit.

1. Pour créer une diffusion, accédez à l’onglet **[!UICONTROL Campagnes]**.

1. Cliquez sur **[!UICONTROL Diffusions]** puis sur le bouton **[!UICONTROL Créer]** au-dessus de la liste des diffusions existantes.

   ![](assets/branding_assign_V8_4.png)

1. Sélectionnez un modèle de diffusion.

1. Accédez aux **[!UICONTROL Propriétés]** du modèle de diffusion sélectionné.

   ![](assets/branding_assign_V8_5.png)

1. Dans l’onglet **[!UICONTROL Général]**, sélectionnez votre marque dans le menu déroulant **[!UICONTROL Branding]**.

   ![](assets/branding_assign_V8_6.png)

1. Une fois la configuration effectuée, sélectionnez **OK**.

1. Personnalisez davantage vos diffusions. Pour plus d’informations sur la création d’un e-mail, consultez la section [Concevoir et envoyer des e-mails](https://experienceleague.adobe.com/fr/docs/campaign-web/v8/msg/email/create-email).

>[!TAB Adobe Campaign Web]

Pour créer une diffusion autonome, procédez comme suit.

1. Accédez au menu **[!UICONTROL Diffusions]** dans le rail de gauche, puis cliquez sur le bouton **[!UICONTROL Créer une diffusion]**.

   ![](assets/branding_assign_web_4.png)

1. Sélectionnez le canal E-mail ou Notification push et choisissez un modèle de diffusion dans la liste.

1. Cliquez sur le bouton **[!UICONTROL Créer une diffusion]** pour confirmer.

1. Sur la page **[!UICONTROL Propriétés]**, cliquez sur **[!UICONTROL Paramètres]**.

   ![](assets/branding_assign_web_5.png)

1. Dans l’onglet **[!UICONTROL Diffusion]**, accédez au champ **[!UICONTROL Branding]**.

   ![](assets/branding_assign_web_6.png)

1. Sélectionnez la marque que vous souhaitez associer au modèle.

   ![](assets/branding_assign_web_7.png)

1. Personnalisez davantage vos diffusions. Pour plus d’informations sur la création d’un e-mail, consultez la section [Créer votre premier e-mail](https://experienceleague.adobe.com/fr/docs/campaign-web/v8/msg/email/create-email).

>[!ENDTABS]
