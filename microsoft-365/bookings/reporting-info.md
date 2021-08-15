---
title: Informations de rapport pour Microsoft bookings
ms.author: kwekua
author: kwekuako
manager: scotv
audience: Admin
ms.topic: article
ms.service: bookings
localization_priority: Normal
ms.assetid: 03a9acc9-f29c-456b-9fb2-0f49474b2708
description: Découvrez comment afficher une vue de 4 mois de votre activité Bookings
ms.openlocfilehash: 8fc8a41a982135550ae711e435905c9bd39460994b1f6757b633aea49a7a48a0
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53838202"
---
# <a name="reporting-info-for-bookings"></a>Informations de rapport pour Bookings

Vous pouvez maintenant voir une vue de quatre mois de votre calendrier Bookings dans un fichier TSV. Le fichier TSV affiche quatre mois de données, mais vous pouvez sélectionner différentes périodes de quatre mois au cours d’une année.

Ces informations de niveau de rendez-vous peuvent être utilisées pour visualiser l’activité des clients autour de votre calendrier Bookings. Les fichiers TSV sont des fichiers de valeurs séparées par des onglets. Vous pouvez afficher ou modifier un fichier comme celui-ci à l’aide d’un éditeur de texte ou d’un programme de feuilles de calcul, Excel.

## <a name="see-four-months-of-booking-activity"></a>Voir quatre mois d’activité de réservation

1. Dans le tableau de bord du calendrier Bookings, **sélectionnez Exporter plus de données en tant que TSV.**

:::image type="content" source="../media/bookings-activities.png" alt-text="Capture d’écran : 4 mois d’activité Bookings":::

1. Enregistrez le fichier sous un nouveau nom et spécifiez le format .xls ou xlsx.

1. Ouvrez le fichier pour afficher l’affichage de quatre mois de votre calendrier Bookings.

1. Choisissez la date de votre rapport et sélectionnez **Exporter.**

:::image type="content" source="../media/bookings-reporting-dates.png" alt-text="Screenshot: Pick a time range and export data to TSV file.":::

1. Le rapport téléchargé contient un nouvel ensemble de champs en plus des champs existants.

Le rapport inclut les champs suivants.

 - **Date Heure**
- **Nom du client**
- **Courrier électronique client**
- **Client Téléphone**
- **Adresse du client**
- **Personnel**
- **Service**
- **Emplacement**
- **Durée (minutes)**
- **Type d’événement**

Le rapport amélioré contient désormais les champs suivants.

- **Type de tarification**   Type de tarification par défaut pour un service lors de la création du service.
- **Prix**   Prix correspondant au type de tarification choisi.
- **Devise**   Type de devise pour une entreprise.
- **Participants Cc**   Destinataires qui reçoivent les notifications par courrier électronique pour une réservation. Cela peut être spécifié à partir de l’application Teams lors de la création d’une réservation.
- **Nombre de participants inscrits**   Nombre de clients qui ont réservé un service de réservation de groupe.
- **Notifications texte activées**   Si les clients peuvent recevoir des notifications textuelles SMS.
- **Champs personnalisés**   Toutes les questions et réponses relatives à une seule réservation sont combinées dans ce champ.
- **ID de réservation**   Cela est utile pour identifier les mêmes réservations d’un service de groupe.
