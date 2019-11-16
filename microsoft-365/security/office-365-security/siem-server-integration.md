---
title: Intégration de serveur SIEM aux services et applications Microsoft 365
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: ITPro
ms.topic: article
ms.date: 11/15/2019
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- M365-security-compliance
ms.custom:
- Ent_Solutions
- SIEM
description: Lisez cet article pour obtenir une vue d’ensemble de l’intégration de serveur SIEM à Microsoft 365.
ms.openlocfilehash: bea6141022fef1275a7e291217f698f52613f170
ms.sourcegitcommit: d8d001c03c28c10bea005d1c9b5f4a8f393af706
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2019
ms.locfileid: "38677507"
---
# <a name="siem-server-integration-with-microsoft-365-services-and-applications"></a>Intégration de serveur SIEM aux services et applications Microsoft 365

## <a name="summary"></a>Résumé

Si votre organisation utilise un serveur de gestion des événements et des informations de sécurité (SIEM), ou si vous envisagez d’obtenir rapidement un serveur SIEM, vous vous demandez peut-être comment l’intégrer à Microsoft 365 ou Office 365. Cet article fournit une liste de ressources que vous pouvez utiliser pour configurer l’intégration de serveur SIEM à vos applications et services Microsoft 365.

> [!TIP]
> Si vous n’avez pas encore de serveur SIEM et que vous Explorez vos options, envisagez **[Microsoft Azure Sentinel](https://docs.microsoft.com/azure/sentinel/overview)**.

## <a name="do-i-need-a-siem-server"></a>Ai-je besoin d’un serveur SIEM ?

La nécessité d’un serveur SIEM dépend de nombreux facteurs, tels que les exigences de sécurité de votre organisation et l’emplacement de stockage de vos données. Microsoft 365 inclut un large éventail de fonctionnalités de sécurité qui répondent aux besoins de sécurité de plusieurs organisations sans serveurs supplémentaires, tels qu’un serveur SIEM. Certaines organisations ont des circonstances spéciales qui nécessitent l’utilisation d’un serveur SIEM. Voici quelques exemples :

- *Fabrikam* dispose de contenu et d’applications sur site, et d’autres dans le Cloud (ils ont un déploiement Cloud hybride). Pour obtenir des rapports de sécurité sur tous les contenus et applications, Fabrikam a implémenté un serveur SIEM. 

- *Contoso* est une organisation de services financiers présentant des exigences de sécurité particulièrement strictes. Ils ont ajouté un serveur SIEM à leur environnement pour tirer parti de la protection de sécurité supplémentaire dont ils ont besoin.

## <a name="siem-server-integration-with-microsoft-365"></a>Intégration de serveur SIEM à Microsoft 365

Un serveur SIEM peut recevoir des données à partir d’un large éventail de services et d’applications Microsoft 365. Le tableau suivant répertorie plusieurs services et applications Microsoft 365 avec des entrées de serveur SIEM, ainsi que des ressources pour en savoir plus sur l’intégration de serveur SIEM. 

| Service ou application Microsoft 365 | Entrées de serveur SIEM | Ressources pour en savoir plus |
| --- | --- | --- |
| [Office 365 Advanced Threat Protection](office-365-atp.md)  | Journaux d'audit | [Intégration SIEM avec Office 365 protection avancée contre les menaces](siem-integration-with-office-365-ti.md) |
| [Microsoft Defender – Protection avancée contre les menaces](https://docs.microsoft.com/windows/security/threat-protection/) | Point de terminaison HTTPs hébergé dans Azure <br/>API REST| [Attirez les alertes sur vos outils SIEM](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/configure-siem) |
| [Microsoft Cloud App Security](https://docs.microsoft.com/cloud-app-security/what-is-cloud-app-security) | Intégration des journaux | [Intégration SIEM à la sécurité des applications Cloud Microsoft](https://docs.microsoft.com/cloud-app-security/siem) |

> [!TIP]
> Jetez un coup d’œil à [Azure Sentinel](https://docs.microsoft.com/azure/sentinel/overview), qui est fourni avec un certain nombre de connecteurs pour les solutions Microsoft, disponible dès à présent et offrant une intégration en temps réel, y compris des solutions de protection contre les menaces Microsoft, ainsi que des sources Microsoft 365, notamment Office 365, Azure ad, Azure ATP et Microsoft Cloud App Security, et bien plus encore.

### <a name="audit-logging-must-be-turned-on"></a>La journalisation d’audit doit être activée.

Assurez-vous que la journalisation d’audit est activée avant de configurer l’intégration de serveur SIEM. 

- Pour SharePoint Online, OneDrive entreprise et Azure Active Directory, [la journalisation d’audit est activée dans le centre de sécurité & conformité](https://docs.microsoft.com/office365/securitycompliance/turn-audit-log-search-on-or-off).

- Pour Exchange Online, la [journalisation d’audit est activée avec Windows PowerShell](https://docs.microsoft.com/office365/securitycompliance/enable-mailbox-auditing).
 
## <a name="additional-resources"></a>Ressources supplémentaires

[Intégrer des solutions de sécurité dans Azure Security Center](https://docs.microsoft.com/azure/security-center/security-center-partner-integration#exporting-data-to-a-siem)

[Intégrer les alertes de l’API de sécurité Microsoft Graph avec des technologies SIEM](https://docs.microsoft.com/graph/security-integration)