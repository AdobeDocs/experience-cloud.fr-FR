---
title: Workflow de publication complet
description: Découvrez le workflow de bout en bout pour gérer une version coordonnée dans les déploiements d’Adobe Experience, de la définition des indicateurs de fonctionnalité à la mise en ligne.
hide: true
exl-id: 086e3192-c22b-4de8-a15a-89edb09ac230
source-git-commit: 12032cbed45e694a3f25f16afe80308b3eb82924
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 1%

---

# Workflow de publication complet {#release-workflow}

Cette page décrit la séquence complète des activités impliquées dans une version coordonnée gérée par un gestionnaire de versions.

## &#x200B;1. Définition des indicateurs de fonctionnalité par application {#define-flags}

Chaque équipe produit affecte un **Propriétaire de version de produit** qui se connecte à la console Déploiements d’expérience et crée des indicateurs de fonctionnalité pour les applications dont il est propriétaire. L’équipe produit implémente ensuite la logique conditionnelle dans son code, en plaçant les fonctionnalités derrière ces indicateurs.

## &#x200B;2. Création de la version {#create-release}

La création d’une nouvelle version nécessite une demande d’assistance. Celle-ci n’est pas entièrement en libre-service. Contactez l’assistance des déploiements d’expérience pour créer la version. Indiquez le nom de la version, l’équipe propriétaire, l’environnement cible, l’objectif, les applications participantes et la durée prévue.

Une fois la version confirmée, le gestionnaire de versions ouvre la console et termine la configuration de la version.

## &#x200B;3. Ajouter des indicateurs de fonctionnalité à la version {#add-flags}

Pour chaque application ajoutée à la version, le propriétaire de la version de produit de l’application se connecte et ajoute les indicateurs de fonctionnalité appropriés à la version. Ces indicateurs représentent les fonctionnalités qui seront mises en ligne avec la version.

## &#x200B;4. Configuration de l’audience {#configure-audience}

Le Gestionnaire de versions sélectionne l’audience de la version, par exemple, 1 % des utilisateurs d’un pays spécifique, tous les utilisateurs disposant d’un domaine d’e-mail spécifique ou une liste d’ID d’utilisateur spécifiques. Une fois configurée, le gestionnaire de versions enregistre et publie la version, qui la met en ligne pour l’audience spécifiée.

## &#x200B;5. Développer et gérer le déploiement {#expand}

Une fois la version mise en ligne, le gestionnaire de versions peut ajuster les règles d’audience pour étendre progressivement le déploiement, surveiller les problèmes et utiliser les commandes d’état de version pour gérer le cycle de vie. Voir [États de publication](release-states.md) pour plus d’informations.

## Points clés {#key-points}

* Toutes les applications participantes déploient leur code en production indépendamment derrière les indicateurs de fonctionnalité, aucun délai de déploiement coordonné n’est nécessaire.
* Cette version est le point de contrôle unique qui active simultanément tous les indicateurs parmi les équipes.
* Le ciblage de l’audience pour les versions est basé sur les attributs de jeton d’authentification (pays, e-mail, ID utilisateur, pourcentage).

## Voir également {#see-also}

* [Demander une version](request-a-release.md)
* [Mise à jour des règles d’audience de version](update-release-audience-rules.md)
* [États de la version](release-states.md)

<!-- -->
