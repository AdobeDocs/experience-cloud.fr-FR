---
title: Marques
description: Découvrez comment configurer votre marque
audience: administration
context-tags: branding,overview;branding,main
role: Admin
level: Experienced
badge: label="DISPONIBILITÉ LIMITÉE" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Limité aux utilisateurs migrés Campaign Standard"
source-git-commit: 56f2d2ff4b2ba4184629615a14724e6640df6961
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 63%

---

# Configurer des marques {#branding-configure}

>[!IMPORTANT]
>
>Les marques ne peuvent pas être créées ni modifiées par des utilisateurs finaux : ces opérations doivent être effectuées par l&#39;administrateur technique Adobe Campaign. Pour toute demande, contactez l&#39;Assistance clientèle Adobe.

Dans Adobe Campaign V8, les marques se trouvent dans la variable **[!UICONTROL Administration > Plateforme > Marques]** .

Une **[!UICONTROL marque]** est définie par les caractéristiques suivantes :

* Une **[!UICONTROL identité]** qui permet d&#39;identifier et de personnaliser votre marque. Cette section contient les champs suivants :

   * **[!UICONTROL Libellé]**, visible dans l&#39;interface
   * **[!UICONTROL ID]**
   * **[!UICONTROL Nom de la marque]**
   * **[!UICONTROL URL du site web]** et **[!UICONTROL Libellé du site web]** de la marque
   * **[!UICONTROL Logo de la marque]**

  ![](assets/branding_1.png)

* **[!UICONTROL Paramètres d&#39;en-tête des emails envoyés]** qui permettent de personnaliser les informations qui seront visibles par les destinataires de vos campagnes. Cette section contient les champs suivants :

   * **[!UICONTROL Expéditeur (adresse email)]** avec l&#39;adresse email de la marque
   * **[!UICONTROL Expéditeur (nom)]** avec le nom de la marque
   * **[!UICONTROL Répondre à (adresse email)]** avec l&#39;adresse email de réponse destinée au client
   * **[!UICONTROL Répondre à (nom)]** avec le nom de la marque
   * **[!UICONTROL Erreur (adresse email)]** avec l&#39;adresse email à utiliser en cas d&#39;erreur

  >[!IMPORTANT]
  >
  >Après avoir mis à jour les paramètres d&#39;en-tête des emails, si le nom et l&#39;adresse email de l&#39;expéditeur ne sont pas modifiés dans l&#39;email créé à partir du modèle, vérifiez les paramètres avancés de ce dernier.

  ![](assets/branding_2.png)

* **[!UICONTROL Configurations de marque]** définit les serveurs utilisés pour le suivi également pour l’accès aux landing pages. Cette section contient les champs suivants :

   * **[!UICONTROL Sous-domaine de marque]** fait référence à l’URL du sous-domaine désigné spécifique à cette marque, demandée pour délégation depuis l’Adobe.

  Notez que la configuration des serveurs de suivi, de miroir et d’application est stockée dans des comptes externes distincts associés au routage. Ces paramètres sont appliqués lors de la mise en service et ne doivent pas être modifiés. Pour afficher les URL, accédez à la **[!UICONTROL Préfixes de marque]** à partir de votre compte externe.

  ![](assets/branding_3.png)

<!--![](assets/branding_05.png)-->

<!--
* **[!UICONTROL Tracking URL configs]**, which defines the configuration of the URLs tracking for your brand.

  The additional parameters that allow the links to be tracked on external systems such as Web Analytics tools like Adobe Analytics or Google Analytics are defined here.
-->
