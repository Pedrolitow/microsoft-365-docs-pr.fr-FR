---
title: Définir l’heure tampon dans Microsoft Bookings
ms.author: kwekua
author: kwekuako
manager: scotv
audience: Admin
ms.topic: article
ms.service: bookings
localization_priority: Normal
ms.assetid: 271f43e4-b8f7-4d63-8059-b5747679bb7e
description: Définissez l’heure tampon avant ou après un rendez-vous dans Microsoft Bookings pour laisser le temps de nettoyer ou de réinitialiser l’équipement.
ms.openlocfilehash: 932dc842b5e81589c4120bf23e53c5d66709830053879a67e30468e72eb4e4b7
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53838106"
---
# <a name="set-buffer-time-in-microsoft-bookings"></a>Définir l’heure tampon dans Microsoft Bookings

Certains de vos rendez-vous peuvent nécessiter un certain temps avant ou après avoir rencontré votre client pour configurer, nettoyer ou réinitialiser votre salle et votre équipement. Ou si vous êtes en déplacement entre des rendez-vous client, vous aurez peut-être besoin de temps pour vous assurer que vous et votre équipe pouvez vous déplacer entre les rendez-vous sans que le client attende.

Vous pouvez définir l’heure tampon avant le début des rendez-vous, après la fin des rendez-vous, ou les deux pour donner au personnel le temps supplémentaire dont il a besoin pour préparer son prochain rendez-vous.

## <a name="set-buffer-time-defaults"></a>Définir les valeurs par défaut de l’heure de mémoire tampon

Les valeurs par défaut de l’heure tampon sont définies dans la page **Détails du service** dans Bookings. Comme toutes les valeurs par défaut de service définies sur cette page, ces valeurs par défaut peuvent être modifiées par vous pour une réservation spécifique afin de répondre aux besoins spécifiques du client.

Le paramètre de durée de la mémoire tampon se trouve juste en dessous **des** s sélectionneurs de durée par défaut dans la page **Détails du** service. Avant de pouvoir la définir pour un service donné, vous devez activer le paramètre de temps tampon en sélectionnant le basculement de l’heure de mémoire tampon. Cela entraîne l’apparition des drop-downs **Avant** et Après, qui sont utilisées pour sélectionner le délai de attente par défaut avant et après chaque réservation, comme illustré ici : 

   ![Image de Bookings avec l’heure tampon activée](../media/bookings-buffertime.png)

## <a name="buffer-time-and-appointment-timing"></a>Heure de la mémoire tampon et minutage des rendez-vous

Pour éviter toute confusion quant au moment où les clients s’attendent à vous rencontrer, Bookings affiche l’heure de la mémoire tampon et l’heure de rendez-vous réelle (heure à l’avance pour vos clients) sur votre calendrier, ainsi que dans des confirmations et rappels par courrier électronique au personnel approprié. Par exemple, voici ce que vous voyez dans Bookings pour un rendez-vous avec un client qui inclut 15 minutes de temps tampon avant rendez-vous.

Notez que l’événement lui-même (à gauche dans l’image ci-dessous) affiche une ombre plus claire pour l’heure de la mémoire tampon et une ombre plus sombre pour le rendez-vous client réel. La sortie de rendez-vous (qui est ouverte lorsque vous sélectionnez l’événement) indique spécifiquement que le rendez-vous est compris entre 9 h 00 et 10 h 00 avec Katie Jordan et inclut 15 minutes de temps tampon avant le rendez-vous et 0 minute après le rendez-vous. Les confirmations et rappels au personnel font de même référence à une mémoire tampon et une heure de rendez-vous spécifiques, tandis que le client reçoit uniquement des confirmations et rappels qui font référence à une heure de rendez-vous de 9 h 00 à 10 h 00.

   ![Image de la sortie de téléphone du rendez-vous Bookings avec l’heure tampon montrant](../media/bookings-buffertime-callout.png)

## <a name="buffer-time-and-availability"></a>Temps et disponibilité de la mémoire tampon

Vos clients ne voient pas directement et ne peuvent pas modifier les heures de mémoire tampon que vous avez définies. Toutefois, étant donné que l’heure tampon est utilisée pour calculer la durée globale du service, les clients voient que vous et votre personnel pertinent êtes réservé à la fois pendant les heures de tampon et de rendez-vous ordinaires. Les clients voient également uniquement la disponibilité pour vous et votre personnel s’il y a suffisamment de temps pour le rendez-vous et son heure tampon.

Par exemple, un rendez-vous d’une heure avec une durée tampon de 15 minutes avant rendez-vous nécessite un bloc de temps disponible d’au moins 1 heure et 15 minutes. Un rendez-vous pour ce service remplirait par conséquent un bloc de temps de 75 minutes sur votre calendrier et nécessite 75 minutes de disponibilité pour la réservation sans conflit.
