---
title: Importer les indicateurs de fonctionnalité
description: Découvrez comment importer des indicateurs de fonctionnalité d’un environnement inférieur dans un environnement supérieur dans les déploiements d’Adobe Experience pour éviter de recréer manuellement des configurations d’indicateur.
source-git-commit: 5c99061a7f2aaaad98190166ea6fd79b7eb26dec
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 1%

---


# Importer les indicateurs de fonctionnalité {#import-feature-flags}

Les déploiements d’expérience vous permettent d’importer des indicateurs de fonctionnalité d’un environnement inférieur (par exemple, l’environnement intermédiaire) dans un environnement supérieur (par exemple, la production). Cela évite d’avoir à recréer manuellement les configurations de drapeau et réduit le risque de dérive de la configuration entre les environnements.

## Conditions préalables {#prerequisites}

Pour utiliser le workflow d’importation, vos instances d’application doivent être liées entre les environnements. Voir [Associer des environnements à une application](associate-environments.md).

## Étape 1 : accéder à l’environnement et à l’application de destination {#step-1}

Connectez-vous à la console pour l’environnement **destination**, l’environnement dans lequel vous souhaitez importer des indicateurs *dans*. Sélectionnez l’application dans laquelle vous souhaitez importer des indicateurs dans la liste déroulante Application de la page Indicateurs de fonctionnalités.

>[!IMPORTANT]
>
>L’environnement actuel et l’application sélectionnée doivent être la **destination** et non la source. Par exemple, pour importer un indicateur de l’environnement intermédiaire vers l’environnement de production, connectez-vous à la console de production et sélectionnez votre application de production.

## Étape 2 : ouvrir la boîte de dialogue d’importation {#step-2}

Sélectionnez **Importer les indicateurs de fonctionnalité**. Une boîte de dialogue s’ouvre. Elle présente l’environnement source et l’application, pré-renseignée en fonction des environnements liés configurés pour votre application. Si nécessaire, vous pouvez modifier l’environnement source et l’application à partir des listes déroulantes de la boîte de dialogue.

## Étape 3 : sélection des indicateurs de fonctionnalité à importer {#step-3}

Dans la liste des indicateurs de fonctionnalité de l’environnement source, sélectionnez les indicateurs à importer. Vous pouvez sélectionner un, plusieurs ou tous les indicateurs à la fois.

## Étape 4 : gérer les indicateurs existants (si nécessaire) {#step-4}

Si un indicateur de fonctionnalité avec la même clé existe déjà dans l’environnement de destination, Déploiements d’expérience vous demandera de confirmer s’il faut le remplacer. Passez en revue la configuration existante de l’indicateur avant de confirmer, car le remplacement remplacera les paramètres de l’indicateur de destination par ceux de la source.

## Remarques importantes {#important-notes}

Tenez compte des points suivants lors de l’importation d’indicateurs de fonctionnalité :

* Les indicateurs importés sont toujours définis à l’état **OFF** dans l’environnement de destination, quel que soit leur état dans l’environnement source. Vous devez les activer manuellement après l’importation.
* Si l’activation d’un indicateur a été planifiée à une date et une heure ultérieures dans l’environnement source, cette planification n’est **pas** reportée. Si nécessaire, vous devez définir un nouveau planning dans l’environnement de destination.

## Voir également {#see-also}

* [Association d’environnements à une application](associate-environments.md)
* [Affichage des indicateurs de fonctionnalité dans les environnements](view-feature-flags-across-environments.md)
* [Concept inter-environnements](cross-environment-concept.md)
