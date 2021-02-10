---
title: Intégration des serveurs SIEM aux services et applications Microsoft 365
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: ITPro
ms.topic: article
ms.date: 11/18/2019
localization_priority: Normal
ms.collection:
- M365-security-compliance
ms.custom:
- Ent_Solutions
- SIEM
- seo-marvel-apr2020
description: Obtenir une vue d’ensemble de l’intégration du serveur SIEM (Security Information and Event Management) à vos applications et services cloud Microsoft 365
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: f29da87aa6eab1852330092d93187a27b2d36eb2
ms.sourcegitcommit: a1846b1ee2e4fa397e39c1271c997fc4cf6d5619
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2021
ms.locfileid: "50167142"
---
# <a name="security-information-and-event-management-siem-server-integration-with-microsoft-365-services-and-applications"></a>Intégration de serveurs SIEM (Security Information and Event Management) aux services et applications Microsoft 365

**S’applique à**
- [Exchange Online Protection](https://go.microsoft.com/fwlink/?linkid=2148611)
- [Microsoft Defender pour Office 365 plan 1 et plan 2](https://go.microsoft.com/fwlink/?linkid=2148715)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

## <a name="summary"></a>Résumé

Votre organisation utilise-t-elle ou prévoit-elle d’obtenir un serveur SIEM (Security Information and Event Management) ? Vous vous demandez peut-être comment il s’intègre à Microsoft 365 ou Office 365. Cet article fournit la liste des ressources que vous pouvez utiliser pour intégrer votre serveur SIEM aux services et applications Microsoft 365.

> [!TIP]
> Si vous n’avez pas encore de serveur SIEM et que vous explorez vos options, envisagez **[Microsoft Azure Sentinel](https://docs.microsoft.com/azure/sentinel/overview)**.

## <a name="do-i-need-a-siem-server"></a>Ai-je besoin d’un serveur SIEM ?

La nécessité d’un serveur SIEM dépend de nombreux facteurs, tels que les exigences de sécurité de votre organisation et l’emplacement où résident vos données. Microsoft 365 inclut un large éventail de fonctionnalités de sécurité qui répondent aux besoins de sécurité de nombreuses organisations sans serveurs supplémentaires, tels qu’un serveur SIEM. Certaines organisations ont des circonstances particulières qui nécessitent l’utilisation d’un serveur SIEM. Voici quelques exemples :

- *Fabrikam possède* du contenu et des applications sur site, et d’autres dans le cloud (ils disposent d’un déploiement cloud hybride). Pour obtenir des rapports de sécurité sur l’ensemble de son contenu et de ses applications, Fabrikam a implémenté un serveur SIEM.

- *Contoso est* une organisation de services financiers qui a des exigences de sécurité particulièrement strictes. Ils ont ajouté un serveur SIEM à leur environnement pour tirer parti de la protection de sécurité supplémentaire dont ils ont besoin.

## <a name="siem-server-integration-with-microsoft-365"></a>Intégration de serveur SIEM à Microsoft 365

Un serveur SIEM peut recevoir des données à partir d’un large éventail de services et d’applications Microsoft 365. Le tableau suivant répertorie plusieurs services et applications Microsoft 365, ainsi que les entrées serveur SIEM et les ressources pour en savoir plus.

****

|Service ou application Microsoft 365|Entrées/méthodes de serveur SIEM|Ressources pour en savoir plus|
|---|---|---|
|[Microsoft Defender pour Office 365](office-365-atp.md)|Journaux d'audit|[Intégration de SIEM à Microsoft Defender pour Office 365](siem-integration-with-office-365-ti.md)|
|[Microsoft Defender pour point de terminaison](https://docs.microsoft.com/windows/security/threat-protection/)|Point de terminaison HTTPS hébergé dans Azure <p> API REST|[Tirer des alertes vers vos outils SIEM](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/configure-siem)|
|[Microsoft Cloud App Security](https://docs.microsoft.com/cloud-app-security/what-is-cloud-app-security)|Intégration des journaux|[Intégration DE SIEM à Microsoft Cloud App Security](https://docs.microsoft.com/cloud-app-security/siem)|
|

> [!TIP]
> Jetez un œil à [Azure Sentinel](https://docs.microsoft.com/azure/sentinel/overview). Azure Sentinel est livré avec des connecteurs pour les solutions Microsoft. Ces connecteurs sont disponibles « dès le début » et assurent une intégration en temps réel. Vous pouvez utiliser Azure Sentinel avec vos solutions Microsoft 365 Defender et vos services Microsoft 365, notamment Office 365, Azure AD, Microsoft Defender pour l’identité, Microsoft Cloud App Security, etc.

### <a name="audit-logging-must-be-turned-on"></a>L’enregistrement d’audit doit être allumé

Assurez-vous que la journalisation d’audit est allumée avant de configurer l’intégration de serveur SIEM.

- Pour SharePoint Online, OneDrive Entreprise et Azure Active Directory, la journalisation d’audit est active dans le Centre de sécurité [& conformité.](../../compliance/turn-audit-log-search-on-or-off.md)

- Pour Exchange Online, voir [Gérer l’audit de boîte aux lettres.](../../compliance/enable-mailbox-auditing.md)

## <a name="more-resources"></a>Autres ressources

[Intégrer des solutions de sécurité dans Azure Defender](https://docs.microsoft.com/azure/security-center/security-center-partner-integration#exporting-data-to-a-siem)

[Intégrer les alertes de l’API de sécurité Microsoft Graph avec des technologies SIEM](https://docs.microsoft.com/graph/security-integration)
