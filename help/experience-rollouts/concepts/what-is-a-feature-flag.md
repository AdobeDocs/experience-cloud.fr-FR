---
title: Qu’est-ce qu’un indicateur de fonctionnalité ?
description: Découvrez les indicateurs de fonctionnalité et comment ils vous permettent d’activer ou de désactiver des fonctionnalités d’application au moment de l’exécution sans redéploiement.
hide: true
exl-id: c4ed4ab5-0d73-4697-b05c-476d6e4010ce
source-git-commit: 12032cbed45e694a3f25f16afe80308b3eb82924
workflow-type: tm+mt
source-wordcount: '154'
ht-degree: 0%

---

# Qu’est-ce qu’un indicateur de fonctionnalité ? {#what-is-a-feature-flag}

Un indicateur de fonctionnalité est un mécanisme qui vous permet d’activer ou de désactiver des fonctionnalités de votre application au moment de l’exécution, sans redéployer le code.

Les indicateurs de fonctionnalité découplent **déploiement du code** de **disponibilité de la fonctionnalité**. Vous pouvez envoyer du nouveau code en production avec la fonction masquée derrière un indicateur, puis l’activer dès que vous êtes prêt (pour tous les utilisateurs ou pour un sous-ensemble ciblé).

Cette séparation réduit considérablement le risque. L’équipe de développement peut créer et envoyer en continu avec un minimum de perturbations, tandis que les équipes produit gardent le contrôle total sur le moment et le destinataire de la visibilité d’une fonctionnalité.

>[!NOTE]
>
>Dans les déploiements d&#39;expérience, un indicateur de fonction est l&#39;unité la plus atomique de contrôle de fonction. Il peut être utilisé seul pour cibler une fonctionnalité unique ou combiné avec d&#39;autres indicateurs dans un [groupe de fonctionnalités](feature-groups-to-control-multiple-features.md).

<!-- -->
