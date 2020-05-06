---
title: Intégration de serveur SIEM aux services et applications Microsoft 365
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: ITPro
ms.topic: article
ms.date: 11/18/2019
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- M365-security-compliance
ms.custom:
- Ent_Solutions
- SIEM
- seo-marvel-apr2020
description: Obtenir une vue d’ensemble de l’intégration du serveur des informations de sécurité et de la gestion des événements (SIEM) à vos applications et services Cloud Microsoft 365
ms.openlocfilehash: c52f24c6260c890b1f6d8612efacb78f9b08be86
ms.sourcegitcommit: a45cf8b887587a1810caf9afa354638e68ec5243
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "44035259"
---
# <a name="security-information-and-event-management-siem-server-integration-with-microsoft-365-services-and-applications"></a>Intégration du serveur de gestion des événements et des informations de sécurité (SIEM) aux services et applications Microsoft 365

## <a name="summary"></a>Résumé

Votre organisation utilise-t-elle ou envisage-t-elle un serveur de gestion des événements et des informations de sécurité (SIEM) ? Vous vous demandez peut-être comment il s’intègre à Microsoft 365 ou Office 365. Cet article fournit une liste de ressources que vous pouvez utiliser pour intégrer votre serveur SIEM aux services et applications Microsoft 365.

> [!TIP]
> Si vous n’avez pas encore de serveur SIEM et que vous Explorez vos options, envisagez **[Microsoft Azure Sentinel](https://docs.microsoft.com/azure/sentinel/overview)**.

## <a name="do-i-need-a-siem-server"></a>Ai-je besoin d’un serveur SIEM ?

La nécessité d’un serveur SIEM dépend de nombreux facteurs, tels que les exigences de sécurité de votre organisation et l’emplacement de stockage de vos données. Microsoft 365 inclut un large éventail de fonctionnalités de sécurité qui répondent aux besoins de sécurité de plusieurs organisations sans serveurs supplémentaires, tels qu’un serveur SIEM. Certaines organisations ont des circonstances spéciales qui nécessitent l’utilisation d’un serveur SIEM. Voici quelques exemples :

- *Fabrikam* dispose de contenu et d’applications sur site, et d’autres dans le Cloud (ils ont un déploiement Cloud hybride). Pour obtenir des rapports de sécurité sur tous les contenus et applications, Fabrikam a implémenté un serveur SIEM.

- *Contoso* est une organisation de services financiers présentant des exigences de sécurité particulièrement strictes. Ils ont ajouté un serveur SIEM à leur environnement pour tirer parti de la protection de sécurité supplémentaire dont ils ont besoin.

## <a name="siem-server-integration-with-microsoft-365"></a>Intégration de serveur SIEM à Microsoft 365

Un serveur SIEM peut recevoir des données à partir d’un large éventail de services et d’applications Microsoft 365. Le tableau suivant répertorie plusieurs applications et services Microsoft 365, ainsi que des ressources et des entrées de serveur SIEM pour en savoir plus.

||||
|---|---|---|
|**Service ou application Microsoft 365**|**Entrées/méthodes du serveur SIEM**|**Ressources pour en savoir plus**|
|[Protection avancée contre les menaces dans Office 365](office-365-atp.md)|Journaux d'audit|[Intégration SIEM avec Office 365 protection avancée contre les menaces](siem-integration-with-office-365-ti.md)|
|[Microsoft Defender – Protection avancée contre les menaces](https://docs.microsoft.com/windows/security/threat-protection/)|Point de terminaison HTTPs hébergé dans Azure <br/>API REST|[Attirez les alertes sur vos outils SIEM](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/configure-siem)|
|[Microsoft Cloud App Security](https://docs.microsoft.com/cloud-app-security/what-is-cloud-app-security)|Intégration des journaux|[Intégration SIEM à la sécurité des applications Cloud Microsoft](https://docs.microsoft.com/cloud-app-security/siem)|
|

> [!TIP]
> Jetez un œil à [Azure Sentinel](https://docs.microsoft.com/azure/sentinel/overview). Azure sentinelle inclut des connecteurs pour les solutions Microsoft. Ces connecteurs sont disponibles « en l’absence de » et permettent une intégration en temps réel. Vous pouvez utiliser Azure Sentinel avec vos solutions de protection contre les menaces Microsoft et les services Microsoft 365, notamment Office 365, Azure AD, Azure ATP, sécurité des applications Cloud Microsoft, et bien plus encore.

### <a name="audit-logging-must-be-turned-on"></a>La journalisation d’audit doit être activée.

Assurez-vous que la journalisation d’audit est activée avant de configurer l’intégration de serveur SIEM.

- Pour SharePoint Online, OneDrive entreprise et Azure Active Directory, [la journalisation d’audit est activée dans le centre de sécurité & conformité](../../compliance/turn-audit-log-search-on-or-off.md).

- Pour Exchange Online, consultez la rubrique [Manage Mailbox Auditing](../../compliance/enable-mailbox-auditing.md).

## <a name="more-resources"></a>Autres ressources

[Intégrer des solutions de sécurité dans Azure Security Center](https://docs.microsoft.com/azure/security-center/security-center-partner-integration#exporting-data-to-a-siem)

[Intégrer les alertes de l’API de sécurité Microsoft Graph avec des technologies SIEM](https://docs.microsoft.com/graph/security-integration)
