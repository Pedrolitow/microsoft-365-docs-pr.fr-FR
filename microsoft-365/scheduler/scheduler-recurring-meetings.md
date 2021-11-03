---
title: Planification de réunions périodiques dynamiques
ms.author: sarichardson
author: sallyri
manager: serdars
audience: Admin
ms.topic: article
ms.service: scheduler
ms.reviewer: strettin
ms.localizationpriority: medium
description: Les utilisateurs peuvent en savoir plus sur la planification de réunions périodiques dynamiques.
ms.openlocfilehash: d4f99b336088e7c565c741a8f631e4fefbada68f
ms.sourcegitcommit: bf3965b46487f6f8cf900dd9a3af8b213a405989
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2021
ms.locfileid: "60701328"
---
# <a name="scheduling-dynamic-recurring-meetings"></a>Planification de réunions périodiques dynamiques

Les réunions dynamiques du scheduler fonctionnent selon les horaires occupés de l’utilisateur. Les réunions périodiques gérées par le Scheduler se comportent différemment des réunions périodiques classiques dans Outlook. Pour maintenir votre calendrier à venir ouvert et minimiser les conflits avec les participants, scheduler planifiera une instance d’une réunion périodique à la fois.

Par exemple, le fait de demander Cortana « Planifier 30 minutes de temps de travail focus tous les jours » crée initialement un rendez-vous de 30 minutes pour la prochaine date disponible dans votre calendrier.  Une fois cette heure de rendez-vous passée, le scheduler procède à la réservation d’une autre instance à la date suivante. Si le créneau horaire d’origine n’est pas disponible actuellement, le Scheduler ajuste l’heure en fonction de votre disponibilité.

La même heuristique peut être appliquée aux réunions avec des invités. Vous pouvez inclure des participants dans votre demande et demander Cortana « Planifier une réunion toutes les deux semaines ». La première réunion et chaque réunion successive sont programmées dynamiquement en fonction de la disponibilité actuelle de tous les participants au sein de votre organisation. Si vous ou un participant n’êtes pas disponible ou absent du bureau à la prochaine date, l’heure de la réunion s’ajuste automatiquement lorsque tout le monde est disponible et la cadence souhaitée est conservée pour les instances de réunion de suivi en fonction de la date nouvellement prévue.

## <a name="booking-with-attendees-outside-your-organization"></a>Réservation avec des participants extérieurs à votre organisation

Lors de la planification avec des participants extérieurs à votre organisation, votre assistant virtuel envoie les options de temps des participants externes pour la première réunion. Toutes les réunions futures sont automatiquement programmées en fonction de la disponibilité de l’organisateur et des participants internes.

Le programme de planification prend en charge les intervalles quotidiens, hebdomadaires et mensuels.

## <a name="examples-of-how-to-request-recurring-meetings"></a>Exemples de demande de réunions périodiques

Voici quelques exemples de la façon dont vous pouvez envoyer des Cortana pour planifier des réunions périodiques :

- « Cortana, planifier une réunion toutes les 2 semaines. »
- « Réservez 30 minutes par mois pour un avis. »
- « Cortana nous trouverons 30 minutes pour nous réunir tous les mardis. »
- « Cortana, planifier 30 minutes tous les vendredis à 15h30 »

## <a name="changing-recurring-frequency"></a>Modification de la fréquence périodique

Vous pouvez modifier la fréquence d’une réunion périodique ou d’une réunion non périodique gérée par le Programmeur. Répondez aux Cortana du dernier e-mail de confirmation dans le thread de réunion et Cortana :

- « Modifiez cette étape pour qu’elle soit une fois par mois. »
- « Cortana, rendez cette réunion tous les deux semaines. »

## <a name="cancelling-recurring-meetings"></a>Annulation de réunions périodiques

Vous pouvez répondre au dernier message de confirmation Cortana et demander d’annuler cette réunion pour annuler l’instance programmée. Toutefois, le scheduler continuera à planifier de futures réunions à la même fréquence. Vous pouvez également demander au Scheduler de reprogrammer l’instance suivante à la date ou à l’heure souhaitée. Si vous souhaitez annuler l’intégralité de la série périodique, répondez par « annuler cette série » et aucune instance future ne sera programmée.

## <a name="recurring-meeting-limitations"></a>Limitations de réunion périodique

Veuillez noter qu’il existe certaines limitations techniques sur les types de récurrences que le Scheduler peut comprendre et prendre en charge :

- Plusieurs occurrences dans le même intervalle ne sont pas pris en charge (par exemple : « deux fois par semaine »).
- Les dates de fin de la récurrence ne sont pas pris en charge (par exemple : « tous les jours jusqu’au 20 décembre »). Étant donné que chaque réunion est programmée à la fin de la réunion précédente, il vous suffit de répondre au dernier message de Cortana en « annuler cette série de réunions ».
- Le programme de planification ne prend actuellement pas en charge les fréquences de récurrence supérieure à 90 jours.
