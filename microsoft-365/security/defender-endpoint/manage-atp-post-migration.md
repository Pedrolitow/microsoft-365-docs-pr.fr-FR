---
title: Gérer Microsoft Defender for Endpoint après la migration
description: Maintenant que vous avez effectué le basculement vers Microsoft Defender pour le point de terminaison, l’étape suivante consiste à gérer vos fonctionnalités de protection contre les menaces.
keywords: post-migration, manage, operations, maintenance, utilization, Microsoft Defender for Endpoint, edr
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: deniseb
author: denisebmsft
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
ms.topic: conceptual
ms.date: 01/26/2021
ms.reviewer: chventou
ms.openlocfilehash: 77777de720d369c09f62d4a7e17e8b4cf5a3519b
ms.sourcegitcommit: f88a0ec621e7d9bc5f376eeaf70c8a9800711f88
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2021
ms.locfileid: "59356824"
---
# <a name="manage-microsoft-defender-for-endpoint-post-migration"></a>Gérer Microsoft Defender pour le point de terminaison, après la migration

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Une fois que vous avez passé de votre solution antivirus et de protection de point de terminaison précédente à Microsoft Defender pour le point de terminaison, l’étape suivante consiste à gérer vos fonctionnalités et fonctionnalités. Nous vous recommandons [d’Microsoft Endpoint Manager,](/mem/endpoint-manager-overview)qui inclut [Microsoft Intune](/mem/intune/fundamentals/what-is-intune) et [Microsoft Endpoint Configuration Manager,](/mem/configmgr/core/understand/introduction)pour gérer les appareils et les paramètres de sécurité de votre organisation. Toutefois, vous pouvez utiliser d’autres outils/méthodes, tels que les objets de stratégie de groupe [dans Azure Active Directory Domain Services](/azure/active-directory-domain-services/manage-group-policy).

Le tableau suivant répertorie les différents outils/méthodes que vous pouvez utiliser, avec des liens pour en savoir plus.

<br/><br/>

|Outil/Méthode|Description|
|---|---|
|**[Informations sur les menaces gestion des vulnérabilités tableau de bord](/windows/security/threat-protection/microsoft-defender-atp/tvm-dashboard-insights)** dans le portail [Microsoft 365 Defender](https://security.microsoft.com/) web|Le tableau de bord & gestion des vulnérabilités des menaces fournit des informations actionnables que votre équipe des opérations de sécurité peut utiliser pour réduire l’exposition et améliorer la posture de sécurité de votre organisation. <p> Voir [Threat & gestion des vulnérabilités](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt) et Overview of [Microsoft 365 Defender](/microsoft-365/security/defender-endpoint/use).|
|**[Microsoft Intune](/mem/intune/fundamentals/what-is-intune)** (recommandé)|Microsoft Intune (Intune), un composant de [Microsoft Endpoint Manager,](/mem/endpoint-manager-overview)se concentre sur la gestion des périphériques mobiles (MDM) et la gestion des applications mobiles (MAM). Avec Intune, vous contrôlez l’utilisation des appareils de votre organisation, notamment les téléphones mobiles, les tablettes et les ordinateurs portables. Vous pouvez également configurer des stratégies spécifiques pour contrôler les applications. <p> Voir [Gérer Microsoft Defender pour le point de terminaison à l’aide d’Intune.](manage-atp-post-migration-intune.md)|
|**[Microsoft Endpoint Configuration Manager](/mem/configmgr/core/understand/introduction)**|Microsoft Endpoint Manager (Configuration Manager), anciennement appelé System Center Configuration Manager, est un composant de [Microsoft Endpoint Manager](/mem/endpoint-manager-overview). Configuration Manager est un outil puissant pour gérer vos utilisateurs, appareils et logiciels. <p> Voir [Gérer Microsoft Defender pour endpoint avec Configuration Manager.](manage-atp-post-migration-configuration-manager.md)|
|**[Objets de stratégie de groupe dans Azure Active Directory Domain Services](/azure/active-directory-domain-services/manage-group-policy)**|[Azure Active Directory Domain Services inclut](/azure/active-directory-domain-services/overview) des objets de stratégie de groupe intégrés pour les utilisateurs et les appareils. Vous pouvez personnaliser les objets de stratégie de groupe intégrés selon les besoins de votre environnement, ainsi que créer des objets de stratégie de groupe personnalisés et des unités d’organisation. <p> Voir [Gérer Microsoft Defender pour le point de terminaison avec les objets de stratégie de groupe.](manage-atp-post-migration-group-policy-objects.md)|
|**[PowerShell, WMI et MPCmdRun.exe](manage-atp-post-migration-other-tools.md)**|*Nous vous recommandons d’Microsoft Endpoint Manager (qui inclut Intune et Configuration Manager) pour gérer les fonctionnalités de protection contre les menaces sur les appareils de votre organisation. Toutefois, vous pouvez configurer certains paramètres, tels que les paramètres Antivirus Microsoft Defender sur des appareils individuels (points de terminaison) avec PowerShell, WMI ou l’outil MPCmdRun.exe.* <p> Vous pouvez utiliser PowerShell pour gérer les Antivirus Microsoft Defender, exploit protection et vos règles de réduction de la surface d’attaque. Voir [Configurer Microsoft Defender pour le point de terminaison avec PowerShell.](manage-atp-post-migration-other-tools.md#configure-microsoft-defender-for-endpoint-with-powershell) <p> Vous pouvez utiliser Windows Management Instrumentation (WMI) pour gérer les Antivirus Microsoft Defender et les exclusions. Voir [Configurer Microsoft Defender pour endpoint avec WMI.](manage-atp-post-migration-other-tools.md#configure-microsoft-defender-for-endpoint-with-windows-management-instrumentation-wmi) <p> Vous pouvez utiliser l’utilitaire Command-Line de protection contre les programmes malveillants de Microsoft (MPCmdRun.exe) pour gérer les Antivirus Microsoft Defender et les exclusions, ainsi que pour valider les connexions entre votre réseau et le cloud. Voir [Configurer Microsoft Defender pour le point de terminaison avec MPCmdRun.exe](manage-atp-post-migration-other-tools.md#configure-microsoft-defender-for-endpoint-with-microsoft-malware-protection-command-line-utility-mpcmdrunexe).|

## <a name="see-also"></a>Voir aussi

- [Résoudre des faux négatifs/positifs dans Microsoft Defender pour point de terminaison](defender-endpoint-false-positives-negatives.md)
