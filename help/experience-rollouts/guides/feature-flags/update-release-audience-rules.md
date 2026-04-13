---
title: Mise à jour des règles d’audience de version
description: Découvrez comment configurer et mettre à jour les critères d’audience pour une version dans les déploiements d’Adobe Experience, y compris les types de règles pris en charge et comment les combiner.
hide: true
exl-id: 8d546cd7-af66-47c7-aab3-c667568e8582
source-git-commit: 12032cbed45e694a3f25f16afe80308b3eb82924
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 3%

---

# Mise à jour des règles d’audience de version {#update-release-audience-rules}

## Accès aux paramètres de l’audience {#access}

Pour commencer à configurer les destinataires de votre version, accédez aux paramètres d’audience dans la console :

1. Ouvrez votre version dans la console Déploiements d’expérience .
2. Accédez à l’onglet **Audience**.
3. Activez le bouton (bascule) en regard de **Règles d’audience**.
4. Indiquez s’il faut ajouter des **règles d’inclusion** (qui doit recevoir la version) ou des **règles d’exclusion** (qui ne doit pas recevoir la version).

## Critères d’audience pris en charge {#criteria}

### Type d’identifiant {#id-type}

Ciblez les utilisateurs en fonction de leur type de compte (par exemple, comptes personnels ou d’entreprise).

### Pays {#country}

Ciblez les utilisateurs et utilisatrices en fonction de leur pays d’enregistrement.

### Identifiant utilisateur {#user-id}

Ciblez des utilisateurs et utilisatrices spécifiques à l’aide de leur identifiant utilisateur unique (GUID).

### Adresse e-mail {#email}

Ciblez les utilisateurs en fonction de leur adresse e-mail exacte. Pour ajouter plusieurs adresses e-mail à la fois, sélectionnez **dans** dans la liste déroulante des opérateurs (au lieu de **is**), puis :

* Saisissez une liste d’adresses séparées par des virgules dans la zone de texte, ou
* Chargez un fichier `.txt` avec une adresse par ligne, ou
* Charger un fichier `.csv` avec la liste des adresses

Si votre liste est très volumineuse, divisez-la en lots plus petits.

### Email domain {#email-domain}

Ciblez tous les utilisateurs dont l’adresse e-mail appartient à un domaine spécifique (par exemple, `yourcompany.com`).

### IP du client {#client-ip}

Ciblez les utilisateurs en fonction de leur adresse IP client.

### Pourcentage {#percentage}

Cibler un pourcentage aléatoire de tous les utilisateurs, y compris les utilisateurs non authentifiés

### Pourcentage (authentifié uniquement) {#percentage-auth}

Ciblez un pourcentage aléatoire d’utilisateurs authentifiés uniquement. Les utilisateurs non authentifiés sont exclus.

## Combinaison de plusieurs règles {#combining-rules}

Vous pouvez combiner plusieurs critères d’audience à l’aide de la logique ET/OU.

**Exemples :**

* Pour cibler uniquement les comptes d’entreprise d’un domaine spécifique, combinez la règle **type d’ID** avec la règle **Domaine d’e-mail** à l’aide de ET.
* Pour cibler 10 % des utilisateurs d’un pays spécifique, combinez la règle **Pays** avec la règle **Pourcentage**.

Utilisez les icônes **+/-** pour ajouter ou supprimer des conditions. Pour dupliquer une condition, sélectionnez l’icône de doublon en regard d’une règle existante. Pour une logique imbriquée complexe, activez **Logique imbriquée** et saisissez une expression valide dans la zone de texte.

## Voir également {#see-also}

* [Demander une version](request-a-release.md)
* [Workflow de publication complet](release-workflow-end-to-end.md)
* [États de la version](release-states.md)

<!-- -->
