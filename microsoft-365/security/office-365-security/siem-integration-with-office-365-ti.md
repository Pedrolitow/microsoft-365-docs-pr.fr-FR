---
title: Intégration SIEM avec protection avancée contre les menaces
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: ITPro
ms.topic: overview
ms.service: O365-seccomp
localization_priority: None
search.appverid:
- MET150
- MOE150
ms.assetid: eb56b69b-3170-4086-82cf-ba40a530fa1b
ms.date: 08/21/2020
ms.collection:
- M365-security-compliance
description: Intégrez le serveur SIEM de votre organisation avec Office 365 protection avancée contre les menaces et les événements de menace associés dans l’API de gestion des activités Office 365.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: cfb76485fec8eca2f2b62da59fa2d18a56177bba
ms.sourcegitcommit: c083602dda3cdcb5b58cb8aa070d77019075f765
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "48203649"
---
# <a name="siem-integration-with-advanced-threat-protection"></a>Intégration SIEM avec protection avancée contre les menaces

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


Si votre organisation utilise un serveur de gestion des événements et des incidents de sécurité (SIEM), vous pouvez intégrer Office 365 Advanced Threat Protection (Office 365 ATP) à votre serveur SIEM. Vous pouvez configurer cette intégration à l’aide de l' [API de gestion des activités Office 365](https://docs.microsoft.com/office/office-365-management-api/office-365-management-activity-api-reference). 

L’intégration SIEM vous permet d’afficher des informations, telles que des programmes malveillants ou des hameçons détectés par la protection avancée contre les menaces d’Office 365, dans vos rapports de serveur SIEM. 

- Pour voir un exemple d’intégration SIEM avec la protection avancée contre les menaces Office 365, voir blog de la [communauté technique : améliorer l’efficacité de votre SOC avec office 365 ATP et l’API de gestion d’O365](https://techcommunity.microsoft.com/t5/microsoft-security-and/improve-the-effectiveness-of-your-soc-with-office-365-atp-and/ba-p/1525185).

- Pour en savoir plus sur les API de gestion d’Office 365, voir [office 365 Management API Overview](https://docs.microsoft.com/office/office-365-management-api/office-365-management-apis-overview).

## <a name="how-siem-integration-works"></a>Fonctionnement de l’intégration SIEM

L’API de gestion des activités Office 365 récupère des informations sur les actions et événements d’utilisateur, d’administrateur, de système et de stratégie à partir des journaux d’activité de Microsoft 365 et Azure Active Directory de votre organisation. Si votre organisation dispose d’Office 365 ATP plan 1 ou 2, ou Office 365 E5, vous pouvez utiliser le [schéma ATP d’office 365](https://docs.microsoft.com/office/office-365-management-api/office-365-management-activity-api-schema#office-365-advanced-threat-protection-and-threat-investigation-and-response-schema).  

Récemment, les événements des fonctionnalités d’analyse et de réponse automatisées dans [office 365 DAV plan 2](office-365-atp.md#office-365-atp-plan-1-and-plan-2) ont été ajoutés à l’API activité de gestion d’Office 365. En plus d’inclure des données sur les détails d’enquête de base, tels que l’ID, le nom et l’État, l’API contient également des informations de haut niveau sur les actions et les entités d’enquête.

Le serveur SIEM ou un autre système similaire interroge l' **audit.** charge de travail générale pour accéder aux événements de détection. Pour plus d’informations, reportez-vous à la rubrique [prise en main des API de gestion d’Office 365](https://docs.microsoft.com/office/office-365-management-api/get-started-with-office-365-management-apis). 


## <a name="enum-auditlogrecordtype---type-edmint32"></a>Énumération : AuditLogRecordType - Type : Edm.Int32

### <a name="auditlogrecordtype"></a>AuditLogRecordType

Le tableau suivant récapitule les valeurs de **AuditLogRecordType** qui sont pertinentes pour les événements ATP Office 365 :

|Valeur|Nom du membre|Description|
|---|---|---|
|vingt|ThreatIntelligence|Événements de hameçonnage et de programmes malveillants à partir d’Exchange Online Protection et Office 365 ATP.|
|41|ThreatIntelligenceUrl|Les événements de blocage des liens approuvés par l’ATP et les événements de remplacement de bloc à partir d’Office 365 ATP.|
|47|ThreatIntelligenceAtpContent|Événements de hameçonnage et de programmes malveillants pour les fichiers dans SharePoint Online, OneDrive entreprise et Microsoft Teams, à partir d’Office 365 ATP.|
|64|AirInvestigation|Des événements d’enquête et de réponse automatisés, tels que des détails d’enquête et des artefacts pertinents, à partir d’Office 365 DAV (plan 2).|
|

> [!IMPORTANT]
> Vous devez être un administrateur général ou avoir le rôle administrateur de sécurité affecté au centre de sécurité & conformité pour configurer l’intégration SIEM avec Office 365 protection avancée contre les menaces.<br/>La journalisation d’audit doit être activée pour votre environnement Microsoft 365. Pour obtenir de l’aide, consultez la rubrique [activer ou désactiver la recherche dans le journal d’audit](../../compliance/turn-audit-log-search-on-or-off.md).

## <a name="see-also"></a>Voir aussi

[Examen et réponse contre les menaces Office 365](office-365-ti.md)

[Recherche et réponse automatiques dans Office 365](automated-investigation-response-office.md)


