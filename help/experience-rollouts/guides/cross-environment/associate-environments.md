---
title: Association d’environnements à une application
description: Découvrez comment lier vos instances d’application entre les environnements dans les déploiements d’Adobe Experience afin de gérer les indicateurs de fonctionnalité de manière cohérente, du développement à la production.
source-git-commit: 5c99061a7f2aaaad98190166ea6fd79b7eb26dec
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 1%

---


# Association d’environnements à une application {#associate-environments}

La liaison de vos instances d’application à travers les environnements permet une visibilité inter-environnements et des workflows d’importation. Pour configurer ce paramètre, vous devez disposer du rôle **Admin**. Voir [&#x200B; Rôles utilisateur &#x200B;](../teams/user-roles.md) si vous devez vérifier votre rôle.

Pour en savoir plus sur son utilité, consultez la section [Concept interenvironnemental](cross-environment-concept.md).

## Étape 1 : ouvrir les paramètres de l&#39;application {#step-1}

1. Connectez-vous à la console Déploiements d’expérience .
2. Accédez à **Admin > Applications**.
3. Sélectionnez **Nouvelle application** pour intégrer une nouvelle application, ou sélectionnez une application existante pour la modifier.

## Étape 2 : configurer la section Environnements associés {#step-2}

Dans le formulaire de demande, faites défiler l’écran jusqu’à la section **Environnements associés**. Chaque ligne de cette section définit l’un des environnements de déploiement de votre application. Pour chaque environnement, configurez les champs suivants :

| Champ | Description |
|---|---|
| **Environnement** | Sélectionnez un identifiant d’environnement standard dans la liste : QA1, QA2, STG1, STG2, PROD1 ou PROD2. Cette option indique aux déploiements d’expérience si l’environnement est en production ou hors production et détermine le codage de couleur utilisé dans la console. |
| **Libellé de l’environnement** | Nom personnalisé de cet environnement, tel que votre équipe l’appelle, par exemple `Dev`, `Staging` ou `Production`. Il s’agit d’une structure libre qui n’a pas besoin de correspondre à l’identifiant standard. |
| **Environnement de déploiements d’expérience** | Environnement de la plateforme (d’évaluation ou de production) dans lequel cette instance d’application est hébergée. Prérempli en fonction de la console dans laquelle vous vous trouvez actuellement. |
| **ID de l’application** | Identifiant client de l’instance d’application dans cet environnement. Automatiquement renseigné lorsque vous sélectionnez une application dans la liste déroulante. |

## Étape 3 : liaison des instances d’application entre les environnements {#step-3}

Pour lier des instances entre des environnements, procédez comme suit pour chaque environnement supplémentaire :

1. Créez l’instance d’application dans son environnement cible (par exemple, créez l’application d’assurance qualité dans la console d’évaluation).
2. Revenez à l’application que vous configurez et ajoutez une nouvelle ligne dans **Environnements associés**.
3. Dans la liste déroulante **ID de l&#39;application**, sélectionnez l&#39;instance d&#39;application que vous venez de créer. La balise et le libellé d’environnement sont renseignés automatiquement.
4. Sélectionnez **Mettre à jour** pour enregistrer.

Répétez ce processus pour chaque environnement à lier, par exemple en liant les instances d’assurance qualité, d’évaluation et de production d’une même application.

## Remarques importantes {#important-notes}

* Les environnements d’assurance qualité et d’évaluation peuvent être hébergés dans l’environnement de plateforme d’évaluation ou de production des déploiements d’expérience.
* Les environnements de production (PROD1, PROD2) ne peuvent être hébergés que dans l’environnement de production Déploiements d’expérience.
* Vous pouvez uniquement créer un lien vers un environnement inférieur à partir d’un environnement supérieur. Par exemple, à partir de la production, vous pouvez créer un lien vers une instance d’évaluation ou d’assurance qualité, mais l’inverse est en lecture seule.

## Voir également {#see-also}

* [Concept inter-environnements](cross-environment-concept.md)
* [Affichage des indicateurs de fonctionnalité dans les environnements](view-feature-flags-across-environments.md)
* [Importer les indicateurs de fonctionnalité](import-feature-flags.md)
