---
title: SDK
description: Découvrez l’architecture de SDK dans Déploiements d’Adobe Experience et l’extension mobile SDK disponible pour Android.
hide: true
exl-id: 110a440d-b52a-4e1e-a94f-86f9741a223a
source-git-commit: 12032cbed45e694a3f25f16afe80308b3eb82924
workflow-type: tm+mt
source-wordcount: '172'
ht-degree: 3%

---

# SDK {#sdks}

Les déploiements d’expérience fournissent des SDK pour intégrer des indicateurs de fonctionnalité à vos applications. Cette page décrit l’architecture de SDK et les options disponibles.

## Architecture de SDK {#architecture}

Tous les SDK de déploiement d’Experience partagent la même architecture principale :

* **Initialisation** — Le SDK est configuré au démarrage et s&#39;enregistre auprès du service de déploiements d&#39;expérience.
* **Récupération de fonctionnalités** — Le SDK récupère les données d&#39;indicateur de fonctionnalité et évalue les indicateurs localement.
* **Mise en cache** — Le SDK met en cache les données d&#39;indicateur de fonctionnalité et les actualise selon un intervalle d&#39;interrogation configurable (TTL).
* **Gestion des erreurs** — Si le service n’est pas disponible, le SDK continue à diffuser les évaluations d’indicateur de fonctionnalité à partir du cache local.

## SDK disponibles {#available-sdks}

### Extension Android {#android-extension}

L’extension Experience Rollout pour Android s’intègre à Adobe Experience Platform Mobile SDK.

Consultez le [guide d’intégration de l’extension &#x200B;](../sdk-releases/android/android-extension-integration-guide.md) pour obtenir des instructions de configuration.

>[!NOTE]
>
>D’autres options de SDK pour les plateformes web et mobiles sont en cours de préparation et seront bientôt disponibles. Contactez votre représentant Adobe pour obtenir des conseils sur l’accès anticipé.

## Voir également {#see-also}

* [Guide d’intégration de l’extension Android](../sdk-releases/android/android-extension-integration-guide.md)
* [Services Web](web-services.md)
* [Étapes d’intégration](integration-steps.md)

<!-- -->
