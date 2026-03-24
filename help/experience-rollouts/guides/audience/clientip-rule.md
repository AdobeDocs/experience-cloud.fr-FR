---
title: Règle d’audience avec variable de contexte IP client
description: Découvrez comment utiliser la variable de contexte IP client dans les règles d’audience dans les déploiements d’Adobe Experience, y compris la prise en charge des adresses IP, des blocs CIDR et des plages réseau.
source-git-commit: 3f3f7145b3c58dc721cbeb850e9e8571e3255bb1
workflow-type: tm+mt
source-wordcount: '215'
ht-degree: 1%

---


# Règle d’audience avec variable de contexte IP client {#clientip-rule}

La variable de contexte `clientip` vous permet de cibler les utilisateurs en fonction de leur adresse IP client. Cela s’avère utile pour restreindre ou activer des fonctionnalités basées sur le réseau à partir duquel les utilisateurs accèdent à votre application, par exemple pour limiter l’accès anticipé aux utilisateurs d’un réseau d’entreprise.

## Types d’entrée pris en charge {#input-types}

La variable contextuelle `clientip` prend en charge trois types de valeurs d’entrée :

| Type d’entrée | Description | Opérateurs pris en charge |
|---|---|---|
| **adresse IP** | Une seule adresse IPv4 ou IPv6 | Est, Est différent de, Dans |
| **Bloc CIDR** | Une plage d’adresses IP dans la notation CIDR (par exemple, `192.168.1.0/24`) | Est, Dans, N’est pas égal à |
| **Plage réseau** | Plage réseau nommée prédéfinie gérée par la plateforme | Fait partie de |

## Ajout d’une règle d’adresse IP client {#adding-rule}

1. Ouvrez l&#39;indicateur de fonctionnalité, le groupe de fonctionnalités ou le groupe de fonctionnalités interéquipes dans la console.
2. Accédez à l’onglet **Audience**.
3. Sous **Context**, ajoutez une condition à l’aide de la variable **clientip**.
4. Sélectionnez l’opérateur et saisissez la valeur (adresse IP, bloc CIDR ou sélection d’une plage réseau prédéfinie).

## Voir également {#see-also}

* [Utilisation du contexte dans les règles d’audience](using-context-in-audience-rules.md)
* [Audience dans les indicateurs de fonctionnalité et les groupes de fonctionnalités](audience-in-feature-flags-and-feature-groups.md)
* [Règles d’audience complexes](complex-rules.md)
