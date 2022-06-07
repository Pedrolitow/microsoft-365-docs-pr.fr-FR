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
ms.openlocfilehash: e6b6f4426b173bced90fcc8f2a705bc3e48cd09e
ms.sourcegitcommit: 8a0de6240facfe26ee391a14076b7fe534ee6598
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2022
ms.locfileid: "65923383"
---
# <a name="scheduling-preferences-used-by-scheduler"></a>Préférences de planification utilisées par Scheduler

Scheduler utilise plusieurs préférences Outlook pour planifier une réunion pour un organisateur. Toute modification apportée aux paramètres de préférence dans les clients Outlook affecte la façon dont Scheduler gère les demandes envoyées à Cortana. Par exemple, si un organisateur modifie la préférence de fuseau horaire sur la page des paramètres dans Outlook Web, toutes les demandes de l’organisateur qui suivent sont définies par défaut sur le nouveau fuseau horaire.

## <a name="supported-settings"></a>Paramètres pris en charge

- **Fuseau horaire**. Le planificateur de fuseau horaire permet de déterminer l’heure appropriée pour les réunions. Pour plus d’informations [, consultez Ajouter, supprimer ou modifier des fuseaux horaires](https://support.microsoft.com/en-us/office/add-remove-or-change-time-zones-5ab3e10e-5a6c-46af-ab48-156fedf70c04) .

- **Heures et jours de travail**. Pour la plupart des types de réunions, Scheduler sélectionne une heure en fonction des préférences de semaine de travail et d’heures de réunion de l’organisateur. Pour plus d’informations, consultez [Modifier vos heures et jours de travail dans Outlook](https://support.microsoft.com/en-us/office/change-your-work-hours-and-days-in-outlook-a27f261d-0681-415f-8ac1-388ab21e833f) .

- **Réunions en ligne**. Vous pouvez activer une option Calendrier afin que toutes les réunions que vous planifiez à partir d’Outlook et de Scheduler se tiennent en ligne avec les détails de la conférence. Scheduler prend actuellement en charge Teams et Skype en tant que fournisseurs de réunions. Pour plus d’informations, consultez [Créer toutes les réunions Teams](https://support.microsoft.com/en-us/office/schedule-a-teams-meeting-from-outlook-883cc15c-580f-441a-92ea-0992c00a9b0f#bkmk_makeallteamsmtngs) .

- **Durée de la réunion par défaut**. Si l’organisateur ne spécifie pas la durée de réunion souhaitée dans la demande, Scheduler utilise la durée de réunion par défaut pour la demande. Ce paramètre est disponible uniquement dans le client Windows Outlook.

   1. Sélectionnez **Options** **de fichier** >  pour afficher la boîte de dialogue Options Outlook.

   2. Sélectionnez **Calendrier** dans la liste à gauche de la boîte de dialogue.

   3. Dans les paramètres des options calendrier à droite de la boîte de dialogue, sélectionnez **Durée par défaut pour les nouveaux rendez-vous et réunions**.

      :::image type="content" source="../media/OutlookOptions.png" alt-text="Boîte de dialogue Options de calendrier Outlook dans Windows où vous pouvez configurer le temps de travail, la durée de la réunion par défaut et sélectionner raccourcir les réunions à utiliser par Scheduler.":::

- **Évitez les réunions de dos à dos**. Un paramètre Outlook peut démarrer les réunions en retard ou mettre fin aux réunions tôt pour éviter les réunions back-to-back. En outre, Scheduler peut raccourcir la durée de la réunion en fonction de la préférence que vous définissez. Pour plus d’informations, consultez [Modifier la longueur de réunion par défaut](https://techcommunity.microsoft.com/t5/hybrid-work/change-default-meeting-length-in-outlook-avoid-back-to-back/m-p/1247361) .

> [!NOTE]
> Si vous utilisez le client Windows, vous devez sélectionner **Stocker mes paramètres Outlook dans le cloud** pour synchroniser vos préférences entre Scheduler et d’autres clients Outlook.
> :::image type="content" source="../media/OutlookOptions2.png" alt-text="Boîte de dialogue Options du calendrier Outlook dans Windows. Sélectionnez Stocker mes paramètres Outlook dans le cloud pour synchroniser les préférences de planification entre les clients.":::
