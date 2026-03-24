---
title: Notes de mise à jour de Java SDK
description: Notes de mise à jour relatives aux déploiements d’expérience de Java SDK, y compris un journal des modifications apportées aux nouvelles fonctionnalités, aux améliorations et aux correctifs de bogues dans toutes les versions publiées.
source-git-commit: 9bfe0e55e89c1d7fbd77cde63831a6a186820e24
workflow-type: tm+mt
source-wordcount: '309'
ht-degree: 2%

---


# Notes de mise à jour de Java SDK {#java-sdk-release-notes}

Cette page répertorie l’historique des versions de SDK Java Déploiements d’expérience. Pour la configuration de l’intégration, voir [Guide d’intégration de Java SDK](java-sdk-integration-guide.md).

## Version 4.0.6 {#v4-0-6}

**Données des témoins dans les réponses**

Vous pouvez désormais récupérer les données de variante et de population témoin dans la réponse SDK, correspondant au comportement des API des fonctionnalités REST. Pour ce faire, ajoutez `.includeControlGroup()` à votre créateur de `FloodgateConfiguration`.

## Version 4.0.5 {#v4-0-5}

**Amélioration de la stabilité et des performances**

Améliorations internes mineures de la fiabilité de l’actualisation du cache et de la gestion des connexions.

## Version 4.0.4 {#v4-0-4}

**Améliorations de la politique de reprise**

Amélioration du comportement par défaut des reprises en cas d’erreurs de service transitoires.

## Version 4.0.3 {#v4-0-3}

**Correctifs de bugs**

Correctifs généraux de stabilité pour les cas de périphérie dans l’initialisation asynchrone.

## Version 4.0.1 (Beta) {#v4-0-1-beta}

**Version Beta du SDK 4.x**

Ajout de la prise en charge des clients DX, de la configuration des zones géographiques DX et de la prise en charge d’AEP (sandbox).

## Version 3.1.0 {#v3-1-0}

**Prise en charge du streaming pour les clients DX**

Ajout d’une fonctionnalité de streaming basée sur SSE pour informer les clients SDK des mises à jour des indicateurs en temps quasi réel.

## Version 3.0.x {#v3-0-x}

**Ajout de l’exigence Java 11**

À partir de la version 3.0.0, le SDK nécessite JDK 11 ou une version ultérieure. Les versions majeures antérieures prennent en charge JDK 8+.

Ajout de la prise en charge de l’audience par référence pour les clients DX, ce qui permet aux définitions d’audience réutilisables d’être référencées par identifiant dans les entités de fonctionnalité.

## Version 2.x {#v2-x}

**Prise en charge des clients non pouvant être mis en cache (à partir de la version 0.8)**

Les clients qui ne peuvent pas être mis en cache peuvent appeler `getFeature()` Live au lieu de lire à partir du cache de SDK. Le SDK poursuit l’interrogation en arrière-plan et passe au service basé sur la mise en cache lorsque le client peut être mis en cache.

Les autres améliorations apportées à la version 2.x comprennent de nouvelles options de créateur (`alwaysCache()`, `neverCache()`, prise en charge de clients HTTP et d’exécuteurs personnalisés), le filtrage des fonctionnalités et des clés de version, ainsi que la récupération des utilisateurs empruntés.

## Version 1.x {#v1-x}

Série de versions initiales. JDK 8+ pris en charge, intégration de dépendance Maven et récupération de base des indicateurs de fonctionnalité authentifiés et anonymes.

## Voir également {#see-also}

* [Guide d’intégration de Java SDK](java-sdk-integration-guide.md)
* [Notes de mise à jour de Node.js SDK](../../sdk-releases/nodejs/nodejs-sdk-release-notes.md)
* [SDK](../../integrate/sdks.md)
