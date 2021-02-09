---
title: Solutions de création de rapports personnalisées avec examen et réponse automatisés
keywords: SIEM, API, AIR, autoIR, ATP, examen automatisé, intégration, rapport personnalisé
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: ITPro
ms.topic: article
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: Découvrez comment intégrer un examen et une réponse automatisés à une solution de création de rapports personnalisée ou tierce.
ms.date: 01/29/2021
ms.custom:
- air
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 3d8363ada4de60d37cb0d247d8b1af74df4226d1
ms.sourcegitcommit: d739f48b991793c08522a3d5323beba27f0111b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "50142968"
---
# <a name="custom-or-third-party-reporting-solutions-for-microsoft-defender-for-office-365"></a>Solutions de création de rapports personnalisées ou tierces pour Microsoft Defender pour Office 365

Avec [Microsoft Defender pour Office 365,](office-365-atp.md)vous obtenez des informations détaillées sur les [enquêtes automatisées.](air-view-investigation-results.md) Toutefois, certaines organisations utilisent également une solution de création de rapports personnalisée ou tierce. Si votre organisation souhaite intégrer des informations sur les [enquêtes](office-365-air.md) automatisées à une telle solution, vous pouvez utiliser l’API Activité de gestion Office 365.

Ressources pour configurer l’intégration

|Ressource|Description|
|:---|:---|
|[Vue d’ensemble des API de gestion d’Office 365](https://docs.microsoft.com/office/office-365-management-api/office-365-management-apis-overview)|L’API Activité de gestion Office 365 fournit des informations sur diverses actions et événements d’utilisateur, d’administrateur, de système et de stratégie à partir des journaux d’activité Microsoft 365 et Azure Active Directory.|
|[Prise en main des API de gestion d’Office 365](https://docs.microsoft.com/office/office-365-management-api/get-started-with-office-365-management-apis)|L’API de gestion Office 365 utilise Azure AD pour fournir des services d’authentification pour que votre application accède aux données Microsoft 365. Suivez les étapes de cet article pour le configurer.|
|[Référence de l’API Activité de gestion Office 365](https://docs.microsoft.com/office/office-365-management-api/office-365-management-activity-api-reference)|Vous pouvez utiliser l’API Activité de gestion Office 365 pour récupérer des informations sur les actions et événements des utilisateurs, des administrateurs, du système et des stratégies à partir des journaux d’activité Microsoft 365 et Azure AD. Lisez cet article pour en savoir plus sur son fonctionnement.|
|[Schéma de l’API Activité de gestion Office 365](https://docs.microsoft.com/office/office-365-management-api/office-365-management-activity-api-schema)|Obtenez une vue [](https://docs.microsoft.com/office/office-365-management-api/office-365-management-activity-api-schema#common-schema) d’ensemble du schéma commun et de Defender pour [Office 365,](https://docs.microsoft.com/office/office-365-management-api/office-365-management-activity-api-schema#office-365-advanced-threat-protection-and-threat-investigation-and-response-schema) ainsi que du schéma d’examen et de réponse aux menaces pour en savoir plus sur des types spécifiques de données disponibles via l’API Activité de gestion Office 365.|
|

## <a name="see-also"></a>Voir aussi

- [Microsoft Defender pour Office 365](office-365-atp.md)
- [Examen et réponse automatisés dans Microsoft 365 Defender](https://docs.microsoft.com/microsoft-365/security/mtp/mtp-autoir)
