---
title: Règles d’audience complexes
description: Découvrez comment utiliser des ensembles de règles d’audience volumineux ou complexes dans les indicateurs, y compris les limites de valeurs en bloc et comment fractionner les règles sur plusieurs conditions.
hide: true
exl-id: 37e037b6-45eb-4261-b580-30d94d8e55da
source-git-commit: b3e13a42c19eb7b8b7d5d402bf9a56f89f573044
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 0%

---

# Règles d’audience complexes {#complex-rules}

## Limites de valeurs groupées {#bulk-value-limits}

Lors de l’ajout d’un grand nombre de valeurs à une règle d’audience unique (par exemple, une longue liste d’adresses e-mail), vous pouvez rencontrer une erreur indiquant que la règle a dépassé la taille maximale autorisée.

Chaque règle d’audience a une limite de taille par attribut. Pour les adresses e-mail, la limite dépend de la longueur totale des caractères des entrées plutôt que d’un nombre fixe. En règle générale, utilisez environ 100 à 115 adresses électroniques **par règle**.

Si vous devez cibler un nombre d’entrées supérieur à cette limite, divisez la liste en blocs plus petits et appliquez-les en tant que conditions distinctes connectées à l’adresse OU à l’aide d’une logique imbriquée.

## Utilisation d’une logique imbriquée pour les règles complexes {#nested-logic}

La logique imbriquée vous permet de combiner plusieurs conditions d’audience avec un contrôle ET/OU précis. Pour l’activer :

1. Ajoutez les conditions d’audience dont vous avez besoin.
2. Activez **Logique imbriquée** dans la section Règles d’audience .
3. Un numéro est attribué à chaque condition. Saisissez une expression logique qui fait référence à ces nombres, par exemple :
   * `1 and (2 or 3)`
   * `(1 and 2) or 3`
   * `(1 and 2) or (3 and 4)`

Il s’agit du même mécanisme que celui utilisé pour les règles de pourcentage en combinaison avec d’autres critères. Consultez [ Ajouter des règles de pourcentage dans les critères d’audience ](adding-percentage-rules.md) pour obtenir des exemples de travail.

## Voir également {#see-also}

* [Audience dans les indicateurs de fonctionnalité et les groupes de fonctionnalités](audience-in-feature-flags-and-feature-groups.md)
* [Ajouter des règles de pourcentage dans les critères d’audience](adding-percentage-rules.md)

<!-- -->
