---
title: Branding
description: Découvrez comment configurer votre marque
audience: administration
context-tags: branding,overview;branding,main
role: Admin
level: Experienced
badge: label="DISPONIBILITÉ LIMITÉE" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Limité aux utilisateurs migrés Campaign Standard"
exl-id: 7afc802d-e90c-48c8-aa04-3ea543dfdfbc
source-git-commit: 34c6f8a137a9085b26c0ea8f78930cff6192cfc9
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 8%

---

# Configurer des marques {#branding-configure}

>[!IMPORTANT]
>
>Les marques ne peuvent pas être créées ni modifiées par les utilisateurs finaux : ces opérations doivent être effectuées par l&#39;administrateur technique d&#39;Adobe Campaign. Pour toute demande, contactez l&#39;Assistance clientèle Adobe.

Dans Adobe Campaign V8, les marques se trouvent dans le menu **[!UICONTROL Administration > Plateforme > Marques]** .

Une **[!UICONTROL marque]** est définie par les caractéristiques suivantes :

* Une **[!UICONTROL identité]**, qui définit et personnalise votre marque. Cette section contient les champs suivants :

   * **[!UICONTROL Libellé]** visible dans l’interface
   * **[!UICONTROL ID]**
   * **[!UICONTROL Nom de la marque]**
   * **[!UICONTROL URL du site Web]** et **[!UICONTROL Libellé du site Web]** de la marque
   * **[!UICONTROL Logo de la marque]**

  ![](assets/branding_1.png)

* **[!UICONTROL Paramètres d&#39;en-tête des emails envoyés]** qui permettent de personnaliser les informations qui seront visibles par les destinataires de vos campagnes. Cette section contient les champs suivants :

   * **[!UICONTROL Expéditeur (adresse email)]** avec l&#39;adresse email de la marque.
   * **[!UICONTROL Expéditeur (nom)]** avec le nom de la marque.
   * **[!UICONTROL Répondre à (adresse électronique)]** avec l’adresse électronique à laquelle le client peut répondre.
   * **[!UICONTROL Répondre à (nom)]** avec le nom de la marque.
   * **[!UICONTROL Erreur (adresse électronique)]** avec l’adresse électronique à utiliser en cas d’erreur.

  >[!IMPORTANT]
  >
  >Après avoir mis à jour les paramètres d’en-tête des emails, si le nom et l’adresse email de l’expéditeur n’ont pas changé dans l’email créé à partir du modèle, vérifiez les paramètres avancés du modèle.

  ![](assets/branding_2.png)

* **[!UICONTROL Les configurations de marque]** définissent les serveurs utilisés pour le suivi également pour l’accès aux landing pages. Cette section contient les champs suivants :

   * **[!UICONTROL Sous-domaine de la marque]** fait référence à l’URL de sous-domaine désigné spécifique à cette marque, demandé pour délégation par Adobe.

  Notez que la configuration des serveurs de suivi, de miroir et d’application est stockée dans des comptes externes distincts associés au routage. Ces paramètres sont appliqués lors de la mise en service et ne doivent pas être modifiés. Pour afficher les URL, accédez à l&#39;onglet **[!UICONTROL Préfixes de branding]** depuis votre compte externe.

  ![](assets/branding_3.png)

<!--![](assets/branding_05.png)-->

<!--
* **[!UICONTROL Tracking URL configs]**, which defines the configuration of the URLs tracking for your brand.

  The additional parameters that allow the links to be tracked on external systems such as Web Analytics tools like Adobe Analytics or Google Analytics are defined here.
-->
