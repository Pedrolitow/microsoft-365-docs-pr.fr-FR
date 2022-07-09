---
title: Scénarios de migration de serveur pour la nouvelle version de Microsoft Defender pour point de terminaison
description: Lisez cet article pour obtenir une vue d’ensemble de la migration de vos serveurs de la solution MMA précédente vers le package de solution unifiée Defender pour point de terminaison actuel.
keywords: migrate server, server, 2012r2, 2016, server migration, device management, configure Microsoft Defender pour point de terminaison servers, onboard Microsoft Defender pour point de terminaison servers
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
author: mjcaparas
ms.author: macapara
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: dca4745b5058ed7b98bf0821e2b715393f7bf77f
ms.sourcegitcommit: 2aa5c026cc06ed39a9c1c2bcabd1f563bf5a1859
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2022
ms.locfileid: "66695963"
---
# <a name="server-migration-scenarios-from-the-previous-mma-based-microsoft-defender-for-endpoint-solution"></a>Scénarios de migration de serveur de la solution de Microsoft Defender pour point de terminaison MMA précédente

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- Windows Server 2012 R2
- Windows Server 2016
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

[!include[Prerelease information](../../includes/prerelease.md)]

> [!NOTE]
> Assurez-vous toujours que le système d’exploitation et l’Antivirus Microsoft Defender sur Windows Server 2016 sont entièrement mis à jour avant de poursuivre l’installation ou la mise à niveau. Pour recevoir régulièrement des améliorations et des correctifs du produit pour le composant capteur EDR, assurez-vous que Windows Update [KB5005292](https://go.microsoft.com/fwlink/?linkid=2168277) est appliqué ou approuvé après l’installation. En outre, pour mettre à jour les composants de protection, consultez [Gérer les mises à jour de l’Antivirus Microsoft Defender et appliquez des lignes de base](/microsoft-365/security/defender-endpoint/manage-updates-baselines-microsoft-defender-antivirus#monthly-platform-and-engine-versions).

Ces instructions s’appliquent au nouveau package de Microsoft Defender pour point de terminaison de solution unifiée et de programme d’installation (MSI) pour Windows Server 2012 R2 et Windows Server 2016. Cet article contient des instructions générales pour différents scénarios de migration possibles de la solution précédente à la solution actuelle. Ces étapes générales sont destinées à être ajustées aux outils de déploiement et de configuration disponibles dans votre environnement. 

**Si vous utilisez Microsoft Defender pour cloud pour effectuer le déploiement, vous pouvez automatiser l’installation et la mise à niveau. Voir [Defender pour serveurs Plan 2 s’intègre désormais à la solution unifiée MDE](https://techcommunity.microsoft.com/t5/microsoft-defender-for-cloud/defender-for-servers-plan-2-now-integrates-with-mde-unified/ba-p/3527534)**

> [!NOTE]
> Les mises à niveau du système d’exploitation avec Microsoft Defender pour point de terminaison installées ne sont pas prises en charge. Désinstallez-la avant de procéder à une mise à niveau.

> [!NOTE]
> L’automatisation et l’intégration complètes du point de terminaison Microsoft Configuration Manager pour effectuer une mise à niveau automatisée seront disponibles dans une version ultérieure de MECM. À partir de la version 2107 avec le dernier correctif cumulatif, vous pouvez utiliser le nœud Endpoint Protection pour la configuration, ainsi que pour stratégie de groupe, PowerShell, l’attachement de locataire Microsoft Endpoint Manager ou la configuration locale. En outre, vous pouvez tirer parti des fonctionnalités existantes dans Microsoft Endpoint Configuration Manager pour automatiser les étapes de mise à niveau manuelles; méthodes pour lesquelles vous trouverez ci-dessous.

## <a name="installer-script"></a>Script du programme d’installation

Pour faciliter les mises à niveau lorsque Microsoft Endpoint Configuration Manager n’est pas encore disponible ou mis à jour pour effectuer la mise à niveau automatisée, vous pouvez utiliser ce [script de mise à niveau](https://github.com/microsoft/mdefordownlevelserver). Il peut vous aider à automatiser les étapes requises suivantes :

1. Supprimez l’espace de travail OMS pour Microsoft Defender pour point de terminaison (FACULTATIF).
2. Supprimez le client System Center Endpoint Protection (SCEP) s’il est installé.
3. Téléchargez et installez les [prérequis](configure-server-endpoints.md#prerequisites) (Windows Server 2012 R2) si nécessaire.
4. Installez Microsoft Defender pour point de terminaison.
5. Appliquez le script d’intégration **à utiliser avec stratégie de groupe** téléchargé à partir de [Microsoft 365 Defender](https://security.microsoft.com).

Pour utiliser le script, téléchargez-le dans un répertoire d’installation où vous avez également placé les packages d’installation et d’intégration (voir [Configurer les points de terminaison de serveur](configure-server-endpoints.md).

EXEMPLE : .\install.ps1 -RemoveMMA <YOUR_WORKSPACE_ID> -OnboardingScript « .\WindowsDefenderATPOnboardingScript.cmd »

## <a name="microsoft-endpoint-configuration-manager-migration-scenarios"></a>Scénarios de migration de Configuration Manager de point de terminaison Microsoft 

>[!NOTE]
>Vous aurez besoin de Microsoft Endpoint Configuration Manager, version 2107 ou ultérieure pour la configuration de stratégie Endpoint Protection.

Étapes de migration : 

1. Mettez entièrement à jour la machine, y compris l’antivirus Microsoft Defender (Windows Server 2016).
2. Créez une collection avec des règles d’appartenance pour inclure les machines à migrer.
3. [Créez une application](/mem/configmgr/apps/deploy-use/create-applications) pour effectuer les tâches suivantes : 
   1. Désinstallez SCEP.
   2. Installez les [prérequis](configure-server-endpoints.md#prerequisites) le cas échéant.
   3. Installez Microsoft Defender pour point de terminaison (voir [Configurer les points de terminaison de serveur](configure-server-endpoints.md).
   4. Appliquez le script d’intégration **à utiliser avec stratégie de groupe** téléchargé à partir de [Microsoft 365 Defender](https://security.microsoft.com). 
   > [!TIP]
   > Vous pouvez utiliser le [script du programme d’installation](server-migration.md#installer-script) dans le cadre de votre application pour automatiser les étapes ci-dessus.
4. Déployez l’application dans la nouvelle collection.
5. Créez et/ou attribuez des stratégies Endpoint Protection (existantes) à la collection.
6. Appliquer les mises à jour.

### <a name="you-are-currently-using-microsoft-endpoint-configuration-manager-to-manage-your-servers-are-running-a-non-microsoft-antivirus-solution-and-the-mma-based-sensor-you-want-to-upgrade-to-the-new-microsoft-defender-for-endpoint"></a>Vous utilisez actuellement Microsoft Endpoint Configuration Manager pour gérer vos serveurs, exécutez une solution antivirus non Microsoft et le capteur MMA. Vous souhaitez effectuer une mise à niveau vers la nouvelle Microsoft Defender pour point de terminaison.

Étapes de migration :

1. Mettez entièrement à jour la machine, y compris l’antivirus Microsoft Defender (Windows Server 2016).
2. Créez une collection avec des règles d’appartenance pour inclure les machines à migrer. 
3. Assurez-vous que la gestion des antivirus tiers n’envoie plus d’antivirus à ces machines.*
4. Créez vos stratégies dans le nœud Endpoint Protection de MECM et ciblez la collection nouvellement créée.*
5. Créez une application pour effectuer les tâches suivantes :
   1. Supprimez la configuration de l’espace de travail MMA pour Microsoft Defender pour point de terminaison. Consultez [Supprimer un espace de travail à l’aide de PowerShell](/azure/azure-monitor/agents/agent-manage). Cette étape est facultative ; le capteur EDR précédent cessera de s’exécuter une fois que le plus récent sera actif.
   2. Installez les [prérequis](configure-server-endpoints.md#prerequisites) le cas échéant.
   3. Installez le Microsoft Defender pour point de terminaison pour Windows Server 2012 package R2 et 2016 et **activez le mode passif**. Consultez [Installer l’antivirus Microsoft Defender à l’aide de la ligne de commande](configure-server-endpoints.md#install-microsoft-defender-for-endpoint-using-the-command-line).
   4. Appliquez le script d’intégration **à utiliser avec stratégie de groupe** téléchargé à partir de [Microsoft 365 Defender](https://security.microsoft.com).
6. Appliquer les mises à jour.
7. Supprimez votre logiciel antivirus non-Microsoft à l’aide de la console antivirus non-Microsoft ou à l’aide du point de terminaison Microsoft Configuration Manager le cas échéant. Veillez à supprimer la configuration du mode passif.*

> [!TIP]
> Vous pouvez utiliser le [script d’installation](server-migration.md#installer script) dans le cadre de votre application pour automatiser les étapes ci-dessus. Pour activer le mode passif, appliquez l’indicateur -Passive. Par exemple, .\install.ps1 -RemoveMMA <YOUR_WORKSPACE_ID> -OnboardingScript « .\WindowsDefenderATPOnboardingScript.cmd » -Passive

*Ces étapes s’appliquent uniquement si vous envisagez de remplacer votre solution antivirus non-Microsoft. Voir [Mieux ensemble : Antivirus Microsoft Defender et Microsoft Defender pour point de terminaison](why-use-microsoft-defender-antivirus.md).

Pour sortir une machine du mode passif, définissez la clé suivante sur 0 :

Chemin d’accès : HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection Name: ForceDefenderPassiveMode Type: REG_DWORD Value: 0

Pour plus d’informations sur la migration de serveurs de MMA vers une solution unifiée, consultez [Migration de serveurs de Microsoft Monitoring Agent vers la solution unifiée](application-deployment-via-mecm.md).

## <a name="other-migration-scenarios"></a>Autres scénarios de migration

### <a name="you-have-a-server-that-has-been-onboarded-using-the-mma-based-microsoft-defender-for-endpoint-it-has-scep-installed-windows-server-2012-r2-or-microsoft-defender-antivirus-windows-server-2016-this-machine-is-not-managed-through-microsoft-defender-for-cloud-microsoft-endpoint-manager-or-microsoft-endpoint-configuration-manager"></a>Vous disposez d’un serveur qui a été intégré à l’aide de la Microsoft Defender pour point de terminaison basée sur MMA. ScEP est installé (Windows Server 2012 R2) ou l’antivirus Microsoft Defender (Windows Server 2016). Cette machine **n’est pas** gérée via Microsoft Defender pour le cloud, Microsoft Endpoint Manager ou Microsoft Endpoint Configuration Manager.

1. Mettez entièrement à jour la machine, y compris l’antivirus Microsoft Defender (Windows Server 2016).
2. Supprimez la configuration de l’espace de travail MMA pour Microsoft Defender pour point de terminaison. Consultez [Supprimer un espace de travail à l’aide de PowerShell](/azure/azure-monitor/agents/agent-manage).
3. Désinstallez System Center Endpoint Protection (Windows Server 2012 R2).
4. Installez les [prérequis](configure-server-endpoints.md#prerequisites) le cas échéant. 
5. Installer Microsoft Defender pour point de terminaison (voir [Configurer les points de terminaison de serveur](configure-server-endpoints.md)).)
6. Appliquez le script d’intégration **à utiliser avec stratégie de groupe** téléchargé à partir de [Microsoft 365 Defender](https://security.microsoft.com). 
7. Appliquer les mises à jour.
8. Créez et appliquez des stratégies à l’aide d’stratégie de groupe, de PowerShell ou d’une solution de gestion tierce.

> [!TIP]
> Vous pouvez utiliser le script du programme d’installation pour automatiser les étapes ci-dessus.

### <a name="you-have-a-server-on-which-you-want-to-install-microsoft-defender-for-endpoint-it-has-a-non-microsoft-endpoint-protection-or-endpoint-detection-and-response-solution-installed-you-do-not-intend-to-use-microsoft-endpoint-configuration-manager-or-microsoft-defender-for-cloud-you-use-your-own-deployment-mechanism"></a>Vous disposez d’un serveur sur lequel vous souhaitez installer Microsoft Defender pour point de terminaison. Une solution de détection et de réponse de point de terminaison ou de détection de point de terminaison non Microsoft est installée. Vous n’avez pas l’intention d’utiliser Microsoft Endpoint Configuration Manager ou Microsoft Defender pour cloud. Vous utilisez votre propre mécanisme de déploiement. 

1. Mettez entièrement à jour la machine, y compris l’antivirus Microsoft Defender (Windows Server 2016).
2. Installez le Microsoft Defender pour point de terminaison pour Windows Server 2012 package R2 & 2016 et **activez le mode passif**. Consultez [Installer l’antivirus Microsoft Defender à l’aide de la ligne de commande](configure-server-endpoints.md#install-microsoft-defender-for-endpoint-using-the-command-line).
3. Appliquez le script d’intégration, approprié à votre environnement, téléchargé à partir de [Microsoft 365 Defender](https://security.microsoft.com). 
4. Supprimez la solution de protection ou de réponse de point de terminaison ou de détection de point de terminaison non Microsoft, puis supprimez le mode passif.*
5. Appliquer les mises à jour.
6. Créez et appliquez des stratégies à l’aide d’stratégie de groupe, de PowerShell ou d’une solution de gestion tierce.

> [!TIP]
> Vous pouvez utiliser le [script du programme d’installation](server-migration.md#installer-script) pour automatiser les étapes 1 à 4. Pour activer le mode passif, appliquez l’indicateur -Passive qui garantit que l’antivirus Defender passe en mode passif avant l’intégration et n’interfère pas avec une solution anti-programme malveillant non Microsoft. Ensuite, pour vous assurer que l’Antivirus Defender reste en mode passif après l’intégration pour prendre en charge les fonctionnalités EDR telles que le bloc EDR, veillez à définir la clé de Registre « ForceDefenderPassiveMode ». EXEMPLE: `.\install.ps1 -OnboardingScript ".\WindowsDefenderATPOnboardingScript.cmd" -Passive`


*Cette étape s’applique uniquement si vous envisagez de remplacer votre solution antivirus non-Microsoft. Nous vous recommandons d’utiliser l’antivirus Microsoft Defender, inclus dans Microsoft Defender pour point de terminaison, pour fournir l’ensemble complet des fonctionnalités. Voir [Mieux ensemble : Antivirus Microsoft Defender et Microsoft Defender pour point de terminaison](why-use-microsoft-defender-antivirus.md).

Pour sortir une machine du mode passif, définissez la clé suivante sur 0 :

Chemin d’accès : HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection Name: ForceDefenderPassiveMode Type: REG_DWORD Value: 0


## <a name="microsoft-defender-for-cloud-scenarios"></a>Scénarios Microsoft Defender pour le cloud

### <a name="youre-using-microsoft-defender-for-cloud-the-microsoft-monitoring-agent-mma-andor-microsoft-antimalware-for-azure-scep-are-installed-and-you-want-to-upgrade"></a>Vous utilisez Microsoft Defender pour cloud. Microsoft Monitoring Agent (MMA) et/ou Microsoft Antimalware pour Azure (SCEP) sont installés et vous souhaitez effectuer une mise à niveau.
Si vous utilisez Microsoft Defender pour cloud, vous pouvez tirer parti du processus de mise à niveau automatisé. Consultez [Protéger vos points de terminaison avec la solution EDR intégrée de Defender pour Cloud : Microsoft Defender pour point de terminaison](/azure/security-center/security-center-wdatp#enable-the-microsoft-defender-for-endpoint-integration).

## <a name="group-policy-configuration"></a>configuration stratégie de groupe
Pour la configuration à l’aide de stratégie de groupe, vérifiez que vous utilisez les derniers fichiers ADMX de votre magasin central pour accéder aux options de stratégie Defender pour point de terminaison correctes. Reportez-vous [à la rubrique How to create and manage the Central Store for stratégie de groupe Administrative Templates in Windows](/troubleshoot/windows-client/group-policy/create-and-manage-central-store) et téléchargez les derniers fichiers **à utiliser avec Windows 10**.
