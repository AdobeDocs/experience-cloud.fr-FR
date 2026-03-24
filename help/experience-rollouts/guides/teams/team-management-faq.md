---
title: FAQ sur la gestion des équipes
description: Trouvez des réponses aux questions courantes sur la gestion des équipes, des membres et des rôles dans les déploiements d’Adobe Experience.
source-git-commit: 53edbee220e7ef17c4a3ea066743192c1e9681f4
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 1%

---


# FAQ sur la gestion des équipes {#team-management-faq}

## J’essaie d’ajouter un utilisateur, mais la recherche ne renvoie aucun résultat {#user-not-found}

Cela peut se produire dans l’environnement d’évaluation si l’utilisateur ne s’est jamais connecté à l’environnement d’évaluation auparavant. Pour résoudre ce problème, demandez à l’utilisateur de se connecter au moins une fois à la console d’évaluation pour créer son compte dans le système d’identités d’évaluation. Une fois qu’ils se sont connectés, essayez de les rechercher à nouveau.

## Je suis un administrateur mais je ne peux pas créer ni modifier les indicateurs de fonctionnalité {#admin-cannot-edit-flags}

Les rôles dans les déploiements d’expérience s’excluent mutuellement. Le rôle **Admin** accorde des autorisations de gestion d’équipe, mais n’inclut pas les autorisations d’un **Propriétaire de la version du produit**. Pour créer et modifier des indicateurs de fonctionnalité, un membre doit disposer du rôle **Propriétaire de la version de produit** en plus du rôle **Administrateur**.

Contactez l’administrateur ou l’administratrice de votre équipe pour que des rôles supplémentaires soient attribués. Voir [Rôles utilisateur](user-roles.md) pour une description complète de ce que chaque rôle peut faire.

## Les administrateurs disposent-ils d’une hiérarchie ? Un administrateur peut-il en remplacer un autre ? {#admin-hierarchy}

Non. Les équipes dans les déploiements d’expérience ont une structure plate. Tous les membres dotés du rôle **Admin** disposent d’autorisations égales et peuvent gérer les configurations des uns et des autres. Il n’existe aucun workflow de validation hiérarchique entre les administrateurs.

## Comment supprimer un membre de mon équipe ? {#remove-member}

Les membres sont supprimés par le biais du système de gestion des accès. En tant qu’administrateur, recherchez l’enregistrement d’accès du membre pour votre équipe et révoquez son rôle. Si vous ne savez pas comment procéder, contactez l’équipe de gestion des accès de votre entreprise.

## Un membre peut-il avoir plus d&#39;un rôle ? {#multiple-roles}

Oui. Attribuez plusieurs rôles à un membre lorsque ses responsabilités s&#39;étendent sur plusieurs fonctions. Par exemple, un membre de l’équipe qui gère l’équipe et crée des indicateurs de fonctionnalité doit disposer des rôles **Admin** et **Propriétaire de la version du produit**.

## Voir également {#see-also}

* [Rôles utilisateur](user-roles.md)
* [Ajouter des membres à votre équipe](add-team-members.md)
* [Gestion des équipes](manage-teams.md)
