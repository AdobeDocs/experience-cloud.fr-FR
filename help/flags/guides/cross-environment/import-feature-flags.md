---
title: Importer les indicateurs de fonctionnalité
description: Découvrez comment importer des indicateurs de fonctionnalité d’un sandbox dans un autre dans Indicateurs pour éviter de recréer manuellement des configurations d’indicateur.
hide: true
exl-id: 37c84d75-a565-4202-8c99-f630e05b6bb6
source-git-commit: b3e13a42c19eb7b8b7d5d402bf9a56f89f573044
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 1%

---

# Importer les indicateurs de fonctionnalité {#import-feature-flags}

Indicateurs vous permet d’importer des indicateurs de fonctionnalité d’un sandbox (par exemple, le sandbox 1) dans un autre sandbox (par exemple, le sandbox 2). Cela évite d’avoir à recréer manuellement les configurations d’indicateurs et réduit le risque de dérive de la configuration entre les sandbox.

## Étape 1 : accéder au sandbox de destination et à l’application {#step-1}

Connectez-vous à la console pour le sandbox **destination**, c’est-à-dire le sandbox dans lequel vous souhaitez importer des indicateurs *dans*. Sélectionnez l’application dans laquelle vous souhaitez importer des indicateurs dans la liste déroulante Application de la page Indicateurs de fonctionnalités.

>[!IMPORTANT]
>
>Le sandbox actuel et l’application sélectionnée doivent être la **destination**, et non la source. Par exemple, pour importer un indicateur de la sandbox 1 dans la sandbox 2, connectez-vous à la console sandbox 2 et sélectionnez votre application sandbox 2.

## Étape 2 : ouvrir la boîte de dialogue d’importation {#step-2}

Sélectionnez **Importer les indicateurs de fonctionnalité**. Une boîte de dialogue s’ouvre, affichant le sandbox source et l’application, pré-renseignée en fonction des applications disponibles. Si nécessaire, vous pouvez modifier le sandbox source et l’application dans les listes déroulantes de la boîte de dialogue.

## Étape 3 : sélection des indicateurs de fonctionnalité à importer {#step-3}

Dans la liste des indicateurs de fonctionnalité du sandbox source, sélectionnez les indicateurs à importer. Vous pouvez sélectionner un, plusieurs ou tous les indicateurs à la fois.

## Étape 4 : sélection de l’état des indicateurs de fonctionnalité à importer {#step-4}

Utilisez la liste déroulante pour choisir comment les indicateurs de fonctionnalité doivent être importés : **Activé**, **Désactivé** ou dans leur **État actuel**. Par défaut, les indicateurs de fonctionnalité sont importés à l’état **Désactivé**.

## Remarques importantes {#important-notes}

Tenez compte des points suivants lors de l’importation d’indicateurs de fonctionnalité :

* Si un indicateur de fonctionnalité avec la même clé existe déjà dans le sandbox de destination, il ne sera pas importé.

## Voir également {#see-also}

* [Fonctionnalités et groupes de fonctionnalités](../feature-flags/features-feature-groups-releases.md)
* [Créer votre premier indicateur de fonctionnalité](../feature-flags/create-your-first-feature-flag.md)

<!-- -->
