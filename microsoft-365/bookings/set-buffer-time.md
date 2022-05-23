---
title: Définir Bookings durée de la mémoire tampon
ms.author: kwekua
author: kwekuako
manager: scotv
audience: Admin
ms.topic: article
ms.service: bookings
ms.localizationpriority: medium
ms.assetid: 271f43e4-b8f7-4d63-8059-b5747679bb7e
description: Définissez la durée de la mémoire tampon avant ou après un rendez-vous dans Microsoft Bookings pour laisser le temps de nettoyer ou de réinitialiser l’équipement.
ms.openlocfilehash: 49e58d53cec466c824a40281e3199f1544e74744
ms.sourcegitcommit: db1e48af88995193f15bbd5962f5101a6088074b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2022
ms.locfileid: "65637580"
---
# <a name="set-buffer-time-in-microsoft-bookings"></a>Définir la durée de la mémoire tampon dans Microsoft Bookings

Certains de vos rendez-vous peuvent nécessiter du temps avant ou après avoir rencontré votre client pour configurer, nettoyer ou réinitialiser votre chambre et votre équipement. Ou si vous êtes sur la route entre les rendez-vous client, vous aurez peut-être besoin de temps pour vous assurer que vous et votre équipe pouvez voyager entre les rendez-vous sans faire attendre le client.

Vous pouvez définir la durée de la mémoire tampon avant le début des rendez-vous, après la fin des rendez-vous, ou les deux pour donner au personnel le temps supplémentaire dont il a besoin pour préparer son prochain rendez-vous.

## <a name="set-buffer-time-defaults"></a>Définir les valeurs par défaut du temps de mémoire tampon

Les valeurs par défaut du temps de mémoire tampon sont définies sur la page **détails du service** dans Bookings. Comme toutes les valeurs par défaut de service définies sur cette page, ces valeurs par défaut peuvent être modifiées par vous pour une réservation spécifique afin de répondre aux besoins spécifiques des clients.

Le paramètre de durée de la mémoire tampon se trouve dans la page **des détails du service** . Pour qu’il puisse être défini pour un service donné, vous devez activer le paramètre d’heure de la mémoire tampon en sélectionnant le basculement de l’heure de la mémoire tampon. Cela entraîne l’affichage des listes déroulantes **Avant** et **Après** , qui sont utilisées pour choisir la durée par défaut à conserver avant et après chaque réservation, comme indiqué ici :

   ![Image de Bookings avec le temps de mémoire tampon activé.](../media/bookings-buffertime.png)

<!--## Buffer time and appointment timing

To avoid confusion about when customers expect to meet with you, Bookings shows buffer time and actual appointment time (the time your customers expect to meet with you) on your calendar, and in email confirmations and reminders to relevant staff. For example, below is what you’d see in Bookings for an appointment with a customer that includes 15 minutes of pre-appointment buffer time.

Note that the event itself (on the left in the image below) shows lighter shading for the buffer time and darker shading for the actual customer appointment. The appointment call-out (which is opened when you select the event) specifically states that the appointment is from 9:00AM to 10:00AM with Katie Jordan and includes 15 minutes of buffer time before the appointment and 0 minutes after the appointment. Confirmations and reminders to staff similarly reference specific buffer and appointment time while the customer would only get confirmations and reminders that reference a 9:00AM to 10:00AM appointment time.

   ![Image of Bookings appointment call-out with buffer time showing.](../media/bookings-buffertime-callout.png)
-->

## <a name="buffer-time-and-availability"></a>Durée et disponibilité de la mémoire tampon

Vos clients ne voient pas directement et ne peuvent pas modifier les temps de mémoire tampon que vous définissez. Toutefois, étant donné que le temps de la mémoire tampon est utilisé pour calculer la durée globale du service, les clients verront que vous et votre personnel concerné êtes réservé pendant les périodes de rendez-vous tampon et régulières. Les clients voient également la disponibilité pour vous et votre personnel uniquement s’il y a suffisamment de temps pour le rendez-vous et son temps de mémoire tampon.

Par exemple, un rendez-vous d’une heure avec une durée de mémoire tampon de 15 minutes avant rendez-vous nécessite un bloc de temps disponible d’au moins 1 heure et 15 minutes. Un rendez-vous pour ce service remplirait donc un bloc de temps de 75 minutes sur votre calendrier et aurait besoin de 75 minutes de disponibilité pour réserver sans conflit.
