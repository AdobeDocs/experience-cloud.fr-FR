---
title: Résolution des problèmes
description: Utilisez le pupitre des déploiements d’expérience pour diagnostiquer les problèmes d’évaluation des indicateurs de fonctionnalité pour des utilisateurs et utilisatrices spécifiques, y compris la vérification des fonctionnalités activées, désactivées ou non appariées pour une identité d’utilisateur donnée.
exl-id: d64e9573-8e18-46a1-a75a-5ae5bfc7c82d
source-git-commit: 4a3133f014a9bb9d6ed26eb9d9f763db79ce63b3
workflow-type: tm+mt
source-wordcount: '650'
ht-degree: 1%

---

# Résolution des problèmes {#troubleshooting}

Le service Déploiements d’expérience comprend un outil de diagnostic intégré appelé **Features Workbench** qui vous aide à comprendre exactement quelles fonctionnalités sont proposées à un utilisateur spécifique et pourquoi. Utilisez-le pour examiner les rapports de comportement inattendu des fonctionnalités sans avoir à reproduire les problèmes de code.

## Accéder au Workbench des fonctionnalités {#access-workbench}

Pour ouvrir le pupitre des fonctionnalités, procédez comme suit :

1. Connectez-vous à la console Déploiements d’expérience .
2. Accédez à **Workbench > Utilisateurs finaux** à partir du menu supérieur.
3. Sélectionnez l’onglet **Fonctions**.

## Saisir une identité d’utilisateur {#input-identity}

Pour rechercher des évaluations d&#39;indicateur de fonctionnalité pour un utilisateur spécifique, saisissez les informations suivantes dans le formulaire Workbench :

* **Type d&#39;identifiant** — Sélectionnez le type d&#39;identifiant utilisé. Les types pris en charge sont les suivants : e-mail, GUID et identifiant visiteur. Vous pouvez également saisir directement un **indicateur de version** pour rechercher les versions activées pour un utilisateur en fonction de leur valeur d’indicateur.
* **Valeur de l&#39;ID** — Saisissez l&#39;identifiant de l&#39;utilisateur. Si vous sélectionnez e-mail comme type d’ID, notez que plusieurs GUID peuvent être associés à la même adresse e-mail. Une liste déroulante de GUID est fournie afin que vous puissiez basculer entre les GUID associés.
* **Type de source d’authentification** — Sélectionnez cette option si elle s’applique à votre intégration.
* **Variables contextuelles** — Fournissez éventuellement des paires clé-valeur contextuelles qui affectent l&#39;évaluation des règles d&#39;audience (par exemple, le pays, le type d&#39;appareil).
* **Équipe et application** — Sélectionnez l&#39;équipe et l&#39;application pour lesquelles vous voulez récupérer les indicateurs de fonctionnalité. Votre équipe actuelle et une de ses applications sont présélectionnées par défaut.

Après avoir rempli le formulaire, sélectionnez **Récupérer les fonctionnalités**.

## Interprétation des résultats {#interpret-results}

Les résultats dépendent du type d’identifiant que vous avez saisi.

### Recherche d’e-mail ou de GUID {#email-guid-lookup}

Lorsque vous recherchez un utilisateur par e-mail ou GUID, deux sections apparaissent dans les résultats :

**Indicateurs de version**

Cette section affiche trois listes pour l&#39;équipe et l&#39;application sélectionnées :

* **Activé** — Versions actuellement actives pour cet utilisateur.
* **Désactivé** — Versions existantes mais non activées pour cet utilisateur.
* **Inutilisé** — Libérer les bits qui n&#39;ont pas de libération attachée.

Les versions associées à l&#39;équipe et à l&#39;application actuellement sélectionnées apparaissent en haut de chaque liste.

**Indicateurs et groupes de fonctionnalités**

Cette section répertorie tous les indicateurs de fonctionnalité de l&#39;équipe et de l&#39;application sélectionnées qui sont actuellement activés pour l&#39;utilisateur. Chaque entrée affiche :

* Clé et nom de l’indicateur de fonctionnalité
* Groupe de fonctionnalités (si l&#39;indicateur appartient à l&#39;un d&#39;eux)
* Variante (si le test A/B est configuré)
* Si l’indicateur est lié à l’audience

Vous pouvez également sélectionner **Afficher la requête/réponse** pour examiner la requête et la réponse exactes de l’API qui ont produit les résultats.

### E-mail non autonome ou ID non GUID {#non-self-lookup}

Lorsque l’e-mail saisi n’est pas le vôtre ou lorsqu’un type d’ID non GUID est utilisé, seule la section **Indicateurs et groupes de fonctionnalités** s’affiche.

### Recherche d’indicateur de version {#release-flag-lookup}

Lorsque vous saisissez un **indicateur de version** comme type d’identifiant, seule la section **Indicateurs de version** s’affiche, répertoriant les versions activées et désactivées pour l’utilisateur associé à cet indicateur.

## Problèmes courants {#common-issues}

Le tableau suivant décrit les problèmes courants et la manière de les examiner à l’aide de Workbench.

| Symptôme | Éléments à vérifier |
|---|---|
| L’utilisateur ne reçoit pas l’indicateur de fonctionnalité qu’il devrait | Vérifiez la sélection de l&#39;équipe et de l&#39;application. Vérifiez que l’identifiant de l’utilisateur correspond au type de règle d’audience (e-mail, GUID, etc.). Vérifiez que la fonctionnalité est à l’état **Publication** ou **Déploiement complet**. |
| La fonctionnalité est activée de manière inattendue pour tous les utilisateurs et utilisatrices | Vérifiez que la fonction n’applique aucune règle d’audience ou que le pourcentage est défini sur 100 %. Vérifiez si la fonctionnalité est à l’état **Déploiement complet**. |
| La règle d’audience ne correspond pas. | Utilisez le Workbench avec des variables contextuelles pour confirmer que les valeurs transmises au moment de l’exécution correspondent à ce qui est configuré dans la règle d’audience. |
| L’état de l’indicateur de fonctionnalité est correct, mais l’utilisateur voit toujours l’ancien comportement | Vérifiez la TTL configurée pour l’application. Le SDK met en cache les données de fonctionnalité et s’actualise uniquement à l’intervalle d’interrogation configuré. |

## Voir également {#see-also}

* [Obtenir de l’aide](get-support.md)
* [Contacter l’assistance](contact-support.md)
