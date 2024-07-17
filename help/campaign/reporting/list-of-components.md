---
title: Liste des composants
description: Cette section contient la liste de tous les composants disponibles dans les rapports dynamiques et leur définition.
level: Beginner
audience: end-user
badge: label="DISPONIBILITÉ LIMITÉE" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Limité aux utilisateurs migrés Campaign Standard"
exl-id: 5c58db92-7878-4c70-b076-a393f1cda8b7
source-git-commit: 34c6f8a137a9085b26c0ea8f78930cff6192cfc9
workflow-type: tm+mt
source-wordcount: '770'
ht-degree: 54%

---

# Liste des composants {#list-of-components}

Notez que si deux composants ne sont pas compatibles, la cellule affiche la valeur **None**.

## Dimensions {#dimensions}

Le tableau ci-dessous contient la liste des dimensions utilisées dans les rapports et leur définition.

<table> 
 <thead> 
  <tr> 
   <th> Dimension<br/> </th> 
   <th> Définition<br/> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Navigateur<br/> </td> 
   <td> Navigateur dans lequel le message a été ouvert ou a fait l’objet d’un clic.<br/> </td> 
  </tr> 
  <tr> 
   <td> Campaign<br/> </td> 
   <td> Libellé et identifiant de votre campagne.<br/> </td> 
  </tr> 
  <tr> 
   <td> Diffusion<br/> </td> 
   <td> Libellé et identifiant de la diffusion.<br/> </td> 
  </tr> 
  <tr> 
   <td> Appareil<br/> </td> 
   <td> Appareil sur lequel l’email/le SMS/la notification push ont été ouverts/vus ou ont fait l’objet d’un clic.<br/> </td> 
  </tr> 
  <tr> 
   <td> Raison de l'échec<br/> </td> 
   <td> Types d’erreurs qui provoquaient des rebonds pour chaque diffusion (par exemple : utilisateur inconnu, domaine non valide ou boîte pleine).<br/> </td> 
  </tr> 
  <tr> 
   <td> Nom de l’application mobile<br/> </td> 
   <td> Nom de l’application mobile.<br/> </td> 
  </tr>
  <tr> 
   <td> Plateforme<br/> </td> 
   <td> Plateforme de l’appareil sur lequel le message a été ouvert/vu ou a fait l’objet d’un clic.<br/> </td> 
  </tr> 
  <tr> 
   <td> Profil<br/> </td> 
   <td> Regroupe les champs de profil personnalisés et d'usine créés lors de l'extension de la ressource de profil.<br/> </td> 
  </tr> 
  <tr> 
   <td> Domaine du destinataire<br/> </td> 
   <td> Domaine utilisé pour ouvrir l’email.<br/> </td> 
  </tr> 
  <tr> 
   <td> Diffusion récurrente<br/> </td> 
   <td> Libellé et identifiant de la diffusion récurrente.<br/> </td> 
  </tr> 
  <tr> 
   <td> Domaine de l’expéditeur<br/> </td> 
   <td> Domaine utilisé pour envoyer l'email.<br/> </td> 
  </tr> 
  <tr> 
   <td> Adresse IP de l’expéditeur<br/> </td> 
   <td> IP utilisée pour envoyer l'email.<br/> </td> 
  </tr> 
  <tr> 
   <td> URL de tracking<br/> </td> 
   <td> URL sur laquelle a cliqué l’utilisateur dans le message.<br/> </td> 
  </tr> 
  <tr> 
   <td> Catégorie de l’URL de tracking<br/> </td> 
   <td> Catégorie affectée à l’URL de tracking.<br/> </td> 
  </tr> 
  <tr> 
   <td> Libellé de l’URL de tracking<br/> </td> 
   <td> Libellé attribué à l'URL (page miroir, contactez-nous ou ouvrir, par exemple).<br/> </td> 
  </tr> 
  <tr> 
   <td> Diffusion transactionnelle<br/> </td> 
   <td> Libellé et identifiant de la diffusion transactionnelle.<br/> </td> 
  </tr> 
  <tr> 
   <td> Variante<br/> </td> 
   <td> Variante de l’email en cas de test A/B.<br/> </td> 
  </tr> 
 </tbody> 
</table>

## Mesures {#metrics}

Les tableaux ci-dessous contiennent la liste des mesures utilisées dans les différents rapports et leur définition en fonction du type de diffusion.

### Mesures des emails {#email-and-sms-metrics}

<table> 
 <thead> 
  <tr> 
   <th> Mesure<br/> </th> 
   <th> Définition<br/> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Sur la liste bloquée<br/> </td> 
   <td> Nombre de destinataires ayant déclaré un email comme étant un spam ou un courrier indésirable.<br/> </td> 
  </tr> 
  <tr> 
   <td> Taux sur la liste bloquée<br/> </td> 
   <td> Pourcentage de diffusions marquées sur la liste bloquée.<br/> </td> 
  </tr> 
  <tr> 
   <td> Rebonds + erreurs<br/> </td> 
   <td> Nombre total d’erreurs cumulées lors des diffusions et du traitement automatique des retours par rapport au nombre total de messages envoyés.<br/> </td> 
  </tr> 
  <tr> 
   <td> Taux de rebond + erreurs<br/> </td> 
   <td> Pourcentage d'emails qui ont fait l'objet d'un bounce par rapport au nombre d'emails envoyés.<br/> </td> 
  </tr> 
  <tr> 
   <td> Clics<br/> </td> 
   <td> Nombre de clics sur un contenu dans une diffusion.<br/> </td> 
  </tr> 
  <tr> 
   <td> Taux de clics<br/> </td> 
   <td> Pourcentage de clics dans une diffusion.<br/> </td> 
  </tr> 
  <tr> 
   <td> Diffusés<br/> </td> 
   <td> Nombre de messages envoyés avec succès, par rapport au nombre total de messages envoyés.<br/> </td> 
  </tr> 
  <tr> 
   <td> Taux de délivrabilité<br/> </td> 
   <td> Pourcentage de messages envoyés avec succès.<br/> </td> 
  </tr> 
  <tr> 
   <td> Rebond définitif<br/> </td> 
   <td> Nombre total d’erreurs permanentes, telles qu’une adresse email incorrecte.<br/> </td> 
  </tr> 
  <tr> 
   <td> Taux de rebond définitif<br/> </td> 
   <td> Pourcentage de diffusions ayant échoué en raison d'erreurs permanentes.<br/> </td> 
  </tr> 
  <tr> 
   <td> Page miroir<br/> </td> 
   <td> Nombre de destinataires ayant cliqué sur le lien de la page miroir.<br/> </td> 
  </tr> 
  <tr> 
   <td> Taux de page miroir<br/> </td> 
   <td> Pourcentage de clics sur le lien de la page miroir par rapport au nombre total de messages de diffusion.<br/> </td> 
  </tr> 
  <tr> 
   <td> Clics sur l’offre<br/> </td> 
   <td> Nombre de clics sur une offre dans une diffusion.<br/> </td> 
  </tr> 
  <tr> 
   <td> Taux de clics sur les offres<br/> </td> 
   <td> Pourcentage de clics sur une offre.<br/> </td> 
  </tr> 
  <tr> 
   <td> Ouvertures<br/> </td> 
   <td> Nombre d'ouvertures d'un message dans une diffusion.<br/> </td> 
  </tr> 
  <tr> 
   <td> Taux d'ouverture<br/> </td> 
   <td> Pourcentage de messages ouverts.<br/> </td> 
  </tr> 
  <tr> 
   <td> Traités/envoyés<br/> </td> 
   <td> Nombre total d’envois pour la diffusion.<br/> </td> 
  </tr> 
  <tr> 
   <td> Quarantaine<br/> </td> 
   <td> Nombre de messages qui ont fait l’objet d’un rebond et qui ont entraîné la mise en quarantaine de l’adresse.<br/> </td> 
  </tr> 
  <tr> 
   <td> Taux de mise en quarantaine<br/> </td> 
   <td> Pourcentage de mises en quarantaine par rapport au nombre de messages envoyés.<br/> </td> 
  </tr> 
  <tr> 
   <td> Rejetés<br/> </td> 
   <td> Nombre de messages classés comme spam par les serveurs SMTP.<br/> </td> 
  </tr> 
  <tr> 
   <td> Taux de rejet<br/> </td> 
   <td> Pourcentage de messages marqués comme rejetés.<br/> </td> 
  </tr> 
  <tr> 
   <td> Rebond temporaire<br/> </td> 
   <td> Nombre total d’erreurs temporaires, telles qu’une boîte de réception pleine.<br/> </td> 
  </tr> 
  <tr> 
   <td> Taux de rebonds temporaires<br/> </td> 
   <td> Pourcentage de diffusions ayant échoué pour une raison temporaire.<br/> </td> 
  </tr> 
  <tr> 
   <td> Clics uniques<br/> </td> 
   <td> Nombre de destinataires ayant cliqué sur un contenu dans une diffusion.<br/> </td> 
  </tr> 
  <tr> 
   <td> Ouvertures uniques<br/> </td> 
   <td> Nombre de destinataires ayant ouvert la diffusion.<br/> </td> 
  </tr> 
  <tr> 
   <td> Désabonnement unique<br/> </td> 
   <td> Nombre de destinataires ayant cliqué sur le lien de désabonnement.<br/> </td> 
  </tr> 
  <tr> 
   <td> Taux de désabonnement<br/> </td> 
   <td> Nombre de désbonnements uniques par rapport aux messages délivrés.<br/> </td> 
  </tr> 
  <tr> 
   <td> Désabonnement<br/> </td> 
   <td> Nombre de clics sur le lien de désabonnement.<br/> </td> 
  </tr> 
 </tbody> 
</table>

<!--
### Push notification metrics {#push-notification-metrics}

<table> 
 <thead> 
  <tr> 
   <th> Metric<br/> </th> 
   <th> Definition<br/> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Bounces + Errors<br/> </td> 
   <td> Total of errors cumulated during delivery in relation to the total number of sent messages, e.g. errors from MCPNS or provider.<br/> </td> 
  </tr> 
  <tr> 
   <td> Bounce + Error rate<br/> </td> 
   <td> Percentage of push notifications that bounced compared to push notifications sent.<br/> </td> 
  </tr> 
  <tr> 
   <td> Click<br/> </td> 
   <td> Number of times a push notification has been delivered to the device and clicked on by the user. The user either wanted to view the notification, which will then be moved to Push Open tracking, or dismiss it.<br/> </td> 
  </tr> 
  <tr> 
   <td> Click through rate<br/> </td> 
   <td> Percentage of users who interacted with the push notification.<br/> </td> 
  </tr> 
  <tr> 
   <td> Delivered<br/> </td> 
   <td> Number of push notifications successfully sent, in relation to the total number of sent push notifications.<br/> </td> 
  </tr> 
  <tr> 
   <td> Delivered rate<br/> </td> 
   <td> Percentage of push notifications successfully sent.<br/> </td> 
  </tr> 
  <tr> 
   <td> Impressions<br/> </td> 
   <td> Number of times a push notification has been delivered to the device and left untouched in the notification center. In most cases, impressions number should be similar to the delivered number. This ensures that the device got the message and relayed that information back to the server.<br/> </td> 
  </tr> 
  <tr> 
   <td> Processed/sent<br/> </td> 
   <td> Total number of push notifications sent.<br/> </td> 
  </tr> 
  <tr> 
   <td> Open<br/> </td> 
   <td> Total number of push notifications delivered to the device and clicked on by users thus opening the app. This is similar to the Push Click except a Push Open will not be triggered if the notification was dismissed.<br/> </td> 
  </tr> 
  <tr> 
   <td> Open rate<br/> </td> 
   <td> Percentage of opened push notifications.<br/> </td> 
  </tr> 
  <tr> 
   <td> Unique clicks<br/> </td> 
   <td> Number of times a unique user interacts with the push notification, e.g. clicks on the notification or button.<br/> </td> 
  </tr> 
  <tr> 
   <td> Unique impressions<br/> </td> 
   <td> Number of impressions by recipient.<br/> </td> 
  </tr> 
  <tr> 
   <td> Unique Opens<br/> </td> 
   <td> Number of recipients who opened the delivery.<br/> </td> 
  </tr> 
 </tbody> 
</table>

### In-App metrics {#in-app-metrics}

<table> 
 <thead> 
  <tr> 
   <th> Metric<br/> </th> 
   <th> Definition<br/> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Delivered<br/> </td> 
   <td> Total number of In-App messages delivered to the device by the service provider.<br/> </td> 
  </tr> 
  <tr> 
   <td> Impressions<br/> </td> 
   <td> Total of In-App messages seen by recipients depending on whether trigger criterion was met.<br/> </td> 
  </tr> 
  <tr> 
   <td> In-App clicks <br/> </td> 
   <td> Total number of recipients who clicked on Button 1 or Button 2.<br/> </td> 
  </tr> 
  <tr> 
   <td> In-App click through rate<br/> </td> 
   <td> Percentage of users who clicked on Button 1 or Button 2 compared to users who saw the message.<br/> </td> 
  </tr> 
  <tr> 
   <td> In-App dismissal<br/> </td> 
   <td> Total number of messages that recipients dismissed either by clicking the close button or auto-dismiss.<br/> </td> 
  </tr> 
  <tr> 
   <td> In-App dismissal rate<br/> </td> 
   <td> Percentage of In-App messages that recipients dismissed.<br/> </td> 
  </tr> 
  <tr> 
   <td> Processed/sent<br/> </td> 
   <td> Total number of In-App messages sent from Adobe Campaign as part of the delivery sent process.<br/> </td> 
  </tr> 
  <tr> 
   <td> Unique impressions<br/> </td> 
   <td> Number of impressions by a unique recipient.<br/> </td> 
  </tr> 
  <tr> 
   <td> Unique In-App clicks<br/> </td> 
   <td> Number of times recipients clicked on Button 1 or Button 2.<br/> </td> 
  </tr> 
  <tr> 
   <td> Unique In-App dismissals<br/> </td> 
   <td> Number of time recipients dismissed an In-App message.<br/> </td> 
  </tr> 
 </tbody> 
</table>
-->

## Segments {#segments}

Le tableau ci-dessous contient la liste des segments utilisés dans les rapports et leur définition.

<table> 
 <thead> 
  <tr> 
   <th> Segment<br/> </th> 
   <th> Définition<br/> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Age : baby boomers 1<br/> </td> 
   <td> Destinataires nés entre 1946 et 1954.<br/> </td> 
  </tr> 
  <tr> 
   <td> Age : baby boomers 2<br/> </td> 
   <td> Destinataires nés entre 1955 et 1965.<br/> </td> 
  </tr> 
  <tr> 
   <td> Age : de 18 à 25<br/> </td> 
   <td> Destinataires âgés de 18 à 25 ans.<br/> </td> 
  </tr> 
  <tr> 
   <td> Age : de 26 à 30<br/> </td> 
   <td> Destinataires âgés de 26 à 30 ans.<br/> </td> 
  </tr> 
  <tr> 
   <td> Age : de 31 à 40<br/> </td> 
   <td> Destinataires âgés de 31 à 40 ans.<br/> </td> 
  </tr> 
  <tr> 
   <td> Age : de 41 à 50<br/> </td> 
   <td> Destinataires âgés de 41 à 50 ans.<br/> </td> 
  </tr> 
  <tr> 
   <td> Age : génération X<br/> </td> 
   <td> Destinataires nés entre 1966 et 1976.<br/> </td> 
  </tr> 
  <tr> 
   <td> Age : génération Y (enfants du millénaire)<br/> </td> 
   <td> Destinataires nés entre 1977 et 1994.<br/> </td> 
  </tr> 
  <tr> 
   <td> Age : génération Z<br/> </td> 
   <td> Destinataires nés entre 1995 et aujourd'hui.<br/> </td> 
  </tr> 
  <tr> 
   <td> Age : plus de 50<br/> </td> 
   <td> Destinataires dont l'âge est supérieur à 50.<br/> </td> 
  </tr> 
  <tr> 
   <td> Age : moins de 25<br/> </td> 
   <td> Destinataires dont l'âge est inférieur à 25 ans.<br/> </td> 
  </tr> 
  <tr> 
   <td> Age : moins de 30<br/> </td> 
   <td> Destinataires dont l'âge est inférieur à 30 ans.<br/> </td> 
  </tr> 
  <tr> 
   <td> Age : moins de 40<br/> </td> 
   <td> Destinataires dont l'âge est inférieur à 40 ans.<br/> </td> 
  </tr> 
  <tr> 
   <td> Age : moins de 50<br/> </td> 
   <td> Destinataires dont l'âge est inférieur à 50 ans.<br/> </td> 
  </tr> 
  <tr> 
   <td> Age : génération silencieuse<br/> </td> 
   <td> Destinataires nés en 1945 ou avant.<br/> </td> 
  </tr> 
  <tr> 
   <td> Toutes les visites <br/> </td> 
   <td> Chaque destinataire<br/> </td> 
  </tr>
 </tbody> 
</table>
