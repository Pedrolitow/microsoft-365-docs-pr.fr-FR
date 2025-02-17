---
title: Gérer Microsoft Defender pour point de terminaison après l’installation ou la migration initiale
description: Maintenant que vous avez effectué le basculement vers Microsoft Defender pour point de terminaison, l’étape suivante consiste à gérer vos fonctionnalités de protection contre les menaces
keywords: post-migration, gérer, opérations, maintenance, utilisation, Microsoft Defender pour point de terminaison, edr
ms.service: microsoft-365-security
ms.subservice: mde
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: deniseb
author: denisebmsft
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- tier2
ms.topic: conceptual
ms.date: 07/01/2022
ms.reviewer: chventou
search.appverid: met150
ms.openlocfilehash: 879a5881ecf34c74a1f7cffb774a85bc734eec0d
ms.sourcegitcommit: 4e42bafee965446f44f7f57d1defed2b9b24fce8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2022
ms.locfileid: "68225061"
---
# <a name="manage-microsoft-defender-for-endpoint-after-initial-setup-or-migration"></a>Gérer Microsoft Defender pour point de terminaison après l’installation ou la migration initiale

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Une fois que vous avez configuré et configuré Microsoft Defender pour point de terminaison, l’étape suivante consiste à gérer vos fonctionnalités et fonctionnalités. Nous vous recommandons d’utiliser [Microsoft Endpoint Manager](/mem/endpoint-manager-overview), qui inclut [Microsoft Intune](/mem/intune/fundamentals/what-is-intune) et Configuration Manager de [point](/mem/configmgr/core/understand/introduction) de terminaison Microsoft, pour gérer les appareils et les paramètres de sécurité de votre organisation. Toutefois, vous pouvez utiliser d’autres outils/méthodes, tels que [stratégie de groupe Objects dans Azure services de domaine Active Directory](/azure/active-directory-domain-services/manage-group-policy).

Le tableau suivant répertorie les différents outils/méthodes que vous pouvez utiliser, avec des liens pour en savoir plus.

|Outil/méthode|Description|
|---|---|
|**[Gestion des vulnérabilités Microsoft Defender insights du tableau de bord](/windows/security/threat-protection/microsoft-defender-atp/tvm-dashboard-insights)** dans le portail [Microsoft 365 Defender](https://security.microsoft.com/)|Le tableau de bord Gestion des vulnérabilités Defender fournit des informations exploitables que votre équipe des opérations de sécurité peut utiliser pour réduire l’exposition et améliorer la posture de sécurité de votre organisation. <br/><br/> Consultez [Gestion des vulnérabilités defender](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt) et [vue d’ensemble de Microsoft 365 Defender](/microsoft-365/security/defender-endpoint/use).|
|**[Microsoft Intune](/mem/intune/fundamentals/what-is-intune)** (recommandé)|Microsoft Intune (Intune), un composant de [Microsoft Endpoint Manager](/mem/endpoint-manager-overview), se concentre sur la gestion des appareils mobiles (GPM) et la gestion des applications mobiles (GAM). Avec Intune, vous contrôlez la façon dont les appareils de votre organisation sont utilisés, notamment les téléphones mobiles, les tablettes et les ordinateurs portables. Vous pouvez également configurer des stratégies spécifiques pour contrôler les applications. <br/><br/> Consultez [Gérer les Microsoft Defender pour point de terminaison à l’aide de Intune](manage-mde-post-migration-intune.md).|
|**[Microsoft Endpoint Configuration Manager](/mem/configmgr/core/understand/introduction)**|Microsoft Endpoint Manager (Configuration Manager), anciennement appelé System Center Configuration Manager, est un composant de [Microsoft Endpoint Manager](/mem/endpoint-manager-overview). Configuration Manager est un outil puissant pour gérer vos utilisateurs, appareils et logiciels. <br/><br/> Consultez [Gérer les Microsoft Defender pour point de terminaison avec Configuration Manager](manage-mde-post-migration-configuration-manager.md).|
|**[objets stratégie de groupe dans Azure services de domaine Active Directory](/azure/active-directory-domain-services/manage-group-policy)**|[Azure services de domaine Active Directory](/azure/active-directory-domain-services/overview) inclut des objets stratégie de groupe intégrés pour les utilisateurs et les appareils. Vous pouvez personnaliser les objets stratégie de groupe intégrés en fonction des besoins de votre environnement, ainsi que créer des objets stratégie de groupe personnalisés et des unités d’organisation (UO). <br/><br/> Consultez [Gérer les Microsoft Defender pour point de terminaison avec des objets stratégie de groupe](manage-mde-post-migration-group-policy-objects.md).|
|**[PowerShell, WMI et MPCmdRun.exe](manage-mde-post-migration-other-tools.md)**|*Nous vous recommandons d’utiliser Microsoft Endpoint Manager (qui inclut Intune et Configuration Manager) pour gérer les fonctionnalités de protection contre les menaces sur les appareils de votre organisation. Toutefois, vous pouvez configurer certains paramètres, tels que Microsoft Defender paramètres antivirus sur des appareils individuels (points de terminaison) avec PowerShell, WMI ou l’outil MPCmdRun.exe.* <br/><br/> Vous pouvez utiliser PowerShell pour gérer Microsoft Defender Antivirus, exploit protection et vos règles de réduction de la surface d’attaque. Voir [Configurer Microsoft Defender pour point de terminaison avec PowerShell](manage-mde-post-migration-other-tools.md#configure-microsoft-defender-for-endpoint-with-powershell). <br/><br/> Vous pouvez utiliser Windows Management Instrumentation (WMI) pour gérer Microsoft Defender Antivirus et les exclusions. Consultez [Configurer Microsoft Defender pour point de terminaison avec WMI](manage-mde-post-migration-other-tools.md#configure-microsoft-defender-for-endpoint-with-windows-management-instrumentation-wmi). <br/><br/> Vous pouvez utiliser l’utilitaire microsoft malware protection Command-Line (MPCmdRun.exe) pour gérer Microsoft Defender antivirus et les exclusions, ainsi que valider les connexions entre votre réseau et le cloud. Voir [Configurer Microsoft Defender pour point de terminaison avec MPCmdRun.exe](manage-mde-post-migration-other-tools.md#configure-microsoft-defender-for-endpoint-with-microsoft-malware-protection-command-line-utility-mpcmdrunexe).|


## <a name="see-also"></a>Voir aussi

- [Résoudre des faux négatifs/positifs dans Microsoft Defender pour point de terminaison](defender-endpoint-false-positives-negatives.md)
