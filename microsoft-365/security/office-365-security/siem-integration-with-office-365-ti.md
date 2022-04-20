---
title: Intégration de SIEM à Microsoft Defender pour Office 365
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: ITPro
ms.topic: article
ms.localizationpriority: ''
search.appverid:
- MET150
- MOE150
ms.assetid: eb56b69b-3170-4086-82cf-ba40a530fa1b
ms.date: 08/21/2020
ms.collection:
- M365-security-compliance
description: Intégrez le serveur SIEM de votre organisation à Microsoft Defender pour Office 365 et aux événements de menace associés dans l’API de gestion des activités Office 365.
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: e53fe703637ba4b33fd9658b2ec53b2c8c57db0f
ms.sourcegitcommit: 45bc65972d4007b2aa7760d4457a0d2699f81926
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2022
ms.locfileid: "64972582"
---
# <a name="siem-integration-with-microsoft-defender-for-office-365"></a>Intégration de SIEM à Microsoft Defender pour Office 365

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

Si votre organisation utilise un serveur SIEM (Security Information and Event Management), vous pouvez intégrer Microsoft Defender pour Office 365 à votre serveur SIEM. Vous pouvez configurer cette intégration à l’aide de [l’API de gestion des activités Office 365](/office/office-365-management-api/office-365-management-activity-api-reference).

L’intégration SIEM vous permet d’afficher des informations, telles que des programmes malveillants ou des hameçonnages détectés par Microsoft Defender pour Office 365, dans vos rapports de serveur SIEM.

- Pour voir un exemple d’intégration de SIEM à Microsoft Defender pour Office 365, consultez [le blog Tech Community : Améliorer l’efficacité de votre SOC avec Defender pour Office 365 et l’API de gestion O365](https://techcommunity.microsoft.com/t5/microsoft-security-and/improve-the-effectiveness-of-your-soc-with-office-365-atp-and/ba-p/1525185).
- Pour en savoir plus sur les API de gestion Office 365, consultez [Office 365 Vue d’ensemble des API de gestion](/office/office-365-management-api/office-365-management-apis-overview).

## <a name="how-siem-integration-works"></a>Fonctionnement de l’intégration SIEM

L’API de gestion des activités Office 365 récupère des informations sur les actions et événements d’utilisateur, d’administrateur, de système et de stratégie à partir des journaux d’activité Microsoft 365 et Azure Active Directory de votre organisation. Si votre organisation a Microsoft Defender pour Office 365 plan 1 ou 2 ou Office 365 E5, vous pouvez utiliser le [schéma Microsoft Defender pour Office 365](/office/office-365-management-api/office-365-management-activity-api-schema#office-365-advanced-threat-protection-and-threat-investigation-and-response-schema).

Récemment, des événements provenant de fonctionnalités d’investigation et de réponse automatisées dans [Microsoft Defender pour Office 365 Plan 2](defender-for-office-365.md#microsoft-defender-for-office-365-plan-1-and-plan-2) ont été ajoutés à l’API activité de gestion Office 365. En plus d’inclure des données sur les détails d’investigation de base tels que l’ID, le nom et l’état, l’API contient également des informations générales sur les actions d’investigation et les entités.

Le serveur SIEM ou un autre système similaire interroge la charge de travail **audit.general** pour accéder aux événements de détection. Pour en savoir plus, consultez [Démarrage avec les API de gestion Office 365](/office/office-365-management-api/get-started-with-office-365-management-apis).

## <a name="enum-auditlogrecordtype---type-edmint32"></a>Énumération : AuditLogRecordType - Type : Edm.Int32

### <a name="auditlogrecordtype"></a>AuditLogRecordType

Le tableau suivant récapitule les valeurs **d’AuditLogRecordType** pertinentes pour les événements Microsoft Defender pour Office 365 :<br/><br/>

| Valeur | Nom du membre | Description |
|---|---|---|
| 28| ThreatIntelligence | Événements de hameçonnage et de programmes malveillants depuis Exchange Online Protection et Microsoft Defender pour Office 365. |
| 41| ThreatIntelligenceUrl | Coffre Lie les événements de remplacement de temps de bloc et de blocage à partir de Microsoft Defender pour Office 365. |
| 47| ThreatIntelligenceAtpContent | Événements d’hameçonnage et de programmes malveillants pour les fichiers dans SharePoint Online, OneDrive Entreprise et Microsoft Teams, à partir de Microsoft Defender pour Office 365. |
| 64| AirInvestigation | Événements d’investigation et de réponse automatisés, tels que les détails de l’enquête et les artefacts pertinents, à partir de Microsoft Defender pour Office 365 plan 2. |

> [!IMPORTANT]
> Le rôle Administrateur général ou Administrateur de sécurité doit être attribué dans le portail Microsoft 365 Defender pour configurer l’intégration de SIEM à Microsoft Defender pour Office 365. Pour plus d’informations, consultez [Autorisations dans le portail Microsoft 365 Defender](permissions-microsoft-365-security-center.md).
>
> La journalisation d’audit doit être activée pour votre environnement Microsoft 365. Pour obtenir de l’aide à ce sujet, consultez [Activer ou désactiver la recherche dans le journal d’audit](../../compliance/turn-audit-log-search-on-or-off.md).

## <a name="see-also"></a>Voir aussi

[Examen et réponse contre les menaces Office 365](office-365-ti.md)

[Investigation et réponse automatisées (AIR) dans Office 365](automated-investigation-response-office.md)