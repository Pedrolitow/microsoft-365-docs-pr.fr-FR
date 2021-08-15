---
title: Journaux de diagnostic
description: Journaux qui peuvent être collectés à partir d’appareils lors de la résolution des problèmes et comment ils sont stockés
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
author: jaimeo
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
ms.author: jaimeo
manager: laurawi
ms.topic: article
ms.openlocfilehash: 04de03e22e270099c647a0dd1ac6d3bb9826ccf87014031bb13ed77b0b580870
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53840118"
---
# <a name="diagnostic-logs"></a>Journaux de diagnostic

Lorsque nous dépannageons un problème sur un appareil géré par Microsoft Manged Desktop, qu’il s’agit d’un problème que vous avez signalé ou identifié par notre service, il se peut que nous deions collecter certains journaux de diagnostic à partir de l’appareil sans l’intervention de l’utilisateur. Nous ne collectons pas de contenu ou d’informations générés par l’utilisateur dans les annuaires des utilisateurs. Nous collectons uniquement les données de diagnostic et de journal qui concernent l’état et l’état de l’appareil.

Nous stockons tous les journaux collectés pendant 28 jours, puis les supprimons. Nous traiterons tous les journaux collectés à partir d’un appareil en suivant nos normes [de gestion des données.](privacy-personal-data.md)

## <a name="data-collected"></a>Données collectées

Cette liste inclut tous les dossiers, journaux d’événements, fichiers exécutables ou emplacements de Registre à partir Microsoft Manged Desktop des journaux de diagnostic. Les données réelles collectées sont un sous-ensemble de cette liste et dépendent du problème identifié.

### <a name="registry-keys"></a>Clés du Registre

- HKLM \\ SYSTEM \\ CurrentControlSet \\ Services
- HKLM \\ SOFTWARE \\ Microsoft \\ Surface
- Stratégies \\ \\ logicielles \\ HKLM \\ microsoft Windows \\ WindowsUpdate
- HKLM \\ SYSTEM \\ CurrentControlSet \\ Control \\ MUI \\ UILanguages
- Stratégies logicielles HKLM \\ \\ Microsoft \\ \\ WindowsStore
- HKLM \\ Software Microsoft Windows \\ \\ \\ CurrentVersion \\ WindowsStore \\ WindowsUpdate
- HKLM \\ SOFTWARE Microsoft Windows \\ \\ NT \\ CurrentVersion
- HKLM \\ SOFTWARE Microsoft Windows \\ \\ NT \\ CurrentVersion
- HKLM \\ SOFTWARE Microsoft Windows \\ \\ \\ CurrentVersion \\ AppModel
- HKLM \\ SYSTEM \\ CurrentControlSet \\ Control \\ FirmwareResources
- HKLM \\ SOFTWARE \\ Microsoft \\ WindowsSelfhost
- HKLM \\ SOFTWARE \\ Microsoft \\ WindowsUpdate
- HKLM \\ SOFTWARE Microsoft Windows \\ \\ \\ CurrentVersion \\ Appx
- HKLM \\ SOFTWARE Microsoft Windows \\ \\ NT \\ CurrentVersion \\ Superfetch
- Configuration DU SYSTÈME HKLM \\ \\
- HKLM \\ Software \\ Microsoft \\ IntuneManagementExtension
- HKLM \\ SOFTWARE \\ Microsoft \\ SystemCertificates \\ AuthRoot
- HKLM \\ SOFTWARE Microsoft Windows - Protection avancée contre les \\ \\ menaces
- HKLM \\ SOFTWARE Microsoft Windows \\ \\ \\ CurrentVersion Authentication \\ \\ LogonUI
- HKLM \\ SOFTWARE Microsoft Windows \\ \\ \\ CurrentVersion Internet \\ Paramètres
- \\Désinstallation de HKLM Software \\ Microsoft Windows \\ \\ CurrentVersion \\
- Stratégies \\ \\ logicielles HKLM
- HKLM \\ SOFTWARE \\ Policies \\ Microsoft \\ Cryptography \\ Configuration \\ SSL
- Stratégies logicielles HKLM \\ microsoft Windows protection avancée contre les \\ \\ \\ menaces
- HKLM \\ SOFTWARE \\ WOW6432Node \\ Microsoft Windows \\ \\ CurrentVersion \\ Uninstall
- HKLM \\ SYSTEM \\ CurrentControlSet \\ Control \\ SecurityProviders \\ SCHANNEL

### <a name="commands"></a>Commandes

- %programfiles% \\ windows defendermpcmdrun.exe \\ -GetFiles
- %windir% \\ system32 \\certutil.exe -store
- %windir% \\ system32 \\certutil.exe -store -user my
- %windir% \\ system32 \\Dsregcmd.exe /status
- %windir% \\ system32 \\ipconfig.exe /all
- %windir% \\ system32 \\ipconfig.exe /displaydns
- %windir% \\ system32 \\mdmdiagnosticstool.exe
- %windir% \\ system32 \\msinfo32.exe /report %temp% \\ MDMDiagnostics \\ msinfo32.log
- %windir% \\ system32 \\netsh.exe advfirewall show allprofiles
- %windir% \\ system32 \\netsh.exe advfirewall show global
- %windir% \\ system32 \\netsh.exe lan show profiles
- %windir% \\ system32 \\netsh.exe winhttp show proxy
- %windir% \\ system32 \\netsh.exe wlan show profiles
- %windir% \\ system32 \\netsh.exe wlan show wlanreport
- %windir% \\ system32 \\ping.exe -n 50 localhost
- %windir% \\ system32 \\powercfg.exe /batteryreport /output %temp% \\ MDMDiagnostics \\battery-report.html
- %windir% \\ system32 \\powercfg.exe /energy /output %temp% \\ MDMDiagnostics \\energy-report.html
- bitsadmin /list /allusers /verbose
- fltMC.exe
- bcdedit /enum all /v
- manage-bde -protectors -get
- Windows PowerShell commande :
    - Get-appxpackage -allusers
    - Get-appxpackage -packagetype bundle
    - Get-Service wuauserv
    - Get-NetFirewallRule
    - Get-WmiObject -Class win32 \_ product
    - Get-ComputerInfo
    - Get-Service
    - Get-Process
    - Get-WmiObject Win32 \_ PnPSignedDriver

### <a name="event-logs"></a>Journaux d’événements

- Application
- Microsoft-Windows-AppLocker/EXE et DLL
- Microsoft-Windows-AppLocker/MSI et Script
- Microsoft-Windows-AppLocker/Packaged app-Deployment
- Microsoft-Windows-AppLocker/Packaged app-Execution
- Microsoft-Windows-Bitlocker/Bitlocker Management
- Microsoft-Windows-SENSE/Opérationnel
- Microsoft-Windows-SenseIR/Operational
- Configuration
- Système

### <a name="files"></a>Fichiers

- %ProgramData% \\ Microsoft \\ DiagnosticLogCSP \\ Collectors \\ \* .etl
- %ProgramData% \\ Microsoft \\ IntuneManagementExtension \\ Logs \\ \* .\*
- %ProgramData% \\ Prise en charge Windows Defender Microsoft \\ \\MpSupportFiles.cab \\
- %ProgramData% \\ Microsoft \\ Windows \\ WlanReport \\wlan-report-latest.html
- %ProgramData% \\ Microsoft \\ Windows \\ WlanReport -SourceFileName wlan-report-latest.html
- %windir% \\ ccm \\ logs \* .log
- %windir% \\ ccmsetup \\ logs \* .log
- %windir% \\ enregistre \\ CBS \\ cbs.log
- %windir% \\ logs \\ measuredboot \* .\*
- %windir% \\ Logs \\ WindowsUpdate \* .etl
- %windir% \\ inf \\ \* .log
- %windir% \\ servicing \\ sessions \\ActionList.xml
- %windir% \\ servicing \\ sessions \\Sessions.xml
- %windir% \\ SoftwareDistribution \\ DataStore \\ Logs \\ edb.log
- %windir% \\ SoftwareDistribution \\ DataStore \\ DataStore.edb
- %windir% \\ logs \\ dism \\ dism.log
- %SystemRoot% \\ System32 \\ Winevt \\ Logs\\
- %appdata% \\ Microsoft \\ Teams \\ media-stack \\ \* .blog
- %appdata% \\ Microsoft \\ Teams \\ skylib \\ \* .blog
- %appdata% \\ Microsoft \\ Teams \\ media-stack \\ \* .etl
- %appdata% \\ Microsoft \\ Teams \\logs.txt
- %windir% \\ Windows \\ System32 \\ winevt \\ \* .\*