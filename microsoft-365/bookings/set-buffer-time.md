---
title: Définir l’heure tampon dans Microsoft Bookings
ms.author: kwekua
author: kwekuako
manager: scotv
audience: Admin
ms.topic: article
ms.service: bookings
ms.localizationpriority: medium
ms.assetid: 271f43e4-b8f7-4d63-8059-b5747679bb7e
description: Définissez l’heure tampon avant ou après un rendez-vous dans Microsoft Bookings pour laisser le temps de nettoyer ou de réinitialiser l’équipement.
ms.openlocfilehash: a33159b0b5f168bbb61c88bc9b4181e05c8abbb1
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63329318"
---
# <a name="set-buffer-time-in-microsoft-bookings"></a>Définir l’heure tampon dans Microsoft Bookings

Certains de vos rendez-vous peuvent nécessiter un certain temps avant ou après avoir rencontré votre client pour configurer, nettoyer ou réinitialiser votre salle et votre équipement. Ou si vous êtes en déplacement entre des rendez-vous client, vous aurez peut-être besoin de temps pour vous assurer que vous et votre équipe pouvez vous déplacer entre les rendez-vous sans que le client attende.

Vous pouvez définir l’heure tampon avant le début des rendez-vous, après la fin des rendez-vous, ou les deux pour donner au personnel le temps supplémentaire dont il a besoin pour préparer son prochain rendez-vous.

## <a name="set-buffer-time-defaults"></a>Définir les valeurs par défaut de l’heure de mémoire tampon

Les valeurs par défaut de l’heure de la mémoire tampon sont définies dans la page **Détails du service** dans Bookings. Comme toutes les valeurs par défaut de service définies sur cette page, ces valeurs par défaut peuvent être modifiées par vous pour une réservation spécifique afin de répondre aux besoins spécifiques du client.

Le paramètre de durée de la mémoire tampon se trouve juste en dessous **des s** sélectionneurs de durée par défaut dans la page **Détails du** service. Avant de pouvoir la définir pour un service donné, vous devez activer le paramètre de temps tampon en sélectionnant le basculement de l’heure de mémoire tampon. Cela entraîne l’apparition  des drop-downs **Avant** et Après, qui sont utilisées pour sélectionner le délai de attente par défaut avant et après chaque réservation, comme illustré ici :

   ![Image de Bookings avec l’heure tampon activée.](../media/bookings-buffertime.png)

<!--## Buffer time and appointment timing

To avoid confusion about when customers expect to meet with you, Bookings shows buffer time and actual appointment time (the time your customers expect to meet with you) on your calendar, and in email confirmations and reminders to relevant staff. For example, below is what you’d see in Bookings for an appointment with a customer that includes 15 minutes of pre-appointment buffer time.

Note that the event itself (on the left in the image below) shows lighter shading for the buffer time and darker shading for the actual customer appointment. The appointment call-out (which is opened when you select the event) specifically states that the appointment is from 9:00AM to 10:00AM with Katie Jordan and includes 15 minutes of buffer time before the appointment and 0 minutes after the appointment. Confirmations and reminders to staff similarly reference specific buffer and appointment time while the customer would only get confirmations and reminders that reference a 9:00AM to 10:00AM appointment time.

   ![Image of Bookings appointment call-out with buffer time showing.](../media/bookings-buffertime-callout.png)
-->

## <a name="buffer-time-and-availability"></a>Temps et disponibilité de la mémoire tampon

Vos clients ne voient pas directement et ne peuvent pas modifier les heures tampons que vous avez définies. Toutefois, étant donné que l’heure tampon est utilisée pour calculer la durée globale du service, les clients voient que vous et votre personnel pertinent êtes réservé à la fois pendant les heures de tampon et de rendez-vous ordinaires. Les clients voient également uniquement la disponibilité pour vous et votre personnel s’il y a suffisamment de temps pour le rendez-vous et son heure tampon.

Par exemple, un rendez-vous d’une heure avec une durée tampon de 15 minutes avant rendez-vous nécessite un bloc de temps disponible d’au moins 1 heure et 15 minutes. Un rendez-vous pour ce service remplirait donc un bloc de temps de 75 minutes sur votre calendrier et nécessite 75 minutes de disponibilité pour la réservation sans conflit.
