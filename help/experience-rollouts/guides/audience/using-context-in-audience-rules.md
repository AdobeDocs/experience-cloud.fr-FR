---
title: Utilisation du contexte dans les règles d’audience
description: Découvrez comment utiliser les variables contextuelles dans les règles d’audience pour les indicateurs de fonctionnalité et les groupes de fonctionnalités dans les déploiements d’Adobe Experience.
source-git-commit: 3f3f7145b3c58dc721cbeb850e9e8571e3255bb1
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---


# Utilisation du contexte dans les règles d’audience {#context-in-audience-rules}

Les variables contextuelles sont des valeurs fournies par l’application cliente au moment de l’exécution. Ils vous permettent de cibler les utilisateurs en fonction d’informations dynamiques au niveau de la session, telles que la langue active de l’utilisateur, le type d’appareil ou l’état de l’application, critères qui ne font pas partie du profil persistant de l’utilisateur.

Les variables contextuelles sont pertinentes pour les clients web, de bureau et mobiles.

## Fonctionnement des variables contextuelles {#how-context-works}

Votre application transmet des variables contextuelles aux déploiements d’expérience lors de l’évaluation d’un indicateur de fonctionnalité. Vous définissez des règles dans la console pour vérifier ces valeurs, et la plateforme les utilise au moment de l’évaluation pour déterminer si l’utilisateur est admissible.

Si vous définissez des conditions dans les sections **Profil** et **Contexte** des règles d’audience, toutes les conditions de profil sont combinées à toutes les conditions de contexte à l’aide de la logique ET.

## Types de variables contextuelles {#variable-types}

### Type prédéfini (liste) {#predefined-type}

Variable contextuelle avec un ensemble fixe de valeurs autorisées, comme une liste de langues ou de pays.

Opérateurs disponibles : **Est**, **N’est pas égal à**, **Existe**, **Dans**

### Type entier {#integer-type}

Variable contextuelle contenant une valeur numérique.

Opérateurs disponibles : **supérieur à**, **supérieur ou égal à**, **est**, **inférieur à**, **inférieur ou égal à**

### Type de chaîne {#string-type}

Variable contextuelle qui contient une valeur de texte de forme libre.

Opérateurs disponibles : **Est**, **Est différent de**

## Ajouter une variable contextuelle {#adding-context-variable}

Pour ajouter une variable contextuelle à une règle d’audience :

1. Ouvrez l&#39;indicateur de fonctionnalité ou le groupe de fonctionnalités dans la console.
2. Accédez à l’onglet **Audience**.
3. Sous **Contexte**, ajoutez une nouvelle condition.
4. Sélectionnez la variable contextuelle, l’opérateur et la valeur.

Si la variable de contexte dont vous avez besoin n’apparaît pas dans la liste, vous pouvez en créer une en libre-service à partir de la section de gestion des variables de contexte de la console.

>[!NOTE]
>
>Lorsque des variables contextuelles sont incluses dans les critères d’audience, le **Calculateur d’audience** ne renvoie pas de nombre estimé, car les valeurs contextuelles sont déterminées au moment de l’exécution et ne peuvent pas être prédites à l’avance.

## Voir également {#see-also}

* [Audience dans les indicateurs de fonctionnalité et les groupes de fonctionnalités](audience-in-feature-flags-and-feature-groups.md)
* [Ajouter des règles de pourcentage dans les critères d’audience](adding-percentage-rules.md)
* [Règle d’audience avec variable de contexte IP client](clientip-rule.md)
