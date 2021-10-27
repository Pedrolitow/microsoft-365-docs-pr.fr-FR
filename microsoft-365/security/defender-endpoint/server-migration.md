---
title: Scénarios de migration de serveur pour la nouvelle version de Microsoft Defender for Endpoint
description: Lisez cet article pour obtenir une vue d’ensemble de la migration de vos serveurs de la solution MMA précédente vers le package de solution unifiée Defender for Endpoint actuel.
keywords: migrer serveur, serveur, 2012r2, 2016, migration de serveur, gestion des appareils, configurer Microsoft Defender pour les serveurs endpoint, intégrer Microsoft Defender pour les serveurs endpoint
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
author: mjcaparas
ms.author: macapara
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: b2bf0bd7f1d20e65921a3d5ee503152b3d3940fb
ms.sourcegitcommit: da11ffdf7a09490313dfc603355799f80b0c60f9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/26/2021
ms.locfileid: "60586992"
---
# <a name="server-migration-scenarios-from-the-previous-mma-based-microsoft-defender-for-endpoint-solution"></a>Scénarios de migration de serveur de la solution Microsoft Defender pour point de terminaison MMA précédente

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- Windows Server 2012 R2
- Windows Server 2016

[!include[Prerelease information](../../includes/prerelease.md)]

> [!NOTE]
> Assurez-vous toujours Antivirus Microsoft Defender mise à jour complète sur Windows Server 2016 avant de poursuivre l’installation ou la mise à niveau. Pour recevoir des améliorations et des correctifs de produit réguliers pour le composant capteur PEPT, assurez-vous Windows mise à jour [KB5005292](https://go.microsoft.com/fwlink/?linkid=2168277) est appliquée ou approuvée. En outre, pour que les composants de protection restent à jour, veuillez référencer Gérer Antivirus Microsoft Defender mises à jour [et appliquer les lignes de base.](/microsoft-365/security/defender-endpoint/manage-updates-baselines-microsoft-defender-antivirus#monthly-platform-and-engine-versions)

Ces instructions s’appliquent à la nouvelle solution unifiée et au nouveau package d’installation de Microsoft Defender for Endpoint pour Windows Server 2012 R2 et Windows Server 2016. Cet article contient des instructions de haut niveau pour différents scénarios de migration possibles de la solution précédente à la solution actuelle. Ces étapes de haut niveau sont destinées à être ajustées aux outils de déploiement et de configuration disponibles dans votre environnement.

> [!NOTE]
> Les mises à niveau du système d’exploitation avec Microsoft Defender pour le point de terminaison installé ne sont pas pris en charge. Désinstallez-le avant de procéder à une mise à niveau.

> [!NOTE]
> Pendant la prévisualisation, Microsoft Endpoint Configuration Manager l’automatisation et l’intégration pour effectuer une mise à niveau automatisée seront disponibles dans la version 2111 de MECM. À partir de la version 2107, vous pouvez utiliser le nœud Endpoint Protection pour la configuration, ainsi que pour la stratégie de groupe, PowerShell, l’attachement Microsoft Endpoint Manager client ou la configuration locale. En outre, vous pouvez tirer parti des fonctionnalités existantes dans Microsoft Endpoint Configuration Manager automatiser les étapes de mise à niveau manuelle. pour lesquelles sont décrites ci-dessous.

## <a name="installer-script"></a>Script du programme d’installation

Pour faciliter les mises à niveau lorsque Microsoft Endpoint Configuration Manager ou Azure Defender ne sont pas en cours d’utilisation ou ne sont pas encore disponibles pour effectuer la mise à niveau, vous pouvez utiliser ce [script de mise à niveau.](https://github.com/microsoft/mdefordownlevelserver) Elle peut vous aider à automatiser les étapes requises suivantes :

1. Supprimez l’espace de travail OMS pour Microsoft Defender pour le point de terminaison (FACULTATIF).
2. Supprimez System Center Endpoint Protection client s’il est installé.
3. Téléchargez et installez (Windows Server 2012 [R2)](configure-server-endpoints.md#prerequisites) si nécessaire.
4. Installez Microsoft Defender pour le point de terminaison.
5. Appliquez le script **d’intégration à utiliser avec la** stratégie de groupe téléchargée à partir [Centre de sécurité Microsoft Defender](https://securitycenter.microsoft.com).

Pour utiliser le script, téléchargez-le dans un répertoire d’installation où vous avez également placé les packages d’installation et d’intégration (voir Configurer les points de terminaison [du serveur).](configure-server-endpoints.md)

EXEMPLE : .\install.ps1 -RemoveMMA <YOUR_WORKSPACE_ID> -OnboardingScript « .\WindowsDefenderATPOnboardingScript.cmd »

## <a name="microsoft-endpoint-configuration-manager-migration-scenarios"></a>Microsoft Endpoint Configuration Manager de migration 

### <a name="you-are-currently-using-microsoft-endpoint-configuration-manager-to-manage-your-servers-including-system-center-endpoint-protection-scep-and-are-running-the-microsoft-monitoring-agent-mma-based-sensor-you-want-to-upgrade-to-the-microsoft-defender-for-endpoint-unified-solution-preview"></a>Vous utilisez actuellement Microsoft Endpoint Configuration Manager pour gérer vos serveurs, notamment System Center Endpoint Protection (SCEP) et exécutez le capteur Microsoft Monitoring Agent (MMA). Vous souhaitez mettre à niveau vers l’aperçu de **solution** unifiée Microsoft Defender for Endpoint.

>[!NOTE]
>Vous aurez besoin Microsoft Endpoint Configuration Manager version 2107.


Étapes de migration : 

1. Mettez entièrement à jour l’ordinateur, Antivirus Microsoft Defender (Windows Server 2016).
2. Créez une collection avec des règles d’appartenance pour inclure les ordinateurs à migrer.
3. [Créez une application](/mem/configmgr/apps/deploy-use/create-applications) pour effectuer les tâches suivantes : 
   1. Supprimez la configuration de l’espace de travail MMA pour Microsoft Defender pour le point de terminaison. Voir [Supprimer un espace de travail à l’aide de PowerShell.](/azure/azure-monitor/agents/agent-manage) Cette étape est facultative . l’PEPT précédent cesse de s’exécute une fois que le nouveau capteur devient actif (notez que cela peut prendre plusieurs heures).
   2. Désinstallez SCEP.
   3. Installez les [conditions préalables le](configure-server-endpoints.md#prerequisites) cas échéant.
   4. Installez Microsoft Defender pour le point de terminaison (voir [Configurer les points de terminaison du serveur).](configure-server-endpoints.md)
   5. Appliquez le script **d’intégration à utiliser avec la** stratégie de groupe téléchargée à partir [Centre de sécurité Microsoft Defender](https://securitycenter.microsoft.com). 

   > [!TIP]
   > Vous pouvez utiliser le [script d’installation](server-migration.md#installer-script) dans le cadre de votre application pour automatiser les étapes ci-dessus.
4. Déployez l’application sur la nouvelle collection.
5. Créer et/ou affecter des stratégies de Endpoint Protection à la collection.
6. Appliquer les mises à jour.

### <a name="you-are-currently-using-microsoft-endpoint-configuration-manager-to-manage-your-servers-are-running-a-non-microsoft-antivirus-solution-and-the-mma-based-sensor-you-want-to-upgrade-to-the-new-microsoft-defender-for-endpoint"></a>Vous utilisez actuellement Microsoft Endpoint Configuration Manager pour gérer vos serveurs, exécutez une solution antivirus non Microsoft et le capteur MMA. Vous souhaitez mettre à niveau vers le nouveau microsoft Defender pour le point de terminaison.

Étapes de migration :

1. Mettez entièrement à jour l’ordinateur, Antivirus Microsoft Defender (Windows Server 2016).
2. Créez une collection avec des règles d’appartenance pour inclure les ordinateurs à migrer. 
3. Assurez-vous que la gestion de l’antivirus tiers n’insérait plus d’antivirus sur ces ordinateurs.*
4. Créez vos stratégies dans le Endpoint Protection de MECM et ciblez la collection nouvellement créée.*
5. Créez une application pour effectuer les tâches suivantes :
   1. Supprimez la configuration de l’espace de travail MMA pour Microsoft Defender pour le point de terminaison. Voir [Supprimer un espace de travail à l’aide de PowerShell.](/azure/azure-monitor/agents/agent-manage) Cette étape est facultative . l’PEPT précédent cesse de s’exécute une fois que le nouveau capteur devient actif (notez que cela peut prendre plusieurs heures).
   2. Installez les [conditions préalables le](configure-server-endpoints.md#prerequisites) cas échéant.
   3. Installez Microsoft Defender for Endpoint pour Windows Server 2012 package R2 et 2016 et **activez le mode passif.** Voir [Installer Antivirus Microsoft Defender à l’aide de la ligne de commande.](configure-server-endpoints.md#install-microsoft-defender-for-endpoint-using-command-line)
   4. Appliquez le script **d’intégration à utiliser avec la** stratégie de groupe téléchargée à partir [Centre de sécurité Microsoft Defender](https://securitycenter.microsoft.com).
6. Appliquer les mises à jour.
7. Supprimez votre logiciel antivirus non-Microsoft à l’aide de la console antivirus non-Microsoft ou en utilisant Microsoft Endpoint Configuration Manager le cas échéant. Veillez à supprimer la configuration du mode passif.*

CONSEIL : vous pouvez utiliser le [script d’installation](server-migration.md#installer script) dans le cadre de votre application pour automatiser les étapes ci-dessus. Pour activer le mode passif, appliquez l’indicateur -Passive. EXEMPLE : .\install.ps1 -RemoveMMA <YOUR_WORKSPACE_ID> -OnboardingScript « .\WindowsDefenderATPOnboardingScript.cmd » -Passive

*Ces étapes s’appliquent uniquement si vous avez l’intention de remplacer votre solution antivirus non-Microsoft. Voir [Mieux ensemble : Antivirus Microsoft Defender et Microsoft Defender pour le point de terminaison.](why-use-microsoft-defender-antivirus.md)


Pour sortir un ordinateur du mode passif, définissez la clé suivante sur 0 : 

Chemin d’accès : HKLM\SOFTWARE\Policies\Microsoft\Windows Nom de la protection avancée contre les menaces : ForceDefenderPassiveMode Type : REG_DWORD valeur : 0

Pour plus d’informations, [voir Need to set Antivirus Microsoft Defender to passive mode?](microsoft-defender-antivirus-on-windows-server.md#passive-mode-and-windows-server).


## <a name="other-migration-scenarios"></a>Autres scénarios de migration 

### <a name="you-have-a-server-that-has-been-onboarded-using-the-mma-based-microsoft-defender-for-endpoint-it-has-scep-installed-windows-server-2012-r2-or-microsoft-defender-antivirus-windows-server-2016-this-machine-is-not-managed-through-azure-defender-microsoft-endpoint-manager-or-microsoft-endpoint-configuration-manager"></a>Vous disposez d’un serveur qui a été intégré à l’aide de Microsoft Defender for Endpoint basé sur MMA. ScEP est installé (Windows Server 2012 R2) ou Antivirus Microsoft Defender (Windows Server 2016). Cet ordinateur **n’est pas** géré via Azure Defender, Microsoft Endpoint Manager ou Microsoft Endpoint Configuration Manager.

1. Mettez entièrement à jour l’ordinateur, Antivirus Microsoft Defender (Windows Server 2016).
2. Supprimez la configuration de l’espace de travail MMA pour Microsoft Defender pour le point de terminaison. Voir [Supprimer un espace de travail à l’aide de PowerShell.](/azure/azure-monitor/agents/agent-manage)
3. Désinstaller System Center Endpoint Protection (Windows Server 2012 R2).
4. Installez les [conditions préalables le](configure-server-endpoints.md#prerequisites) cas échéant. 
5. Installez Microsoft Defender pour le point de terminaison (voir [Configurer les points de terminaison du serveur).)](configure-server-endpoints.md)
6. Appliquez le script **d’intégration à utiliser avec la** stratégie de groupe téléchargée à partir [Centre de sécurité Microsoft Defender](https://securitycenter.microsoft.com). 
7. Appliquer les mises à jour.
8. Créez et appliquez des stratégies à l’aide d’une stratégie de groupe, de PowerShell ou d’une solution de gestion tierce.

> [!TIP]
> Vous pouvez utiliser le script d’installation pour automatiser les étapes ci-dessus.

### <a name="you-have-a-server-on-which-you-want-to-install-microsoft-defender-for-endpoint-it-has-a-non-microsoft-endpoint-protection-or-endpoint-detection-and-response-solution-installed-you-do-not-intend-to-use-microsoft-endpoint-configuration-manager-or-azure-defender-you-use-your-own-deployment-mechanism"></a>Vous avez un serveur sur lequel vous souhaitez installer Microsoft Defender pour le point de terminaison. Il dispose d’une solution de protection de point de terminaison non-Microsoft protection évolutive des points de terminaison solution installée. Vous n’avez pas l’intention d’utiliser Microsoft Endpoint Configuration Manager ou Azure Defender. Vous utilisez votre propre mécanisme de déploiement. 

1. Mettez entièrement à jour l’ordinateur, Antivirus Microsoft Defender (Windows Server 2016).
2. Installez microsoft Defender pour le point de terminaison pour Windows Server 2012 package R2 & 2016 et **activez le mode passif.** Voir [Installer Antivirus Microsoft Defender à l’aide de la ligne de commande.](configure-server-endpoints.md#install-microsoft-defender-for-endpoint-using-command-line)
3. Appliquez le script d’intégration, approprié à votre environnement, téléchargé à partir [de Centre de sécurité Microsoft Defender](https://securitycenter.microsoft.com). 
4. Supprimez la solution de protection de point de terminaison ou de protection évolutive des points de terminaison Non-Microsoft et supprimez le mode passif.*
5. Appliquer les mises à jour.
6. Créez et appliquez des stratégies à l’aide d’une stratégie de groupe, de PowerShell ou d’une solution de gestion tierce.

> [!TIP]
> Vous pouvez utiliser le [script d’installation](server-migration.md#installer-script) pour automatiser les étapes 1 à 4. Pour activer le mode passif, appliquez l’indicateur -Passive qui garantit que Defender passe en mode passif avant l’intégration et n’interfère pas avec une solution anti-programme malveillant non Microsoft. Ensuite, pour vous assurer que l’Antivirus Defender reste en mode passif après l’intégration pour prendre en charge les fonctionnalités PEPT telles que PEPT Block, veillez à définir la clé de Registre « ForceDefenderPassiveMode ». EXEMPLE : `.\install.ps1 -OnboardingScript ".\WindowsDefenderATPOnboardingScript.cmd" -Passive` Pour plus d’informations, [voir Need to set Antivirus Microsoft Defender to passive mode?](microsoft-defender-antivirus-on-windows-server.md#passive-mode-and-windows-server).

*Cette étape s’applique uniquement si vous avez l’intention de remplacer votre solution antivirus non-Microsoft. Nous vous recommandons d Antivirus Microsoft Defender, inclus dans Microsoft Defender pour Endpoint, pour fournir l’ensemble complet des fonctionnalités. Voir [Mieux ensemble : Antivirus Microsoft Defender et Microsoft Defender pour le point de terminaison.](why-use-microsoft-defender-antivirus.md) 


Pour sortir un ordinateur du mode passif, définissez la clé suivante sur 0 : 

Chemin d’accès : HKLM\SOFTWARE\Policies\Microsoft\Windows Nom de la protection avancée contre les menaces : ForceDefenderPassiveMode Type : REG_DWORD valeur : 0

Pour plus d’informations, [voir Need to set Antivirus Microsoft Defender to passive mode?](microsoft-defender-antivirus-on-windows-server.md#passive-mode-and-windows-server).

## <a name="azure-defender-scenarios"></a>Scénarios Azure Defender

### <a name="youre-using-azure-defender-the-microsoft-monitoring-agent-mma-andor-microsoft-antimalware-for-azure-scep-are-installed-and-you-want-to-upgrade"></a>Vous utilisez Azure Defender. Les Microsoft Monitoring Agent (MMA) et/ou Microsoft Antimalware pour Azure (SCEP) sont installés et vous souhaitez mettre à niveau.
Si vous utilisez Azure Defender, vous pouvez tirer parti du processus de mise à niveau automatisée. Voir [Protéger vos points de terminaison à l’aide](/azure/security-center/security-center-wdatp#enable-the-microsoft-defender-for-endpoint-integration)de la solution PEPT intégrée du Centre de sécurité : Microsoft Defender pour point de terminaison.

## <a name="group-policy-configuration"></a>Configuration de la stratégie de groupe
Pour la configuration à l’aide de la stratégie de groupe, assurez-vous que vous utilisez les derniers fichiers ADMX de votre magasin central pour accéder aux options de stratégie Microsoft Defender correctes. Veuillez [référencer comment créer et](/troubleshoot/windows-client/group-policy/create-and-manage-central-store) gérer le magasin central pour les modèles d’administration de stratégie de groupe dans Windows et télécharger les fichiers les plus récents à utiliser avec **Windows 10**. 

