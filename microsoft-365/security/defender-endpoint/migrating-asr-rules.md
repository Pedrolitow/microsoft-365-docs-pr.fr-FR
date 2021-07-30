---
title: Migration d’un hips tiers vers des règles asr
description: Décrit comment aborder une migration d’une solution hips (Host Intrusion Prevention System) tierce vers des règles asr.
keywords: Règles de réduction de la surface d’attaque, règles asr, règles d’attaque, système de prévention des intrusions hôtes, règles de protection, anti-attaque, attaque, prévention des infections, Microsoft Defender pour point de terminaison
search.product: eADQiWindows 10XVcnh
ms.topic: article
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
localization_priority: normal
audience: ITPro
author: lovina-saldanha
ms.author: v-lsaldanha
manager: dansimp
ms.custom: asr
ms.technology: mde
ms.openlocfilehash: b1aae75f411af4f9d745c67831222c5ceee6bb0d
ms.sourcegitcommit: b3091791196828883d8284497561027df692d109
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2021
ms.locfileid: "53663826"
---
# <a name="migrating-from-a-third-party-hips-to-asr-rules"></a>Migration d’un hips tiers vers des règles asr

Cet article vous aide à ma cartographier des règles communes à Microsoft Defender pour endpoint.

## <a name="scenarios-when-migrating-from-a-third-party-hips-product-to-asr-rules"></a>Scénarios lors de la migration d’un produit HIPS tiers vers des règles asr

### <a name="block-creation-of-specific-files-and-registry-keys"></a>Bloquer la création de fichiers et de clés de Registre spécifiques

- **S’applique** à - Tous les processus
- **Opération**: création de fichier
- Exemples de **fichiers/dossiers, clés de Registre/valeurs, processus, services**- *.zepto, *.odin, *.locky, *.jaff, *.lukitus, *.wnry, *.krab
- **Règles de réduction de la surface d’attaque**: les règles de réduction de la surface d’attaque bloquent les techniques d’attaque et non les indicateurs de compromis (IOC). Le blocage d’une extension de fichier spécifique n’est pas toujours utile, car cela n’empêche pas un appareil d’être compromis. Elle ne déjoue que partiellement une attaque jusqu’à ce que les attaquants créent un nouveau type d’extension pour la charge utile.
- **Autres fonctionnalités recommandées**: l’antivirus Microsoft Defender activé, ainsi que l’analyse du comportement et de la protection cloud sont vivement recommandés. Nous vous recommandons d’utiliser d’autres préventions, telles que la règle asr « Utiliser une protection avancée contre les ransomware ». Cela offre un niveau de protection plus élevé contre les attaques par ransomware. En outre, la plupart de ces clés de Registre sont surveillées par Microsoft Defender pour le point de terminaison, telles que les techniques ASEP, qui déclenchent des alertes spécifiques. Les clés de Registre utilisées nécessitent un minimum de privilèges d’administrateur local ou de programme d’installation approuvé qui peuvent être modifiés. L’utilisation d’un environnement verrouillé, avec des comptes ou des droits d’administration minimaux, est recommandée. D’autres configurations système peuvent être activées, notamment « Désactiver SeDebug pour les rôles non requis » qui font partie de nos recommandations de sécurité plus larges.

### <a name="block-creation-of-specific-files-and-registry-keys"></a>Bloquer la création de fichiers et de clés de Registre spécifiques

- **S’applique** à - Tous les processus
- **Processus**- N/A
- **Opération**: modifications du Registre
- **Exemples de fichiers/dossiers, clés/valeurs de Registre, processus, services** -  *\Software*,HKCU\Environment\UserInitMprLogonScript,HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Accessibility\ATs *\StartExe, HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Image File Execution Options*\Debugger, HKEY_CURRENT_USER\Software\Microsoft\HtmlHelp Author\location, HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\SilentProcessExit*\MonitorProcess
- **Règles de réduction de la surface d’attaque**: les règles de réduction de la surface d’attaque bloquent les techniques d’attaque et non les indicateurs de compromis (IOC). Le blocage d’une extension de fichier spécifique n’est pas toujours utile, car cela n’empêche pas un appareil d’être compromis. Elle ne déjoue que partiellement une attaque jusqu’à ce que les attaquants créent un nouveau type d’extension pour la charge utile.
- **Autres fonctionnalités recommandées**: l’antivirus Microsoft Defender activé, ainsi que l’analyse du comportement et de la protection cloud sont vivement recommandés. Nous vous recommandons d’utiliser une prévention supplémentaire, telle que la règle asr « Utiliser une protection avancée contre les ransomware ». Cela offre un niveau de protection plus élevé contre les attaques par ransomware. En outre, plusieurs de ces clés de Registre sont surveillées par Microsoft Defender pour endpoint, telles que les techniques ASEP, qui déclenchent des alertes spécifiques. En outre, les clés de Registre utilisées nécessitent un minimum de privilèges d’administrateur local ou de programme d’installation approuvé qui peuvent être modifiés. L’utilisation d’un environnement verrouillé, avec des comptes ou des droits d’administration minimaux, est recommandée. D’autres configurations système peuvent être activées, notamment « Désactiver SeDebug pour les rôles non requis » qui font partie de nos recommandations de sécurité plus larges.

### <a name="block-untrusted-programs-from-running-from-removable-drives"></a>Empêcher l’exécution de programmes non confiance à partir de lecteurs amovibles

- **S’applique** à - Programmes nontrus à partir du port USB
- **Processus**- *
- **Operation**- Process Execution
- **Exemples de fichiers/dossiers, clés/valeurs de Registre, processus, services :-*
- Règles de réduction de la **surface** d’attaque : les règles de réduction de la surface d’attaque ont une règle intégrée pour empêcher le lancement de programmes non signés et non signés à partir de lecteurs amovibles : « Bloquer les processus nontrus et non signés qui s’exécutent à partir de USB », GUID « b2b3f03d-6a65-4f7b-a9c7-1c7ef74a9ba4 ».
- Autres fonctionnalités recommandées : explorez les contrôles supplémentaires pour les périphériques USB et autres supports amovibles à l’aide de Microsoft Defender pour le point de terminaison : comment contrôler les périphériques USB et autres supports amovibles à l’aide de[Microsoft Defender pour endpoint](/windows/security/threat-protection/device-control/control-usb-devices-using-intune).

### <a name="block-mshta-from-launching-certain-child-processes"></a>Empêcher Mshta de lancer certains processus enfants

- **S’applique** à - Mshta
- **Processus**- mshta.exe
- **Operation**- Process Execution
- **Exemples de fichiers/dossiers, clés/valeurs de Registre, processus, services**- powershell.exe, cmd.exe, regsvr32.exe
- **Règles de réduction de** la surface d’attaque : les règles de réduction de la surface d’attaque ne contiennent aucune règle spécifique pour empêcher les processus enfants de « mshta.exe ». Ce contrôle est dans le cadre des missions d’Exploit Protection Windows Defender Application Control.
- **Autres fonctionnalités recommandées**: activez Windows Defender contrôle d’application pour empêcher mshta.exe'exécution. Si votre organisation nécessite des mshta.exe pour les applications métier, configurez une règle Windows Defender Exploit Protection spécifique, afin d’empêcher mshta.exe de lancer des processus enfants.

### <a name="block-outlook-from-launching-child-processes"></a>Empêcher les Outlook lancement de processus enfants

- **S’applique** à - Outlook
- **Processus**- outlook.exe
- **Operation**- Process Execution
- **Exemples de fichiers/dossiers, clés/valeurs de Registre, processus, services**- powershell.exe
- Règles de réduction de la surface d’attaque : les règles de réduction de la surface d’attaque ont une règle intégrée pour empêcher les applications de communication Office (Outlook, Skype et Teams) de lancer des processus enfants : « Empêcher l’application de communication Office de créer des processus enfants », GUID « 26190899-1602-49e8-8b27-eb1d0a1ce869 ».
- **Autres fonctionnalités recommandées**: nous vous recommandons d’activer le mode de langue contrainte PowerShell pour réduire la surface d’attaque à partir de PowerShell.


### <a name="block-office-apps-from-launching-child-processes-and-from-creating-executable-content"></a>Empêcher Office applications de lancer des processus enfants et de créer du contenu exécutable

- **S’applique** à - Office  
- **Processus**: winword.exe, powerpnt.exe, excel.exe
- **Operation**- Process Execution
- Exemples de **fichiers/dossiers, clés/valeurs de Registre, processus, services**- powershell.exe, cmd.exe, wscript.exe, mshta.exe, EQNEDT32.EXE, regsrv32.exe
- Règles de réduction de la **surface** d’attaque : les règles de réduction de la surface d’attaque ont une règle intégrée pour empêcher les applications Office de lancer des processus enfants : « Empêcher toutes les applications Office de créer des processus enfants », GUID « d4f940ab-401b-4efc-aadc-ad5f3c50688a ».
- **Autres fonctionnalités recommandées**: N/A
    
### <a name="block-office-apps-from-launching-child-processes-and-from-creating-executable-content"></a>Empêcher Office applications de lancer des processus enfants et de créer du contenu exécutable

- **S’applique** à - Office
- **Processus**: winword.exe, powerpnt.exe, excel.exe
- **Opération**: création de fichier
- **Exemples de fichiers/dossiers, clés/valeurs de Registre, processus, services**- C:\Users *\AppData **.exe, C:\ProgramData**.exe, C:\ProgramData**.com, C:\Users* AppData\Local\Temp **.com, C:\Users*\Downloads**.exe, C:\Users *\AppData **.scf, C:\ProgramData**.scf, C:\Users\Public*.exe, C:\Users*\Desktop***.exe
- **Règles de réduction de la surface d’attaque**- N/A.

### <a name="block-wscript-from-reading-certain-types-of-files"></a>Empêcher Wscript de lire certains types de fichiers

- **S’applique** à - Wscript
- **Processus**- wscript.exe
- **Opération**- Lecture de fichier
- Exemples de **fichiers/dossiers, clés/valeurs de Registre, processus, services**- C:\Users *\AppData**.js, C:\Users*\Downloads**.js
- **Règles de** réduction de la surface d’attaque : en raison de problèmes de fiabilité et de performances, les règles de réduction de la surface d’attaque n’ont pas la possibilité d’empêcher un processus spécifique de lire un certain type de fichier de script. Nous avons une règle pour empêcher les vecteurs d’attaque qui peuvent provenir de ces scénarios. Le nom de la règle est « Empêcher JavaScript ou VBScript de lancer le contenu exécutable téléchargé » (GUID " d3e037e1-3eb8-44c8-a917-5792794759 « Bloquer l’exécution de scripts potentiellement obscurcis » (GUID « 5beb7efe-fd9a-4556-801d-275e5ffc04cc »).
- Autres fonctionnalités recommandées : bien qu’il existe des règles asr spécifiques qui atténuent certains vecteurs d’attaque dans ces scénarios, il est important de mentionner que l’Antivirus peut par défaut inspecter les scripts (PowerShell, Windows Script Host, JavaScript, VBScript, et bien plus encore) en temps réel, via l’interface AMSI (Antimalware Scan Interface). Plus d’informations sont disponibles ici : Interface d’analyse [anti-programme malveillant (AMSI).](/windows/win32/amsi/antimalware-scan-interface-portal)

### <a name="block-launch-of-child-processes"></a>Bloquer le lancement des processus enfants

- **S’applique** à - Adobe Acrobat
- **Processus**: AcroRd32.exe, Acrobat.exe
- **Operation**- Process Execution
- **Exemples de fichiers/dossiers, clés/valeurs de Registre, processus, services**- cmd.exe, powershell.exe, wscript.exe
- **Règles de réduction de la surface d’attaque**: les règles de réduction de la surface d’attaque empêchent Adobe Reader de lancer des processus enfants. Le nom de la règle est « Empêcher Adobe Reader de créer des processus enfants », GUID « 7674ba52-37eb-4a4f-a9a1-f0f9a1619a2c ».
- **Autres fonctionnalités recommandées**: N/A


### <a name="block-download-or-creation-of-executable-content"></a>Bloquer le téléchargement ou la création de contenu exécutable

- **S’applique** à - CertUtil : bloquer le téléchargement ou la création d’exécutables 
- **Processus**- certutil.exe
- **Opération**: création de fichier
- **Exemples de fichiers/dossiers, clés/valeurs de Registre, processus, services**- *.exe
- **Règles de réduction de la surface** d’attaque : les règles de réduction de la surface d’attaque ne sont pas pris en charge dans ces scénarios, car elles font partie de Antivirus Microsoft Defender protection.
- **Autres fonctionnalités recommandées**: Microsoft Defender AV empêche CertUtil de créer ou de télécharger du contenu exécutable.


### <a name="block-processes-from-stopping-critical-system-components"></a>Empêcher les processus d’arrêter les composants système critiques

- **S’applique** à - Tous les processus
- **Processus**- *
- **Opération**: arrêt du processus
- Exemples de **fichiers/dossiers, clés/valeurs de Registre, processus, services**- MsSense.exe, MsMpEng.exe, NisSrv.exe, svchost.exe*, services.exe, csrss.exe, smss.exe, wininit.exe, etc.
- **Règles de** réduction de la surface d’attaque : les règles de réduction de la surface d’attaque ne sont pas pris en charge dans ces scénarios, car elles sont protégées Windows 10 protections de sécurité intégrées.
- **Autres fonctionnalités recommandées**: ELAM (logiciel anti-programme malveillant à lancement précoce), PPL (Protection Process Light), PPL AntiMalware Light et System Guard.

### <a name="block-specific-launch-process-attempt"></a>Bloquer une tentative de processus de lancement spécifique

- **S’applique** à - Processus spécifiques
- **Processus**: « Nommez votre processus »
- **Operation**- Process Execution
- **Exemples de fichiers/dossiers, clés/valeurs de Registre, processus, services**- tor.exe, bittorrent.exe, cmd.exe, powershell.exe, et bien plus encore
- **Règles de réduction de la surface d’attaque**: globalement, les règles de réduction de la surface d’attaque ne sont pas conçues pour fonctionner en tant que gestionnaire d’applications.
- **Autres fonctionnalités recommandées**: pour empêcher les utilisateurs de lancer des processus ou des programmes spécifiques, il est recommandé d’utiliser Windows Defender Contrôle d’application. Les indicateurs Microsoft Defender for Endpoint File et Cert peuvent être utilisés dans un scénario de réponse aux incidents (ne doit pas être considéré comme un mécanisme de contrôle d’application).
    
### <a name="block-unauthorized-changes-to-microsoft-defender-antivirus-configurations"></a>Bloquer les modifications non autorisées apportées Antivirus Microsoft Defender configurations

- **S’applique** à - Tous les processus
- **Processus**- *
- **Opération**: modifications du Registre
- Exemples de **fichiers/dossiers, clés de Registre/valeurs, processus, services**- HKLM\SOFTWARE\Policies\Microsoft\Windows Defender\DisableAntiSpyware, HKLM\SOFTWARE\Policies\Microsoft\Windows Defender\Policy Manager\AllowRealTimeMonitoring, etc.
- **Règles de réduction de** la surface d’attaque : les règles de réduction de la surface d’attaque ne couvrent pas ces scénarios, car elles font partie de la protection intégrée de Microsoft Defender for Endpoint.
- Autres fonctionnalités recommandées : la protection contre la falsification (opt-in, géré à partir d’Intune) empêche les modifications non autorisées apportées aux clés de Registre DisableAntiVirus, DisableAntiSpyware, DisableRealtimeMonitoring, DisableOnAccessProtection, DisableBehaviorMonitoring et DisableIOAVProtection (et bien plus encore).

Voir aussi

- [FAQ sur la réduction de la surface d’attaque](attack-surface-reduction-faq.yml)
- [Activer les règles de réduction de la surface d’attaque](enable-attack-surface-reduction.md)
- [Évaluer les règles de réduction de la surface d’attaque](evaluate-attack-surface-reduction.md)
