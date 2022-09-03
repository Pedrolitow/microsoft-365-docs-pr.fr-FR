---
title: Exécuter et personnaliser des analyses à la demande dans l’Antivirus Microsoft Defender
description: Exécuter et configurer des analyses à la demande à l’aide de PowerShell, de Windows Management Instrumentation ou individuellement sur des points de terminaison avec l’application Sécurité Windows
keywords: analyse, à la demande, dos, intune, analyse instantanée
ms.service: microsoft-365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
ms.topic: article
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 10/22/2021
ms.reviewer: ''
manager: dansimp
ms.subservice: mde
ms.collection: M365-security-compliance
ms.openlocfilehash: 582edcff46b6576b1e11ddff0e10cd1e1b43facb
ms.sourcegitcommit: d3ef9391f621e8f4ca70661184b3bb82c6cbda94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2022
ms.locfileid: "67584548"
---
# <a name="configure-and-run-on-demand-microsoft-defender-antivirus-scans"></a>Configurer et exécuter des analyses à la demande avec l’antivirus Microsoft Defender

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- Antivirus Microsoft Defender

**Plateformes**
- Windows

Vous pouvez exécuter une analyse à la demande sur des points de terminaison individuels. Ces analyses démarrent immédiatement et vous pouvez définir des paramètres pour l’analyse, tels que l’emplacement ou le type. Lorsque vous exécutez une analyse, vous pouvez choisir parmi trois types : analyse rapide, analyse complète et analyse personnalisée. Dans la plupart des cas, utilisez une analyse rapide. Une analyse rapide examine tous les emplacements où des programmes malveillants peuvent être inscrits pour démarrer avec le système, tels que les clés de Registre et les dossiers de démarrage Windows connus.

Combinée à une protection en temps réel toujours activée, qui examine les fichiers lorsqu’ils sont ouverts et fermés, et chaque fois qu’un utilisateur accède à un dossier, une analyse rapide permet de fournir une protection forte contre les programmes malveillants qui commencent par le système et les programmes malveillants au niveau du noyau. Dans la plupart des cas, une analyse rapide est suffisante et est l’option recommandée pour les analyses planifiées ou à la demande. [En savoir plus sur les types d’analyse](schedule-antivirus-scans.md#quick-scan-full-scan-and-custom-scan).

> [!IMPORTANT]
> L’Antivirus Microsoft Defender s’exécute dans le contexte du compte [LocalSystem](/windows/win32/services/localsystem-account) lors d’une analyse locale. Pour les analyses réseau, il utilise le contexte du compte d’appareil. Si le compte d’appareil de domaine ne dispose pas des autorisations appropriées pour accéder au partage, l’analyse ne fonctionnera pas. Vérifiez que l’appareil dispose des autorisations d’accès au partage réseau.

## <a name="use-microsoft-endpoint-manager-to-run-a-scan"></a>Utiliser Microsoft Endpoint Manager pour exécuter une analyse

1. Accédez au Centre d’administration Microsoft Endpoint Manager ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) et connectez-vous.

2. Choisissez **l’antivirus de sécurité de point de terminaison**\>.

3. Dans la liste des onglets, sélectionnez Windows 10 points de **terminaison non sains** ou **Windows 11 points de terminaison non sains**.

4. Dans la liste des actions fournies, sélectionnez **Analyse rapide** (recommandée) ou **Analyse complète**.

   [![Options d’analyse sous l’onglet Windows 10 points de terminaison non sains.](images/mem-antivirus-scan-on-demand.png)](images/mem-antivirus-scan-on-demand.png#lightbox)

> [!TIP]
> Pour plus d’informations sur l’utilisation de Microsoft Endpoint Manager pour exécuter une analyse, consultez [Antimalware et les tâches de pare-feu : Comment effectuer une analyse à la demande](/configmgr/protect/deploy-use/endpoint-antimalware-firewall#how-to-perform-an-on-demand-scan-of-computers).

## <a name="use-the-mpcmdrunexe-command-line-utility-to-run-a-scan"></a>Utiliser l’utilitaire de ligne de commande mpcmdrun.exe pour exécuter une analyse

Utilisez le paramètre suivant :`-scan`

```console
mpcmdrun.exe -scan -scantype 1
```

Pour plus d’informations sur l’utilisation de l’outil et des paramètres supplémentaires, notamment le démarrage d’une analyse complète ou la définition de chemins d’accès, consultez [l’outil de ligne de commande mpcmdrun.exe pour configurer et gérer l’antivirus Microsoft Defender](command-line-arguments-microsoft-defender-antivirus.md).

## <a name="use-microsoft-intune-to-run-a-scan"></a>Utiliser Microsoft Intune pour exécuter une analyse

1. Accédez au Centre d’administration Microsoft Endpoint Manager ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) et connectez-vous.

2. Dans la barre latérale, sélectionnez **Appareils** \> **tous les appareils** et choisissez l’appareil que vous souhaitez analyser.

3. Sélectionnez **... Plus encore**. Dans les options, sélectionnez **Analyse rapide** (recommandée) ou **Analyse complète**.

## <a name="use-the-windows-security-app-to-run-a-scan"></a>Utiliser l’application Sécurité Windows pour exécuter une analyse

Consultez [Exécuter une analyse dans l’application Sécurité Windows](microsoft-defender-security-center-antivirus.md) pour obtenir des instructions sur l’exécution d’une analyse sur des points de terminaison individuels.

## <a name="use-powershell-cmdlets-to-run-a-scan"></a>Utiliser des applets de commande PowerShell pour exécuter une analyse

Utilisez l’applet de commande suivante :

```PowerShell
Start-MpScan
```

Pour plus d’informations sur l’utilisation de PowerShell avec l’Antivirus Microsoft Defender, consultez [Utiliser les applets de commande PowerShell pour configurer et exécuter](use-powershell-cmdlets-microsoft-defender-antivirus.md) les [applets](/powershell/module/defender/) de commande antivirus Microsoft Defender et Defender.

## <a name="use-windows-management-instruction-wmi-to-run-a-scan"></a>Utiliser WMI (Windows Management Instruction) pour exécuter une analyse

Utilisez la [méthode **Start**](/previous-versions/windows/desktop/defender/start-msft-mpscan) de la classe **MSFT_MpScan**.

Pour plus d’informations sur les paramètres autorisés, consultez [Windows Defender API WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

> [!TIP]
> Si vous recherchez des informations relatives à l’antivirus pour d’autres plateformes, consultez :
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur macOS](mac-preferences.md)
> - [Microsoft Defender pour point de terminaison sur Mac](microsoft-defender-endpoint-mac.md)
> - [Paramètres de stratégie antivirus macOS pour Antivirus Microsoft Defender pour Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur Linux](linux-preferences.md)
> - [Microsoft Defender pour point de terminaison Linux](microsoft-defender-endpoint-linux.md)
> - [Configurer Defender pour point de terminaison pour des fonctionnalités Android](android-configure.md)
> - [configurer Microsoft Defender pour point de terminaison sur les fonctionnalités iOS](ios-configure-features.md)