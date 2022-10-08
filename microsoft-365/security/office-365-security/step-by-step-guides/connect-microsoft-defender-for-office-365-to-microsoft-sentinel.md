---
title: Connecter Microsoft Defender pour Office 365 à Microsoft Sentinel
description: Étapes de connexion Microsoft Defender pour Office 365 à Sentinel. Ajoutez vos données Microsoft Defender pour Office 365 (*et* les données du reste de la suite Microsoft 365 Defender), y compris les incidents, à Microsoft Sentinel pour un seul volet de sécurité.
search.product: ''
ms.service: microsoft-365-security
ms.subservice: mdo
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-guidance-templates
- m365-security
- tier3
ms.topic: how-to
search.appverid: met150
ms.openlocfilehash: dcc7d486b41d6a60a0fbda1c8398e81e8516d093
ms.sourcegitcommit: 4e42bafee965446f44f7f57d1defed2b9b24fce8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2022
ms.locfileid: "68222867"
---
# <a name="connect-microsoft-defender-for-office-365-to-microsoft-sentinel"></a>Connecter Microsoft Defender pour Office 365 à Microsoft Sentinel

Vous pouvez ingérer vos données Microsoft Defender pour Office 365 (*et* les données du reste de la suite Microsoft 365 Defender), y compris les incidents, dans Microsoft Sentinel.

Tirez parti de la gestion complète des événements d’informations de sécurité (SIEM) combinée avec des données provenant d’autres sources Microsoft 365, de la synchronisation des incidents et des alertes, et de la chasse avancée.

> [!IMPORTANT]
> Le connecteur Microsoft 365 Defender est actuellement en **préversion**. Consultez les conditions d’utilisation supplémentaires pour les préversions Microsoft Azure pour obtenir des conditions juridiques supplémentaires qui s’appliquent aux fonctionnalités Azure qui sont en version bêta, en préversion ou qui ne sont pas encore publiées en disponibilité générale.>

## <a name="what-you-will-need"></a>Ce dont vous aurez besoin
- Microsoft Defender pour Office 365 plan 2 ou supérieur. (Inclus dans les plans E5)
- Guide de [démarrage rapide](/azure/sentinel/quickstart-onboard) de Microsoft Sentinel.
- Autorisations suffisantes (administrateur de sécurité dans M365 & autorisations de lecture/écriture dans Sentinel).

## <a name="add-the-microsoft-365-defender-connector"></a>Ajouter le connecteur Microsoft 365 Defender
1. [Connectez-vous au portail Azure](https://portal.azure.com) et accédez à **Microsoft Sentinel** > Sélectionnez l’espace de travail approprié à intégrer à Microsoft 365 Defender
    1. Dans le menu de navigation de gauche sous l’en-tête **Configuration** > choisissez **Connecteurs de données**.
2. Lorsque la page se charge, **recherchez** Microsoft 365 Defender **et sélectionnez le connecteur Microsoft 365 Defender (préversion**).
3. Dans le menu volant de droite, sélectionnez **Ouvrir la page du connecteur**.
4. Dans la section **Configuration** de la page qui se charge, sélectionnez **Connecter les incidents & alertes**, ce qui permet de désactiver toutes les règles de création d’incidents Microsoft pour ces produits.
5. Faites défiler jusqu’à **Microsoft Defender pour Office 365** dans la section **Connecter les événements** de la page. Sélectionnez **EmailEvents, EmailUrlInfo, EmailAttachmentInfo & EmailPostDeliveryEvents** , puis  **appliquez les modifications** en bas de la page. (Choisissez des tables parmi d’autres produits Defender, le cas échéant, au cours de cette étape.)

## <a name="next-steps"></a>Étapes suivantes

Les administrateurs pourront désormais voir les incidents, les alertes et les données brutes dans Microsoft Sentinel et utiliser ces données pour *la chasse avancée*, en pivotant sur les données existantes et nouvelles de Microsoft Defender.

## <a name="more-information"></a>Informations supplémentaires

[Connecter des données Microsoft 365 Defender à Microsoft Sentinel | Microsoft Docs](/azure/sentinel/connect-microsoft-365-defender?tabs=MDE)

[Connecter Microsoft Teams à Microsoft Sentinel](/microsoftteams/teams-sentinel-guide)
