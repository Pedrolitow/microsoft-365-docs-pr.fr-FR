---
title: Ajuster les préférences de planification pour Scheduler pour Microsoft 365 Vue d’ensemble
ms.author: shivb
author: shivbijlani
manager: charlle
audience: Admin
ms.topic: article
ms.service: scheduler
ms.localizationpriority: medium
description: Découvrez comment ajuster les préférences de planification pour Scheduler pour Microsoft 365.
ms.openlocfilehash: 4c6bf31472f9237f82905ce36f7db534a99896b0
ms.sourcegitcommit: 6c2ab5e8efe74d0dc2df610e2d9d2fdda8aaf074
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/25/2022
ms.locfileid: "65670375"
---
<a name="scheduling-preferences"></a>Préférences de planification
======================

Scheduler prend en compte plusieurs préférences Outlook pour planifier une réunion pour un organisateur. Toutes les modifications apportées à leurs paramètres de préférence via Outlook clients sont automatiquement reflétées dans la façon dont Scheduler gère les demandes suivantes envoyées à Cortana. Par exemple, si un organisateur modifie sa préférence de fuseau horaire sur la page Paramètres dans Outlook Web, toutes les demandes suivantes de l’organisateur sont définies par défaut sur la nouvelle valeur de fuseau horaire.

<a name="supported-settings"></a>Paramètres pris en charge
------------------

<a name="time-zone"></a>Fuseau horaire
---------

Fuseau horaire utilisé pour déterminer l’heure appropriée pour planifier des réunions. Consultez la documentation [ajouter, supprimer ou modifier des fuseaux horaires](https://support.microsoft.com/en-us/office/add-remove-or-change-time-zones-5ab3e10e-5a6c-46af-ab48-156fedf70c04) .

<a name="work-hours-and-days"></a>Heures et jours de travail
-------------------

Pour la plupart des types de réunions, Scheduler planifie une heure en fonction des préférences de la semaine de travail et des heures de réunion de l’organisateur. Consultez [modifier vos heures et jours de travail dans Outlook](https://support.microsoft.com/en-us/office/change-your-work-hours-and-days-in-outlook-a27f261d-0681-415f-8ac1-388ab21e833f) documentation.

<a name="online-meetings"></a>Réunions en ligne
---------------

Vous pouvez activer une option Calendrier afin que toutes les réunions que vous planifiez à partir de Outlook et scheduler soient organisées en ligne avec les détails de la conférence. Scheduler prend actuellement en charge Teams et Skype en tant que fournisseurs de réunions. Consultez [la documentation Créer toutes les réunions Teams réunions](https://support.microsoft.com/en-us/office/schedule-a-teams-meeting-from-outlook-883cc15c-580f-441a-92ea-0992c00a9b0f#bkmk_makeallteamsmtngs).

<a name="default-meeting-duration"></a>Durée de la réunion par défaut
------------------------

Si l’organisateur ne spécifie pas la durée de réunion souhaitée dans la demande, Scheduler utilise la durée de réunion préférée pour la demande. Ce paramètre est disponible uniquement dans le client Windows Outlook.

1. Cliquez sur **Options** de **fichier** >  

2. Sélectionnez **Calendrier** dans le **volet de navigation**.

3. Le paramètre de durée par défaut se trouve sous **Options** de **calendrier**.

![Calendrier Outlook boîte de dialogue options dans Windows. Configurez le temps de travail, la durée par défaut et raccourcissez les options de réunions que Scheduler utilisera par défaut.](../media/OutlookOptions.png)

<a name="avoid-back-to-back-meetings"></a>Éviter les réunions de dos à dos
---------------------------

Outlook dispose maintenant d’un paramètre qui démarre automatiquement les réunions en retard ou met fin aux réunions tôt pour éviter les réunions back-to-back. S’il est défini, Scheduler raccourcit également la durée de la réunion en fonction du paramètre de préférence. Consultez [Modifier la longueur de réunion par défaut](https://techcommunity.microsoft.com/t5/hybrid-work/change-default-meeting-length-in-outlook-avoid-back-to-back/m-p/1247361) dans Outlook documentation.

##<a name="additional-note"></a>Remarque supplémentaire

- Si vous utilisez le client Windows, vous devez définir l’option suivante pour vous assurer que vos préférences sont synchronisées entre Scheduler et d’autres clients Outlook :

![Calendrier Outlook boîte de dialogue options dans Windows. Activez « Stocker mes paramètres de Outlook dans le cloud ».](../media/OutlookOptions2.png)
