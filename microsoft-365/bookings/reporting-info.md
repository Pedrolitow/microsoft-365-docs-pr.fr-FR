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
ms.openlocfilehash: 70d73da86e40555a5754a4284cbfbb0510e8c9e6
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60175634"
---
# <a name="reporting-info-for-bookings"></a>Informations de rapport pour Bookings

Vous pouvez maintenant voir une vue de quatre mois de votre calendrier Bookings dans un fichier TSV. Le fichier TSV affiche quatre mois de données, mais vous pouvez sélectionner différentes périodes de quatre mois au cours d’une année.

Ces informations de niveau de rendez-vous peuvent être utilisées pour visualiser l’activité des clients autour de votre calendrier Bookings. Les fichiers TSV sont des fichiers de valeurs séparées par des onglets. Vous pouvez afficher ou modifier un fichier comme celui-ci à l’aide d’un éditeur de texte ou d’un programme de feuilles de calcul, Excel.

## <a name="see-four-months-of-booking-activity"></a>Voir quatre mois d’activité de réservation

1. Dans Microsoft 365, sélectionnez le lanceur d’applications, puis **sélectionnez Bookings.**

1. Dans la page d’accueil Bookings, sélectionnez **Exporter.**

1. Dans la page **Exporter les données récentes,** sélectionnez votre plage de dates et sélectionnez **Exporter.**

1. Enregistrez le fichier sous un nouveau nom et spécifiez .xls format xlsx.

1. Ouvrez le fichier pour afficher l’affichage de quatre mois de votre calendrier Bookings.

1. Choisissez la date de votre rapport et sélectionnez **Exporter.**

1. Le rapport téléchargé contient un nouvel ensemble de champs en plus des champs existants.

Le rapport inclut les champs suivants.

 - **Date Heure**
- **Nom du client**
- **Courrier électronique client**
- **Client Téléphone**
- **Adresse du client**
- **Personnel**
- **Service**
- **Location**
- **Durée (minutes)**
- **Type d’événement**

Le rapport amélioré contient désormais les champs suivants.

- **Type de tarification**   Type de tarification par défaut pour un service lors de la création du service.
- **Prix**   Prix correspondant au type de tarification choisi.
- **Devise**   Type de devise pour une entreprise.
- **Participants Cc**   Destinataires qui reçoivent les notifications par courrier électronique pour une réservation. Cela peut être spécifié à partir de l’application Teams lors de la création d’une réservation.
- **Nombre de participants inscrits**   Nombre de clients qui ont réservé un service de réservation de groupe.
- **Notifications texte activées**   Si les clients peuvent recevoir des notifications texte SMS.
- **Champs personnalisés**   Toutes les questions et réponses relatives à une seule réservation sont combinées dans ce champ.
- **ID de réservation**   Cela permet d’identifier les mêmes réservations d’un service de groupe.
