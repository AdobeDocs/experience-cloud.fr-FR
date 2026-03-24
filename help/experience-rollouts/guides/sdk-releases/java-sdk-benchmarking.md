---
title: évaluation des performances de SDK
description: Consultez les résultats de l’évaluation des performances de Java SDK pour les déploiements d’Adobe Experience , y compris les mesures de temps de réponse sur un nombre variable d’indicateurs de fonctionnalité dans des conditions de charge standard.
source-git-commit: 8b8b5db1a28af3a3ac29aecf26482f70eb84c714
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 7%

---


# évaluation des performances de SDK {#sdk-benchmarking}

Le SDK Java des déploiements d’expérience est soumis à un test de référence afin de donner aux équipes d’intégration une estimation fiable des ressources et des temps de réponse à attendre lorsque le SDK s’exécute dans leur infrastructure.

## Environnement de test {#test-environment}

L&#39;évaluation comparative a été effectuée sur une application Spring Boot avec la configuration fixe suivante :

* **Cœurs CPU :** 8
* **Mémoire JVM :** 4 096 Mo

## Hypothèses de test {#test-assumptions}

Les conditions suivantes ont été maintenues constantes pour toutes les exécutions de référence :

* Indicateurs de fonctionnalités testés : 8 à 128
* Variables contextuelles par indicateur de fonctionnalité : 2 (type `STRING`, longueur de 36 caractères)
* Charge moyenne : 15 000 requêtes par minute (tr/min)
* Threads actifs : 100

## Résultats {#results}

Le tableau ci-dessous indique le temps de réponse du 99,99e centile pour les appels `getFeatures()` à mesure que le nombre d’indicateurs de fonctionnalité augmente :

| Nombre d’indicateurs de fonctionnalité | Variables contextuelles par indicateur | Temps de réponse (ms, p99,99) |
|---|---|---|
| 8 | 2 | &lt; 0.5 |
| 16 | 2 | &lt; 0.5 |
| 32 | 2 | &lt; 0.5 |
| 64 | 2 | &lt; 1 |
| 128 | 2 | &lt; 1 |

## Interprétation des résultats {#interpretation}

Les références ci-dessus représentent les performances dans les conditions d’essai spécifiques décrites. Comme SDK s’exécute dans l’infrastructure de votre application, les temps de réponse réels varient en fonction de facteurs spécifiques à votre environnement :

* CPU et nombre de cœurs disponibles
* Taille du tas JVM et comportement du nettoyage de la mémoire
* Disponibilité des threads et changement de contexte
* Charge actuelle du système au moment de la demande

Utilisez ces chiffres comme référence de planification plutôt que comme cibles de performances garanties pour votre environnement de production.

## Voir également {#see-also}

* [Guide d’intégration de Java SDK](java/java-sdk-integration-guide.md)
* [Notes de mise à jour de Java SDK](java/java-sdk-release-notes.md)
* [SDK](../integrate/sdks.md)
