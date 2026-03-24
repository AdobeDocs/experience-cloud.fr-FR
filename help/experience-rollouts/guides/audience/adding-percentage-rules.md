---
title: Ajouter des règles de pourcentage dans les critères d’audience
description: Découvrez comment ajouter des règles basées sur des pourcentages au sein des critères d’audience dans les déploiements d’Adobe Experience afin de cibler différents pourcentages de déploiement pour différents segments d’audience.
source-git-commit: ae420329b94b24fcd173734b414aecf1c5fc16ca
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---


# Ajouter des règles de pourcentage dans les critères d’audience {#adding-percentage-rules}

## Quand utiliser des règles de pourcentage dans l’onglet Audience {#when-to-use}

Le champ **déploiement en pourcentage** de l’onglet Détails de base applique un seul pourcentage à l’ensemble de votre audience. Par exemple, un déploiement de 50 % signifie que 50 % de tous les utilisateurs qui correspondent à vos critères d’audience recevront la fonctionnalité.

Cependant, certains scénarios de déploiement nécessitent des pourcentages différents pour différents groupes, par exemple :

* 100 % des utilisateurs britanniques et 50 % des utilisateurs américains
* Tous les utilisateurs d’une liste d’e-mails importée, plus 50 % des utilisateurs d’un pays spécifique

Dans ces cas, utilisez la règle **Pourcentage** dans la section de profil de l’onglet **Audience**, associée à une logique imbriquée.

>[!TIP]
>
>Si vous souhaitez appliquer un seul pourcentage à l’ensemble de votre audience, par exemple 10 % des utilisateurs aux (États-Unis et Royaume-Uni), utilisez plutôt le **déploiement en pourcentage** sur l’onglet Détails de base .

## Comment ajouter une règle de pourcentage {#how-to-add}

L’option **Pourcentage** est disponible en règle générale dans la section Profil de l’onglet Audience .

1. Accédez à l’onglet **Audience** de votre indicateur de fonctionnalité ou de votre groupe de fonctionnalités.
2. Sous **Profil**, ajoutez une règle **Pourcentage** et définissez la valeur souhaitée.
3. Ajoutez toutes les autres conditions d’audience dont vous avez besoin (par exemple, une règle Pays).

## Combinaison de règles de pourcentage avec une logique imbriquée {#nested-logic}

Pour appliquer différents pourcentages à différents segments, utilisez **logique imbriquée** pour combiner les conditions :

1. Activez **Logique imbriquée** dans la section Règles d’audience .
2. Chaque condition se voit attribuer automatiquement un numéro.
3. Saisissez une expression logique référençant ces nombres.

Utilisez l’une des expressions suivantes pour décrire la relation entre vos conditions :

* `1 and (2 or 3)` — condition 1 ET (condition 2 OU condition 3)
* `(1 and 2) or 3` — (condition 1 ET condition 2) OU condition 3
* `(1 and 2) or (3 and 4)` — deux groupes indépendants

## Exemples {#examples}

**Exemple 1 : tous les utilisateurs d’une liste importée et 10 % des utilisateurs d’un pays spécifique**

Ajoutez deux règles : l’une pour la liste des utilisateurs importés et l’autre pour la règle de pourcentage (10 %), combinée à une règle Pays . Utilisez une logique imbriquée : `1 or (2 and 3)`.

**Exemple 2 : 10 % des utilisateurs américains et 20 % des utilisateurs britanniques**

Ajoutez quatre règles : Pays = États-Unis, Pourcentage = 10 %, Pays = Royaume-Uni, Pourcentage = 20 %. Utilisez une logique imbriquée : `(1 and 2) or (3 and 4)`.

## Voir également {#see-also}

* [Audience dans les indicateurs de fonctionnalité et les groupes de fonctionnalités](audience-in-feature-flags-and-feature-groups.md)
* [Règles d’audience complexes](complex-rules.md)
* [Définir une fonctionnalité à déployer progressivement](../feature-flags/set-feature-gradual-rollout.md)
