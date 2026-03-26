---
title: Déploiements d’Adobe Experience
description: Découvrez comment utiliser les déploiements d’Adobe Experience pour diffuser des fonctionnalités en toute sécurité et progressivement avec des déploiements contrôlés, des indicateurs de fonctionnalité et une gestion d’audience ciblée.
exl-id: c400d75d-d928-4cf6-a094-1a2f443389f0
source-git-commit: 4a3133f014a9bb9d6ed26eb9d9f763db79ce63b3
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 1%

---

# Déploiements d’Adobe Experience {#experience-rollouts-home}

Les déploiements d’Adobe Experience permettent aux équipes produit d’expédier de nouvelles fonctionnalités progressivement et en toute sécurité, sans redéploiements ni temps d’arrêt. Vous définissez qui voit quoi, quand et à quel rythme. En cas de problème, vous désactivez immédiatement la fonctionnalité. Si tout se passe bien, vous augmentez l’audience selon votre calendrier.

## Ce que vous pouvez faire

**Contrôlez qui voit les nouvelles fonctionnalités.** Target est destiné à des utilisateurs, des organisations, des régions ou des attributs personnalisés spécifiques. Commencez par un petit groupe, validez l’expérience, puis développez - le tout à partir de la console, sans modification de code.

**Exécuter des expériences A/B.** Proposez différentes variantes à différents segments de votre audience et mesurez celui qui fonctionne le mieux. Utilisez les résultats pour prendre des décisions éclairées sur les produits avant une mise à jour complète.

**Réduction des risques de publication.** Divisez les modifications importantes en déploiements contrôlés plus petits. Si un bogue ou un problème de performances apparaît, désactivez uniquement la fonctionnalité concernée ; le reste de votre application reste stable.

**Coordination entre les équipes.** Les groupes de fonctionnalités multi-équipes permettent à plusieurs équipes de participer à une mise à jour coordonnée unique, chacune gérant ses propres indicateurs de fonctionnalité tout en partageant un planning de déploiement et une audience communs.

## Intégrer votre première fonctionnalité

Pour tirer parti des déploiements d’expérience, commencez par trois étapes :

1. **Configurez votre équipe et votre application** — [Demandez l’accès](guides/console/request-access.md) à la console, puis [intégrez votre application](guides/applications/onboard-your-application.md) afin que les déploiements d’expérience sachent quels clients servir.

2. **Créer et publier un indicateur de fonctionnalité** — Suivez le guide [Créer votre premier indicateur de fonctionnalité](guides/feature-flags/create-your-first-feature-flag.md) pour définir un indicateur, définir votre audience initiale et la publier dans votre environnement.

3. **Intégrer à votre application** — Connectez votre application à l’API de déploiements d’expérience ou à SDK afin qu’elle puisse récupérer et appliquer des indicateurs de fonctionnalité au moment de l’exécution. Commencez par les [&#x200B; étapes d’intégration &#x200B;](guides/integrate/integration-steps.md) pour votre type d’application.

Une fois votre premier indicateur activé, vous pouvez affiner son audience, configurer un déploiement progressif et le promouvoir d’un déploiement enregistré à un déploiement complet.

## Besoin d’aide ?

Si quelque chose ne se comporte pas comme prévu, le [&#x200B; guide de dépannage &#x200B;](guides/support/troubleshooting.md) couvre les problèmes les plus courants. Pour toute autre raison, [contactez l’assistance &#x200B;](guides/support/contact-support.md).
