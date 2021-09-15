---
title: Intégration DE SIEM à Microsoft Defender pour Office 365
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: ITPro
ms.topic: article
localization_priority: None
search.appverid:
- MET150
- MOE150
ms.assetid: eb56b69b-3170-4086-82cf-ba40a530fa1b
ms.date: 08/21/2020
ms.collection:
- M365-security-compliance
description: Intégrez le serveur SIEM de votre organisation à Microsoft Defender pour Office 365 et les événements de menace associés dans l’API Office 365 gestion des activités.
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 3eb38325c9695ae0ed5cfb9389e8972ee599739f
ms.sourcegitcommit: f88a0ec621e7d9bc5f376eeaf70c8a9800711f88
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2021
ms.locfileid: "59356002"
---
# <a name="siem-integration-with-microsoft-defender-for-office-365"></a>Intégration DE SIEM à Microsoft Defender pour Office 365

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


Si votre organisation utilise un serveur de gestion des événements et des informations de sécurité (SIEM), vous pouvez intégrer Microsoft Defender pour Office 365 à votre serveur SIEM. Vous pouvez configurer cette intégration à l’aide de [l’API Office 365 Gestion des activités.](/office/office-365-management-api/office-365-management-activity-api-reference)

L’intégration SIEM vous permet d’afficher des informations, telles que des programmes malveillants ou des hameçonnages détectés par Microsoft Defender pour Office 365, dans vos rapports de serveur SIEM.

- Pour voir un exemple d’intégration SIEM avec Microsoft Defender pour Office 365, consultez le blog Tech Community : Améliorer l’efficacité de votre SOC avec Defender pour Office 365 et l’API de gestion [O365.](https://techcommunity.microsoft.com/t5/microsoft-security-and/improve-the-effectiveness-of-your-soc-with-office-365-atp-and/ba-p/1525185)
- Pour en savoir plus sur les API Office 365 gestion des Office 365, consultez la vue [d’ensemble des API de gestion des Office 365.](/office/office-365-management-api/office-365-management-apis-overview)

## <a name="how-siem-integration-works"></a>Fonctionnement de l’intégration SIEM

L’API Office 365 gestion des activités récupère des informations sur les actions et événements des utilisateurs, des administrateurs, du système et des stratégies à partir des journaux d’activité Microsoft 365 et Azure Active Directory de votre organisation. Si votre organisation dispose de Microsoft Defender pour Office 365 Plan 1 ou 2, ou Office 365 E5, vous pouvez utiliser [microsoft Defender pour Office 365 schéma](/office/office-365-management-api/office-365-management-activity-api-schema#office-365-advanced-threat-protection-and-threat-investigation-and-response-schema).

Récemment, des événements provenant des fonctionnalités d’investigation et de réponse automatisées dans Microsoft Defender pour [Office 365 Plan 2](defender-for-office-365.md#microsoft-defender-for-office-365-plan-1-and-plan-2) ont été ajoutés à l’API activité Office 365 gestion automatisée. En plus d’inclure des données sur les détails d’investigation principaux tels que l’ID, le nom et l’état, l’API contient également des informations de haut niveau sur les actions d’investigation et les entités.

Le serveur SIEM ou un autre système similaire sonde la charge de travail **audit.general** pour accéder aux événements de détection. Pour plus d’informations, voir [Prise en Office 365 API de gestion des données.](/office/office-365-management-api/get-started-with-office-365-management-apis)

## <a name="enum-auditlogrecordtype---type-edmint32"></a>Énumération : AuditLogRecordType - Type : Edm.Int32

### <a name="auditlogrecordtype"></a>AuditLogRecordType

Le tableau suivant récapitule les valeurs **d’AuditLogRecordType** qui sont pertinentes pour Microsoft Defender pour Office 365 événements :<br/><br/>

| Valeur | Nom du membre | Description |
|---|---|---|
| 28| ThreatIntelligence | Événements de hameçonnage et de programmes malveillants depuis Exchange Online Protection et Microsoft Defender pour Office 365. |
| 41| ThreatIntelligenceUrl | Coffre Lie les événements de remplacement d’heure de bloc et de bloc à partir de Microsoft Defender Office 365. |
| 47| ThreatIntelligenceAtpContent | Événements de hameçonnage et de programmes malveillants pour les fichiers dans SharePoint Online, OneDrive Entreprise et Microsoft Teams, à partir de Microsoft Defender pour Office 365. |
| 64| AirInvestigation | Événements d’investigation et de réponse automatisés, tels que les détails de l’enquête et les artefacts pertinents, de Microsoft Defender pour Office 365 Plan 2. |

> [!IMPORTANT]
> Vous devez avoir le rôle Administrateur général ou Administrateur de la sécurité affecté dans le portail Microsoft 365 Defender pour configurer l’intégration SIEM avec Microsoft Defender pour Office 365. Pour plus d’informations, consultez [Autorisations dans le portail Microsoft 365 Defender](permissions-microsoft-365-security-center.md).
>
> La journalisation d’audit doit être désactivée pour Microsoft 365 environnement de travail. Pour obtenir de l’aide, voir Activer ou désactiver la recherche dans le journal [d’audit.](../../compliance/turn-audit-log-search-on-or-off.md)

## <a name="see-also"></a>Voir aussi

[Examen et réponse contre les menaces Office 365](office-365-ti.md)

[Examen et réponse automatisés (AIR) dans Office 365](automated-investigation-response-office.md)