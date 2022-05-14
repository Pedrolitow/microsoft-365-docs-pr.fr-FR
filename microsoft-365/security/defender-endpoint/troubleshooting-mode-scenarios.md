---
title: Scénarios de mode de dépannage dans Microsoft Defender pour point de terminaison
description: Utilisez le mode de résolution des problèmes Microsoft Defender pour point de terminaison pour résoudre différents problèmes antivirus.
keywords: antivirus, résolution des problèmes, mode de résolution des problèmes, protection contre les falsifications, compatibilité
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: b62ed508640fcf9523c768d2af8e038e4d269e85
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2022
ms.locfileid: "65420055"
---
# <a name="troubleshooting-mode-scenarios-in-microsoft-defender-for-endpoint"></a>Scénarios de mode de dépannage dans Microsoft Defender pour point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-configureendpointsscript-abovefoldlink)


Microsoft Defender pour point de terminaison mode de résolution des problèmes vous permet de résoudre les problèmes liés aux différentes fonctionnalités de l’antivirus Microsoft Defender en les activant à partir de l’appareil et en testant différents scénarios, même s’ils sont contrôlés par la stratégie d’organisation. Le mode de résolution des problèmes est désactivé par défaut et vous oblige à l’activer pour un appareil (et/ou un groupe d’appareils) pendant une durée limitée. Notez qu’il s’agit exclusivement d’une fonctionnalité Enterprise et nécessite un accès Microsoft 365 Defender.

## <a name="scenario-1-unable-to-install-application"></a>Scénario 1 : Impossible d’installer l’application

Si vous souhaitez installer une application mais recevez un message d’erreur indiquant que Antivirus Microsoft Defender et la protection contre les falsifications sont activées, suivez les étapes ci-dessous pour résoudre le problème.

1. Demandez à l’administrateur SOC d’activer le mode de résolution des problèmes. Vous recevrez une notification de Sécurité Windows une fois le mode de résolution des problèmes démarré.  

2. Connecter à l’appareil (à l’aide de Terminal Services par exemple) avec des autorisations d’administrateur local.  

3. Démarrer le moniteur de processus (ProcMon). Consultez les étapes décrites dans [Résoudre les problèmes de performances liés à la protection en temps réel](troubleshoot-performance-issues.md).  

4. Accédez à **Windows securityThreat** >  **& virus protectionManage** >  **settingsTamper** >  **protectionOff** > .  

5. Lancez une invite de commandes PowerShell avec élévation de privilèges et désactivez RTP. 

    - Exécuter `get-mppreference` pour vérifier l’état RTP.
    - Exécuter `set–mppreference` pour désactiver l’exécution RTP. 

6. Essayez d’installer l’application.

## <a name="scenario-2-high-cpu-usage-due-to-windows-defender-msmpengexe"></a>Scénario 2 : Utilisation élevée du processeur en raison de Windows Defender (MsMpEng.exe)

Parfois, lors d’une analyse planifiée, MsMpEng.exe pouvez consommer un processeur élevé.

1. Accédez à l’onglet **Task** **ManagerDetails** >  pour confirmer que MsMpEng.exe est la raison de l’utilisation élevée du processeur. Vérifiez également si une analyse planifiée est en cours.

2. Exécutez ProcMon pendant le pic du processeur pendant environ 5 minutes, puis examinez le journal ProcMon pour obtenir des indices. 

3. Une fois la cause racine déterminée, activez le mode de résolution des problèmes. 

4. Connectez-vous à la machine et lancez une invite de commandes PowerShell avec élévation de privilèges. 

5. Ajoutez des exclusions de processus/de fichier/de dossier/d’extension basées sur les résultats de ProcMon à l’aide de l’une des commandes suivantes (le chemin d’accès, l’extension et les exclusions de processus mentionnés ci-dessous sont uniquement des exemples) : 

    - Set-mppreference -ExclusionPath (par exemple, C:\DB\DataFiles) 
    
    - Set-mppreference –ExclusionExtension (par exemple, .dbx) 
    
    - Set-mppreference –ExclusionProcess (par exemple, C:\DB\Bin\Convertdb.exe) 

6. Après avoir ajouté l’exclusion, vérifiez si l’utilisation de l’UC a diminué. 

Pour plus d’informations sur Set-MpPreference préférences de configuration des applets de commande pour les analyses et mises à jour Windows Defender, consultez [Set-MpPreference](/powershell/module/defender/set-mppreference). 

## <a name="scenario-3-application-taking-longer-to-perform-an-action"></a>Scénario 3 : L’application prend plus de temps pour effectuer une action

Lorsque Antivirus Microsoft Defender protection en temps réel est activée, l’application prend beaucoup de temps pour effectuer des tâches de base. Pour désactiver la protection en temps réel et résoudre le problème, suivez les étapes ci-dessous. 

1. Demandez à l’administrateur SOC d’activer le mode de résolution des problèmes sur l’appareil. 

2. Pour désactiver RTP pour ce scénario, commencez par désactiver la protection contre les falsifications. Pour plus d’informations, consultez [Protéger les paramètres de sécurité avec la protection contre les falsifications](prevent-changes-to-security-settings-with-tamper-protection.md). 

3. Une fois la protection contre les falsifications désactivée, connectez-vous à l’appareil. 

4. Lancez une invite de commandes PowerShell avec élévation de privilèges. 

    - Set-mppreference -DisableRealtimeMonitoring $true 

5. Après avoir désactivé RTP, vérifiez si l’application est lente. 

## <a name="scenario-4-microsoft-office-plugin-blocked-by-attack-surface-reduction"></a>Scénario 4 : Microsoft Office plug-in bloqué par la réduction de la surface d’attaque

La réduction de la surface d’attaque (ASR) n’autorise pas Microsoft Office plug-in à fonctionner correctement, car **empêcher toutes les applications Office de créer des processus enfants** est défini sur le mode bloquer. 

1. Activez le mode de résolution des problèmes et connectez-vous à l’appareil. 

2. Lancez une invite de commandes PowerShell avec élévation de privilèges. 

    - Set-MpPreference -AttackSurfaceReductionRules_Ids D4F940AB-401B-4EFC-AADC-AD5F3C50688A -AttackSurfaceReductionRules_Actions désactivé 

3. Après avoir désactivé la règle ASR, vérifiez que le plug-in Microsoft Office fonctionne désormais.

Pour plus d’informations, consultez [Vue d’ensemble de la réduction de la surface d’attaque](overview-attack-surface-reduction.md). 

## <a name="scenario-5-domain-blocked-by-network-protection"></a>Scénario 5 : Domaine bloqué par la protection réseau

La protection réseau bloque le domaine Microsoft, empêchant les utilisateurs d’y accéder. 

1. Activez le mode de résolution des problèmes et connectez-vous à l’appareil. 

2. Lancez une invite de commandes PowerShell avec élévation de privilèges. 

    - Set-MpPreference -EnableNetworkProtection Désactivé 

3. Après la désactivation de la protection réseau, vérifiez si le domaine est maintenant autorisé. 

Pour plus d’informations, consultez [Utiliser la protection réseau pour empêcher les connexions à des sites incorrects](network-protection.md). 

## <a name="related-topics"></a>Voir aussi

- [Activer le mode de résolution des problèmes](enable-troubleshooting-mode.md)
- [Protéger les paramètres de sécurité avec la protection contre la falsifiation](prevent-changes-to-security-settings-with-tamper-protection.md)
- [Set-MpPreference](/powershell/module/defender/set-mppreference)
- [Protéger votre réseau](network-protection.md)
- [Vue d’ensemble de la réduction de la surface d'attaque](overview-attack-surface-reduction.md)
- [Détecter et bloquer des applications potentiellement indésirables](detect-block-potentially-unwanted-apps-microsoft-defender-antivirus.md)
- [Obtenir une vue d’ensemble de Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/)
- [Mieux ensemble : Antivirus Microsoft Defender et Microsoft Defender pour point de terminaison](why-use-microsoft-defender-antivirus.md)