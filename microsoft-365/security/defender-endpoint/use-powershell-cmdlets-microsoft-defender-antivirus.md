---
title: Utiliser des applets de commande PowerShell pour configurer et exécuter Antivirus Microsoft Defender
description: Dans Windows 10 et Windows 11, vous pouvez utiliser des applets de commande PowerShell pour exécuter des analyses, mettre à jour security intelligence et modifier les paramètres dans Antivirus Microsoft Defender.
keywords: scan, ligne de commande, mpcmdrun, defender
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 10/18/2020
ms.reviewer: ''
manager: dansimp
ms.technology: mde
audience: ITPro
ms.topic: how-to
ms.collection: m365-security-compliance
ms.openlocfilehash: 1cd19ff6010badd7386e937dfddb4420e76335b0
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/12/2022
ms.locfileid: "64790315"
---
# <a name="use-powershell-cmdlets-to-configure-and-manage-microsoft-defender-antivirus"></a>Utiliser des applets de commande PowerShell pour configurer et gérer Antivirus Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- Antivirus Microsoft Defender

**Plateformes**
- Windows

Vous pouvez utiliser PowerShell pour effectuer différentes fonctions dans Windows Defender. À l’instar de l’invite de commandes ou de la ligne de commande, PowerShell est un interpréteur de commandes et un langage de script basés sur des tâches conçu spécialement pour l’administration du système. Vous pouvez en savoir plus à ce sujet sur le [hub PowerShell sur MSDN](/previous-versions/msdn10/mt173057(v=msdn.10)).

Pour obtenir la liste des applets de commande et de leurs fonctions et paramètres disponibles, consultez la rubrique [sur les applets de commande Antivirus Defender](/powershell/module/defender) .

Les applets de commande PowerShell sont les plus utiles dans les environnements Windows Server qui ne s’appuient pas sur une interface utilisateur graphique (GUI) pour configurer les logiciels.

> [!NOTE]
> Les applets de commande PowerShell ne doivent pas être utilisées comme remplacement d’une infrastructure de gestion de stratégie réseau complète, telle que [Microsoft Endpoint Configuration Manager](/configmgr), [stratégie de groupe Console de gestion](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)) ou [Antivirus Microsoft Defender stratégie de groupe modèles ADMX](https://www.microsoft.com/download/101445).

Les modifications apportées à PowerShell affectent les paramètres locaux sur le point de terminaison où les modifications sont déployées ou effectuées. Cela signifie que les déploiements de stratégie avec stratégie de groupe, Microsoft Endpoint Configuration Manager ou Microsoft Intune peuvent remplacer les modifications apportées avec PowerShell.

Vous pouvez [configurer les paramètres qui peuvent être remplacés localement avec des remplacements de stratégie locale](configure-local-policy-overrides-microsoft-defender-antivirus.md).

PowerShell est généralement installé sous le dossier `%SystemRoot%\system32\WindowsPowerShell`.

## <a name="use-microsoft-defender-antivirus-powershell-cmdlets"></a>Utiliser Antivirus Microsoft Defender applets de commande PowerShell

1. Dans la barre de recherche Windows, tapez **PowerShell**.
2. Sélectionnez **Windows PowerShell** dans les résultats pour ouvrir l’interface.
3. Entrez la commande PowerShell et tous les paramètres.

> [!NOTE]
> Vous devrez peut-être ouvrir PowerShell en mode administrateur. Cliquez avec le bouton droit sur l’élément dans le menu Démarrer, cliquez sur **Exécuter en tant qu’administrateur**, puis cliquez sur **Oui** à l’invite d’autorisations.

Pour ouvrir l’aide en ligne pour l’une des applets de commande, tapez ce qui suit :

```PowerShell
Get-Help <cmdlet> -Online
```

Omettre le `-online` paramètre pour obtenir de l’aide mise en cache localement.

> [!TIP]
> Si vous recherchez des informations relatives à l’antivirus pour d’autres plateformes, consultez :
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur macOS](mac-preferences.md)
> - [Microsoft Defender pour point de terminaison sur Mac](microsoft-defender-endpoint-mac.md)
> - [Paramètres de stratégie antivirus macOS pour Antivirus Microsoft Defender pour Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur Linux](linux-preferences.md)
> - [Microsoft Defender pour point de terminaison Linux](microsoft-defender-endpoint-linux.md)
> - [Configurer Defender pour point de terminaison sur les fonctionnalités Android](android-configure.md)
> - [Configurer Microsoft Defender pour point de terminaison sur les fonctionnalités iOS](ios-configure-features.md)

## <a name="related-topics"></a>Sujets associés

- [Rubriques de référence sur les outils de gestion et de configuration](configuration-management-reference-microsoft-defender-antivirus.md)
- [Antivirus Microsoft Defender dans Windows 10](microsoft-defender-antivirus-in-windows-10.md)
- [applets de commande Antivirus Microsoft Defender](/powershell/module/defender)
