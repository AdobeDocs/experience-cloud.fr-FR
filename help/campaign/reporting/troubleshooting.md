---
title: Résoudre des problèmes liés aux rapports dynamiques
description: Vous trouverez ici des questions courantes relatives aux rapports dynamiques.
audience: end-user
level: Intermediate
badge: label="DISPONIBILITÉ LIMITÉE" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Limité aux utilisateurs migrés Campaign Standard"
exl-id: a58fc8fd-e510-45ef-8fe9-c75ff4498113
source-git-commit: 34c6f8a137a9085b26c0ea8f78930cff6192cfc9
workflow-type: tm+mt
source-wordcount: '1239'
ht-degree: 97%

---

# Dépannage{#troubleshooting}

Cette section contient des questions courantes relatives aux rapports dynamiques.

## Pour les ouvertures uniques et les clics uniques, le décompte de la ligne agrégée ne correspond pas à ceux de chaque ligne.  {#unique-open-clicks-no-match}

Il s&#39;agit d&#39;un comportement attendu.
Prenons l&#39;exemple suivant pour expliquer ce comportement.

Un e-mail est envoyé aux profils P1 et P2.

P1 ouvre l&#39;e-mail deux fois le premier jour, puis trois fois le jour suivant.

P2, quant à lui, ouvre l&#39;e-mail une fois le premier jour et ne le rouvre pas les jours suivants.
Voici une représentation visuelle de l&#39;interaction des profils avec l&#39;e-mail envoyé :

<table> 
 <thead> 
  <tr> 
   <th align="center"> <strong>Jour</strong> <br/> </th> 
   <th align="center"> <strong>Ouvertures</strong><br/> </th> 
   <th align="center"> <strong>Ouvertures uniques</strong> <br/> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td align="center"> Jour 1<br/> </td> 
   <td align="center"> 2 + 1 = 3<br/> </td> 
   <td align="center"> 1 + 1 = 2<br/> </td> 
  </tr> 
  <tr> 
   <td align="center"> Jour 2<br/> </td> 
   <td align="center"> 3 + 0 = 3<br/> </td> 
   <td align="center"> 1 + 0 = 1<br/> </td> 
  </tr>
 </tbody> 
</table>

Pour comprendre le nombre total des ouvertures uniques, nous devons additionner les chiffres des lignes des **[!UICONTROL Ouvertures uniques]**, ce qui nous donne la valeur 3. Toutefois, comme l&#39;e-mail n&#39;était ciblé que sur 2 profils, le taux d&#39;ouverture devrait être de 150 %.

Pour ne pas obtenir de pourcentage supérieur à 100, la définition des **[!UICONTROL ouvertures uniques]** est le nombre de broadlogs uniques ouverts. Dans ce cas, même si P1 a ouvert l’e-mail le jour 1 et le jour 2, les ouvertures uniques sont toujours égales à 1.

Cela donne le tableau suivant :

<table> 
 <thead> 
  <tr> 
   <th align="center"> <strong></strong> <br/> </th> 
   <th align="center"> <strong>Ouvertures</strong><br/> </th> 
   <th align="center"> <strong>Ouvertures uniques</strong> <br/> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td align="center"> <strong> Jour </strong><br/> </td> 
   <td align="center"> <strong> 6 </strong><br/> </td> 
   <td align="center"> <strong> 2</strong><br/> </td>
  </tr> 
  <tr> 
   <td align="center"> Jour 1<br/> </td> 
   <td align="center"> 3<br/> </td> 
   <td align="center"> 2<br/> </td>
  </tr> 
  <tr> 
   <td align="center"> Jour 2<br/> </td> 
   <td align="center"> 3<br/> </td> 
   <td align="center"> 1<br/> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Les décomptes uniques reposent sur un sketch HLL, ce qui peut entraîner de légères imprécisions dans le cas de nombres élevés.

## Les décomptes des ouvertures ne correspondent pas à ceux de la base de données.  {#open-counts-no-match-database}

Cela peut être dû au fait que la méthode heuristique est utilisée dans les rapports dynamiques pour tracker les ouvertures, même lorsque nous ne pouvons pas tracker l&#39;action **[!UICONTROL Ouvrir]**.

Par exemple, si un utilisateur a désactivé les images sur son client et qu&#39;il clique sur un lien dans l&#39;e-mail, l&#39;**[!UICONTROL Ouverture]** peut ne pas être trackée par la base de données mais le **[!UICONTROL clic]** oui.

Par conséquent, les logs de tracking des **[!UICONTROL ouvertures]** peuvent ne pas avoir le même décompte que dans la base de données.

Ces occurrences sont ajoutées car **&quot;un clic sur un e-mail implique l&#39;ouverture de l&#39;e-mail&quot;**.

>[!NOTE]
>
>Comme les décomptes uniques reposent sur le sketch HLL, des incohérences mineures entre les décomptes sont possibles.

## Comment les décomptes des diffusions récurrentes/transactionnelles sont-ils calculés ?  {#counts-recurring-deliveries}

Lors de l&#39;utilisation de diffusions récurrentes et transactionnelles, les décomptes sont attribués aux diffusions parents et enfants.
Prenons comme exemple une diffusion récurrente appelée **R1** définie pour s&#39;exécuter tous les jours le jour 1 (RC1), le jour 2 (RC2) et le jour 3 (RC3).
Supposons que seule une personne a ouvert toutes les diffusions enfants à plusieurs reprises. Dans ce cas, chaque diffusion enfant récurrente affichera le nombre 1 d&#39;**[!UICONTROL Ouverture.]**
Toutefois, comme la même personne a cliqué sur toutes les diffusions, la diffusion récurrente parent aura également un décompte de 1 pour les **[!UICONTROL ouvertures uniques]**.

Les rapports doivent se présenter comme suit :

<table> 
 <thead> 
  <tr> 
   <th align="center"> <strong>Diffusion</strong> <br/> </th> 
   <th align="center"> <strong>Envoyés</strong> <br/> </th> 
   <th align="center"> <strong>Delivrés</strong> <br/> </th>
   <th align="center"> <strong>Ouvertures</strong><br/> </th> 
   <th align="center"> <strong>Ouvertures uniques</strong> <br/> </th>
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td align="center"> <strong>R1</strong><br/> </td> 
   <td align="center"> <strong>100</strong><br/> </td> 
   <td align="center"> <strong>90</strong><br/> </td> 
   <td align="center"> <strong>10</strong><br/> </td> 
   <td align="center"> <strong>3</strong><br/> </td> 
  </tr> 
  <tr> 
   <td align="center"> RC1<br/> </td> 
   <td align="center"> 20<br/> </td> 
   <td align="center"> 20<br/> </td> 
   <td align="center"> 6<br/> </td> 
   <td align="center"> 1<br/> </td> 
  </tr>
    <tr> 
   <td align="center"> RC2<br/> </td> 
   <td align="center"> 40<br/> </td> 
   <td align="center"> 30<br/> </td> 
   <td align="center"> 2<br/> </td> 
   <td align="center"> 1<br/> </td> 
  </tr> 
    <tr> 
   <td align="center"> RC3<br/> </td> 
   <td align="center"> 40<br/> </td> 
   <td align="center"> 40<br/> </td> 
   <td align="center"> 2<br/> </td> 
   <td align="center"> 1<br/> </td> 
  </tr> 
 </tbody> 
</table>

## Quelle est la signification des couleurs dans le tableau des rapports ?  {#reports-color-signification}

Les couleurs affichées dans vos rapports sont aléatoires et ne peuvent pas être personnalisées. Elles représentent une barre de progression et s&#39;affichent pour mettre en évidence la valeur maximale atteinte dans vos rapports.

Dans l&#39;exemple ci-dessous, la cellule est de la même couleur car sa valeur est 100 %.

![](assets/troubleshooting_1.png)

Si vous définissez la **[!UICONTROL mise en forme conditionnelle]** sur personnalisée, lorsque la valeur atteint la limite supérieure, la cellule devient verte. En revanche, si elle atteint la limite inférieure, elle devient rouge.

Par exemple, ici, nous définissons la **[!UICONTROL limite supérieure]** sur 500 et la **[!UICONTROL limite inférieure]** sur 0.

![](assets/troubleshooting_2.png)

## Pourquoi la valeur N/A apparaît-elle dans mes rapports ?

![](assets/troubleshooting_3.png)

La valeur **N/A** peut parfois apparaître dans vos rapports dynamiques. Elle peut s&#39;afficher pour trois raisons :

* La diffusion a été supprimée et s&#39;affiche ici sous la forme **N/A** pour ne pas entraîner d&#39;incohérence dans les résultats.
* Lorsque vous placez la dimension **[!UICONTROL Diffusion transactionnelle]** dans vos rapports, la valeur **N/A** peut apparaître. Elle s&#39;affiche, car le rapport dynamique récupère chaque diffusion, même si elle n&#39;est pas transactionnelle. Elle peut également s&#39;afficher lorsque vous placez la dimension **[!UICONTROL Diffusion]** dans votre rapport. Dans ce cas, la valeur **N/A** représente les diffusions transactionnelles.
* Lorsqu&#39;une dimension est utilisée avec une mesure qui n&#39;est pas liée à la dimension. Dans l’exemple ci-dessous, une répartition est ajoutée avec la dimension **[!UICONTROL URL de tracking]** même si le nombre de **[!UICONTROL clics]** est défini sur 0 dans cette diffusion.

  ![](assets/troubleshooting_4.png)

## Les rapports des diffusions affichent des données incomplètes lors de l’utilisation du mapping de ciblage personnalisé.

Si vous utilisez des mappings de ciblage personnalisés importés dans des diffusions et qu’aucune donnée n’est affichée dans les différents rapports, cela peut signifier que les enrichissements du reporting n’ont pas été créés pour ces mappings de ciblage.

Pour résoudre ce problème, procédez comme suit :

* Après avoir importé votre mapping de ciblage à partir d’un fichier XML, vous devrez également importer l’enrichissement du reporting.

* Au lieu d&#39;importer votre mapping de ciblage, vous pouvez le créer directement dans l&#39;interface utilisateur web d&#39;Adobe Campaign qui va automatiquement créer l&#39;enrichissement de reporting.

## Divergence entre le nombre d’en-têtes de colonnes et la somme des lignes

Une divergence entre le nombre d’en-têtes de colonnes et la somme de toutes les lignes est attendue dans les cas suivants :

* **Mesures uniques** : l’utilisation de mesures uniques peut modifier le nombre total affiché dans l’en-tête, car il est basé sur les identifiants des destinataires et non sur le nombre de lignes. Par conséquent, un seul profil peut déclencher de nombreux événements dans différentes dimensions, ce qui entraîne plusieurs lignes dans le jeu de données. Cependant, dans l’en-tête, chaque profil n’est comptabilisé qu’une seule fois.

  Par exemple :

   * Si un profil A ouvre un e-mail sur trois jours différents, la ventilation par jour affichera A sur trois lignes, bien que dans l’en-tête, A compte pour 1.

   * Si le profil A clique sur trois liens différents dans un e-mail le même jour, la ventilation par URL de suivi affiche A sur trois lignes, bien que dans l’en-tête, A compte pour 1. Il en va de même pour les ventilations par appareil et navigateur.

* **Mesures d’ouverture** : le nombre d’ouvertures est déterminé par l’agrégation du total des événements d’ouverture réels et des événements de clic unique (par identifiant de personne destinataire), à l’exception des cas où aucun événement d’ouverture n’a eu lieu, puisqu’il n’est pas possible de cliquer sur un lien d’e-mail sans événement d’ouverture.

  Par exemple :

   * Lorsque le profil A ouvre un e-mail suivi (avec l’URL U1), il s’enregistre en tant qu’événement d’ouverture avec l’URL indiquée comme nulle. Cliquer sur U1 ultérieurement génère un événement de clic. Bien que le clic de A sur U1 soit également comptabilisé comme événement d’ouverture, il n’existe aucun événement d’ouverture spécifique pour U1. Par conséquent, A n’est compté qu’une seule fois dans le nombre d’ouvertures uniques.

   * Un profil R ouvre un e-mail le jour 1, enregistrant ainsi un événement d’ouverture, puis clique sur un lien. Au cours des deux jours suivants, R rouvre l’e-mail et clique à nouveau sur le lien, générant ainsi un événement de clic chaque jour. Bien que l’engagement de R soit suivi quotidiennement dans le nombre d’ouvertures, R n’est compté qu’une seule fois dans l’en-tête de colonne, qui se concentre sur les engagements uniques.

* **Événement négatif** : dans les rapports, un événement négatif signifie que les tentatives de diffusion qui ont été initialement marquées comme réussies ont finalement échoué après les nouvelles tentatives. Elles sont indiquées par le nombre -1. Pour éviter toute confusion, ces nombres négatifs sont exclus des nombres de mesures de diffusion affichés. Par conséquent, le total de toutes les lignes pour la mesure de diffusion peut ne pas correspondre au nombre d’en-têtes de colonnes.
