---
title: Intégration de serveur SIEM avec Microsoft 365 services et applications
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
description: Obtenir une vue d’ensemble de l’intégration du serveur SIEM (Security Information and Event Management) à vos applications et services cloud Microsoft 365 de sécurité
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 3b4f0275ed9f63aaf3e5717a3511caa28055f0bf0e469c1c17a46e17e4a25a56
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "56968025"
---
# <a name="security-information-and-event-management-siem-server-integration-with-microsoft-365-services-and-applications"></a>Intégration de serveurs SIEM (Security Information and Event Management) avec Microsoft 365 services et applications

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

## <a name="summary"></a>Résumé

Votre organisation utilise-t-elle ou prévoit-elle d’obtenir un serveur SIEM (Security Information and Event Management) ? Vous vous demandez peut-être comment il s’intègre Microsoft 365 ou Office 365. Cet article fournit la liste des ressources que vous pouvez utiliser pour intégrer votre serveur SIEM à Microsoft 365 services et applications.

> [!TIP]
> Si vous n’avez pas encore de serveur SIEM et que vous explorez vos options, envisagez **[Microsoft Azure Sentinel](/azure/sentinel/overview)**.

## <a name="do-i-need-a-siem-server"></a>Ai-je besoin d’un serveur SIEM ?

La nécessité d’un serveur SIEM dépend de nombreux facteurs, tels que les exigences de sécurité de votre organisation et l’emplacement où résident vos données. Microsoft 365 inclut un large éventail de fonctionnalités de sécurité qui répondent aux besoins de sécurité de nombreuses organisations sans serveurs supplémentaires, tels qu’un serveur SIEM. Certaines organisations ont des circonstances particulières qui nécessitent l’utilisation d’un serveur SIEM. Voici quelques exemples :

- *Fabrikam possède* du contenu et des applications sur site, et d’autres dans le cloud (ils disposent d’un déploiement cloud hybride). Pour obtenir des rapports de sécurité sur tout leur contenu et applications, Fabrikam a implémenté un serveur SIEM.
- *Contoso est* une organisation de services financiers qui a des exigences de sécurité particulièrement strictes. Ils ont ajouté un serveur SIEM à leur environnement pour tirer parti de la protection de sécurité supplémentaire dont ils ont besoin.

## <a name="siem-server-integration-with-microsoft-365"></a>Intégration de serveur SIEM à Microsoft 365

Un serveur SIEM peut recevoir des données à partir d’un large éventail Microsoft 365 services et applications. Le tableau suivant répertorie Microsoft 365 services et applications, ainsi que des ressources et des entrées serveur SIEM pour en savoir plus.

<br>

****

|Microsoft 365 Service ou application|Entrées/méthodes de serveur SIEM|Ressources pour en savoir plus|
|---|---|---|
|[Microsoft Defender pour Office 365](defender-for-office-365.md)|Journaux d'audit|[Intégration DE SIEM à Microsoft Defender pour Office 365](siem-integration-with-office-365-ti.md)|
|[Microsoft Defender pour point de terminaison](/windows/security/threat-protection/)|Point de terminaison HTTPS hébergé dans Azure <p> API REST|[Tirer des alertes vers vos outils SIEM](../defender-endpoint/configure-siem.md)|
|[Microsoft Cloud App Security](/cloud-app-security/what-is-cloud-app-security)|Intégration des journaux|[Intégration DE SIEM à Microsoft Cloud App Security](/cloud-app-security/siem)|
|

> [!TIP]
> Jetez un œil à [Azure Sentinel](/azure/sentinel/overview). Azure Sentinel est livré avec des connecteurs pour les solutions Microsoft. Ces connecteurs sont disponibles « dès le début » et assurent une intégration en temps réel. Vous pouvez utiliser Azure Sentinel avec vos solutions Microsoft 365 Defender et vos services Microsoft 365, notamment Office 365, Azure AD, Microsoft Defender pour l’identité, Microsoft Cloud App Security, etc.

### <a name="audit-logging-must-be-turned-on"></a>L’enregistrement d’audit doit être allumé

Assurez-vous que la journalisation d’audit est allumée avant de configurer l’intégration de serveur SIEM.

- Pour SharePoint online, OneDrive Entreprise et Azure Active Directory, voir Activer [ou désactiver l’audit.](../../compliance/turn-audit-log-search-on-or-off.md)
- Pour plus Exchange Online, voir [Gérer l’audit de boîte aux lettres.](../../compliance/enable-mailbox-auditing.md)

## <a name="more-resources"></a>Plus de ressources

[Intégrer des solutions de sécurité dans Azure Defender](/azure/security-center/security-center-partner-integration#exporting-data-to-a-siem)

[Intégrer les alertes de l’API de sécurité Microsoft Graph avec des technologies SIEM](/graph/security-integration)
