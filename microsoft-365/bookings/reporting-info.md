---
title: Informations de rapport pour Microsoft bookings
ms.author: kwekua
author: kwekuako
manager: scotv
audience: Admin
ms.topic: article
ms.service: bookings
ms.localizationpriority: medium
ms.assetid: 03a9acc9-f29c-456b-9fb2-0f49474b2708
description: Découvrez comment afficher une vue de 4 mois de votre activité Bookings
ms.openlocfilehash: 191194d112fe231c1a2f64245d33850ecb1266c0
ms.sourcegitcommit: 1c5f9d17a8b095cd88b23f4874539adc3ae021de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2022
ms.locfileid: "64714304"
---
# <a name="reporting-info-for-bookings"></a>Informations de création de rapports pour Bookings

> [!NOTE]
> Cet article vous aide à interagir avec la dernière version de Microsoft Bookings. Les versions précédentes seront mises hors service dans les prochains mois.

Vous pouvez maintenant voir une vue de quatre mois de votre calendrier Bookings dans un fichier TSV. Le fichier TSV affiche quatre mois de données, mais vous pouvez sélectionner différentes périodes de quatre mois au cours d’une année.

Ces informations de niveau rendez-vous peuvent être utilisées pour visualiser l’activité du client autour de votre calendrier Bookings. Les fichiers TSV sont des fichiers de valeurs séparés par des onglets. Vous pouvez afficher ou modifier un fichier comme celui-ci avec n’importe quel éditeur de texte ou programme de feuille de calcul, tel que Excel.

## <a name="see-four-months-of-booking-activity"></a>Voir quatre mois d’activité Booking

1. Dans Microsoft 365, sélectionnez le lanceur d’applications, puis sélectionnez **Bookings**.

1. Dans la page d’accueil Bookings, sélectionnez **Exporter**.

1. Dans la page **Exporter les données récentes** , sélectionnez votre plage de dates, puis **Export**.

1. Enregistrez le fichier avec un nouveau nom et spécifiez le format .xls ou xlsx.

1. Ouvrez le fichier pour afficher l’affichage de quatre mois de votre calendrier Bookings.

1. Choisissez la date de votre rapport, puis sélectionnez **Exporter**.

1. Le rapport téléchargé contient un nouvel ensemble de champs en plus des champs existants.

Le rapport inclut les champs suivants.

 - **Date Heure**
- **Nom du client**
- **E-mail du client**
- **Téléphone client**
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
