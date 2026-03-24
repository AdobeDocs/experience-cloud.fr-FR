---
title: Qu’est-ce qu’un indicateur de fonctionnalité ?
description: Découvrez les indicateurs de fonctionnalité et comment ils vous permettent d’activer ou de désactiver des fonctionnalités d’application au moment de l’exécution sans redéploiement.
source-git-commit: 1c8fd9b42d08f657b4e6b16efae86faa04d15565
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 0%

---


# Qu’est-ce qu’un indicateur de fonctionnalité ? {#what-is-a-feature-flag}

Un indicateur de fonctionnalité est un mécanisme qui vous permet d’activer ou de désactiver des fonctionnalités de votre application au moment de l’exécution, sans redéployer le code.

Les indicateurs de fonctionnalité découplent **déploiement du code** de **disponibilité de la fonctionnalité**. Vous pouvez envoyer du nouveau code en production avec la fonction masquée derrière un indicateur, puis l’activer dès que vous êtes prêt (pour tous les utilisateurs ou pour un sous-ensemble ciblé).

Cette séparation réduit considérablement le risque. L’équipe de développement peut créer et envoyer en continu avec un minimum de perturbations, tandis que les équipes produit gardent le contrôle total sur le moment et le destinataire de la visibilité d’une fonctionnalité.

>[!NOTE]
>
>Dans les déploiements d&#39;expérience, un indicateur de fonction est l&#39;unité la plus atomique de contrôle de fonction. Il peut être utilisé seul pour cibler une seule fonctionnalité ou combiné avec d’autres indicateurs dans une [version de groupe de fonctionnalités](feature-groups-to-control-multiple-features.md) ou [version](release-management.md).
