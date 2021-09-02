---
title: Utiliser les cmdlets PowerShell pour configurer et exécuter des Antivirus Microsoft Defender
description: Dans Windows 10, vous pouvez utiliser les cmdlets PowerShell pour exécuter des analyses, mettre à jour les informations de sécurité et modifier les paramètres dans Antivirus Microsoft Defender.
keywords: analyse, ligne de commande, mpcmdrun, defender
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
localization_priority: normal
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 07/23/2020
ms.reviewer: ''
manager: dansimp
ms.technology: mde
audience: ITPro
ms.topic: how-to
ms.openlocfilehash: 41d36f93ad371842d4ffe81e02cb46adb9e12288
ms.sourcegitcommit: ef9cd046c47b340686a4f7bb123ea3b0a269769a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2021
ms.locfileid: "58863952"
---
# <a name="use-powershell-cmdlets-to-configure-and-manage-microsoft-defender-antivirus"></a>Utiliser les cmdlets PowerShell pour configurer et gérer les Antivirus Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**

- [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/)

Vous pouvez utiliser PowerShell pour effectuer différentes fonctions dans Windows Defender. À l’exemple de l’invite de commandes ou de la ligne de commande, PowerShell est un shell de ligne de commande basé sur des tâches et un langage de script spécialement conçu pour l’administration du système. Pour en savoir plus, consultez le hub [PowerShell sur MSDN.](/previous-versions/msdn10/mt173057(v=msdn.10))

Pour obtenir la liste des cmdlets, leurs fonctions et les paramètres disponibles, consultez la rubrique sur les [cmdlets](/powershell/module/defender) Defender.

Les cmdlets PowerShell sont particulièrement utiles dans les environnements Windows Server qui ne reposent pas sur une interface utilisateur graphique (GUI) pour configurer des logiciels.

> [!NOTE]
> Les cmdlets PowerShell ne doivent pas être utilisées en remplacement d’une infrastructure de gestion de stratégie de réseau complète, telle que [Microsoft Endpoint Configuration Manager,](/configmgr)la [console](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11))de gestion des stratégies de groupe ou les [modèles ADMX](https://www.microsoft.com/download/101445)de stratégie de groupe Antivirus Microsoft Defender.

Les modifications apportées avec PowerShell affecteront les paramètres locaux sur le point de terminaison où les modifications sont déployées ou apportées. Cela signifie que les déploiements de stratégie avec la stratégie de groupe, Microsoft Endpoint Configuration Manager ou Microsoft Intune peuvent modifier les modifications apportées avec PowerShell.

Vous pouvez configurer les paramètres qui peuvent être remplacer localement avec les [remplacements de stratégie locale.](configure-local-policy-overrides-microsoft-defender-antivirus.md)

PowerShell est généralement installé sous le `%SystemRoot%\system32\WindowsPowerShell` dossier.

## <a name="use-microsoft-defender-antivirus-powershell-cmdlets"></a>Utiliser Antivirus Microsoft Defender cmdlets PowerShell

1. Dans la Windows de recherche, **tapez powershell.**
2. Sélectionnez **Windows PowerShell** dans les résultats pour ouvrir l’interface.
3. Entrez la commande PowerShell et tous les paramètres.

> [!NOTE]
> Vous devrez peut-être ouvrir PowerShell en mode administrateur. Cliquez avec le bouton droit sur l’élément menu Démarrer, cliquez sur Exécuter **en** tant qu’administrateur et cliquez sur **Oui** à l’invite d’autorisations.

Pour ouvrir l’aide en ligne pour l’une des cmdlets, tapez ce qui suit :

```PowerShell
Get-Help <cmdlet> -Online
```

Omettez le `-online` paramètre pour obtenir de l’aide mise en cache localement.

## <a name="related-topics"></a>Rubriques connexes

- [Rubriques de référence pour les outils de gestion et de configuration](configuration-management-reference-microsoft-defender-antivirus.md)
- [Antivirus Microsoft Defender dans Windows 10](microsoft-defender-antivirus-in-windows-10.md)
- [Antivirus Microsoft Defender Cmdlets](/powershell/module/defender)