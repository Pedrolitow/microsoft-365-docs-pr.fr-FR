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
- Tier1
- scotvorg
ms.assetid: 03a9acc9-f29c-456b-9fb2-0f49474b2708
description: Découvrez comment afficher une vue sur 4 mois de votre activité Bookings
ms.openlocfilehash: bcb6b90585299469dbbe4b67b628d4cfee88c463
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68733282"
---
# <a name="reporting-info-for-bookings"></a>Informations de création de rapports pour Bookings

Vous pouvez maintenant voir une vue de quatre mois de votre calendrier Bookings dans un fichier TSV. Le fichier TSV affiche quatre mois de données, mais vous pouvez sélectionner différentes périodes de quatre mois au cours d’une année.

Ces informations de niveau de rendez-vous peuvent être utilisées pour visualiser l’activité des clients autour de votre calendrier Bookings. Les fichiers TSV sont des fichiers de valeurs séparés par des onglets. Vous pouvez afficher ou modifier un fichier comme celui-ci avec n’importe quel éditeur de texte ou programme de feuille de calcul, tel qu’Excel.

## <a name="see-four-months-of-booking-activity"></a>Voir quatre mois d’activité booking

1. Dans Microsoft 365, sélectionnez le lanceur d’applications, puis **Bookings**.

1. Dans la page d’accueil Bookings, sélectionnez **Exporter**.

1. Dans la page **Exporter les données récentes** , sélectionnez votre plage de dates, puis **sélectionnez Exporter**.

1. Enregistrez le fichier sous un nouveau nom et spécifiez le format .xls ou xlsx.

1. Ouvrez le fichier pour afficher l’affichage de quatre mois de votre calendrier Bookings.

1. Choisissez la date de votre rapport, puis sélectionnez **Exporter**.

1. Le rapport téléchargé contient un nouvel ensemble de champs en plus des champs existants.

Le rapport inclut les champs suivants.

 - **Date Heure**
- **Nom du client**
- **Email client**
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
- **Nombre de participants inscrits**   Nombre de clients ayant réservé un service de réservation de groupe.
- **Notifications texte activées**   Indique si les clients peuvent recevoir des notifications sms.
- **Champs personnalisés**   Toutes les questions et réponses relatives à une réservation unique sont combinées dans ce champ.
- **ID de réservation**   Cela est utile pour identifier les mêmes réservations d’un service de groupe.
- **Données de suivi**   Suivez les métriques des ID de campagne que vous utilisez dans vos campagnes marketing.
