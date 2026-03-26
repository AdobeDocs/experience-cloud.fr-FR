---
title: FAQ sur la gestion des versions
description: Trouvez des réponses aux questions courantes sur la gestion des versions dans les déploiements d’Adobe Experience.
exl-id: 802b99bd-85ee-4f4d-afca-88d1297f8782
source-git-commit: 4a3133f014a9bb9d6ed26eb9d9f763db79ce63b3
workflow-type: tm+mt
source-wordcount: '254'
ht-degree: 1%

---

# FAQ sur la gestion des versions {#release-management-faqs}

## Comment puis-je demander une version ? {#request-release}

Contactez l’assistance des déploiements d’expérience pour demander une version. Indiquez le nom de votre équipe, les détails de l’application, l’audience cible et le calendrier de déploiement souhaité.

## Quels critères d’audience sont pris en charge pour les versions d’ ? {#audience-criteria}

Les versions prennent en charge les règles d’audience suivantes :

* Type d’identifiant (type de compte)
* Pays
* Identifiant utilisateur (GUID)
* Adresse e-mail (liste individuelle ou en bloc)
* Email domain
* IP du client
* Pourcentage (tous les utilisateurs)
* Pourcentage (utilisateurs authentifiés uniquement)

Vous pouvez combiner plusieurs règles à l’aide de la logique AND/OR, y compris des conditions imbriquées.

## Comment ajouter une application à une version ? {#onboard-application}

Une fois la version créée, ouvrez-la dans la console et ajoutez votre application à la configuration de version. Le ou la propriétaire de version de produit pour chaque application peut ensuite ajouter les indicateurs de fonctionnalité appropriés.

## Une fonctionnalité n’est pas renvoyée pour un utilisateur qui devrait remplir les critères. Comment résoudre le problème ? {#troubleshoot}

Pour déboguer, procédez comme suit :

1. **Vérifiez l’état de publication.** La version doit être à l’état **Publiée** ou **Déploiement complet** pour servir les fonctionnalités.
2. **Vérifiez l’indicateur d’application et de fonctionnalité.** Vérifiez que l&#39;indicateur de fonctionnalité est créé pour l&#39;application appropriée et que l&#39;application est associée à la version appropriée.
3. **Vérifiez que l’indicateur de fonctionnalité est activé.** Un indicateur désactivé ne sera pas diffusé même si la version est active.
4. **Consultez les critères d’audience.** Vérifiez que l’utilisateur remplit toutes les conditions définies dans les règles d’audience. Vérifiez à nouveau les critères de la version spécifique à laquelle la fonctionnalité est associée.

## Voir également {#see-also}

* [Contacter l’assistance](../support/contact-support.md)
