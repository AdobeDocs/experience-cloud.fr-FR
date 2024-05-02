---
title: Prise en main des API REST de Campaign
description: Créez des intégrations et construisez votre propre écosystème en connectant Campaign à un ensemble de technologies.
audience: developing
content-type: reference
topic-tags: campaign-standard-apis
role: Data Engineer
level: Experienced
badge: label="DISPONIBILITÉ LIMITÉE" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Limité aux utilisateurs migrés Campaign Standard"
exl-id: c6968252-a012-4029-bbb8-66f4f693e99b
source-git-commit: 3f4400f24b75e8e435610afbe49e9d9444dbf563
workflow-type: tm+mt
source-wordcount: '231'
ht-degree: 48%

---

# Prise en main des API REST de Campaign {#get-started-apis}

>[!CAUTION]
>
>Cette documentation est destinée aux clients Adobe Campaign Standard effectuant la migration vers Campaign v8.
>
>Avant d’effectuer des appels aux API, vérifiez les limites de taille correspondant à votre contrat de licence. Pour plus d’informations, consultez [cette page](https://helpx.adobe.com/fr/legal/product-descriptions/campaign-standard.html#RessourcesdinfrastructureinformatiqueparniveauxdeProfilsactifs).

Les API REST de Campaign ont pour but de vous permettre **créer des intégrations** pour Adobe Campaign et **construire votre propre écosystème ;** en interfaçant Adobe Campaign avec le panneau des technologies que vous utilisez.

Avec les API REST Adobe Campaign, vous avez accès aux fonctionnalités suivantes :

<table><tr>
 <td valign="top"><a href="retrieving-profiles.md"><img width="60px" alt="conditions" src="assets/icon_profile.svg"/></a><p><a href="retrieving-profiles.md">Profils</a></p></td>
<td valign="top"><a href="creating-a-service.md"><img width="60px" alt="conditions" src="assets/icon_services.svg"/></a><p><a href="creating-a-service.md">Services et abonnements</a></p></td>
<td valign="top"><a href="interacting-with-custom-resources.md"><img width="60px" alt="conditions" src="assets/icon_customresources.svg"/></a><p><a href="interacting-with-custom-resources.md">Ressources personnalisées</a></p></td>
<td valign="top"><a href="controlling-a-workflow.md"><img width="60px" alt="conditions" src="assets/icon_workflows.svg"/></a><p><a href="controlling-a-workflow.md">Workflows</a></p></td>
</tr></table>

Pour utiliser les API REST Campaign, vous avez besoin d’un compte d’Adobe I/O. Il s’agit d’une première étape obligatoire pour découvrir les fonctionnalités des API.
Voir à ce propos [cette section](setting-up-api-access.md).

Les API fournies utilisent des **concepts standard** avec une interface REST et des payloads JSON.

Tous les points de terminaison sont décrits en détail dans cette documentation avec les notions générales que vous devez connaître pour manipuler l’API, les références d’API complètes, des exemples de code et des guides de démarrage rapide. Tous les exemples fonctionnent avec Postman, mais n’hésitez pas à utiliser votre client REST préféré.

S’il manque quelque chose ou si une information semble incorrecte, posez une question à la [communauté](https://experienceleaguecommunities.adobe.com/t5/adobe-campaign-standard/ct-p/adobe-campaign-standard-community).
