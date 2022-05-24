---
title: Solutions de création de rapports personnalisées avec investigation et réponse automatisées
keywords: SIEM, API, AIR, autoIR, Microsoft Defender pour point de terminaison, investigation automatisée, intégration, rapport personnalisé
f1.keywords:
- NOCSH
author: dansimp
ms.author: dansimp
manager: dansimp
audience: ITPro
ms.topic: article
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: Découvrez comment intégrer l’investigation et la réponse automatisées à une solution de création de rapports personnalisée ou tierce.
ms.date: 01/29/2021
ms.custom:
- air
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: f21ed51cc9e89c2d60c924df377f109c6e29eec6
ms.sourcegitcommit: 725a92b0b1555572b306b285a0e7a7614d34e5e5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/24/2022
ms.locfileid: "65647884"
---
# <a name="custom-or-third-party-reporting-solutions-for-microsoft-defender-for-office-365"></a>Solutions de création de rapports personnalisées ou tierces pour Microsoft Defender pour Office 365

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à**
- [Microsoft Defender pour Office 365 Plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Avec [Microsoft Defender pour Office 365](defender-for-office-365.md), vous obtenez [des informations détaillées sur les enquêtes automatisées](air-view-investigation-results.md). Toutefois, certaines organisations utilisent également une solution de création de rapports personnalisée ou tierce. Si votre organisation souhaite intégrer des informations sur [les investigations automatisées](office-365-air.md) à une telle solution, vous pouvez utiliser l’API d’activité de gestion Office 365.

Avec [Microsoft Defender pour Office 365](defender-for-office-365.md), vous obtenez [des informations détaillées sur les enquêtes automatisées](air-view-investigation-results.md). Toutefois, certaines organisations utilisent également une solution de création de rapports personnalisée ou tierce. Si votre organisation souhaite intégrer des informations sur les investigations automatisées à une telle solution, vous pouvez utiliser l’API d’activité de gestion Office 365.

|Ressource|Description|
|:---|:---|
|[Vue d’ensemble des API de gestion d’Office 365](/office/office-365-management-api/office-365-management-apis-overview)|L’API activité de gestion Office 365 fournit des informations sur les différentes actions et événements utilisateur, administrateur, système et stratégie à partir des journaux d’activité Microsoft 365 et Azure Active Directory.|
|[Prise en main des API de gestion d’Office 365](/office/office-365-management-api/get-started-with-office-365-management-apis)|L’API de gestion Office 365 utilise Azure AD pour fournir des services d’authentification permettant à votre application d’accéder aux données Microsoft 365. Suivez les étapes décrites dans cet article pour configurer ce paramètre.|
|[Référence de l’API Activité de gestion Office 365](/office/office-365-management-api/office-365-management-activity-api-reference)|Vous pouvez utiliser l’API d’activité de gestion Office 365 pour récupérer des informations sur les actions et événements utilisateur, administrateur, système et stratégie à partir des journaux d’activité Microsoft 365 et Azure AD. Lisez cet article pour en savoir plus sur le fonctionnement.|
|[Schéma de l’API Activité de gestion Office 365](/office/office-365-management-api/office-365-management-activity-api-schema)|Obtenez une vue d’ensemble du [schéma commun](/office/office-365-management-api/office-365-management-activity-api-schema#common-schema) et du [schéma d’Defender pour Office 365 et d’investigation et de réponse aux menaces](/office/office-365-management-api/office-365-management-activity-api-schema#office-365-advanced-threat-protection-and-threat-investigation-and-response-schema) pour en savoir plus sur des types spécifiques de données disponibles via l’API d’activité de gestion Office 365.|

## <a name="see-also"></a>Voir aussi

- [Microsoft Defender pour Office 365](defender-for-office-365.md)
- [Enquête et réponse automatisées dans Microsoft 365 Defender](/microsoft-365/security/defender/m365d-autoir)
