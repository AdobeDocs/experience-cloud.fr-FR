---
title: Rôles utilisateur
description: Découvrez les cinq rôles utilisateur disponibles dans Déploiements d’Adobe Experience et comment choisir le rôle approprié pour chaque membre de l’équipe.
source-git-commit: 53edbee220e7ef17c4a3ea066743192c1e9681f4
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 2%

---


# Rôles utilisateur {#user-roles}

Les déploiements d’expérience fournissent cinq rôles. Chaque rôle est conçu pour un ensemble spécifique de responsabilités. Par défaut, les rôles s’excluent mutuellement : un membre ayant le rôle d’administrateur ne dispose pas automatiquement des autorisations de Propriétaire de la version de produit. Attribuez plusieurs rôles à un membre lorsque un accès plus étendu est nécessaire.

## Rôles disponibles {#roles}

| Rôle | Responsabilités |
|---|---|
| **Administration** | Intégration des applications à la console , gestion des membres de l’équipe et approbation ou rejet des demandes d’accès. Requis pour que l&#39;équipe puisse commencer à utiliser les indicateurs de fonctionnalité. |
| **Propriétaire de la version de produit** | Crée et met à jour des indicateurs de fonctionnalité et des groupes de fonctionnalités pour leur application. Possibilité de lier les audiences aux indicateurs de fonctionnalité pour rendre les fonctionnalités disponibles pour les utilisateurs externes. |
| **Développeur ou développeuse** | Fonctionne dans un contexte de sandbox pour tester les fonctionnalités derrière des indicateurs de fonctionnalité sans affecter les autres utilisateurs. Peut exposer un indicateur de fonctionnalité à une audience privée (comme un ID utilisateur ou une adresse e-mail spécifique) dans les environnements d’évaluation ou de production. |
| **Administrateur de fonctionnalités** | Crée et gère des groupes de fonctionnalités interéquipes. Utilisez ce rôle lors de la coordination des indicateurs entre les applications détenues par différentes équipes. |
| **Gestionnaire de versions** | Gère les versions multi-équipes et multi-applications et met à jour les règles d’audience qui définissent les destinataires d’une version. |

## Choisir le bon rôle {#choosing}

Suivez les conseils suivants pour affecter des rôles :

* **Ajout ou mise à jour d’indicateurs de fonctionnalité pour votre application** → **Propriétaire de la version du produit**
* **Test privé des fonctionnalités sans affecter les autres** → **développeur**
* **Gestion des groupes de fonctionnalités inter-équipes** → **Administration des fonctionnalités**
* **Gestion des versions dans plusieurs équipes et applications** → **Gestionnaire de versions**
* **Intégration d’applications et gestion de l’appartenance à une équipe** → **Admin**

>[!NOTE]
>
>Un membre peut détenir plusieurs rôles. Par exemple, un ingénieur qui teste les fonctionnalités et gère les applications de l’équipe doit disposer des rôles **Développeur** et **Administrateur**.

## Erreur d’autorisations {#permissions-error}

Si un membre rencontre une erreur « autorisations insuffisantes » lors de la tentative de mise à jour d’une fonctionnalité ou d’un groupe, il a besoin du rôle **Propriétaire de la version du produit**. Contactez l’administrateur ou l’administratrice de votre équipe pour ajouter ce rôle.

## Voir également {#see-also}

* [Ajouter des membres à votre équipe](add-team-members.md)
* [Gestion des équipes](manage-teams.md)
