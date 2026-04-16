---
title: Analytics
description: Découvrez comment activer et utiliser le tableau de bord d’analyse intégré dans Indicateurs pour suivre les performances des indicateurs de fonctionnalité et mesurer l’impact du déploiement.
hide: true
exl-id: edddca99-f263-461b-a16f-b46ee7c15f6c
source-git-commit: b3e13a42c19eb7b8b7d5d402bf9a56f89f573044
workflow-type: tm+mt
source-wordcount: '311'
ht-degree: 1%

---

# Analytics {#analytics}

Flags fournit des analyses intégrées pour les indicateurs de fonctionnalité, les groupes de fonctionnalités, les groupes de fonctionnalités inter-équipes et les versions. Utilisez le tableau de bord Analytics pour comprendre le nombre d’utilisateurs participant à votre déploiement et la comparaison entre la variante et les populations témoins. Vous pouvez également exporter des données Indicateurs vers votre environnement de création de rapports préféré à des fins d’analyse avec vos autres données Adobe.

## Activer Analytics {#enable}

Analytics doit être activé à deux niveaux :

1. **Niveau de l’application** — Contactez le support des indicateurs pour activer les analyses pour votre application.
2. **Niveau d’indicateur de fonctionnalité** — Une fois que les analyses sont activées pour votre application, cochez la case **Activer les analyses** dans l’onglet **Détails de base** de chaque indicateur de fonctionnalité que vous souhaitez suivre.

>[!NOTE]
>
>Par défaut, Analytics peut être activé pour un maximum de 20 indicateurs de fonctionnalité par application. Contactez l’assistance clientèle si vous devez augmenter cette limite.

## Affichage du tableau de bord d’analyse {#dashboard}

Une fois qu’Analytics est activé, tous les indicateurs de fonctionnalité, groupes de fonctionnalités et versions de votre application commencent à suivre les données. Accédez au tableau de bord en sélectionnant **Résultats** sur l&#39;indicateur de fonctionnalité, le groupe de fonctionnalités ou la version que vous souhaitez analyser.

Le tableau de bord affiche :

* **Participants** — Nombre total d’utilisateurs qualifiés pour la fonctionnalité (variante + population témoin combinées)
* **Population témoin** — Nombre d&#39;utilisateurs affectés à la population témoin (utilisateurs ayant bénéficié de l&#39;expérience par défaut)
* **Graphique au niveau du jour** — Graphiques en courbes quotidiens montrant l’inscription dans la variante et la population témoin au fil du temps ; les marqueurs indiquent le moment où la configuration des indicateurs de fonctionnalité a été mise à jour
* **Analyse au niveau des variantes** — Nombre cumulé d’utilisateurs inscrits dans la population témoin et chaque variante

Pour les groupes de fonctionnalités et les versions, sélectionnez le menu déroulant **Résultats** pour sélectionner une application et afficher les analyses pour cette application. Analytics n’est disponible que pour les applications qui l’ont activé.

## Voir également {#see-also}

* [Créer votre premier indicateur de fonctionnalité](create-your-first-feature-flag.md)
* [Test A/B avec indicateurs de fonctionnalité](a-b-testing.md)
* [Créer un groupe de fonctionnalités](create-a-feature-group.md)

<!-- -->
