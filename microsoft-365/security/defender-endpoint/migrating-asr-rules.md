---
title: Migration d’un hips tiers vers des règles ASR
description: Décrit comment aborder une migration à partir d’une solution HIPS (Host Intrusion Prevention System) tierce vers des règles ASR.
keywords: Règles de réduction de la surface d’attaque, asr, règles asr, hanches, système de prévention des intrusions de l’hôte, règles de protection, anti-exploitation, antiexploitation, exploit, prévention des infections, Microsoft Defender pour point de terminaison
ms.topic: article
ms.service: microsoft-365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
audience: ITPro
author: lovina-saldanha
ms.author: dansimp
manager: dansimp
ms.custom: asr
ms.subservice: mde
ms.collection:
- m365-security
- tier2
search.appverid: met150
ms.openlocfilehash: edbf7121a23bd5effda50256fdc07a6d58e09493
ms.sourcegitcommit: 4e42bafee965446f44f7f57d1defed2b9b24fce8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2022
ms.locfileid: "68231635"
---
# <a name="migrating-from-a-third-party-hips-to-asr-rules"></a>Migration d’un hips tiers vers des règles ASR

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Cet article vous aide à mapper des règles communes à Microsoft Defender pour point de terminaison.

## <a name="scenarios-when-migrating-from-a-third-party-hips-product-to-asr-rules"></a>Scénarios lors de la migration d’un produit HIPS tiers vers des règles ASR

### <a name="block-creation-of-specific-files"></a>Bloquer la création de fichiers spécifiques

- **S’applique à** - Tous les processus
- **Opération** - Création de fichier
- **Exemples de fichiers/dossiers, clés/valeurs de Registre, processus, services** - *.zepto, *.odin, *.locky, *.jaff, *.lukitus, *.wnry, *.krab
- **Règles de réduction de la surface d’attaque** : les règles ASR bloquent les techniques d’attaque et non les indicateurs de compromission (IOC). Le blocage d’une extension de fichier spécifique n’est pas toujours utile, car il n’empêche pas un appareil de compromettre. Il déjoue partiellement une attaque uniquement jusqu’à ce que les attaquants créent un nouveau type d’extension pour la charge utile.
- **Autres fonctionnalités recommandées** : il est vivement recommandé d’activer Microsoft Defender Antivirus, ainsi que la protection cloud et l’analyse du comportement. Nous vous recommandons d’utiliser d’autres préventions, telles que la règle ASR « Utiliser une protection avancée contre les ransomware ». Cela offre un niveau de protection plus élevé contre les attaques par ransomware. En outre, la plupart de ces clés de Registre sont surveillées par Microsoft Defender pour point de terminaison, telles que les techniques ASEP, qui déclenchent des alertes spécifiques. Les clés de Registre utilisées nécessitent un minimum de privilèges de Administration local ou de programme d’installation approuvé peuvent être modifiés. Il est recommandé d’utiliser un environnement verrouillé, avec des comptes ou droits d’administration minimaux. D’autres configurations système peuvent être activées, notamment « Désactiver SeDebug pour les rôles non requis » qui font partie de nos recommandations de sécurité plus larges.

### <a name="block-creation-of-specific-registry-keys"></a>Bloquer la création de clés de Registre spécifiques

- **S’applique à** - Tous les processus
- **Processus** - N/A
- **Opération** - Modifications du Registre
- **Exemples de fichiers/dossiers, clés/valeurs de Registre, processus, services**-  *\Software,HKCU*\Environment\UserInitMprLogonScript,HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Accessibility\ATs *\StartExe, HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Image File Execution Options*\Debugger, HKEY_CURRENT_USER\Software\Microsoft\HtmlHelp Author\location, HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\SilentProcessExit*\MonitorProcesss
- **Règles de réduction de la surface d’attaque** : les règles ASR bloquent les techniques d’attaque et non les indicateurs de compromission (IOC). Le blocage d’une extension de fichier spécifique n’est pas toujours utile, car il n’empêche pas un appareil de compromettre. Il déjoue partiellement une attaque uniquement jusqu’à ce que les attaquants créent un nouveau type d’extension pour la charge utile.
- **Autres fonctionnalités recommandées** : il est vivement recommandé d’activer Microsoft Defender Antivirus, ainsi que la protection cloud et l’analyse du comportement. Nous vous recommandons d’utiliser une prévention supplémentaire, telle que la règle ASR « Utiliser une protection avancée contre les ransomware ». Cela offre un niveau de protection plus élevé contre les attaques par ransomware. En outre, plusieurs de ces clés de Registre sont surveillées par Microsoft Defender pour point de terminaison, telles que les techniques ASEP, qui déclenchent des alertes spécifiques. En outre, les clés de Registre utilisées nécessitent un minimum de privilèges de Administration local ou de programme d’installation approuvé peuvent être modifiés. Il est recommandé d’utiliser un environnement verrouillé, avec des comptes ou droits d’administration minimaux. D’autres configurations système peuvent être activées, notamment « Désactiver SeDebug pour les rôles non requis » qui font partie de nos recommandations de sécurité plus larges.

### <a name="block-untrusted-programs-from-running-from-removable-drives"></a>Empêcher les programmes non approuvés de s’exécuter à partir de lecteurs amovibles

- **S’applique à** - Programmes non approuvés à partir d’USB
- **Processus**- *
- **Opération** - Exécution du processus
- **Exemples de fichiers/dossiers, clés/valeurs de Registre, processus, services :-*
- **Règles de réduction de la surface** d’attaque : les règles ASR ont une règle intégrée pour empêcher le lancement de programmes non approuvés et non signés à partir de lecteurs amovibles : « Bloquer les processus non approuvés et non signés qui s’exécutent à partir d’USB », GUID « b2b3f03d-6a65-4f7b-a9c7-1c7ef74a9ba4 ».
- **Autres fonctionnalités recommandées** : explorez des contrôles supplémentaires pour les périphériques USB et d’autres supports amovibles à l’aide de Microsoft Defender pour point de terminaison :[Comment contrôler des périphériques USB et d’autres supports amovibles à l’aide de Microsoft Defender pour point de terminaison](/windows/security/threat-protection/device-control/control-usb-devices-using-intune).

### <a name="block-mshta-from-launching-certain-child-processes"></a>Empêcher Mshta de lancer certains processus enfants

- **S’applique à** - Mshta
- **Processus** - mshta.exe
- **Opération** - Exécution du processus
- **Exemples de fichiers/dossiers, clés/valeurs de Registre, processus, services**- powershell.exe, cmd.exe, regsvr32.exe
- **Règles de réduction de la surface d’attaque** : les règles ASR ne contiennent aucune règle spécifique pour empêcher les processus enfants de « mshta.exe ». Ce contrôle appartient à Exploit Protection ou Windows Defender Application Control.
- **Autres fonctionnalités recommandées** : activez Windows Defender Contrôle d’application pour empêcher l’exécution complète de mshta.exe. Si votre organisation a besoin de « mshta.exe » pour les applications métier, configurez une règle exploit protection Windows Defender spécifique pour empêcher mshta.exe de lancer des processus enfants.

### <a name="block-outlook-from-launching-child-processes"></a>Empêcher Outlook de lancer des processus enfants

- **S’applique à** - Outlook
- **Processus** - outlook.exe
- **Opération** - Exécution du processus
- **Exemples de fichiers/dossiers, clés/valeurs de Registre, processus, services** powershell.exe
- **Règles de réduction de la surface** d’attaque : les règles ASR ont une règle intégrée pour empêcher les applications de communication Office (Outlook, Skype et Teams) de lancer des processus enfants : « Empêcher l’application de communication Office de créer des processus enfants », GUID « 26190899-1602-49e8-8b27-eb1d0a1ce869 ».
- **Autres fonctionnalités recommandées** : nous vous recommandons d’activer le mode de langage limité PowerShell pour réduire la surface d’attaque à partir de PowerShell.

### <a name="block-office-apps-from-launching-child-processes"></a>Empêcher Office Apps de lancer des processus enfants

- **S’applique à**- Office
- **Processus** - winword.exe, powerpnt.exe, excel.exe
- **Opération** - Exécution du processus
- **Exemples de fichiers/dossiers, clés/valeurs de Registre, processus, powershell.exe de services**, cmd.exe, wscript.exe, mshta.exe, EQNEDT32.EXE, regsrv32.exe
- **Règles de réduction de la surface** d’attaque : les règles ASR ont une règle intégrée pour empêcher les applications Office de lancer des processus enfants : « Empêcher toutes les applications Office de créer des processus enfants », GUID « d4f940ab-401b-4efc-aadc-ad5f3c50688a ».
- **Autres fonctionnalités recommandées** - N/A

### <a name="block-office-apps-from-creating-executable-content"></a>Empêcher Office Apps de créer du contenu exécutable

- **S’applique à**- Office
- **Processus** - winword.exe, powerpnt.exe, excel.exe
- **Opération** - Création de fichier
- **Exemples de fichiers/dossiers, clés/valeurs de Registre, processus, services** - C:\Users *\AppData **.exe, C:\ProgramData**.exe, C:\ProgramData**.com, C:\Users* AppData\Local\**Temp.com, C:\Users*\Downloads**.exe, C:\Users *\AppData.scf **, C:\ProgramData.scf**, C:\Users\Public*.exe, C:\Users*\Desktop***.exe
- **Règles de réduction de la surface d’attaque** - N/A.

### <a name="block-wscript-from-reading-certain-types-of-files"></a>Empêcher Wscript de lire certains types de fichiers

- **S’applique à** - Wscript
- **Processus** - wscript.exe
- **Opération** - Lecture du fichier
- **Exemples de fichiers/dossiers, clés/valeurs de Registre, processus, services**- C:\Users *\AppData**.js, C:\Users*\Downloads**.js
- **Règles de réduction de la surface d’attaque** : en raison de problèmes de fiabilité et de performances, les règles ASR n’ont pas la possibilité d’empêcher un processus spécifique de lire un certain type de fichier de script. Nous avons une règle pour empêcher les vecteurs d’attaque qui peuvent provenir de ces scénarios. Le nom de la règle est « Empêcher JavaScript ou VBScript de lancer le contenu exécutable téléchargé » (GUID « d3e037e1-3eb8-44c8-a917-57927947596 « Bloquer l’exécution de scripts potentiellement masqués » (GUID « 5beb7efe-fd9a-4556-801d-275e5ffc04cc »).
- **Autres fonctionnalités recommandées**: bien qu’il existe des règles ASR spécifiques qui atténuent certains vecteurs d’attaque dans ces scénarios, il est important de mentionner qu’AV est en mesure par défaut d’inspecter les scripts (PowerShell, Hôte de script Windows, JavaScript, VBScript, etc.) en temps réel, via l’interface d’analyse anti-programme malveillant (AMSI). Plus d’informations sont disponibles ici : [AmSI (Antimalware Scan Interface).](/windows/win32/amsi/antimalware-scan-interface-portal)

### <a name="block-launch-of-child-processes"></a>Bloquer le lancement des processus enfants

- **S’applique à** Adobe Acrobat
- **Processus** - AcroRd32.exe, Acrobat.exe
- **Opération** - Exécution du processus
- **Exemples de fichiers/dossiers, clés/valeurs de Registre, processus, services**- cmd.exe, powershell.exe, wscript.exe
- **Règles de réduction de la surface d’attaque** : les règles ASR permettent de bloquer Adobe Reader de lancer des processus enfants. Le nom de la règle est « Empêcher Adobe Reader de créer des processus enfants », GUID « 7674ba52-37eb-4a4f-a9a1-f0f9a1619a2c ».
- **Autres fonctionnalités recommandées** - N/A

### <a name="block-download-or-creation-of-executable-content"></a>Bloquer le téléchargement ou la création de contenu exécutable

- **S’applique à** - CertUtil : Bloquer le téléchargement ou la création de l’exécutable
- **Processus** - certutil.exe
- **Opération** - Création de fichier
- **Exemples de fichiers/dossiers, clés/valeurs de Registre, processus, services** - *.exe
- **Règles de réduction de la surface** d’attaque : les règles ASR ne prennent pas en charge ces scénarios, car elles font partie de Microsoft Defender protection antivirus.
- **Autres fonctionnalités recommandées** : Microsoft Defender Antivirus empêche CertUtil de créer ou de télécharger du contenu exécutable.

### <a name="block-processes-from-stopping-critical-system-components"></a>Empêcher les processus d’arrêter les composants système critiques

- **S’applique à** - Tous les processus
- **Processus**- *
- **Opération** - Arrêt du processus
- **Exemples de fichiers/dossiers, clés/valeurs de Registre, processus, MsSense.exe services**, MsMpEng.exe, NisSrv.exe, svchost.exe*, services.exe, csrss.exe, smss.exe, wininit.exe, etc.
- **Règles de réduction de la surface d’attaque** : les règles ASR ne prennent pas en charge ces scénarios, car elles sont protégées par des protections de sécurité intégrées à Windows.
- **Autres fonctionnalités recommandées** : ELAM (Early Launch AntiMalware), PPL (Protection Process Light), PPL AntiMalware Light et System Guard.

### <a name="block-specific-launch-process-attempt"></a>Bloquer une tentative de processus de lancement spécifique

- **S’applique à** des processus spécifiques
- **Processus** : « Nommez votre processus »
- **Opération** - Exécution du processus
- **Exemples de fichiers/dossiers, clés/valeurs de Registre, processus, tor.exe de services**, bittorrent.exe, cmd.exe, powershell.exe, etc.
- **Règles de réduction de la surface d’attaque** : dans l’ensemble, les règles ASR ne sont pas conçues pour fonctionner en tant que gestionnaire d’applications.
- **Autres fonctionnalités recommandées** : pour empêcher les utilisateurs de lancer des processus ou des programmes spécifiques, il est recommandé d’utiliser Windows Defender Contrôle d’application. Microsoft Defender pour point de terminaison indicateurs de fichier et de certificat, peuvent être utilisés dans un scénario de réponse aux incidents (ne doivent pas être considérés comme un mécanisme de contrôle d’application).

### <a name="block-unauthorized-changes-to-microsoft-defender-antivirus-configurations"></a>Bloquer les modifications non autorisées apportées aux configurations antivirus Microsoft Defender

- **S’applique à** - Tous les processus
- **Processus**- *
- **Opération** - Modifications du Registre
- **Exemples de fichiers/dossiers, clés/valeurs de Registre, processus, services**- HKLM\SOFTWARE\Policies\Microsoft\Windows Defender\DisableAntiSpyware, HKLM\SOFTWARE\Policies\Microsoft\Windows Defender\Policy Manager\AllowRealTimeMonitoring, et ainsi de suite.
- **Règles de réduction de la surface d’attaque** : les règles ASR ne couvrent pas ces scénarios, car elles font partie de la protection intégrée Microsoft Defender pour point de terminaison.
- **Autres fonctionnalités recommandées** : la protection contre les falsifications (opt-in, gérée à partir de Intune) empêche les modifications non autorisées apportées aux clés de Registre DisableAntiVirus, DisableAntiSpyware, DisableRealtimeMonitoring, DisableOnAccessProtection, DisableBehaviorMonitoring et DisableIOAVProtection (et bien plus encore).

Voir aussi

- [FAQ sur la réduction de la surface d’attaque](attack-surface-reduction-faq.yml)
- [Activer les règles de réduction de la surface d’attaque](enable-attack-surface-reduction.md)
- [Évaluer les règles de réduction de la surface d’attaque](evaluate-attack-surface-reduction.md)
