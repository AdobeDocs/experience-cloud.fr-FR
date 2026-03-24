---
title: Notes de mise à jour de Node.js SDK
description: Notes de mise à jour de SDK de Node.js Déploiements d’expérience , y compris un journal des modifications apportées aux nouvelles fonctionnalités, aux améliorations et aux correctifs de bugs sur toutes les versions publiées.
source-git-commit: 9bfe0e55e89c1d7fbd77cde63831a6a186820e24
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 1%

---


# Notes de mise à jour de Node.js SDK {#nodejs-sdk-release-notes}

Cette page répertorie l’historique des versions du SDK Node.js de déploiements d’expérience. Pour la configuration de l’intégration, voir [Guide d’intégration de Node.js SDK](nodejs-sdk-integration-guide.md).

## Version 1.0.10 {#v1-0-10}

**Correctifs de bugs et améliorations des socket**

* Correction d’une exception de `ESOCKETTIMEDOUT` déclenchée lors des actualisations planifiées du cache. Suppression du paramètre `maxSockets` de `featureRequestHttpParams` et `ingestAnalyticsHttpParams` dans `createInstance()`.
* Correction d’un bug en raison duquel les clients pouvant être mis en cache étaient incorrectement marqués comme ne pouvant pas être mis en cache après les réponses HTTP 304 (Not Modified).
* Supprimé `isReleaseBitEnabled()` : cette méthode n&#39;est plus prise en charge.
* Amélioration de la sortie de journalisation pour de meilleurs diagnostics.
* Les dossiers de test et de couverture ne sont plus inclus dans le package npm publié.

## Version 1.0.5 {#v1-0-5}

**Amélioration de la stabilité**

Correctifs généraux pour la gestion de l’actualisation du cache et les cas Edge d’initialisation de SDK.

## Version 1.0.3 {#v1-0-3}

**Version stable initiale**

Première version de production du SDK Node.js prenant en charge l’authentification, l’anonymat et la récupération de l’indicateur de fonctionnalité du déploiement complet par défaut.

## Voir également {#see-also}

* [Guide d’intégration de Node.js SDK](nodejs-sdk-integration-guide.md)
* [Notes de mise à jour de Java SDK](../../sdk-releases/java/java-sdk-release-notes.md)
* [SDK](../../integrate/sdks.md)
