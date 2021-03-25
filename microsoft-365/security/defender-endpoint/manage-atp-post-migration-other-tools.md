---
title: Gérer Microsoft Defender pour le point de terminaison à l’aide de PowerShell, WMI et MPCmdRun.exe
description: Découvrez comment gérer Microsoft Defender for Endpoint avec PowerShell, WMI et MPCmdRun.exe
keywords: post-migration, gérer, opérations, maintenance, utilisation, PowerShell, WMI, MPCmdRun.exe, protection avancée contre les menaces Windows Defender, atp, edr
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
ms.topic: article
ms.date: 09/22/2020
ms.reviewer: chventou
ms.openlocfilehash: 5f0e94360cfaa0c66aedec400e81adc85f4f5450
ms.sourcegitcommit: 6f2288e0c863496dfd0ee38de754bd43096ab3e1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2021
ms.locfileid: "51185872"
---
# <a name="manage-microsoft-defender-for-endpoint-with-powershell-wmi-and-mpcmdrunexe"></a>Gérer Microsoft Defender pour le point de terminaison avec PowerShell, WMI et MPCmdRun.exe

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez découvrir Microsoft Defender pour le point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink)

> [!NOTE]
> Nous vous recommandons [d’utiliser Microsoft Endpoint Manager](https://docs.microsoft.com/mem) pour gérer les fonctionnalités de protection contre les menaces de votre organisation pour les appareils (également appelés points de terminaison). Endpoint Manager inclut [Microsoft Intune](https://docs.microsoft.com/mem/intune/fundamentals/what-is-intune) et [Microsoft Endpoint Configuration Manager.](https://docs.microsoft.com/mem/configmgr/core/understand/introduction) 
> - [En savoir plus sur endpoint Manager](https://docs.microsoft.com/mem/endpoint-manager-overview)
> - [Co-gérer Microsoft Defender pour endpoint sur les appareils Windows 10 avec Configuration Manager et Intune](manage-atp-post-migration-intune.md)
> - [Gérer Microsoft Defender pour le point de terminaison avec Intune](manage-atp-post-migration-intune.md) 

Vous pouvez gérer certains paramètres de l’Antivirus Microsoft Defender sur les appareils avec [PowerShell,](#configure-microsoft-defender-for-endpoint-with-powershell)  [Windows Management Instrumentation](#configure-microsoft-defender-for-endpoint-with-windows-management-instrumentation-wmi) (WMI) et l’utilitaire de ligne de commande Microsoft Malware [Protection](#configure-microsoft-defender-for-endpoint-with-microsoft-malware-protection-command-line-utility-mpcmdrunexe) (MPCmdRun.exe). Par exemple, vous pouvez gérer certains paramètres de l’Antivirus Microsoft Defender. Et, dans certains cas, vous pouvez personnaliser vos règles de réduction de la surface d’attaque et exploiter les paramètres de protection. 

> [!IMPORTANT]
> Les fonctionnalités de protection contre les menaces que vous configurez à l’aide de PowerShell, WMI ou MCPmdRun.exe peuvent être écrasées par des paramètres de configuration déployés avec Intune ou Configuration Manager.

## <a name="configure-microsoft-defender-for-endpoint-with-powershell"></a>Configurer Microsoft Defender pour le point de terminaison avec PowerShell

Vous pouvez utiliser PowerShell pour gérer l’Antivirus Microsoft Defender, Exploit Protection et vos règles de réduction de la surface d’attaque.

|Tâche  |Ressources pour en savoir plus  |
|---------|---------|
|**Gérer l’Antivirus Microsoft Defender** <br/><br/>*Afficher l’état de la protection contre les programmes malveillants, configurer les préférences pour les analyses antivirus & mises à jour et apporter d’autres modifications à votre protection antivirus.*    |[Utiliser les cmdlets PowerShell pour configurer et gérer l’Antivirus Microsoft Defender](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-antivirus/use-powershell-cmdlets-microsoft-defender-antivirus)  <br/><br/>[Utiliser les cmdlets PowerShell pour activer la protection cloud](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-antivirus/enable-cloud-protection-microsoft-defender-antivirus#use-powershell-cmdlets-to-enable-cloud-delivered-protection)       |
|**Configurer Exploit Protection pour** atténuer les menaces sur les appareils de votre organisation<br/><br/> *Nous vous recommandons d’utiliser Exploit Protection en [mode audit](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/evaluate-exploit-protection#powershell) au début. De cette façon, vous pouvez voir l’impact d’Exploit Protection sur les applications utilisées par votre organisation.*     | [Personnaliser Exploit Protection](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/customize-exploit-protection)<br/><br/>[Cmdlets PowerShell pour Exploit Protection](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/customize-exploit-protection#powershell-reference)        |
|**Configurer des règles de réduction de la surface d’attaque** avec PowerShell <br/><br/>*Vous pouvez utiliser PowerShell pour exclure des fichiers et des dossiers des règles de réduction de la surface d’attaque.* |[Personnaliser les règles de réduction de la surface d’attaque : utiliser PowerShell pour exclure des fichiers & dossiers](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/customize-attack-surface-reduction#use-powershell-to-exclude-files-and-folders)<br/><br/>Voir également [l’outil d’interface utilisateur graphique d’Antócée Vasconcelo](https://github.com/anvascon/MDATP_PoSh_Scripts/tree/master/ASR%20GUI)pour définir des règles de réduction de la surface d’attaque avec PowerShell. |
|**Activer la protection réseau** avec PowerShell <br/><br/>*Vous pouvez utiliser PowerShell pour activer la Protection du réseau.* |[Activer la protection du réseau avec PowerShell](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/enable-network-protection#powershell) |
|**Configurer l’accès contrôlé aux dossiers pour** la protection contre les ransomware <br/><br/>*[L’accès contrôlé aux](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/controlled-folders) dossiers est également appelé protection antiransomware.* |[Activer l’accès contrôlé aux dossiers avec PowerShell](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/enable-controlled-folders#powershell) |
|**Configurer le Pare-feu Microsoft Defender** pour bloquer le trafic réseau non autorisé qui circule vers ou hors des appareils de votre organisation |[Administration du Pare-feu Microsoft Defender avec fonctions avancées de sécurité à l’aide Windows PowerShell](https://docs.microsoft.com/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security-administration-with-windows-powershell) |
|**Configurer le chiffrement et BitLocker pour** protéger les informations sur les appareils de votre organisation exécutant Windows |[Guide de référence sur BitLocker PowerShell](https://docs.microsoft.com/powershell/module/bitlocker/?view=win10-ps&preserve-view=true) |

## <a name="configure-microsoft-defender-for-endpoint-with-windows-management-instrumentation-wmi"></a>Configurer Microsoft Defender pour endpoint avec Windows Management Instrumentation (WMI)

WMI est une interface de script qui vous permet de récupérer, modifier et mettre à jour les paramètres. Pour plus d’informations, voir [Utilisation de WMI.](https://docs.microsoft.com/windows/win32/wmisdk/using-wmi) 

|Tâche  |Ressources pour en savoir plus  |
|---------|---------|
|**Activer la protection cloud sur** un appareil    |[Utiliser Windows Management Instruction (WMI) pour activer la protection cloud](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-antivirus/enable-cloud-protection-microsoft-defender-antivirus#use-windows-management-instruction-wmi-to-enable-cloud-delivered-protection)       |
|**Récupérer, modifier et mettre à jour les paramètres de** l’Antivirus Microsoft Defender     | [Utiliser WMI pour configurer et gérer l’Antivirus Microsoft Defender](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-antivirus/use-wmi-microsoft-defender-antivirus)<br/><br/>[Passer en revue la liste des classes WMI disponibles et des exemples de scripts](https://docs.microsoft.com/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal) <br/><br/>Voir également les informations de Windows Defender de référence du fournisseur [WMIv2 archivés](https://docs.microsoft.com/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal?redirectedfrom=MSDN)   |


## <a name="configure-microsoft-defender-for-endpoint-with-microsoft-malware-protection-command-line-utility-mpcmdrunexe"></a>Configurer Microsoft Defender pour le point de terminaison avec l’utilitaire Command-Line Protection Microsoft contre les programmes malveillants (MPCmdRun.exe)

Sur un appareil individuel, vous pouvez exécuter une analyse, démarrer le suivi des diagnostics, vérifier les mises à jour de l’intelligence de la sécurité et bien plus encore à l’aide de lmpcmdrun.exe de ligne de commande. Vous pouvez trouver l’utilitaire dans `%ProgramFiles%\Windows Defender\MpCmdRun.exe` . Exécutez-le à partir d’une invite de commandes.

|Tâche  |Ressources pour en savoir plus  |
|---------|---------|
|**Gérer l’Antivirus Microsoft Defender**  |[Configurer et gérer l’Antivirus Microsoft Defender avec mpcmdrun.exe](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-antivirus/command-line-arguments-microsoft-defender-antivirus)        |

## <a name="configure-your-microsoft-defender-security-center"></a>Configurer votre Centre de sécurité Microsoft Defender

Si vous ne l’avez pas déjà fait, configurez votre Centre de sécurité **Microsoft Defender** ( ) pour afficher les alertes, configurer les fonctionnalités de protection contre les menaces et afficher des informations détaillées sur la posture de sécurité globale de votre [https://securitycenter.windows.com](https://securitycenter.windows.com) organisation. 

Vous pouvez également configurer si et quelles fonctionnalités les utilisateurs finaux peuvent voir dans le Centre de sécurité Microsoft Defender.

- [Vue d’ensemble du Centre de sécurité Microsoft Defender](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/use)

- [Protection des points de terminaison : Centre de sécurité Microsoft Defender](https://docs.microsoft.com/mem/intune/protect/endpoint-protection-windows-10#microsoft-defender-security-center)


## <a name="next-steps"></a>Étapes suivantes

- [Obtenir une vue d’ensemble de la gestion des menaces et des vulnérabilités](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt)

- [Visiter le tableau de bord opérations de sécurité du Centre de sécurité Microsoft Defender](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/security-operations-dashboard)

- [Gérer Microsoft Defender pour le point de terminaison avec Intune](manage-atp-post-migration-intune.md)
