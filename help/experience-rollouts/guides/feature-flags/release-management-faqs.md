---
title: FAQ sur la gestion des versions
description: Trouvez des réponses aux questions courantes sur la gestion des versions dans les déploiements d’Adobe Experience.
source-git-commit: d311efb995b20ffc17370d68d57dd84a8605896c
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 1%

---


# FAQ sur la gestion des versions {#release-management-faqs}

## Comment puis-je demander une version ? {#request-release}

Voir [Demande de publication](request-a-release.md) pour le processus complet et les informations que vous devez fournir.

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

Vous pouvez combiner plusieurs règles à l’aide de la logique AND/OR, y compris des conditions imbriquées. Consultez [Mise à jour des règles d’audience de version](update-release-audience-rules.md) pour obtenir des instructions de configuration détaillées.

## Comment ajouter une application à une version ? {#onboard-application}

Une fois la version créée, ouvrez-la dans la console et ajoutez votre application à la configuration de version. Le ou la propriétaire de version de produit pour chaque application peut ensuite ajouter les indicateurs de fonctionnalité appropriés. Voir [Workflow de publication de bout en bout](release-workflow-end-to-end.md) pour la séquence complète.

## Une fonctionnalité n’est pas renvoyée pour un utilisateur qui devrait remplir les critères. Comment résoudre le problème ? {#troubleshoot}

Pour déboguer, procédez comme suit :

1. **Vérifiez l’état de publication.** La version doit être à l’état **Publiée** ou **Déploiement complet** pour servir les fonctionnalités. Voir [États de publication](release-states.md).
2. **Vérifiez l’indicateur d’application et de fonctionnalité.** Vérifiez que l&#39;indicateur de fonctionnalité est créé pour l&#39;application appropriée et que l&#39;application est associée à la version appropriée.
3. **Vérifiez que l’indicateur de fonctionnalité est activé.** Un indicateur désactivé ne sera pas diffusé même si la version est active.
4. **Consultez les critères d’audience.** Vérifiez que l’utilisateur remplit toutes les conditions définies dans les règles d’audience. Vérifiez à nouveau les critères de la version spécifique à laquelle la fonctionnalité est associée.

## Voir également {#see-also}

* [Demander une version](request-a-release.md)
* [Mise à jour des règles d’audience de version](update-release-audience-rules.md)
* [États de la version](release-states.md)
* [Workflow de publication complet](release-workflow-end-to-end.md)
