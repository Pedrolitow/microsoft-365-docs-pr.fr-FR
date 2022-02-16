---
title: Journaux de diagnostic
description: Journaux qui peuvent être collectés à partir d’appareils lors de la résolution des problèmes et comment ils sont stockés
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.openlocfilehash: 808ce2e426a0540c95195f26c9872f569e595715
ms.sourcegitcommit: 559df2c86a7822463ce0597140537bab260c746a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/15/2022
ms.locfileid: "62825420"
---
# <a name="diagnostic-logs"></a>Journaux de diagnostic

Que vous avez signalé un problème ou qu’un problème a été identifié par notre service, nous devons peut-être collecter certains journaux de diagnostic à partir de l’appareil sans intervention de l’utilisateur.

Nous ne collectons pas de contenu ou d’informations générés par l’utilisateur à partir des annuaires d’utilisateurs. Nous collectons uniquement les données de diagnostic et de journal qui concernent l’état et l’état de l’appareil.

Nous stockons tous les journaux collectés pendant 28 jours, puis les supprimons. Nous traiterons tous les journaux collectés à partir d’un appareil en suivant nos normes [de gestion des données](privacy-personal-data.md).

## <a name="data-collected"></a>Données collectées

La liste ci-dessous inclut tous les dossiers, journaux d’événements, fichiers exécutables ou emplacements de Registre à partir Microsoft Manged Desktop des journaux de diagnostic. Les données réelles collectées sont un sous-ensemble de cette liste et dépendent du problème identifié.

### <a name="registry-keys"></a>Clés du Registre

- HKLMSYSTEMCurrentControlSetServices\\\\\\
- HKLMSOFTWAREMicrosoftSurface\\\\\\
- HKLMSOFTWAREPoliciesMicrosoft\\\\\\\\ Windows\\ WindowsUpdate
- HKLMSYSTEMCurrentControlSetControlMUIUILanguages\\\\\\\\\\
- HKLMSoftwarePoliciesMicrosoftWindowsStore\\\\\\\\
- HKLMSoftwareMicrosoft\\\\\\ Windows\\ CurrentVersionWindowsStoreWindowsUpdate\\\\
- HKLMSOFTWAREMicrosoft\\\\\\ Windows NTCurrentVersion\\
- HKLMSOFTWAREMicrosoft\\\\\\ Windows NTCurrentVersion\\
- HKLMSOFTWAREMicrosoft\\\\\\ Windows\\ CurrentVersionAppModel\\
- HKLMSYSTEMCurrentControlSetControlFirmwareResources\\\\\\\\
- HKLMSOFTWAREMicrosoftWindowsSelfhost\\\\\\
- HKLMSOFTWAREMicrosoftWindowsUpdate\\\\\\
- HKLMSOFTWAREMicrosoft\\\\\\ Windows\\ CurrentVersionAppx\\
- HKLMSOFTWAREMicrosoft\\\\\\ Windows NTCurrentVersionSuperfetch\\\\
- HKLMSYSTEMSetup\\\\
- HKLMSoftwareMicrosoftIntuneManagementExtension\\\\\\
- HKLMSOFTWAREMicrosoftSystemCertificatesAuthRoot\\\\\\\\
- HKLMSOFTWAREMicrosoft\\\\\\ Windows Protection avancée contre les menaces
- HKLMSOFTWAREMicrosoft\\\\\\ Windows\\ CurrentVersionAuthenticationLogonUI\\\\
- HKLMSOFTWAREMicrosoft\\\\\\ Windows\\ CurrentVersionInternet\\ Paramètres
- HKLMSoftwareMicrosoft\\\\\\ Windows\\ CurrentVersionUninstall\\
- HKLMSoftwarePolicies\\\\
- HKLMSOFTWAREPoliciesMicrosoftCryptographyConfigurationSSL\\\\\\\\\\\\
- HKLMSOFTWAREPoliciesMicrosoft\\\\\\\\ Windows Protection avancée contre les menaces
- HKLMSOFTWAREWOW6432NodeMicrosoft\\\\\\\\ Windows\\ CurrentVersionUninstall\\
- HKLMSYSTEMCurrentControlSetControlSecurityProvidersSCHANNEL\\\\\\\\\\

### <a name="commands"></a>Commandes

- %programfiles%\\windows defender\\mpcmdrun.exe -GetFiles
- %windir%\\system32\\certutil.exe -store
- %windir%\\system32\\certutil.exe -store -user my
- %windir%\\system32\\Dsregcmd.exe /status
- %windir%\\system32\\ipconfig.exe /all
- %windir%\\system32\\ipconfig.exe /displaydns
- %windir%\\system32\\mdmdiagnosticstool.exe
- %windir%\\system32\\msinfo32.exe /report %temp%\\MDMDiagnosticsmsinfo32.log\\
- %windir%\\system32\\netsh.exe advfirewall show allprofiles
- %windir%\\system32\\netsh.exe advfirewall show global
- %windir%\\system32netsh.exe\\ afficher les profils
- %windir%\\system32\\netsh.exe winhttp show proxy
- %windir%\\system32netsh.exe\\ wlan show profiles
- %windir%\\system32\\netsh.exe wlan show wlanreport
- %windir%\\system32\\ping.exe -n 50 localhost
- %windir%\\system32\\powercfg.exe /batteryreport /output %temp%\\MDMDiagnostics\\battery-report.html
- %windir%\\system32\\powercfg.exe /energy /output %temp%\\MDMDiagnostics\\energy-report.html
- bitsadmin /list /allusers /verbose
- fltMC.exe
- bcdedit /enum all /v
- manage-bde -protectors -get
- Windows PowerShell commande :
    - Get-appxpackage -allusers
    - Get-appxpackage -packagetype bundle
    - Get-Service wuauserv
    - Get-NetFirewallRule
    - Get-WmiObject -Class win32product\_
    - Get-ComputerInfo
    - Get-Service
    - Get-Process
    - Get-WmiObject Win32PnPSignedDriver\_

### <a name="event-logs"></a>Journaux d’événements

- Application
- Microsoft-Windows-AppLocker/EXE et DLL
- Microsoft-Windows-AppLocker/MSI et Script
- Microsoft-Windows-AppLocker/Packaged app-Deployment
- Microsoft-Windows-AppLocker/Packaged app-Execution
- Microsoft-Windows-Bitlocker/Bitlocker Management
- Microsoft-Windows-SENSE/Operational
- Microsoft-Windows-SenseIR/Operational
- Configuration
- Système

### <a name="files"></a>Fichiers

- %ProgramData%\\MicrosoftDiagnosticLogCSPCollectors.etl\\\\\\\*
- %ProgramData%\\MicrosoftIntuneManagementExtensionLogs\\\\\\\*.\*
- %ProgramData%\\Microsoft\\ Windows Defender\\ SupportMpSupportFiles.cab\\
- %ProgramData%\\Microsoft\\ Windows\\ WlanReport\\wlan-report-latest.html
- %ProgramData%\\Microsoft\\ Windows\\ WlanReport -SourceFileName wlan-report-latest.html
- %windir%\\ccmlogs.log\\\*
- %windir%\\ccmsetuplogs.log\\\*
- %windir%\\logsCBScbs.log\\\\
- %windir%\\logsmeasuredboot\*\\.\*
- %windir%\\LogsWindowsUpdate.etl\\\*
- %windir%\\inf.log\\\*
- %windir%\\servicingsessions\\\\ActionList.xml
- %windir%\\servicingsessions\\\\Sessions.xml
- %windir%\\SoftwareDistributionDataStoreLogsedb.log\\\\\\
- %windir%\\SoftwareDistributionDataStoreDataStore.edb\\\\
- %windir%\\logsdismdism.log\\\\
- %SystemRoot%\\System32WinevtLogs\\\\\\
- %appdata%\\Microsoft\\ Teams\\ media-stack.blog\\\*
- %appdata%\\Microsoft\\ Teams\\ skylib.blog\\\*
- %appdata%\\Microsoft\\ Teams\\ media-stack.etl\\\*
- %appdata%\\Microsoft\\ Teams\\logs.txt
- %windir%\\Windows System32winevt\\\\\*.\\\*