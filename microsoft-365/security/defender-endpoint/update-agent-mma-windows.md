---
title: Mettre à jour votre agent sur les appareils pour Microsoft Defender pour point de terminaison
description: Découvrez les options de mise à jour ou de remplacement de votre agent MMA sur les appareils Windows pour Defender pour point de terminaison.
keywords: MMA, agent, journal Azure
ms.service: microsoft-365-security
ms.subservice: mde
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: deniseb
author: denisebmsft
ms.localizationpriority: medium
ms.date: 10/24/2022
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- tier2
ms.topic: conceptual
ms.reviewer: pahuijbr
search.appverid: met150
ms.openlocfilehash: 48642c497be5b379e5d72c4e6538ffd1997b30bf
ms.sourcegitcommit: e7dbe3b0d97cd8c64b5ae15f990d5e4b1dc9c464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2022
ms.locfileid: "68688947"
---
# <a name="updating-mma-on-windows-devices-for-microsoft-defender-for-endpoint"></a>Mise à jour de MMA sur les appareils Windows pour Microsoft Defender pour point de terminaison

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Si vous utilisez Microsoft Monitoring Agent (MMA) sur des appareils Windows, vous devez maintenir cet agent à jour. Avec l’agent moderne et unifié pour Windows Server 2012 R2 et Windows Server 2016, vous devez plutôt migrer vers la nouvelle solution. 

- [Mettre à jour Microsoft Monitoring Agent (MMA) sur vos appareils](#option-1-update-mma-on-your-devices)
- [Utiliser un nouvel agent sur Windows Server 2012 R2 ou Windows Server 2016](#option-2-use-a-new-agent-on-windows-server-2012-r2-or-windows-server-2016)

Cet article décrit les deux options et inclut des liens vers des informations supplémentaires.

## <a name="option-1-update-mma-on-your-devices"></a>Option 1 : Mettre à jour MMA sur vos appareils

*Cette option s’applique aux appareils exécutant Windows 7 SP1 Entreprise, Windows 7 SP1 Professionnel, Windows 8.1 Professionnel, Windows 8.1 Entreprise et Windows Server 2008 R2 SP1.* 

- Consultez [Gérer et gérer l’agent Log Analytics pour Windows et Linux](/azure/azure-monitor/agents/agent-manage?tabs=PowerShellLinux) pour obtenir des instructions sur la mise à niveau de l’agent à l’aide de Azure Automation ou d’une approche en ligne de commande à utiliser avec différents outils et méthodes de déploiement à votre disposition. 

- Mettez à jour MMA à l’aide de [Microsoft Update](/windows/deployment/update/how-windows-update-works), via [Windows Server Update Services](/windows/deployment/update/waas-manage-updates-wsus) ou [Configuration Manager](/mem/configmgr/osd/deploy-use/manage-windows-as-a-service). Utilisez la méthode qui a été configurée lors de la première installation de MMA sur l’appareil.

- Téléchargez le fichier d’installation de MMA :

   - **Agent Windows 64 bits** : [https://go.microsoft.com/fwlink/?LinkId=828603](https://go.microsoft.com/fwlink/?LinkId=828603)
   - **Agent Windows 32 bits** : [https://go.microsoft.com/fwlink/?LinkId=828604](https://go.microsoft.com/fwlink/?LinkId=828604)

## <a name="option-2-use-a-new-agent-on-windows-server-2012-r2-or-windows-server-2016"></a>Option 2 : Utiliser un nouvel agent sur Windows Server 2012 R2 ou Windows Server 2016

*Cette option s’applique aux serveurs exécutant Windows Server 2012 R2 et Windows Server 2016.*

Un nouvel agent a été publié en avril 2022 pour Windows Server 2012 R2 et Windows Server 2016. Le nouvel agent ne dépend pas de MMA. Le passage à ce nouvel agent présente des avantages significatifs, tels qu’un ensemble de fonctionnalités largement étendu. Pour en savoir plus, consultez [blog de la communauté technique : Défendre les Windows Server 2012 R2 et 2016](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/defending-windows-server-2012-r2-and-2016/ba-p/2783292).

- Gestion des vulnérabilités Microsoft Defender fournit une évaluation (SCID-2030) intitulée « Mettre à jour Microsoft Defender pour point de terminaison composants principaux » qui vous permettra de suivre les Windows Server 2012  Les machines R2 et 2016 n’ont pas encore été mises à niveau.

- Consultez [Scénarios de migration de serveur de la solution de Microsoft Defender pour point de terminaison MMA précédente](server-migration.md) pour comprendre les options de mise à niveau vers le nouvel agent.

- Si vous utilisez Microsoft Endpoint Configuration Manager (SCCM/ConfigMgr) 2107 ou version ultérieure pour gérer vos serveurs exécutant Windows Server 2012 R2 ou Windows Server 2016, consultez [Migration de serveurs de Microsoft Monitoring Agent vers la solution unifiée](application-deployment-via-mecm.md) pour effectuer une mise à niveau **orchestrée**.

- Si vous utilisez Microsoft Endpoint Configuration Manager (SCCM/ConfigMgr) 2207 ou version ultérieure pour gérer vos serveurs exécutant Windows Server 2012 R2 ou Windows Server 2016, consultez [Intégration à Microsoft Defender pour point de terminaison avec Configuration Manager 2207 et versions ultérieures](/mem/configmgr/protect/deploy-use/defender-advanced-threat-protection) pour effectuer une mise à niveau **automatisée**.

- Si vous utilisez Microsoft Defender pour le cloud avec des serveurs exécutant Windows Server 2012 R2 ou Windows Server 2016, vous pouvez automatiser la mise à niveau en sélectionnant **Activer la solution unifiée**. Consultez [Utilisateurs avec Defender pour serveurs activé et Microsoft Defender pour point de terminaison déployé](/azure/defender-for-cloud/integration-defender-for-endpoint?tabs=windows).

## <a name="important-information-about-mma"></a>Informations importantes sur MMA

- Si vous avez déterminé que vous n’utilisez pas MMA pour Defender pour point de terminaison, ou si vous avez déjà mis à jour votre agent, aucune autre étape n’est nécessaire. 

- Toutefois, si vous utilisez toujours MMA à d’autres fins (comme Log Analytics), MMA est actuellement mis hors service en août 2024. Consultez [Nous mettons hors service l’agent Log Analytics dans Azure Monitor le 31 août 2024](https://azure.microsoft.com/updates/were-retiring-the-log-analytics-agent-in-azure-monitor-on-31-august-2024/). Selon votre scénario particulier, il peut s’agir d’un bon moment pour effectuer une mise à niveau vers [Azure Monitoring Agent, le successeur de MMA](/azure/azure-monitor/agents/azure-monitor-agent-migration). 

> [!IMPORTANT]
> Les appareils exécutant Windows 7 SP1, Windows 8.1, Windows Server 2008 R2, Windows Server 2012 R2 ou Windows Server 2016 qui n’ont pas été mis à niveau vers la [nouvelle solution unifiée](application-deployment-via-mecm.md) restent dépendants de MMA. Dans ce cas, [AMA](/azure/azure-monitor/agents/agents-overview) ne peut pas être utilisé comme substitut de Defender pour point de terminaison. 