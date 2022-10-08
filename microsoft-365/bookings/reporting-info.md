---
title: Afficher les informations du calendrier Bookings
ms.author: kwekua
author: kwekuako
manager: scotv
audience: Admin
ms.topic: article
ms.service: bookings
ms.localizationpriority: medium
ms.collection:
- scotvorg
ms.assetid: 03a9acc9-f29c-456b-9fb2-0f49474b2708
description: Découvrez comment afficher une vue de votre activité Bookings sur 4 mois
ms.openlocfilehash: 4ca1a4c94ce14a8d673ff88be49dbb67b013a9c3
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68207817"
---
# <a name="reporting-info-for-bookings"></a>Informations de création de rapports pour Bookings

Vous pouvez maintenant voir une vue de quatre mois de votre calendrier Bookings dans un fichier TSV. Le fichier TSV affiche quatre mois de données, mais vous pouvez sélectionner différentes périodes de quatre mois au cours d’une année.

Ces informations de niveau rendez-vous peuvent être utilisées pour visualiser l’activité du client autour de votre calendrier Bookings. Les fichiers TSV sont des fichiers de valeurs séparés par des onglets. Vous pouvez afficher ou modifier un fichier comme celui-ci avec n’importe quel éditeur de texte ou programme de feuille de calcul, tel qu’Excel.

## <a name="see-four-months-of-booking-activity"></a>Voir quatre mois d’activité Booking

1. Dans Microsoft 365, sélectionnez le lanceur d’applications, puis **bookings**.

1. Dans la page d’accueil bookings, sélectionnez **Exporter**.

1. Dans la page **Exporter les données récentes** , sélectionnez votre plage de dates, puis **Export**.

1. Enregistrez le fichier avec un nouveau nom et spécifiez le format .xls ou xlsx.

1. Ouvrez le fichier pour afficher l’affichage de quatre mois de votre calendrier Bookings.

1. Choisissez la date de votre rapport, puis sélectionnez **Exporter**.

1. Le rapport téléchargé contient un nouvel ensemble de champs en plus des champs existants.

Le rapport inclut les champs suivants.

 - **Date Heure**
- **Nom du client**
- **Email client**
- **Téléphone du client**
- **Adresse du client**
- **Personnel**
- **Service**
- **Emplacement**
- **Durée (minutes)**
- **Type d’événement**

Le rapport amélioré contient désormais les champs suivants.

- **Type de tarification**   Type de tarification par défaut défini pour un service lors de la création du service.
- **Prix**   Prix correspondant au type de tarification choisi.
- **Monnaie**   Type de devise défini pour une entreprise.
- **Participants Cc**   Destinataires qui recevront les notifications par e-mail pour une réservation. Cela peut être spécifié à partir de l’application Teams lors de la création d’une réservation.
- **Nombre de participants inscrits**   Nombre de clients qui ont réservé un service de réservation de groupe.
- **Notifications de texte activées**   Indique si les clients peuvent recevoir des notifications par SMS liées au texte.
- **Champs personnalisés**   Toutes les questions et réponses relatives à une réservation unique sont combinées dans ce domaine.
- **ID de réservation**   Cela est utile pour identifier les mêmes réservations d’un service de groupe.
- **Suivi des données**   Suivez les métriques des ID de campagne que vous utilisez dans vos campagnes marketing.
