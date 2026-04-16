---
title: Pourquoi utiliser des indicateurs ?
description: Découvrez les principaux cas d’utilisation des indicateurs dans Adobe Target, des tests de fonctionnalités sélectifs aux versions multi-applications coordonnées.
hide: true
exl-id: c39c6b34-2024-4c38-b2f2-a9b58f5eff63
source-git-commit: b3e13a42c19eb7b8b7d5d402bf9a56f89f573044
workflow-type: tm+mt
source-wordcount: '254'
ht-degree: 1%

---

# Pourquoi utiliser des indicateurs ? {#why-use}

Les indicateurs sont l’outil idéal lorsque vous devez contrôler qui voit une fonctionnalité et quand, que vous testiez en cours de développement, que vous effectuiez une validation avec un sous-ensemble d’utilisateurs ou que vous coordonniez une mise à jour volumineuse entre plusieurs équipes.

## Cas d’utilisation courants {#use-cases}

**Tests sélectifs pendant le développement**
Testez une fonctionnalité par rapport à votre propre session pendant que d’autres développeurs continuent leur travail sans être affectés. Aucun embranchement de code complexe n’est requis.

**Déploiement par étapes avec commentaires de l’utilisateur**
Commencez par proposer une fonctionnalité à un petit groupe d’utilisateurs. Collectez des commentaires, résolvez les problèmes, puis étendez progressivement l’audience avant une publication complète.

**Déploiement progressif en production**
Ouvrez une nouvelle fonctionnalité progressivement (1 %, 10 %, 50 %, puis 100 % des utilisateurs). Surveillez les performances et la réponse de l’utilisateur à chaque étape. Si quelque chose ne va pas, éteignez-le immédiatement.

**Gestion du chargement principal**
Déployez progressivement pour éviter les pics de trafic soudains sur les services principaux, plutôt que d’exposer tous les utilisateurs et utilisatrices à une nouvelle fonctionnalité à la fois.

**Versions multi-applications coordonnées**
Activez une fonctionnalité simultanément dans plusieurs applications et équipes pour un ensemble spécifique d’utilisateurs. Les indicateurs assurent la cohérence sur toute la surface de libération.

**Versions différées**
Déployez le code en production à l’avance, puis activez la fonctionnalité à un moment précis (par exemple, au début d’un événement de lancement de produit) sans changement de code de dernière minute.

Commutateur **Kill**
Si un problème est détecté après la publication de la version, désactivez instantanément la fonctionnalité sans correctif ni redéploiement.

<!-- -->
