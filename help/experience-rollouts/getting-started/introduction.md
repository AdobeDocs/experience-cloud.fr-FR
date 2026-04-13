---
title: Présentation des déploiements d’expérience
description: Découvrez comment Adobe Experience Rollouts fournit un système de version contrôlée pour déployer progressivement des fonctionnalités vers les audiences ciblées.
hide: true
exl-id: befe7899-096d-4f74-a5a2-35b1fc3cbc58
source-git-commit: 12032cbed45e694a3f25f16afe80308b3eb82924
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%

---

# Présentation des déploiements d’expérience {#introduction}

Les déploiements d’Adobe Experience sont un système de version contrôlée qui permet aux équipes de déployer des fonctionnalités jusqu’à la production tout en gardant un contrôle précis sur qui les voit et quand. Une fonctionnalité peut être en production et invisible pour les utilisateurs finaux (puis activée progressivement pour une audience ciblée) sans aucun redéploiement.

## Du développement à la production {#dev-to-prod}

Les déploiements d’expérience prennent en charge le parcours complet d’une fonctionnalité, depuis son développement initial jusqu’à sa disponibilité générale :

1. **Test du développeur** — Un développeur crée un indicateur de fonctionnalité, déploie son code dans n&#39;importe quel environnement et effectue des tests uniquement sur sa propre session. Aucun autre utilisateur n’est affecté et aucun embranchement n’est nécessaire.

2. **Aperçu ciblé** : un propriétaire de produit associe une audience à l’indicateur de fonctionnalité, rendant la fonctionnalité disponible à un sous-ensemble défini d’utilisateurs (par exemple, les participants à la version bêta ou une région spécifique) pour validation et commentaires.

3. **Déploiement progressif** — La fonctionnalité est progressivement ouverte à une audience plus large (1 %, 10 %, 50 %, 100 %) avec la possibilité de suspendre, d’ajuster ou de désactiver la fonctionnalité à n’importe quelle étape.

4. **Disponibilité générale** — Une fois la validation terminée, la fonctionnalité est mise à la disposition de tous les utilisateurs.

## Fonctionnalités principales {#capabilities}

Les déploiements d’expérience constituent une plateforme de gestion des fonctionnalités qui offre les avantages suivants :

* **Indicateurs de fonctionnalité** — Activez ou désactivez n’importe quelle fonctionnalité au moment de l’exécution pour une audience ciblée, sans redéployer le code.

* **Ciblage des audiences** — Contrôlez qui voit une fonctionnalité à l’aide des données de profil utilisateur, des règles basées sur un pourcentage, de l’adresse e-mail, du domaine de messagerie, de l’adresse IP ou des attributs contextuels.

* **Groupes de fonctionnalités** : regroupez plusieurs indicateurs de fonctionnalités associés dans les applications et gérez-les comme une seule unité, afin de garantir une expérience cohérente pour la même audience.

* **Versions** — Coordonnez les déploiements importants entre les équipes en regroupant les indicateurs de fonctionnalité de plusieurs équipes et applications en un seul événement de version.

* **Déploiements graduels** - Déployez progressivement les fonctionnalités pour réduire les risques, recueillir des commentaires et gérer la charge du serveur principal.

* **Interrupteur de blocage** — Désactivez immédiatement toute fonction si un problème est détecté, sans changement de code ni redéploiement.

<!-- -->
