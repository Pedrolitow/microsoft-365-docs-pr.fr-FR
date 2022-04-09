---
title: Intégration du serveur SIEM aux services et applications Microsoft 365
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: ITPro
ms.topic: article
ms.date: 11/18/2019
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
ms.custom:
- Ent_Solutions
- SIEM
- seo-marvel-apr2020
description: Obtenir une vue d’ensemble de l’intégration du serveur SIEM (Security Information and Event Management) à vos applications et services cloud Microsoft 365
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 978319cca91322c7eb737d89cbfc167574f14093
ms.sourcegitcommit: 1ef176c79a0e6dbb51834fe30807409d4e94847c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2021
ms.locfileid: "64731414"
---
# <a name="security-information-and-event-management-siem-server-integration-with-microsoft-365-services-and-applications"></a>Intégration du serveur SIEM (Security Information and Event Management) à Microsoft 365 services et applications

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

## <a name="summary"></a>Résumé

Votre organisation utilise-t-elle ou envisage-t-elle d’obtenir un serveur SIEM (Security Information and Event Management) ? Vous vous demandez peut-être comment il s’intègre à Microsoft 365 ou Office 365. Cet article fournit la liste des ressources que vous pouvez utiliser pour intégrer votre serveur SIEM à Microsoft 365 services et applications.

> [!TIP]
> Si vous n’avez pas encore de serveur SIEM et que vous explorez vos options, envisagez **[Microsoft Sentinel](/azure/sentinel/overview)**.

## <a name="do-i-need-a-siem-server"></a>Ai-je besoin d’un serveur SIEM ?

Si vous avez besoin d’un serveur SIEM dépend de nombreux facteurs, tels que les exigences de sécurité de votre organisation et l’emplacement de vos données. Microsoft 365 comprend une grande variété de fonctionnalités de sécurité qui répondent aux besoins de sécurité de nombreuses organisations sans serveurs supplémentaires, tels qu’un serveur SIEM. Certaines organisations ont des circonstances particulières qui nécessitent l’utilisation d’un serveur SIEM. Voici quelques exemples :

- *Fabrikam* a du contenu et des applications en local, et d’autres dans le cloud (ils ont un déploiement de cloud hybride). Pour obtenir des rapports de sécurité sur l’ensemble de leur contenu et de leurs applications, Fabrikam a implémenté un serveur SIEM.
- *Contoso* est une organisation de services financiers qui a des exigences de sécurité particulièrement strictes. Ils ont ajouté un serveur SIEM à leur environnement pour tirer parti de la protection de sécurité supplémentaire dont ils ont besoin.

## <a name="siem-server-integration-with-microsoft-365"></a>Intégration du serveur SIEM à Microsoft 365

Un serveur SIEM peut recevoir des données d’un large éventail de services et d’applications Microsoft 365. Le tableau suivant répertorie plusieurs services et applications Microsoft 365, ainsi que les entrées et ressources du serveur SIEM pour en savoir plus.

<br/><br/>

|Microsoft 365 service ou application|Entrées/méthodes du serveur SIEM|Ressources pour en savoir plus|
|---|---|---|
|[Microsoft Defender pour Office 365](defender-for-office-365.md)|Journaux d'audit|[Intégration de SIEM à Microsoft Defender pour Office 365](siem-integration-with-office-365-ti.md)|
|[Microsoft Defender pour point de terminaison](/windows/security/threat-protection/)|Point de terminaison HTTPS hébergé dans Azure <p> API REST|[Extraire des alertes vers vos outils SIEM](../defender-endpoint/configure-siem.md)|
|[Microsoft Defender for Cloud Apps](/cloud-app-security/what-is-cloud-app-security)|Intégration des journaux|[Intégration de SIEM à Microsoft Defender for Cloud Apps](/cloud-app-security/siem)|

> [!TIP]
> Jetez un coup d’œil à [Microsoft Sentinel](/azure/sentinel/overview). Microsoft Sentinel est fourni avec des connecteurs pour les solutions Microsoft. Ces connecteurs sont disponibles « out of the box » et fournissent une intégration en temps réel. Vous pouvez utiliser Microsoft Sentinel avec vos solutions Microsoft 365 Defender et vos services Microsoft 365, notamment Office 365, Azure AD, Microsoft Defender pour Identity, Microsoft Defender for Cloud Apps, et bien plus encore.

### <a name="audit-logging-must-be-turned-on"></a>La journalisation d’audit doit être activée

Vérifiez que la journalisation d’audit est activée avant de configurer l’intégration du serveur SIEM.

- Pour SharePoint Online, OneDrive Entreprise et Azure Active Directory, consultez [Activer ou désactiver l’audit](../../compliance/turn-audit-log-search-on-or-off.md).
- Pour Exchange Online, consultez [Gérer l’audit de boîte aux lettres](../../compliance/enable-mailbox-auditing.md).

## <a name="more-resources"></a>Plus de ressources

[Intégrer des solutions de sécurité dans Microsoft Defender pour le cloud](/azure/security-center/security-center-partner-integration#exporting-data-to-a-siem)

[Intégrer les alertes de l’API de sécurité Microsoft Graph avec des technologies SIEM](/graph/security-integration)
