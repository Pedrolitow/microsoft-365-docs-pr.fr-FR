---
title: Microsoft Defender pour Office 365 conservation des données
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: article
ms.service: microsoft-365-security
ms.subservice: mdo
ms.localizationpriority: medium
search.appverid: ''
ms.collection:
- M365-security-compliance
ms.custom: ''
description: Microsoft Defender pour Office 365 des informations de rétention des donnéesThreat Explorer/ détections de Real-Time
ms.openlocfilehash: d57865649dbba96dc4e2d66c0618dc6d52d87205
ms.sourcegitcommit: 2b89bcff547e00be3d38dc8d1e6cbcf8f41eba42
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2022
ms.locfileid: "67596399"
---
# <a name="data-retention-information-for-microsoft-defender-for-office-365"></a>Informations de conservation des données pour Microsoft Defender pour Office 365

Par défaut, les données de différentes fonctionnalités sont conservées pendant un maximum de 30 jours. Toutefois, pour certaines des fonctionnalités, vous pouvez spécifier la période de rétention en fonction de la stratégie. Consultez le tableau suivant pour connaître les différentes périodes de rétention de chaque fonctionnalité.

> [!NOTE]
> Microsoft Defender pour Office 365 est disponible en deux types de plans différents. Vous pouvez déterminer si vous avez le **Plan 1** si vous avez des détections en temps réel, et le **Plan 2**, si vous avez l’Explorateur de menaces. Le plan que vous avez influence les outils que vous verrez, alors soyez certain que vous êtes conscient de votre plan au fur et à mesure que vous apprenez.

## <a name="defender-for-office-365-plan-1"></a>Microsoft Defender pour Office 365 Plan 1

|Fonctionnalité|Période de rétention|
|---|---|
|Détails des métadonnées d’alerte (alertes Microsoft Defender pour Office) | 90 jours |
|Détails des métadonnées d’entité (e-mails) | 30 jours |
|Détails de l’alerte d’activité (journaux d’audit) | 7 jours |
|Page de l’entité d’e-mail | 30 jours |
|Quarantaine | 30 jours (configurable jusqu’à 30 jours maximum) |
|Rapports | 90 jours (pour toutes les données agrégées) <br>30 jours (pour toutes les informations détaillées sauf ci-dessous) <br> 10 jours (pour les détails du rapport d’état de la protection contre les menaces et les détails du rapport de courrier d’usurpation d’identité) <br> 7 jours (pour les détails du rapport de protection d’URL) <br>
|Soumissions | 30 jours |
|Détections de l’Explorateur de menaces/Real-Time | 30 jours |

## <a name="defender-for-office-365-plan-2"></a>Microsoft Defender pour Office 365 Plan 2

Defender pour Office 365 fonctionnalités du plan 1, ainsi que :

|Fonctionnalité|Période de rétention|
|---|---|
|Centre de notifications | 180 jours, 30 jours (Centre d’action Office)   |
|Repérage avancé | 30 jours |
|AIR (Examen et réponse automatisés) | 60 jours (pour les métadonnées d’investigation)<br> 30 jours (pour les métadonnées de messagerie)  |
|Données de simulation d’attaque | 18 mois |
|Campagnes | 30 jours |
|Incidents | 30 jours|
|Assainissement | 30 jours |
|Analyses de menaces | 30 jours |
|Suivi des menaces | 30 jours |
