---
title: Déploiement graduel
description: Découvrez comment les déploiements progressifs dans les déploiements d’expérience vous permettent d’échelonner la diffusion des fonctionnalités en production en toute sécurité, avec des commentaires en temps réel et un risque minimal.
source-git-commit: 1c8fd9b42d08f657b4e6b16efae86faa04d15565
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 2%

---


# Déploiement graduel {#gradual-rollout}

Le déploiement progressif met progressivement en production une nouvelle fonctionnalité, au lieu de l’activer pour tous les utilisateurs en même temps. Cette approche réduit les risques, permet de gérer la charge du serveur principal et crée une boucle de commentaires étroite avant la publication complète.

## Avantages {#benefits}

**Filet de sécurité**
En commençant par diffuser à une petite audience, vous pouvez suivre les commentaires et surveiller le comportement en production avant le développement. Si des problèmes apparaissent, l’impact est limité et la fonctionnalité peut être désactivée immédiatement, sans changement de code ni redéploiement.

**Gestion de la charge principale**
L’ouverture d’une fonctionnalité à tous les utilisateurs et utilisatrices simultanément peut provoquer des pics soudains de charge du serveur. Un déploiement progressif répartit l’augmentation du trafic au fil du temps, ce qui permet à l’infrastructure de se dimensionner en douceur.

**Commentaires en temps réel**
Chaque phase du déploiement fait apparaître les commentaires des utilisateurs réels. Les équipes peuvent agir sur ces commentaires (affiner l’expérience, corriger les cas de périphérie ou ajuster le message) avant la phase suivante.

## Fonctionnement {#how-it-works}

Les déploiements d’expérience fournissent des règles de ciblage granulaires pour augmenter l’exposition des utilisateurs étape par étape. Un déploiement progressif standard peut suivre le modèle suivant :

1. Activer la fonctionnalité pour **1 %** des utilisateurs
2. Surveiller les retours d’informations et les mesures de performances
3. Augmentez jusqu&#39;à **10 %**, puis **25 %** et enfin **50 %**
4. Atteindre **100 %** une fois la confiance établie

À chaque étape, une seule action peut suspendre le déploiement ou désactiver entièrement la fonctionnalité en cas de problème.

## Voir également {#see-also}

* [Indicateurs de fonctionnalité pour activer et désactiver des fonctionnalités](feature-flags-to-enable-disable-features.md)
* [Gestion des versions](release-management.md)
