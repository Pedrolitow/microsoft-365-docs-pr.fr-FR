---
title: Utiliser des applets de commande PowerShell pour configurer et exécuter l’antivirus Microsoft Defender
description: Dans Windows 10 et Windows 11, vous pouvez utiliser des applets de commande PowerShell pour exécuter des analyses, mettre à jour security intelligence et modifier les paramètres dans l’Antivirus Microsoft Defender.
keywords: scan, ligne de commande, mpcmdrun, defender
ms.service: microsoft-365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 09/06/2022
ms.reviewer: ''
manager: dansimp
ms.subservice: mde
audience: ITPro
ms.topic: how-to
ms.collection: m365-security-compliance
search.appverid: met150
ms.openlocfilehash: 6214a8bdfd3f2d5e3fcd05ac06bc99699bf4b7a8
ms.sourcegitcommit: 9b133379196da2b3a4bb311b07ff274f43780f68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2022
ms.locfileid: "67691516"
---
# <a name="use-powershell-cmdlets-to-configure-and-manage-microsoft-defender-antivirus"></a>Utiliser des applets de commande PowerShell pour configurer et gérer l’antivirus Microsoft Defender

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- Antivirus Microsoft Defender

**Plateformes**
- Windows

Vous pouvez utiliser PowerShell pour effectuer différentes fonctions dans Windows Defender. À l’instar de l’invite de commandes ou de la ligne de commande, PowerShell est un interpréteur de commandes et un langage de script basés sur des tâches conçu spécialement pour l’administration du système. Vous pouvez en savoir plus à ce sujet dans la [documentation PowerShell](/powershell/scripting/overview).

Pour obtenir la liste des applets de commande et de leurs fonctions et paramètres disponibles, consultez la rubrique [sur les applets de commande Antivirus Defender](/powershell/module/defender) .

Les applets de commande PowerShell sont les plus utiles dans les environnements Windows Server qui ne reposent pas sur une interface utilisateur graphique (GUI) pour configurer les logiciels.

> [!NOTE]
> Les applets de commande PowerShell ne doivent pas être utilisées comme remplacement d’une infrastructure de gestion de stratégie réseau complète, telle que [microsoft endpoint Configuration Manager](/configmgr), [stratégie de groupe Management Console](use-group-policy-microsoft-defender-antivirus.md) ou les [modèles Antivirus Microsoft Defender stratégie de groupe ADMX](https://www.microsoft.com/download/101445).

Les modifications apportées à PowerShell affectent les paramètres locaux sur le point de terminaison où les modifications sont déployées ou effectuées. Cela signifie que les déploiements de stratégie avec stratégie de groupe, Microsoft Endpoint Configuration Manager ou Microsoft Intune peuvent remplacer les modifications apportées avec PowerShell.

Vous pouvez [configurer les paramètres qui peuvent être remplacés localement avec des remplacements de stratégie locale](configure-local-policy-overrides-microsoft-defender-antivirus.md).

PowerShell est généralement installé sous le dossier `%SystemRoot%\system32\WindowsPowerShell`.

## <a name="use-microsoft-defender-antivirus-powershell-cmdlets"></a>Utiliser les applets de commande PowerShell de l’antivirus Microsoft Defender

1. Dans la barre de recherche Windows, tapez **PowerShell**.
2. Sélectionnez **Windows PowerShell** dans les résultats pour ouvrir l’interface.
3. Entrez la commande PowerShell et tous les paramètres.

> [!NOTE]
> Vous devrez peut-être ouvrir PowerShell en mode administrateur. Cliquez avec le bouton droit sur l’élément dans le menu Démarrer, cliquez sur **Exécuter en tant qu’administrateur** , puis cliquez sur **Oui** à l’invite d’autorisations.

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
> - [Configurer Defender pour point de terminaison pour des fonctionnalités Android](android-configure.md)
> - [configurer Microsoft Defender pour point de terminaison sur les fonctionnalités iOS](ios-configure-features.md)

## <a name="related-topics"></a>Voir aussi

- [Rubriques de référence sur les outils de gestion et de configuration](configuration-management-reference-microsoft-defender-antivirus.md)
- [Antivirus Microsoft Defender dans Windows 10](microsoft-defender-antivirus-in-windows-10.md)
- [Applets de commande antivirus Microsoft Defender](/powershell/module/defender)
