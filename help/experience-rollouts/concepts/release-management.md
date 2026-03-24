---
title: Gestion des versions dans les déploiements d’expérience
description: Découvrez comment la gestion des versions dans les déploiements d’expérience coordonne la diffusion de fonctionnalités multi-équipes par le biais de déploiements sombres, de tests de production et de déploiements progressifs.
source-git-commit: 1c8fd9b42d08f657b4e6b16efae86faa04d15565
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 1%

---


# Gestion des versions dans les déploiements d’expérience {#release-management}

Une mise à jour majeure type implique plusieurs équipes et plusieurs applications, chacune ayant sa propre chronologie de déploiement et ses propres dépendances. Les déploiements d’expérience fournissent un modèle de gestion des versions qui permet aux équipes de travailler de manière indépendante tout en fournissant une version coordonnée et contrôlée aux utilisateurs finaux.

## Fonctionnalités principales {#capabilities}

### Déploiements sombres {#dark-deployments}

Les équipes n’ont plus besoin d’horodater le déploiement de leur code avec une date de mise en production spécifique. Le code peut être déployé en production derrière des indicateurs de fonctionnalité à tout moment. Les utilisateurs finaux ne voient aucune modification tant que la version n’est pas activée. Les équipes peuvent se déployer à leur propre rythme, persuadées que rien n’est exposé prématurément.

### Tests en production {#testing-in-production}

Une fois que le code est déployé en production (déploiement sombre), les déploiements d’expérience peuvent ouvrir les fonctionnalités aux testeurs internes et aux équipes d’assurance qualité. Cela permet des tests complets par rapport à l’environnement de production et aux données de production réelles, sans risque d’exposer les modifications aux utilisateurs finaux.

### Déploiement graduel {#gradual-rollout}

Lorsqu’une version est prête à être mise en ligne, elle n’a pas besoin d’être tout ou rien. Les déploiements d’expérience permettent de contrôler le déploiement progressivement, en commençant par un petit pourcentage d’utilisateurs, en surveillant les commentaires et les performances et en élargissant l’audience au fil du temps. Cela réduit la pression sur les systèmes principaux et donne aux équipes le temps de répondre à tous les problèmes avant une exposition complète.

### Activation coordonnée {#coordinated-activation}

Plusieurs équipes développent des fonctionnalités indépendamment, chacune derrière ses propres indicateurs de fonctionnalité. Une fois que toutes les équipes sont prêtes, les déploiements d’expérience fournissent un point de contrôle unique pour activer tous les indicateurs entre les équipes et les applications simultanément (ou progressivement), de sorte que la version soit publiée comme une expérience cohérente.

## Voir également {#see-also}

* [Concept de gestion des versions](concept-of-release-management.md)
* [Groupes de fonctionnalités pour contrôler plusieurs fonctionnalités](feature-groups-to-control-multiple-features.md)
* [Déploiement graduel](gradual-rollout.md)
