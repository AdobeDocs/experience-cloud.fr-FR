---
title: Présentation des environnements
description: Découvrez les environnements d’évaluation et de production dans Déploiements d’Adobe Experience et quand les utiliser.
source-git-commit: 9bfe0e55e89c1d7fbd77cde63831a6a186820e24
workflow-type: tm+mt
source-wordcount: '204'
ht-degree: 4%

---


# Présentation des environnements {#environments}

Les déploiements d’expérience fournissent des environnements distincts afin que vous puissiez valider vos indicateurs de fonctionnalité avant de promouvoir les modifications auprès de vos utilisateurs actifs.

## Environnements disponibles {#available-environments}

| Environnement | Rôle |
|---|---|
| **Phase** | Tests et validation. Utilisez cet environnement pour configurer et tester les indicateurs de fonctionnalité avant de les activer en production. |
| **Production** | Déploiements en direct. Les indicateurs de fonctionnalité configurés ici sont évalués par rapport à votre base d’utilisateurs réelle. |

>[!IMPORTANT]
>
>Les modifications apportées à l’étape d’évaluation ne sont pas automatiquement transférées en production. Les indicateurs de fonctionnalité et les règles d’audience doivent être configurés séparément dans chaque environnement.

## Sélection d’un environnement {#selecting}

Après vous être connecté à la console Déploiements d’expérience , sélectionnez l’environnement à partir du sélecteur d’environnement en haut de l’interface. Assurez-vous de travailler dans l&#39;environnement approprié avant de créer ou de modifier des indicateurs de fonctionnalité.

## Bonnes pratiques {#best-practices}

Suivez ces recommandations pour éviter les erreurs de configuration et protéger votre audience de production :

* Créez et testez toujours d’abord les indicateurs de fonctionnalité dans **Stage**.
* Validez les règles d’audience, les déploiements en pourcentage et la logique de ciblage dans l’environnement intermédiaire avant de répliquer en production.
* Utilisez le [workflow interenvironnement](../cross-environment/cross-environment-concept.md) pour afficher et gérer le statut des indicateurs dans les environnements.

## Voir également {#see-also}

* [Connexion à la console](log-in-to-the-console.md)
* [Association d’environnements à une application](../cross-environment/associate-environments.md)
* [Affichage des indicateurs de fonctionnalité dans les environnements](../cross-environment/view-feature-flags-across-environments.md)
