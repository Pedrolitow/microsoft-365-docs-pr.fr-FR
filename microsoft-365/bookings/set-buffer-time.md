---
title: Définir la durée de la mémoire tampon Bookings
ms.author: kwekua
author: kwekuako
manager: scotv
audience: Admin
ms.topic: article
ms.service: bookings
ms.localizationpriority: medium
ms.collection:
- Tier1
- scotvorg
ms.assetid: 271f43e4-b8f7-4d63-8059-b5747679bb7e
description: Définissez la durée de la mémoire tampon avant ou après un rendez-vous dans Microsoft Bookings afin de laisser le temps nécessaire au nettoyage ou à la réinitialisation de l’équipement.
ms.openlocfilehash: 02586ff6ad6d1676c4a596a4eca6eb98959c4005
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68726528"
---
# <a name="set-buffer-time-in-microsoft-bookings"></a>Définir la durée de la mémoire tampon dans Microsoft Bookings

Certains de vos rendez-vous peuvent nécessiter du temps avant ou après votre rencontre avec votre client pour configurer, nettoyer ou réinitialiser votre salle et votre équipement. Ou si vous êtes en déplacement entre les rendez-vous clients, vous aurez peut-être besoin de temps pour vous assurer que votre équipe et vous-même pouvez voyager entre les rendez-vous sans faire attendre le client.

Vous pouvez définir une durée de mémoire tampon avant le début des rendez-vous, après la fin des rendez-vous, ou les deux pour donner au personnel le temps supplémentaire dont il a besoin pour se préparer à son prochain rendez-vous.

## <a name="set-buffer-time-defaults"></a>Définir les valeurs par défaut du temps de mémoire tampon

Les valeurs par défaut du temps de mémoire tampon sont définies dans la page **Détails du service** dans Bookings. Comme toutes les valeurs par défaut de service définies sur cette page, ces valeurs par défaut peuvent être modifiées par vous-même pour une réservation spécifique afin de répondre aux besoins spécifiques des clients.

Le paramètre de temps de mémoire tampon se trouve dans la page **Détails du service** . Avant de pouvoir être défini pour un service donné, vous devez activer le paramètre de temps de mémoire tampon en sélectionnant le bouton bascule durée de la mémoire tampon. Cela entraîne l’affichage des listes déroulantes **Avant** et **Après** , qui sont utilisées pour choisir la durée par défaut de conservation avant et après chaque réservation, comme illustré ici :

   ![Image de Bookings avec le temps de mémoire tampon activé.](../media/bookings-buffertime.png)

<!--## Buffer time and appointment timing

To avoid confusion about when customers expect to meet with you, Bookings shows buffer time and actual appointment time (the time your customers expect to meet with you) on your calendar, and in email confirmations and reminders to relevant staff. For example, below is what you’d see in Bookings for an appointment with a customer that includes 15 minutes of pre-appointment buffer time.

Note that the event itself (on the left in the image below) shows lighter shading for the buffer time and darker shading for the actual customer appointment. The appointment call-out (which is opened when you select the event) specifically states that the appointment is from 9:00AM to 10:00AM with Katie Jordan and includes 15 minutes of buffer time before the appointment and 0 minutes after the appointment. Confirmations and reminders to staff similarly reference specific buffer and appointment time while the customer would only get confirmations and reminders that reference a 9:00AM to 10:00AM appointment time.

   ![Image of Bookings appointment call-out with buffer time showing.](../media/bookings-buffertime-callout.png)
-->

## <a name="buffer-time-and-availability"></a>Temps et disponibilité de la mémoire tampon

Vos clients ne voient pas directement et ne peuvent pas modifier les temps de mémoire tampon que vous définissez. Toutefois, étant donné que le temps de mémoire tampon est utilisé pour calculer la durée globale du service, les clients vous voient, ainsi que votre personnel concerné, comme réservé pendant les heures de rendez-vous régulières et pendant la mémoire tampon. Les clients voient également la disponibilité pour vous et votre personnel uniquement s’il y a suffisamment de temps pour le rendez-vous et son temps de mémoire tampon.

Par exemple, un rendez-vous d’une heure avec un temps tampon de pré-rendez-vous de 15 minutes nécessite un bloc de temps disponible d’au moins 1 heure et 15 minutes. Un rendez-vous pour ce service remplirait donc un bloc de temps de 75 minutes sur votre calendrier et nécessite 75 minutes de disponibilité pour réserver sans conflit.
