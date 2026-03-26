---
title: Utilisation des données d’organisation d’entreprise dans les règles d’audience
description: Découvrez comment utiliser les identifiants d’organisation d’entreprise en tant que critères d’audience dans les déploiements d’Adobe Experience pour cibler des organisations clientes spécifiques.
exl-id: 74f97ec7-a809-41bf-a41d-bb57f033040f
source-git-commit: 4a3133f014a9bb9d6ed26eb9d9f763db79ce63b3
workflow-type: tm+mt
source-wordcount: '233'
ht-degree: 1%

---

# Utilisation des données d’organisation d’entreprise dans les règles d’audience {#enterprise-org-data}

Les déploiements d’expérience prennent en charge le ciblage des utilisateurs en fonction de leur identifiant d’organisation (org). Vous pouvez ainsi déployer des fonctionnalités vers des organisations clientes spécifiques avant de les rendre largement disponibles.

## Ajout d’une organisation dans une règle d’audience {#adding-org-rule}

Le ciblage d’organisation d’entreprise est disponible dans l’onglet **Audience** sous **Règles d’audience > Profil > Entreprise**.

Deux types d’organisation sont pris en charge :

### Organisations DME {#dme-orgs}

Les organisations DME sont identifiées par leur ID d’organisation. Lors de la création de la règle, saisissez uniquement l’ID d’organisation - n’incluez pas de source d’authentification.

### Organisations DMA {#dma-orgs}

Les organisations DMA utilisent des ID d’organisation au format `XXXXXXXXXXXXXXXXXXXXXXXX@ADOBEORG`. Lors de la saisie d’un ID d’organisation DMA :

* Utilisez l’ID d’organisation complet, y compris le suffixe `@ADOBEORG`.
* Saisissez `ADOBEORG` en majuscules.

**Exemple :** `57F22B5D5A5F83AE0A495E6E@ADOBEORG`

## Remarques importantes {#important-notes}

* Le ciblage basé sur l’organisation est évalué par rapport à l’organisation associée à la session authentifiée de l’utilisateur. Assurez-vous que l’utilisateur est connecté à la bonne organisation lors du test.
* Si une organisation que vous prévoyez de trouver n’apparaît pas dans les critères d’audience ou si des fonctionnalités ne sont pas renvoyées comme prévu pour une organisation spécifique, contactez l’assistance Déploiements d’expérience.
* Les environnements d’évaluation et de production peuvent différer selon les organisations disponibles. Testez vos règles d’audience dans l’environnement intermédiaire avant de passer en production.

## Voir également {#see-also}

* [Audience dans les indicateurs de fonctionnalité et les groupes de fonctionnalités](audience-in-feature-flags-and-feature-groups.md)
* [Règles d’audience complexes](complex-rules.md)
