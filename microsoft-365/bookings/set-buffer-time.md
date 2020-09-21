---
title: Définir le temps de mémoire tampon dans les ouvrages Microsoft
ms.author: kwekua
author: kwekuako
manager: scotv
audience: Admin
ms.topic: article
ms.service: bookings
localization_priority: Normal
ms.assetid: 271f43e4-b8f7-4d63-8059-b5747679bb7e
description: Définir le temps de mémoire tampon avant ou après un rendez-vous dans Microsoft bookings pour autoriser le nettoyage ou la réinitialisation de l’équipement.
ms.openlocfilehash: 882ab0340fe56976429ed8294f2fa386b801941f
ms.sourcegitcommit: 7c0873d2a804f17697844fb13f1a100fabce86c4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2020
ms.locfileid: "47962346"
---
# <a name="set-buffer-time-in-microsoft-bookings"></a>Définir le temps de mémoire tampon dans les ouvrages Microsoft

Certains de vos rendez-vous peuvent nécessiter du temps avant ou après la réunion avec votre client pour configurer, nettoyer ou réinitialiser votre salle et votre équipement. Ou si vous êtes en déplacement entre les rendez-vous du client, vous aurez peut-être besoin de temps pour vous assurer que votre équipe et vous pouvez passer entre les rendez-vous sans faire attendre le client.

Vous pouvez définir le temps de mise en mémoire tampon avant le début des rendez-vous, après la fin des rendez-vous, ou les deux pour donner au personnel le temps supplémentaire nécessaire pour préparer leur prochain rendez-vous.

## <a name="set-buffer-time-defaults"></a>Définir les valeurs par défaut des temps de mise en mémoire tampon

Les valeurs par défaut de temps de mémoire tampon sont définies dans la page **Détails du service** dans bookings. Comme toutes les valeurs par défaut de service définies sur cette page, vous pouvez modifier ces paramètres par défaut pour une réservation spécifique afin de répondre à des besoins spécifiques du client.

Le paramètre de temps de la mémoire tampon se trouve juste en dessous des sélecteurs de **durée par défaut** sur la page des **Détails du service** . Avant de pouvoir la définir pour un service donné, vous devez activer le paramètre de temps de la mémoire tampon en sélectionnant le bouton bascule de temps de la mémoire tampon. Cela entraîne l’affichage des listes déroulantes **avant** et **après** , qui permettent de choisir la durée de conservation par défaut avant et après chaque réservation, comme illustré ci-dessous :

   ![Image de livres avec temps tampon activé](../media/bookings-buffertime.png)

## <a name="buffer-time-and-appointment-timing"></a>Temps de la mémoire tampon et synchronisation des rendez-vous

Pour éviter toute confusion sur le moment où les clients s’attendent à vous répondre, les réservations indiquent le temps de mise en mémoire tampon et l’heure du rendez-vous réel (le temps que vos clients attendent de se réunir) sur votre calendrier, ainsi que les confirmations de messagerie et les rappels pour le personnel concerné. Par exemple, vous trouverez ci-dessous les informations qui s’affichent dans les réservations pour un rendez-vous avec un client qui inclut 15 minutes de temps de mémoire tampon de pré-rendez-vous.

Notez que l’événement lui-même (à gauche dans l’image ci-dessous) affiche un ombrage plus clair pour le temps de mémoire tampon et un ombrage plus sombre pour le rendez-vous réel du client. Le rendez-vous (ouvert lorsque vous sélectionnez l’événement) indique spécifiquement que le rendez-vous est compris entre 9:00:00 et 10:00:00 avec Katie Jordanie et inclut 15 minutes de temps de mémoire tampon avant le rendez-vous et 0 minutes après le rendez-vous. Des confirmations et des rappels pour le personnel font référence à un tampon et un rendez-vous spécifiques de la même manière, tandis que le client ne peut obtenir que les confirmations et les rappels qui font référence à un 9:00:00 à 10:00:00 de rendez-vous.

   ![Image de l’appel de rendez-vous de livrets avec le temps de mémoire tampon affiché](../media/bookings-buffertime-callout.png)

## <a name="buffer-time-and-availability"></a>Temps et disponibilité des tampons

Vos clients ne voient pas directement et ne peuvent pas modifier les temps de mémoire tampon que vous avez définis. Toutefois, étant donné que le temps de la mémoire tampon est utilisé pour calculer la durée globale du service, les clients vous verront, ainsi que votre personnel concerné, enregistrés pendant les heures de la mémoire tampon et des rendez-vous réguliers. Les clients voient également uniquement la disponibilité pour vous et votre personnel s’il y a suffisamment de temps pour le rendez-vous et son temps de mémoire tampon.

Par exemple, un rendez-vous d’une heure avec une durée de mise en mémoire tampon de 15 minutes nécessite un bloc de temps disponible d’au moins 1 heure et 15 minutes. Un rendez-vous pour ce service occuperait donc un temps de 75 minutes sur votre calendrier et nécessitera 75 minutes de disponibilité pour livre sans conflit.
