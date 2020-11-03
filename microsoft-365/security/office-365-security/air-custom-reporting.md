---
title: Utilisation de solutions de création de rapports personnalisées avec une enquête et une réponse automatisées
keywords: SIEM, API, AIR, autoIR, ATP, analyse automatisée, intégration, rapport personnalisé
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: Découvrez comment intégrer une enquête et une réponse automatisées à une solution de création de rapports personnalisée ou tierce.
ms.date: 09/29/2020
ms.custom:
- air
ms.openlocfilehash: 8b08b441ca468b5efa1c4c003c636de2a43b3e7d
ms.sourcegitcommit: 815229e39a0f905d9f06717f00dc82e2a028fa7c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2020
ms.locfileid: "48844547"
---
# <a name="use-the-management-activity-api-for-custom-or-third-party-reporting-solutions"></a>Utiliser l’API activité de gestion pour les solutions de création de rapports personnalisées ou tierces

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


Avec [Microsoft Defender pour Office 365](https://docs.microsoft.com/microsoft-365/security/office-365-security/office-365-atp), vous obtenez des [informations détaillées sur les analyses automatisées](air-view-investigation-results.md). Toutefois, certaines organisations utilisent également une solution de création de rapports personnalisée ou tierce. Si votre organisation souhaite intégrer des informations sur des enquêtes automatisées avec une telle solution, vous pouvez utiliser l’API activité de gestion d’Office 365.

Pour ce faire, utilisez les ressources suivantes :

****

|Ressource|Description|
|---|---|
|[Vue d’ensemble des API de gestion d’Office 365](https://docs.microsoft.com/office/office-365-management-api/office-365-management-apis-overview)|L’API d’activité de gestion d’Office 365 fournit des informations sur les différentes actions et événements d’utilisateur, d’administrateur, de système et de stratégie à partir des journaux d’activité de Microsoft 365 et Azure Active Directory.|
|[Prise en main des API de gestion d’Office 365](https://docs.microsoft.com/office/office-365-management-api/get-started-with-office-365-management-apis)|L’API de gestion d’Office 365 utilise Azure AD pour fournir des services d’authentification pour votre application afin d’accéder aux données Microsoft 365. Suivez les étapes décrites dans cet article pour le configurer.|
|[Référence de l’API Activité de gestion Office 365](https://docs.microsoft.com/office/office-365-management-api/office-365-management-activity-api-reference)|Vous pouvez utiliser l’API activité de gestion d’Office 365 pour récupérer des informations sur les actions et événements d’utilisateur, d’administrateur, de système et de stratégie à partir des journaux d’activité de Microsoft 365 et Azure AD. Lisez cet article pour en savoir plus sur le fonctionnement de cette procédure.|
|[Schéma de l’API Activité de gestion Office 365](https://docs.microsoft.com/office/office-365-management-api/office-365-management-activity-api-schema)|Pour en savoir plus sur des types de données spécifiques disponibles via l’API activité de gestion Office 365, consultez l’aperçu des [schémas communs](https://docs.microsoft.com/office/office-365-management-api/office-365-management-activity-api-schema#common-schema) et des [schémas d’enquête et de réponse des menaces pour Office 365 et les menaces](https://docs.microsoft.com/office/office-365-management-api/office-365-management-activity-api-schema#office-365-advanced-threat-protection-and-threat-investigation-and-response-schema) .|
|

## <a name="see-also"></a>Voir aussi

- [Microsoft Defender pour Office 365](office-365-atp.md)

- [Recherche et réponse automatisées dans Microsoft 365 Defender](https://docs.microsoft.com/microsoft-365/security/mtp/mtp-autoir)
