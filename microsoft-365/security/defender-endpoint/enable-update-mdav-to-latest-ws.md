---
title: Activer et mettre à jour Microsoft Defender Antivirus sur Windows Server
description: Découvrez comment activer et mettre à jour Microsoft Defender Antivirus sur Windows Server
keywords: Windows Server, Defender Antivirus
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: v-smandalika
author: v-smandalika
ms.localizationpriority: high
ms.date: 08/10/2022
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- tier2
ms.custom: intro-overview
ms.topic: conceptual
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: 16c1dc690ad6cf297059b8589818cb57596b7a9e
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68203660"
---
# <a name="enable-and-update-defender-antivirus-to-the-latest-version-on-windows-server"></a>Activer et mettre à jour l’antivirus Defender vers la dernière version sur Windows Server

Si vous souhaitez utiliser Microsoft Defender Antivirus sur votre serveur Windows Server et qu’il a déjà été désactivé ou désinstallé, vous devrez peut-être prendre d’autres mesures pour le réactiver et vous assurer qu’il est entièrement mis à jour.

Pour activer et mettre à jour Microsoft Defender Antivirus sur Windows Server, procédez comme suit :

1. Installez la dernière mise à jour de la pile de maintenance (SSU).
2. Installez la dernière mise à jour cumulative (LCU).
3. Réinstallez Microsoft Defender Antivirus ou réactivez-le. Pour plus d’informations sur la réinstallation ou la réactivation de Microsoft Defender Antivirus sur Windows Server, consultez [Réactiver Microsoft Defender Antivirus sur Windows Server s’il a été désactivé](#re-enable-microsoft-defender-antivirus-on-windows-server-if-it-was-disabled) et [Réactiver Microsoft Defender Antivirus sur Windows Server s’il a été désinstallé](#re-enable-microsoft-defender-antivirus-on-windows-server-if-it-was-uninstalled).
4. Redémarrez le système.
5. Installez la dernière version de la mise à jour de la plateforme.

   > [!NOTE]
   > La réactivation de Microsoft Defender Antivirus n’installe pas automatiquement la mise à jour de la plateforme. Vous pouvez télécharger et installer la dernière version de la plateforme à l’aide de Windows Update. Vous pouvez également télécharger le package de mise à jour à partir du [catalogue Microsoft Update](https://www.catalog.update.microsoft.com/Search.aspx?q=KB4052623) ou du [portail anti-programme malveillant et de cybersécurité](https://go.microsoft.com/fwlink/?linkid=870379&arch=x64).
   >  
   > Si vous préparez l’installation de la solution unifiée moderne sur Windows Server 2016, vous pouvez tirer parti du [script d’aide du programme d’installation](https://github.com/microsoft/mdefordownlevelserver/blob/main/Install.ps1) pour automatiser la mise à jour de la plateforme et l’installation et l’intégration suivantes. Ce script peut également aider à réactiver Microsoft Defender Antivirus.

## <a name="re-enable-microsoft-defender-antivirus-on-windows-server-if-it-was-disabled"></a>Réactiver Microsoft Defender Antivirus sur Windows Server s’il a été désactivé

Tout d’abord, assurez-vous que Microsoft Defender Antivirus n’est pas désactivé via stratégie de groupe ou le Registre. Pour plus d’informations, consultez [Résolution des problèmes Microsoft Defender Antivirus lors de la migration à partir d’une solution tierce](/microsoft-365/security/defender-endpoint/troubleshoot-microsoft-defender-antivirus-when-migrating).

Sur Windows Server 2016, dans certains cas, vous devrez peut-être utiliser [l’utilitaire de protection contre les programmes malveillants Command-Line](command-line-arguments-microsoft-defender-antivirus.md) pour réactiver Microsoft Defender Antivirus.

En tant qu’administrateur local sur le serveur, procédez comme suit :

1. Ouvrez une invite de commandes.
2. Exécutez la commande suivante : `MpCmdRun.exe -wdenable`.
3. Redémarrez lʼappareil.

## <a name="re-enable-microsoft-defender-antivirus-on-windows-server-if-it-was-uninstalled"></a>Réactiver Microsoft Defender Antivirus sur Windows Server s’il a été désinstallé

Si la fonctionnalité Defender a été désinstallée/supprimée, vous pouvez la rajouter.

En tant qu’administrateur local sur le serveur, procédez comme suit :

1. Ouvrez Windows PowerShell.

2. Exécutez les commandes suivantes :

   ```powershell
   # For Windows Server 2016
   Dism /Online /Enable-Feature /FeatureName:Windows-Defender-Features
   Dism /Online /Enable-Feature /FeatureName:Windows-Defender
   Dism /Online /Enable-Feature /FeatureName:Windows-Defender-Gui
   
   # For Windows Server 1803 and later, including Windows Server 2019 and 2022
   Dism /Online /Enable-Feature /FeatureName:Windows-Defender
   ```

   Lorsque la commande DISM est utilisée dans une séquence de tâches exécutant PowerShell, le chemin d’accès suivant à cmd.exe est requis.
   
   ```powershell
   C:\Windows\System32\cmd.exe /c Dism /Online /Enable-Feature /FeatureName:Windows-Defender-Features
   C:\Windows\System32\cmd.exe /c Dism /Online /Enable-Feature /FeatureName:Windows-Defender
   ```

   > [!NOTE]
   > Vous pouvez également utiliser des applets de commande Gestionnaire de serveur ou PowerShell pour installer la fonctionnalité antivirus Microsoft Defender.

3. Redémarrez le système.
