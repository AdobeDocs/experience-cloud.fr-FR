---
title: Flags
description: Découvrez comment utiliser les indicateurs dans Adobe Target pour diffuser progressivement et en toute sécurité des fonctionnalités avec des déploiements contrôlés, des indicateurs de fonctionnalités et une gestion d’audience ciblée.
hide: true
index: false
exl-id: c400d75d-d928-4cf6-a094-1a2f443389f0
source-git-commit: b3e13a42c19eb7b8b7d5d402bf9a56f89f573044
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 1%

---

# Flags {#experience-rollouts-home}

>[!AVAILABILITY]
>
>Flags est actuellement dans Beta et disponible pour les clients Adobe Target. Contactez votre représentant Adobe pour demander l’accès.

Les indicateurs dans Adobe Target permettent aux équipes produit d’expédier de nouvelles fonctionnalités progressivement et en toute sécurité, sans redéploiements ni temps d’arrêt. Vous définissez qui voit quoi, quand et à quel rythme. En cas de problème, vous désactivez immédiatement la fonctionnalité. Si tout se passe bien, vous augmentez l’audience selon votre calendrier.

## Ce que vous pouvez faire

**Contrôlez qui voit les nouvelles fonctionnalités.** Target est destiné à des utilisateurs, des organisations, des régions ou des attributs personnalisés spécifiques. Commencez par un petit groupe, validez l’expérience, puis développez - le tout à partir de la console, sans modification de code.

**Exécuter des expériences A/B.** Proposez différentes variantes à différents segments de votre audience et mesurez celui qui fonctionne le mieux. Utilisez les résultats pour prendre des décisions éclairées sur les produits avant une mise à jour complète.

**Réduction des risques de publication.** Divisez les modifications importantes en déploiements contrôlés plus petits. Si un bogue ou un problème de performances apparaît, désactivez uniquement la fonctionnalité concernée ; le reste de votre application reste stable.

**Coordination entre les applications.** Les groupes de fonctionnalités vous permettent de gérer plusieurs indicateurs de fonctionnalité ensemble, partageant une audience de déploiement commune entre les applications.

**Exporter vos données.** Exportez les données des indicateurs vers l’environnement de création de rapports de votre choix pour l’analyse et la mesure avec vos autres données Adobe.

## Intégrer votre premier indicateur

Pour obtenir de la valeur à partir des indicateurs , commencez par trois étapes :

1. **Indicateurs d’accès via Adobe Target** — Les indicateurs sont disponibles dans Adobe Target. [Demandez l’accès](guides/console/request-access.md) et ouvrez les indicateurs depuis l’interface de Target.

1. **Créer et publier un indicateur** — Suivez le guide [Créer votre premier indicateur de fonctionnalité](guides/feature-flags/create-your-first-feature-flag.md) pour définir un indicateur, définir votre audience initiale et la publier dans votre environnement.

1. **Intégrer à votre application** — Connectez votre application à l’aide d’AEP Web SDK ou d’AEP Mobile SDK afin qu’elle puisse récupérer et appliquer des indicateurs au moment de l’exécution. Commencez par les [ étapes d’intégration ](guides/integrate/integration-steps.md) pour votre type d’application.

Une fois votre premier indicateur activé, vous pouvez affiner son audience, configurer un déploiement progressif et le promouvoir d’un déploiement enregistré à un déploiement complet.

## Besoin d’aide ?

Si quelque chose ne se comporte pas comme prévu, contactez votre représentant Adobe pour obtenir de l’aide.

<!-- 
Bob was here
-->
