---
title: Gérer Microsoft Defender pour le point de terminaison à l’aide de PowerShell, WMI et MPCmdRun.exe
description: Découvrez comment gérer Microsoft Defender for Endpoint avec PowerShell, WMI et MPCmdRun.exe
keywords: post-migration, manage, operations, maintenance, utilization, PowerShell, WMI, MPCmdRun.exe, Microsoft Defender for Endpoint, edr
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
ms.openlocfilehash: b20107b33a0bff72375885b11f205fa915a3b718
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59165012"
---
# <a name="manage-microsoft-defender-for-endpoint-with-powershell-wmi-and-mpcmdrunexe"></a>Gérer Microsoft Defender pour le point de terminaison avec PowerShell, WMI et MPCmdRun.exe

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

> [!NOTE]
> Nous vous recommandons [d’Microsoft Endpoint Manager](/mem) pour gérer les fonctionnalités de protection contre les menaces de votre organisation pour les appareils (également appelés points de terminaison). Endpoint Manager [inclut Microsoft Intune](/mem/intune/fundamentals/what-is-intune) et [Microsoft Endpoint Configuration Manager](/mem/configmgr/core/understand/introduction).
>
> - [En savoir plus sur Endpoint Manager](/mem/endpoint-manager-overview)
> - [Co-gérer Microsoft Defender for Endpoint sur Windows 10 appareils avec Configuration Manager et Intune](manage-atp-post-migration-intune.md)
> - [Gérer Microsoft Defender pour le point de terminaison avec Intune](manage-atp-post-migration-intune.md)

Vous pouvez gérer certains paramètres de Antivirus Microsoft Defender sur les appareils avec [PowerShell,](#configure-microsoft-defender-for-endpoint-with-powershell) [Windows Management Instrumentation](#configure-microsoft-defender-for-endpoint-with-windows-management-instrumentation-wmi) (WMI) et l’utilitaire de ligne de commande Microsoft Malware [Protection](#configure-microsoft-defender-for-endpoint-with-microsoft-malware-protection-command-line-utility-mpcmdrunexe) (MPCmdRun.exe). Par exemple, vous pouvez gérer certains paramètres Antivirus Microsoft Defender paramètres. Et, dans certains cas, vous pouvez personnaliser vos règles de réduction de la surface d’attaque et exploiter les paramètres de protection.

> [!IMPORTANT]
> Les fonctionnalités de protection contre les menaces que vous configurez à l’aide de PowerShell, WMI ou MCPmdRun.exe peuvent être écrasées par des paramètres de configuration déployés avec Intune ou Configuration Manager.

## <a name="configure-microsoft-defender-for-endpoint-with-powershell"></a>Configurer Microsoft Defender pour le point de terminaison avec PowerShell

Vous pouvez utiliser PowerShell pour gérer les Antivirus Microsoft Defender, exploit protection et vos règles de réduction de la surface d’attaque.

|Tâche|Ressources pour en savoir plus|
|---|---|
|**Gérer les Antivirus Microsoft Defender** <p> Afficher l’état de la protection contre les programmes malveillants, configurer les préférences pour les analyses antivirus & mises à jour et apporter d’autres modifications à votre protection antivirus.*|[Utiliser les cmdlets PowerShell pour configurer et gérer les Antivirus Microsoft Defender](/windows/security/threat-protection/microsoft-defender-antivirus/use-powershell-cmdlets-microsoft-defender-antivirus) <p> [Utiliser les cmdlets PowerShell pour activer la protection cloud](/windows/security/threat-protection/microsoft-defender-antivirus/enable-cloud-protection-microsoft-defender-antivirus#use-powershell-cmdlets-to-enable-cloud-delivered-protection)|
|**Configurer Exploit Protection pour** atténuer les menaces sur les appareils de votre organisation <p> *Nous vous recommandons d’utiliser Exploit Protection en [mode audit](/microsoft-365/security/defender-endpoint/evaluate-exploit-protection#powershell) au début. De cette façon, vous pouvez voir l’impact d’Exploit Protection sur les applications utilisées par votre organisation.*|[Personnaliser la protection contre les codes malveillants exploitant une faille de sécurité](/microsoft-365/security/defender-endpoint/customize-exploit-protection) <p> [Cmdlets PowerShell pour Exploit Protection](/microsoft-365/security/defender-endpoint/customize-exploit-protection#powershell-reference)|
|**Configurer des règles de réduction de la surface d’attaque** avec PowerShell <p> *Vous pouvez utiliser PowerShell pour exclure des fichiers et des dossiers des règles de réduction de la surface d’attaque.*|[Personnaliser les règles de réduction de la surface d’attaque : utiliser PowerShell pour exclure des fichiers & dossiers](/microsoft-365/security/defender-endpoint/customize-attack-surface-reduction#use-powershell-to-exclude-files-and-folders) <p> Voir également [l’outil d’interface utilisateur graphique d’Antócée Vasconcelo](https://github.com/anvascon/MDATP_PoSh_Scripts/tree/master/ASR%20GUI)pour définir des règles de réduction de la surface d’attaque avec PowerShell.|
|**Activer la protection du** réseau avec PowerShell <p> *Vous pouvez utiliser PowerShell pour activer la Protection du réseau.*|[Activer la protection du réseau avec PowerShell](/microsoft-365/security/defender-endpoint/enable-network-protection#powershell)|
|**Configurer l’accès contrôlé aux dossiers pour** la protection contre les ransomware <p> *[L’accès contrôlé aux](/microsoft-365/security/defender-endpoint/controlled-folders) dossiers est également appelé protection anti-programme malveillant.*|[Activer l’accès contrôlé aux dossiers avec PowerShell](/microsoft-365/security/defender-endpoint/enable-controlled-folders#powershell)|
|**Configurer le Pare-feu Microsoft Defender** pour bloquer le trafic réseau non autorisé qui circule dans ou hors des appareils de votre organisation|[Administration du Pare-feu Microsoft Defender avec fonctions avancées de sécurité à l’aide Windows PowerShell](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security-administration-with-windows-powershell)|
|**Configurer le chiffrement et BitLocker pour** protéger les informations sur les appareils de votre organisation exécutant Windows|[Guide de référence sur BitLocker PowerShell](/powershell/module/bitlocker/)|

## <a name="configure-microsoft-defender-for-endpoint-with-windows-management-instrumentation-wmi"></a>Configurer Microsoft Defender pour endpoint avec Windows Management Instrumentation (WMI)

WMI est une interface de script qui vous permet de récupérer, modifier et mettre à jour les paramètres. Pour plus d’informations, voir [Utilisation de WMI.](/windows/win32/wmisdk/using-wmi)

|Tâche|Ressources pour en savoir plus|
|---|---|
|**Activer la protection cloud sur** un appareil|[Utiliser Windows Management Instruction (WMI) pour activer la protection cloud](/windows/security/threat-protection/microsoft-defender-antivirus/enable-cloud-protection-microsoft-defender-antivirus#use-windows-management-instruction-wmi-to-enable-cloud-delivered-protection)|
|**Récupérer, modifier et mettre à jour les paramètres** de Antivirus Microsoft Defender|[Utiliser WMI pour configurer et gérer les Antivirus Microsoft Defender] (/windows/security/threat-protection/microsoft-defender-antivirus/use-wmi-microsoft-defender-antivirus <p> [Passer en revue la liste des classes WMI disponibles et des exemples de scripts](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal) <p> Voir également les informations de Windows Defender de référence du fournisseur [WMIv2 archivés](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal?redirectedfrom=MSDN)|

## <a name="configure-microsoft-defender-for-endpoint-with-microsoft-malware-protection-command-line-utility-mpcmdrunexe"></a>Configurer Microsoft Defender pour le point de terminaison avec l’utilitaire Command-Line Protection Microsoft contre les programmes malveillants (MPCmdRun.exe)

Sur un appareil individuel, vous pouvez exécuter une analyse, démarrer le suivi des diagnostics, vérifier les mises à jour de l’intelligence de la sécurité et bien plus encore à l’aide de lmpcmdrun.exe de ligne de commande. Vous pouvez trouver l’utilitaire dans `%ProgramFiles%\Windows Defender\MpCmdRun.exe` . Exécutez-le à partir d’une invite de commandes.

|Tâche|Ressources pour en savoir plus|
|---|---|
|**Gérer les Antivirus Microsoft Defender**|[Configurer et gérer les Antivirus Microsoft Defender avec mpcmdrun.exe](/windows/security/threat-protection/microsoft-defender-antivirus/command-line-arguments-microsoft-defender-antivirus)|

## <a name="configure-your-microsoft-365-defender-portal"></a>Configurer votre portail Microsoft 365 Defender client

Si ce n’est pas déjà fait, configurez votre portail [Microsoft 365 Defender](https://security.microsoft.com/) pour afficher les alertes, configurer les fonctionnalités de protection contre les menaces et afficher des informations détaillées sur la posture de sécurité globale de votre organisation.

Vous pouvez également configurer si les fonctionnalités que les utilisateurs finaux peuvent voir dans le Centre de sécurité Microsoft Defender.

- [Vue d’ensemble du Centre de sécurité Microsoft Defender](/microsoft-365/security/defender-endpoint/use)

- [Protection des points de terminaison : Centre de sécurité Microsoft Defender](/mem/intune/protect/endpoint-protection-windows-10#microsoft-defender-security-center)

## <a name="next-steps"></a>Étapes suivantes

- [Obtenir une vue d’ensemble de la gestion des menaces et des vulnérabilités](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt)

- [Visiter le tableau de bord Centre de sécurité Microsoft Defender opérations de sécurité de l’utilisateur](/microsoft-365/security/defender-endpoint/security-operations-dashboard)

- [Gérer Microsoft Defender pour le point de terminaison avec Intune](manage-atp-post-migration-intune.md)
