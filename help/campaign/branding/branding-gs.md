---
title: Marques
description: Découvrir tous les outils disponibles pour gérer les identités de branding
audience: administration
context-tags: branding,overview;branding,main
role: Admin
level: Experienced
badge: label="DISPONIBILITÉ LIMITÉE" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Limité aux utilisateurs migrés Campaign Standard"
source-git-commit: 51abadc86b97097d13824651d8c50d4ddd014a51
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 54%

---

# Prise en main de la marque {#branding-gs}

>[!IMPORTANT]
>
>Les marques ne peuvent pas être créées ni modifiées par des utilisateurs finaux : ces opérations doivent être effectuées par l&#39;administrateur technique Adobe Campaign. Pour toute demande, contactez l&#39;Assistance clientèle Adobe.

Chaque entreprise dispose de directives de marque qui définissent à la fois des éléments visuels et des détails techniques. Adobe Campaign vous aide à gérer ces consignes de manière centralisée, afin que vous puissiez présenter une image de marque cohérente à vos clients dans tous vos domaines, depuis les logos contenus dans les emails jusqu’aux URL et domaines utilisés dans vos campagnes.

Les administrateurs techniques peuvent créer et gérer plusieurs marques dans Adobe Campaign. Vous pouvez ainsi définir tous les éléments qui constituent votre identité de marque, y compris les logos et même les paramètres de tracking des emails. Une fois créées, ces marques peuvent être facilement liées à vos diffusions.

Vous pouvez ajouter de nouvelles entités de votre organisation dans Campaign ou créer un nouveau type d’e-mail que vous devez envoyer sous un autre sous-domaine. Pour ce faire, suivez les étapes ci-après :

1. **Configurer un nouveau sous-domaine** - Pour tout nouveau sous-domaine utilisé par Adobe, la première étape consiste à le configurer. Vous pouvez effectuer cette opération via le [Panneau de contrôle Campaign](https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-certificates/subdomains-branding.html?lang=fr) ou contacter votre contact technique Adobe. En savoir plus sur la configuration des sous-domaines [dans cette page](https://experienceleague.adobe.com/en/docs/deliverability-learn/deliverability-best-practice-guide/additional-resources/campaign/ac-domain-name-setup).

   >[!NOTE]
   >
   >Le Panneau de contrôle est accessible à tous les utilisateurs administrateurs. Les étapes permettant d&#39;octroyer un accès administrateur à un utilisateur sont présentées sur [cette page](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html?lang=fr#discover-control-panel).

1. **Créer un modèle de diffusion** - Une fois la nouvelle marque disponible, il est recommandé de créer au moins un modèle de diffusion vierge qui fait référence à cette nouvelle marque. [En savoir plus](branding-assign.md).

1. **Vérifier les instructions relatives à la délivrabilité** : avant de commencer à utiliser le nouveau domaine, la stratégie doit être discutée avec l&#39;équipe Adobe chargée de la délivrabilité Elles aideront à définir les bonnes pratiques, si une nouvelle affinité doit être créée pour fractionner les adresses IP entre les domaines, par exemple, et/ou si un plan de montée en puissance doit être défini.

