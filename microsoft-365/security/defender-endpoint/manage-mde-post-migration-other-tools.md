---
title: Gérer Microsoft Defender pour point de terminaison à l’aide de PowerShell, WMI et MPCmdRun.exe
description: Découvrez comment gérer Microsoft Defender pour point de terminaison avec PowerShell, WMI et MPCmdRun.exe
keywords: post-migration, gestion, opérations, maintenance, utilisation, PowerShell, WMI, MPCmdRun.exe, Microsoft Defender pour point de terminaison, edr
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: deniseb
author: denisebmsft
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
ms.custom: admindeeplinkDEFENDER
ms.topic: article
ms.reviewer: chventou
ms.openlocfilehash: 51ead270b8e8223b2fd67cfd5fb1cf4e9f8a05d4
ms.sourcegitcommit: e9692a40dfe1f8c2047699ae3301c114a01b0d3a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2022
ms.locfileid: "66603294"
---
# <a name="manage-microsoft-defender-for-endpoint-with-powershell-wmi-and-mpcmdrunexe"></a>Gérer Microsoft Defender pour point de terminaison avec PowerShell, WMI et MPCmdRun.exe

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

> [!NOTE]
> Nous vous recommandons d’utiliser [Microsoft Endpoint Manager](/mem) pour gérer les fonctionnalités de protection contre les menaces de votre organisation pour les appareils (également appelés points de terminaison). Endpoint Manager inclut [Microsoft Intune](/mem/intune/fundamentals/what-is-intune) et [Configuration Manager de point de terminaison Microsoft](/mem/configmgr/core/understand/introduction).
>
> - [En savoir plus sur Endpoint Manager](/mem/endpoint-manager-overview)
> - [Cogestion des Microsoft Defender pour point de terminaison sur les appareils Windows 10 et Windows 11 avec Configuration Manager et Intune](manage-mde-post-migration-intune.md)
> - [Gérer Microsoft Defender pour point de terminaison avec Intune](manage-mde-post-migration-intune.md)

Vous pouvez gérer certains paramètres de l’antivirus Microsoft Defender sur les appareils avec [PowerShell](#configure-microsoft-defender-for-endpoint-with-powershell),  [Windows Management Instrumentation](#configure-microsoft-defender-for-endpoint-with-windows-management-instrumentation-wmi) (WMI) et l’utilitaire de [ligne de commande Microsoft Malware Protection](#configure-microsoft-defender-for-endpoint-with-microsoft-malware-protection-command-line-utility-mpcmdrunexe) (MPCmdRun.exe). Par exemple, vous pouvez gérer certains paramètres de l’Antivirus Microsoft Defender. Et, dans certains cas, vous pouvez personnaliser vos règles de réduction de la surface d’attaque et les paramètres de protection contre les attaques.

> [!IMPORTANT]
> Les fonctionnalités de protection contre les menaces que vous configurez à l’aide de PowerShell, WMI ou MCPmdRun.exe peuvent être remplacées par des paramètres de configuration déployés avec Intune ou Configuration Manager.

## <a name="configure-microsoft-defender-for-endpoint-with-powershell"></a>Configurer Microsoft Defender pour point de terminaison avec PowerShell

Vous pouvez utiliser PowerShell pour gérer l’antivirus Microsoft Defender, exploit protection et vos règles de réduction de la surface d’attaque.

|Tâche|Ressources pour en savoir plus|
|---|---|
|**Gérer l’antivirus Microsoft Defender** <br/><br/> Affichez l’état de la protection anti-programme malveillant, configurez les préférences pour les analyses antivirus & mises à jour et apportez d’autres modifications à votre protection antivirus.*|[Utiliser des applets de commande PowerShell pour configurer et gérer l’antivirus Microsoft Defender](/windows/security/threat-protection/microsoft-defender-antivirus/use-powershell-cmdlets-microsoft-defender-antivirus) <br/><br/> [Utiliser des applets de commande PowerShell pour activer la protection fournie par le cloud](/windows/security/threat-protection/microsoft-defender-antivirus/enable-cloud-protection-microsoft-defender-antivirus#use-powershell-cmdlets-to-enable-cloud-delivered-protection)|
|**Configurer exploit protection** pour atténuer les menaces sur les appareils de votre organisation <br/><br/> *Nous vous recommandons d’abord d’utiliser exploit protection en [mode audit](/microsoft-365/security/defender-endpoint/evaluate-exploit-protection#powershell) . De cette façon, vous pouvez voir comment la protection contre l’exploitation affecte les applications utilisées par votre organisation.*|[Personnaliser la protection contre les codes malveillants exploitant une faille de sécurité](/microsoft-365/security/defender-endpoint/customize-exploit-protection) <br/><br/> [Applets de commande PowerShell pour la protection contre les attaques](/microsoft-365/security/defender-endpoint/customize-exploit-protection#powershell-reference)|
|**Configurer des règles de réduction de la surface d’attaque** avec PowerShell <br/><br/> *Vous pouvez utiliser PowerShell pour exclure les fichiers et dossiers des règles de réduction de la surface d’attaque.*|[Personnaliser les règles de réduction de la surface d’attaque : Utiliser PowerShell pour exclure des fichiers & dossiers](/microsoft-365/security/defender-endpoint/enable-attack-surface-reduction) <br/><br/> Consultez également [l’outil d’interface utilisateur graphique d’António Vasconcelo pour définir des règles de réduction de la surface d’attaque avec PowerShell](https://github.com/anvascon/MDATP_PoSh_Scripts/tree/master/ASR%20GUI).|
|**Activer la protection réseau** avec PowerShell <br/><br/> *Vous pouvez utiliser PowerShell pour activer la protection réseau.*|[Activer la protection réseau avec PowerShell](/microsoft-365/security/defender-endpoint/enable-network-protection#powershell)|
|**Configurer l’accès contrôlé aux dossiers** pour vous protéger contre les ransomware <br/><br/> *[L’accès contrôlé aux dossiers](/microsoft-365/security/defender-endpoint/controlled-folders) est également appelé protection antiransomware.*|[Activer l’accès contrôlé aux dossiers avec PowerShell](/microsoft-365/security/defender-endpoint/enable-controlled-folders#powershell)|
|**Configurer Pare-feu Microsoft Defender** pour bloquer le trafic réseau non autorisé entrant ou sortant des appareils de votre organisation|[Pare-feu Microsoft Defender avec Advanced Security Administration à l’aide de Windows PowerShell](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security-administration-with-windows-powershell)|
|**Configurer le chiffrement et BitLocker** pour protéger les informations sur les appareils de votre organisation exécutant Windows|[Guide de référence sur BitLocker PowerShell](/powershell/module/bitlocker/)|

## <a name="configure-microsoft-defender-for-endpoint-with-windows-management-instrumentation-wmi"></a>Configurer Microsoft Defender pour point de terminaison avec Windows Management Instrumentation (WMI)

WMI est une interface de script qui vous permet de récupérer, modifier et mettre à jour les paramètres. Pour en savoir plus, consultez [Utilisation de WMI](/windows/win32/wmisdk/using-wmi).<br/><br/>

|Tâche|Ressources pour en savoir plus|
|---|---|
|**Activer la protection fournie par le cloud** sur un appareil|[Utiliser l’instruction de gestion Windows (WMI) pour activer la protection fournie par le cloud](/windows/security/threat-protection/microsoft-defender-antivirus/enable-cloud-protection-microsoft-defender-antivirus#use-windows-management-instruction-wmi-to-enable-cloud-delivered-protection)|
|**Récupérer, modifier et mettre à jour les paramètres** de l’antivirus Microsoft Defender|[Utiliser WMI pour configurer et gérer l’antivirus Microsoft Defender] (/windows/security/threat-protection/microsoft-defender-antivirus/use-wmi-microsoft-defender-antivirus <br/><br/> [Passez en revue la liste des classes WMI disponibles et des exemples de scripts](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal) <br/><br/> Consultez également les informations de [référence du fournisseur Windows Defender WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal?redirectedfrom=MSDN) archivées|

## <a name="configure-microsoft-defender-for-endpoint-with-microsoft-malware-protection-command-line-utility-mpcmdrunexe"></a>Configurer Microsoft Defender pour point de terminaison avec l’utilitaire Command-Line protection contre les programmes malveillants Microsoft (MPCmdRun.exe)

Sur un appareil individuel, vous pouvez exécuter une analyse, démarrer le suivi des diagnostics, rechercher des mises à jour du renseignement de sécurité et bien plus encore à l’aide de l’outil en ligne de commande mpcmdrun.exe. Vous pouvez trouver l’utilitaire dans `%ProgramFiles%\Windows Defender\MpCmdRun.exe`. Exécutez-le à partir d’une invite de commandes.

Pour en savoir plus, consultez [Configurer et gérer l’antivirus Microsoft Defender avec mpcmdrun.exe](/windows/security/threat-protection/microsoft-defender-antivirus/command-line-arguments-microsoft-defender-antivirus).

## <a name="configure-your-microsoft-365-defender-portal"></a>Configurer votre portail Microsoft 365 Defender

Si vous ne l’avez pas déjà fait, configurez votre <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portail Microsoft 365 Defender</a> pour afficher les alertes, configurer les fonctionnalités de protection contre les menaces et afficher des informations détaillées sur la posture de sécurité globale de votre organisation.

Vous pouvez également configurer si et quelles fonctionnalités les utilisateurs finaux peuvent voir dans le Centre de sécurité Microsoft Defender.

- [Vue d’ensemble de la Centre de sécurité Microsoft Defender](/microsoft-365/security/defender-endpoint/use)
- [Endpoint Protection : Centre de sécurité Microsoft Defender](/mem/intune/protect/endpoint-protection-windows-10#microsoft-defender-security-center)

## <a name="next-steps"></a>Étapes suivantes

- [Obtenir une vue d’ensemble de la gestion des menaces et des vulnérabilités](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt)
- [Visitez le tableau de bord des opérations de sécurité Centre de sécurité Microsoft Defender](/microsoft-365/security/defender-endpoint/security-operations-dashboard)
- [Gérer Microsoft Defender pour point de terminaison avec Intune](manage-mde-post-migration-intune.md)
