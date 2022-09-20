---
title: Scénarios de migration de serveur pour la nouvelle version de Microsoft Defender pour point de terminaison
description: Lisez cet article pour obtenir une vue d’ensemble de la migration de vos serveurs de la solution MMA précédente vers le package de solution unifiée Defender pour point de terminaison actuel.
keywords: migrate server, server, 2012r2, 2016, server migration, device management, configure Microsoft Defender pour point de terminaison servers, onboard Microsoft Defender pour point de terminaison servers
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
author: mjcaparas
ms.author: macapara
ms.localizationpriority: medium
ms.date: 09/19/2022
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.subservice: mde
ms.openlocfilehash: 602b80f93d4c2c9b0f204eaa347a5f5e75941147
ms.sourcegitcommit: 95ac076310ab9006ed92c69938f7ae771cd10826
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2022
ms.locfileid: "67850383"
---
# <a name="server-migration-scenarios-from-the-previous-mma-based-microsoft-defender-for-endpoint-solution"></a>Scénarios de migration de serveur de la solution de Microsoft Defender pour point de terminaison MMA précédente

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- Windows Server 2012 R2
- Windows Server 2016
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

> [!NOTE]
> Assurez-vous toujours que le système d’exploitation et l’Antivirus Microsoft Defender sur Windows Server 2016 sont entièrement mis à jour avant de poursuivre l’installation ou la mise à niveau. Pour recevoir régulièrement des améliorations et des correctifs du produit pour le composant capteur EDR, assurez-vous que Windows Update [KB5005292](https://go.microsoft.com/fwlink/?linkid=2168277) est appliqué ou approuvé après l’installation. En outre, pour mettre à jour les composants de protection, consultez [Gérer les mises à jour de l’Antivirus Microsoft Defender et appliquez des lignes de base](/microsoft-365/security/defender-endpoint/manage-updates-baselines-microsoft-defender-antivirus#monthly-platform-and-engine-versions).

Ces instructions s’appliquent au nouveau package de Microsoft Defender pour point de terminaison de solution unifiée et de programme d’installation (MSI) pour Windows Server 2012 R2 et Windows Server 2016. Cet article contient des instructions générales pour différents scénarios de migration possibles de la solution précédente à la solution actuelle. Ces étapes générales sont destinées à être ajustées aux outils de déploiement et de configuration disponibles dans votre environnement. 

**Si vous utilisez Microsoft Defender pour cloud pour effectuer le déploiement, vous pouvez automatiser l’installation et la mise à niveau. Voir [Defender pour serveurs Plan 2 s’intègre désormais à la solution unifiée MDE](https://techcommunity.microsoft.com/t5/microsoft-defender-for-cloud/defender-for-servers-plan-2-now-integrates-with-mde-unified/ba-p/3527534)**

> [!NOTE]
> Les mises à niveau du système d’exploitation avec Microsoft Defender pour point de terminaison installées ne sont pas prises en charge. Veuillez désinstaller et désinstaller, mettre à niveau le système d’exploitation, puis procéder à l’installation.

> [!NOTE]
> L’automatisation et l’intégration complètes du point de terminaison Microsoft Configuration Manager pour effectuer une mise à niveau automatisée seront disponibles dans une version ultérieure de MECM. À partir de la version 2107 avec le dernier correctif cumulatif, vous pouvez utiliser le nœud Endpoint Protection pour la configuration, ainsi que pour stratégie de groupe, PowerShell, l’attachement de locataire Microsoft Endpoint Manager ou la configuration locale. En outre, vous pouvez tirer parti des fonctionnalités existantes dans Microsoft Endpoint Configuration Manager pour automatiser les étapes de mise à niveau manuelles; méthodes pour lesquelles vous trouverez ci-dessous.

## <a name="installer-script"></a>Script du programme d’installation

>[!NOTE]
>Assurez-vous que les machines sur laquelle vous exécutez le script ne bloquent pas l’exécution du script. Le paramètre de stratégie d’exécution recommandé pour PowerShell est Allsigned. Cela nécessite l’importation du certificat de signature du script dans le magasin serveurs de publication approuvés de l’ordinateur local si le script s’exécute en tant que système sur le point de terminaison.

Pour faciliter les mises à niveau lorsque Microsoft Endpoint Configuration Manager n’est pas encore disponible ou mis à jour pour effectuer la mise à niveau automatisée, vous pouvez utiliser ce [script de mise à niveau](https://github.com/microsoft/mdefordownlevelserver). Téléchargez-le en sélectionnant le bouton « Code » et en téléchargeant le fichier .zip, puis en extrayant install.ps1. Il peut vous aider à automatiser les étapes requises suivantes :

1. Supprimez l’espace de travail OMS pour Microsoft Defender pour point de terminaison (FACULTATIF).
2. Supprimez le client System Center Endpoint Protection (SCEP) s’il est installé.
3. Téléchargez et installez les [prérequis](configure-server-endpoints.md#prerequisites) (Windows Server 2012 R2) si nécessaire.
4. Installez Microsoft Defender pour point de terminaison.
5. Appliquez le script d’intégration **à utiliser avec stratégie de groupe** téléchargé à partir de [Microsoft 365 Defender](https://security.microsoft.com).

Pour utiliser le script, téléchargez-le dans un répertoire d’installation où vous avez également placé les packages d’installation et d’intégration (voir [Configurer les points de terminaison de serveur](configure-server-endpoints.md)).

EXEMPLE : .\install.ps1 -RemoveMMA <YOUR_WORKSPACE_ID> -OnboardingScript « .\WindowsDefenderATPOnboardingScript.cmd »

Pour plus d’informations sur l’utilisation du script, utilisez la commande PowerShell « get-help .\install.ps1 ».

## <a name="microsoft-endpoint-configuration-manager-migration-scenarios"></a>Scénarios de migration de Configuration Manager de point de terminaison Microsoft 

>[!NOTE]
>Vous aurez besoin de Microsoft Endpoint Configuration Manager, version 2107 ou ultérieure pour la configuration de stratégie Endpoint Protection.

Pour obtenir des instructions sur la migration à l’aide du point de terminaison Microsoft Configuration Manager antérieure à la version 2207, consultez [Migration de serveurs de Microsoft Monitoring Agent vers la solution unifiée.](/microsoft-365/security/defender-endpoint/application-deployment-via-mecm)

## <a name="if-you-are-running-a-non-microsoft-antivirus-solution"></a>Si vous exécutez une solution antivirus non-Microsoft

1. Mettez entièrement à jour l’ordinateur, y compris l’antivirus Microsoft Defender (Windows Server 2016), en veillant à ce que [les conditions préalables soient remplies](configure-server-endpoints.md#prerequisites). Pour plus d’informations sur les conditions préalables à respecter, consultez [Conditions préalables pour Windows Server 2016](configure-server-endpoints.md#prerequisites-for-windows-server-2016).
2. Assurez-vous que la gestion des antivirus tiers n’envoie plus d’agents antivirus à ces machines.*
3. Créez vos stratégies pour les fonctionnalités de protection dans Microsoft Defender pour point de terminaison et ciblez-les sur l’ordinateur dans l’outil de votre choix.*
4. Installez le Microsoft Defender pour point de terminaison pour Windows Server 2012 package R2 et 2016 et **activez le mode passif**. Consultez [Installer l’antivirus Microsoft Defender à l’aide de la ligne de commande](configure-server-endpoints.md#install-microsoft-defender-for-endpoint-using-the-command-line).
   a. Appliquez le script d’intégration **à utiliser avec stratégie de groupe** téléchargé à partir de [Microsoft 365 Defender](https://security.microsoft.com).
5. Appliquer les mises à jour.
6. Supprimez votre logiciel antivirus non-Microsoft à l’aide de la console antivirus non-Microsoft ou à l’aide du point de terminaison Microsoft Configuration Manager le cas échéant. Veillez à supprimer la configuration du mode passif.*

> [!TIP]
> Vous pouvez utiliser le [script d’installation](server-migration.md#installer script) dans le cadre de votre application pour automatiser les étapes ci-dessus. Pour activer le mode passif, appliquez l’indicateur -Passive. Par exemple, .\install.ps1 -RemoveMMA <YOUR_WORKSPACE_ID> -OnboardingScript « .\WindowsDefenderATPOnboardingScript.cmd » -Passive

*Ces étapes s’appliquent uniquement si vous envisagez de remplacer votre solution antivirus non-Microsoft. Voir [Mieux ensemble : Antivirus Microsoft Defender et Microsoft Defender pour point de terminaison](why-use-microsoft-defender-antivirus.md).

Pour sortir une machine du mode passif, définissez la clé suivante sur 0 :

Chemin d’accès : HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection Name: ForceDefenderPassiveMode Type: REG_DWORD Value: 0

## <a name="if-you-are-running-system-center-endpoint-protection-but-are-not-managing-the-machine-using-microsoft-endpoint-configuration-manager-mecmconfigmgr"></a>Si vous exécutez System Center Endpoint Protection mais que vous ne gérez pas la machine à l’aide de Microsoft Endpoint Configuration Manager (MECM/ConfigMgr)

1. Mettez entièrement à jour l’ordinateur, y compris l’antivirus Microsoft Defender (Windows Server 2016), en veillant à ce que [les conditions préalables soient remplies](configure-server-endpoints.md#prerequisites).
2. Créez et appliquez des stratégies à l’aide d’stratégie de groupe, de PowerShell ou d’une solution de gestion tierce.
3. Désinstallez System Center Endpoint Protection (Windows Server 2012 R2).
5. Installer Microsoft Defender pour point de terminaison (voir [Configurer les points de terminaison de serveur](configure-server-endpoints.md)).)
6. Appliquez le script d’intégration **à utiliser avec stratégie de groupe** téléchargé à partir de [Microsoft 365 Defender](https://security.microsoft.com). 
7. Appliquer les mises à jour.

> [!TIP]
> Vous pouvez utiliser le script du programme d’installation pour automatiser les étapes ci-dessus.

## <a name="microsoft-defender-for-cloud-scenarios"></a>Scénarios Microsoft Defender pour le cloud

### <a name="youre-using-microsoft-defender-for-cloud-the-microsoft-monitoring-agent-mma-andor-microsoft-antimalware-for-azure-scep-are-installed-and-you-want-to-upgrade"></a>Vous utilisez Microsoft Defender pour cloud. Microsoft Monitoring Agent (MMA) et/ou Microsoft Antimalware pour Azure (SCEP) sont installés et vous souhaitez effectuer une mise à niveau.
Si vous utilisez Microsoft Defender pour cloud, vous pouvez tirer parti du processus de mise à niveau automatisé. Consultez [Protéger vos points de terminaison avec la solution EDR intégrée de Defender pour Cloud : Microsoft Defender pour point de terminaison](/azure/security-center/security-center-wdatp#enable-the-microsoft-defender-for-endpoint-integration).

## <a name="group-policy-configuration"></a>configuration stratégie de groupe
Pour la configuration à l’aide de stratégie de groupe, vérifiez que vous utilisez les derniers fichiers ADMX de votre magasin central pour accéder aux options de stratégie Defender pour point de terminaison correctes. Reportez-vous [à la rubrique How to create and manage the Central Store for stratégie de groupe Administrative Templates in Windows](/troubleshoot/windows-client/group-policy/create-and-manage-central-store) et téléchargez les derniers fichiers **à utiliser avec Windows 10**.
