---
title: Gérer Microsoft Defender for Endpoint après la migration
description: Maintenant que vous avez effectué le basculement vers Microsoft Defender pour le point de terminaison, l’étape suivante consiste à gérer vos fonctionnalités de protection contre les menaces.
keywords: post-migration, gérer, opérations, maintenance, utilisation, protection avancée contre les menaces Windows Defender, atp, edr
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
ms.openlocfilehash: 54302f38f0fd63560ecd1c5545efa4621c6b9bbd
ms.sourcegitcommit: 6f2288e0c863496dfd0ee38de754bd43096ab3e1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2021
ms.locfileid: "51185860"
---
# <a name="manage-microsoft-defender-for-endpoint-post-migration"></a>Gérer Microsoft Defender pour le point de terminaison, après la migration

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez découvrir Microsoft Defender pour le point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink)

Une fois que vous avez passé de votre solution antivirus et de protection de point de terminaison précédente à Microsoft Defender pour le point de terminaison, l’étape suivante consiste à gérer vos fonctionnalités et fonctionnalités. Nous vous recommandons d’utiliser [Microsoft Endpoint Manager,](https://docs.microsoft.com/mem/endpoint-manager-overview)qui inclut [Microsoft Intune](https://docs.microsoft.com/mem/intune/fundamentals/what-is-intune) et [Microsoft Endpoint Configuration Manager,](https://docs.microsoft.com/mem/configmgr/core/understand/introduction)pour gérer les appareils et les paramètres de sécurité de votre organisation. Toutefois, vous pouvez utiliser d’autres outils/méthodes, tels que les objets de stratégie de [groupe dans Azure Active Directory Domain Services](https://docs.microsoft.com/azure/active-directory-domain-services/manage-group-policy). 

Le tableau suivant répertorie les différents outils/méthodes que vous pouvez utiliser, avec des liens pour en savoir plus. 
<br/><br/>

|Outil/Méthode  |Description  |
|---------|---------|
|Informations sur le tableau de bord **[de gestion des menaces](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/tvm-dashboard-insights)** et des vulnérabilités dans le Centre de sécurité Microsoft Defender ( [https://securitycenter.windows.com](https://securitycenter.windows.com) ) |Le tableau de bord de gestion & des menaces fournit des informations actionnables que votre équipe en charge des opérations de sécurité peut utiliser pour réduire l’exposition et améliorer la posture de sécurité de votre organisation. <br/><br/>Voir [La gestion & des menaces et](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt) la vue d’ensemble du Centre de sécurité Microsoft [Defender.](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/use)  |
|**[Microsoft Intune](https://docs.microsoft.com/mem/intune/fundamentals/what-is-intune)**  (recommandé)    |Microsoft Intune (Intune), un composant de [Microsoft Endpoint Manager,](https://docs.microsoft.com/mem/endpoint-manager-overview)se concentre sur la gestion des périphériques mobiles (MDM) et la gestion des applications mobiles (MAM). Avec Intune, vous contrôlez l’utilisation des appareils de votre organisation, notamment les téléphones mobiles, les tablettes et les ordinateurs portables. Vous pouvez également configurer des stratégies spécifiques pour contrôler les applications. <br/><br/>Voir [Gérer Microsoft Defender pour le point de terminaison à l’aide d’Intune.](manage-atp-post-migration-intune.md)         |
|**[Microsoft Endpoint Configuration Manager](https://docs.microsoft.com/mem/configmgr/core/understand/introduction)**     |Microsoft Endpoint Manager (Configuration Manager), anciennement appelé System Center Configuration Manager, est un composant de [Microsoft Endpoint Manager](https://docs.microsoft.com/mem/endpoint-manager-overview). Configuration Manager est un outil puissant pour gérer vos utilisateurs, appareils et logiciels.<br/><br/>Voir [Gérer Microsoft Defender pour endpoint avec Configuration Manager.](manage-atp-post-migration-configuration-manager.md)        |
|**[Objets de stratégie de groupe dans les services de domaine Azure Active Directory](https://docs.microsoft.com/azure/active-directory-domain-services/manage-group-policy)** |[Azure Active Directory Domain Services](https://docs.microsoft.com/azure/active-directory-domain-services/overview) inclut des objets de stratégie de groupe intégrés pour les utilisateurs et les appareils. Vous pouvez personnaliser les objets de stratégie de groupe intégrés selon les besoins de votre environnement, ainsi que créer des objets de stratégie de groupe personnalisés et des unités d’organisation. <br/><br/>Voir [Gérer Microsoft Defender pour le point de terminaison avec les objets de stratégie de groupe.](manage-atp-post-migration-group-policy-objects.md) |
|**[PowerShell, WMI et MPCmdRun.exe](manage-atp-post-migration-other-tools.md)** |*Nous vous recommandons d’utiliser Microsoft Endpoint Manager (qui inclut Intune et Configuration Manager) pour gérer les fonctionnalités de protection contre les menaces sur les appareils de votre organisation. Toutefois, vous pouvez configurer certains paramètres, tels que les paramètres de l’Antivirus Microsoft Defender sur des appareils individuels (points de terminaison) avec PowerShell, WMI ou l’outil MPCmdRun.exe.*<br/><br/>Vous pouvez utiliser PowerShell pour gérer l’Antivirus Microsoft Defender, Exploit Protection et vos règles de réduction de la surface d’attaque. Voir [Configurer Microsoft Defender pour le point de terminaison avec PowerShell.](manage-atp-post-migration-other-tools.md#configure-microsoft-defender-for-endpoint-with-powershell)<br/><br/>Vous pouvez utiliser Windows Management Instrumentation (WMI) pour gérer l’Antivirus Microsoft Defender et les exclusions. Voir [Configurer Microsoft Defender pour endpoint avec WMI.](manage-atp-post-migration-other-tools.md#configure-microsoft-defender-for-endpoint-with-windows-management-instrumentation-wmi)<br/><br/>Vous pouvez utiliser l’utilitaire Command-Line de protection microsoft contre les programmes malveillants (MPCmdRun.exe) pour gérer l’Antivirus Microsoft Defender et les exclusions, ainsi que pour valider les connexions entre votre réseau et le cloud. Voir [Configurer Microsoft Defender pour le point de terminaison avec MPCmdRun.exe](manage-atp-post-migration-other-tools.md#configure-microsoft-defender-for-endpoint-with-microsoft-malware-protection-command-line-utility-mpcmdrunexe). |

## <a name="see-also"></a>Voir aussi

- [Corriger les faux positifs/négatifs dans Microsoft Defender pour le point de terminaison](defender-endpoint-false-positives-negatives.md)
