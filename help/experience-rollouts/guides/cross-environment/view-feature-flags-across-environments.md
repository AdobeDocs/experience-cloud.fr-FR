---
title: Affichage des indicateurs de fonctionnalité dans les environnements
description: Découvrez comment afficher le statut des indicateurs de fonctionnalité dans tous les environnements liés pour une application dans les déploiements d’Adobe Experience.
source-git-commit: 5c99061a7f2aaaad98190166ea6fd79b7eb26dec
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 3%

---


# Affichage des indicateurs de fonctionnalité dans les environnements {#view-flags-across-environments}

Une fois que vous avez lié vos instances d’application entre les environnements, Déploiements d’expérience affiche le statut de chaque indicateur de fonctionnalité dans tous les environnements liés directement dans la page de liste des indicateurs de fonctionnalité. Vous disposez ainsi d’une vue unique pour comparer les états des indicateurs (par exemple, si un indicateur est ACTIVÉ dans l’environnement intermédiaire et DÉSACTIVÉ dans l’environnement de production) sans changer d’environnement.

## Conditions préalables {#prerequisites}

Vos instances d’application doivent être liées entre les environnements avant que le statut inter-environnements ne soit visible. Voir [Associer des environnements à une application](associate-environments.md) pour obtenir des instructions de configuration.

## Fonctionnement {#how-it-works}

Lorsque vous accédez à **Fonctionnalités et versions > Indicateurs de fonctionnalité** et sélectionnez une application qui comporte des instances liées, la page de liste affiche des colonnes supplémentaires pour chaque environnement lié. Chaque colonne affiche l&#39;état actuel de l&#39;indicateur de fonctionnalité dans cet environnement.

Les indicateurs de fonctionnalité sont associés à tous les environnements par leur **clé**, et non par leur nom. Autrement dit :

* Un indicateur peut avoir un nom d’affichage différent dans chaque environnement, à condition que la clé soit la même.
* Le nom affiché dans chaque colonne d’environnement est celui utilisé dans cet environnement.

## Cas d’utilisation {#use-case}

Un workflow type consiste à développer et à tester un indicateur de fonctionnalité dans un environnement inférieur (par exemple, l’environnement d’évaluation), puis à vérifier son statut avant de promouvoir la configuration en environnement de production. La visibilité inter-environnements vous permet de confirmer que l’indicateur est correctement configuré dans l’environnement intermédiaire avant de l’importer en production, le tout à partir de la console de production.

## Voir également {#see-also}

* [Association d’environnements à une application](associate-environments.md)
* [Importer les indicateurs de fonctionnalité](import-feature-flags.md)
* [Concept inter-environnements](cross-environment-concept.md)
