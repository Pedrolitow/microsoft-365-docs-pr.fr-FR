---
title: Planifier des analyses rapides et complètes régulières avec l'Antivirus Microsoft Defender
description: Configurer des analyses périodiques (programmées), notamment quand elles doivent s'exécuter et s'ils s'exécutent en tant qu'analyses complètes ou rapides
keywords: analyse rapide, analyse complète, rapide ou complète, analyse de planification, quotidienne, hebdomadaire, heure, programmée, périodique, régulière
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 11/02/2020
ms.reviewer: pauhijbr
manager: dansimp
ms.technology: mde
ms.openlocfilehash: 66907fca7a117eeba7ca0b9bd95d59af24c31341
ms.sourcegitcommit: 3fe7eb32c8d6e01e190b2b782827fbadd73a18e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/13/2021
ms.locfileid: "51690627"
---
# <a name="configure-scheduled-quick-or-full-microsoft-defender-antivirus-scans"></a>Configurer des analyses rapides ou complètes de l'Antivirus Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**

- [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/)


> [!NOTE]
> Par défaut, l'Antivirus Microsoft Defender recherche une mise à jour 15 minutes avant l'heure des analyses programmées. Vous pouvez [gérer la planification du téléchargement](manage-protection-update-schedule-microsoft-defender-antivirus.md) et de l'application des mises à jour de la protection pour remplacer cette valeur par défaut. 

Outre la protection en temps réel [](run-scan-microsoft-defender-antivirus.md) toujours en cours et les analyses à la demande, vous pouvez configurer des analyses régulières et programmées. 

Vous pouvez configurer le type d'analyse, le moment où l'analyse doit se produire et si l'analyse doit se produire après une mise à jour de [la protection](manage-protection-updates-microsoft-defender-antivirus.md) ou si le point de terminaison est utilisé. Vous pouvez également spécifier à quel moment des analyses spéciales doivent être nécessaires pour terminer la correction.

Cet article explique comment configurer des analyses programmées avec la stratégie de groupe, les cmdlets PowerShell et WMI. Vous pouvez également configurer des analyses de planifications avec [Microsoft Endpoint Configuration Manager](/configmgr/protect/deploy-use/endpoint-antimalware-policies#scheduled-scans-settings) ou Microsoft [Intune.](/mem/intune/configuration/device-restrictions-windows-10)

## <a name="to-configure-the-group-policy-settings-described-in-this-article"></a>Pour configurer les paramètres de stratégie de groupe décrits dans cet article

1.  Sur votre ordinateur de gestion des stratégies de groupe, ouvrez la [Console](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11))de gestion des stratégies de groupe, cliquez avec le bouton droit sur l'objet de stratégie de groupe à configurer, puis cliquez sur **Modifier.**

3.  Dans **l'Éditeur de gestion des stratégies de** groupe, allez à **Configuration ordinateur.**

4.  Cliquez **sur Modèles d'administration.**

5.  Développez l'arborescence **des composants Windows > Antivirus Microsoft Defender,** puis l'emplacement spécifié dans le tableau ci-dessous. 

6. Double-cliquez sur le paramètre **de** stratégie comme indiqué dans le tableau ci-dessous et définissez l'option sur la configuration souhaitée. 

7. Cliquez **sur OK,** puis répétez l'une des autres configurations.

Consultez également la rubrique Gérer quand les mises à jour de [la protection](manage-protection-update-schedule-microsoft-defender-antivirus.md) doivent être téléchargées et appliquées, et empêcher ou autoriser les utilisateurs à modifier localement les [paramètres de](configure-local-policy-overrides-microsoft-defender-antivirus.md) stratégie.

## <a name="quick-scan-versus-full-scan-and-custom-scan"></a>Analyse rapide par rapport à l'analyse complète et à l'analyse personnalisée

Lorsque vous définissez des analyses programmées, vous pouvez définir si l'analyse doit être une analyse complète ou rapide.

Les analyses rapides recherchent tous les emplacements où des programmes malveillants peuvent être enregistrés pour démarrer avec le système, tels que les clés de Registre et les dossiers de démarrage Windows connus. 

Combinée avec la fonctionnalité de [protection](configure-real-time-protection-microsoft-defender-antivirus.md) en temps réel toujours en cours (qui examine les fichiers lorsqu'ils sont ouverts et fermés, et chaque fois qu'un utilisateur navigue vers un dossier), une analyse rapide permet de fournir une couverture solide à la fois pour les programmes malveillants qui commencent par le système et les programmes malveillants au niveau du noyau.  

Dans la plupart des cas, cela signifie qu'une analyse rapide est adéquate pour rechercher des programmes malveillants qui n'ont pas été détectés par la protection en temps réel.

Une analyse complète peut être utile sur les points de terminaison qui ont rencontré une menace de programmes malveillants pour identifier s'il existe des composants inactifs nécessitant un nettoyage plus approfondi. Dans ce cas, vous pouvez utiliser une analyse complète lors de l'exécution [d'une analyse à la demande.](run-scan-microsoft-defender-antivirus.md)

Une analyse personnalisée vous permet de spécifier les fichiers et dossiers à analyser, tels qu'un lecteur USB. 

>[!NOTE]
>Par défaut, les analyses rapides s'exécutent sur des appareils amovibles montés, tels que des lecteurs USB.

## <a name="set-up-scheduled-scans"></a>Configurer des analyses programmées

Les analyses programmées s'exécuteront au jour et à l'heure que vous spécifiez. Vous pouvez utiliser la stratégie de groupe, PowerShell et WMI pour configurer des analyses programmées.

>[!NOTE]
>Si un ordinateur est débranché et s'exécute sur batterie pendant une analyse complète programmée, l'analyse programmée s'arrête avec l'événement 1002, qui indique que l'analyse s'est arrêtée avant la fin. L'Antivirus Microsoft Defender exécutera une analyse complète à l'heure prévue suivante.

### <a name="use-group-policy-to-schedule-scans"></a>Utiliser une stratégie de groupe pour planifier des analyses

|Emplacement | Paramètre | Description | Paramètre par défaut (s'il n'est pas configuré) |
|:---|:---|:---|:---|
|Analyser | Spécifier le type d'analyse à utiliser pour une analyse programmée | Analyse rapide |
|Analyser | Spécifier le jour de la semaine pour exécuter une analyse programmée | Spécifiez le jour (ou jamais) d'exécuter une analyse. | Jamais |
|Analyser | Spécifier l'heure de la journée pour exécuter une analyse programmée | Spécifiez le nombre de minutes après minuit (par exemple, entrez **60** pour 1 heure du matin). | 2 h 00 |
|Root | Randomize scheduled task times |Dans l'Antivirus Microsoft Defender : rendre aléatoire l'heure de début de l'analyse à n'importe quel intervalle de 0 à 4 heures. <br>En FEP/SCEP : rendre aléatoire à n'importe quel intervalle plus ou moins 30 minutes. Cela peut être utile dans les déploiements VM ou VDI. | Activé |


### <a name="use-powershell-cmdlets-to-schedule-scans"></a>Utiliser les cmdlets PowerShell pour planifier des analyses

Utilisez les cmdlets suivantes :

```PowerShell
Set-MpPreference -ScanParameters
Set-MpPreference -ScanScheduleDay
Set-MpPreference -ScanScheduleTime
Set-MpPreference -RandomizeScheduleTaskTimes

```

Pour [plus d'informations](use-powershell-cmdlets-microsoft-defender-antivirus.md) sur l'utilisation de PowerShell avec l'Antivirus Microsoft Defender, voir les [cmdlets](/powershell/module/defender/) Utiliser PowerShell pour configurer et exécuter l'Antivirus Microsoft Defender.

### <a name="use-windows-management-instruction-wmi-to-schedule-scans"></a>Utiliser Windows Management Instruction (WMI) pour planifier des analyses

Utilisez la [ **méthode Set** de la **classe MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) pour les propriétés suivantes :

```WMI
ScanParameters
ScanScheduleDay
ScanScheduleTime
RandomizeScheduleTaskTimes
```

Pour plus d'informations et les paramètres autorisés, voir les informations suivantes :
- [Windows Defender API WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)




## <a name="start-scheduled-scans-only-when-the-endpoint-is-not-in-use"></a>Démarrer des analyses programmées uniquement lorsque le point de terminaison n'est pas en cours d'utilisation

Vous pouvez définir l'analyse programmée de façon à ce qu'elle se produise uniquement lorsque le point de terminaison est allumé mais qu'il n'est pas utilisé avec la stratégie de groupe, PowerShell ou WMI.

> [!NOTE]
> Ces analyses ne respectent pas la configuration de limitation du processeur et tirez pleinement parti des ressources disponibles pour effectuer l'analyse aussi rapidement que possible.

### <a name="use-group-policy-to-schedule-scans"></a>Utiliser une stratégie de groupe pour planifier des analyses

|Emplacement | Paramètre | Description | Paramètre par défaut (s'il n'est pas configuré) |
|:---|:---|:---|:---|
|Analyser | Démarrer l'analyse programmée uniquement lorsque l'ordinateur est en cours d'utilisation | Les analyses programmées ne s'exécutent pas, sauf si l'ordinateur est en cours d'utilisation | Activé |

### <a name="use-powershell-cmdlets"></a>Utiliser les cmdlets PowerShell

Utilisez les cmdlets suivantes :

```PowerShell
Set-MpPreference -ScanOnlyIfIdleEnabled
```

Pour [plus d'informations](use-powershell-cmdlets-microsoft-defender-antivirus.md) sur l'utilisation de PowerShell avec l'Antivirus Microsoft Defender, voir les cmdlets Utiliser PowerShell pour configurer et exécuter les [cmdlets](/powershell/module/defender/) Antivirus Microsoft Defender et Defender.

### <a name="use-windows-management-instruction-wmi"></a>Utiliser Windows Management Instruction (WMI)

Utilisez la [ **méthode Set** de la **classe MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) pour les propriétés suivantes :

```WMI
ScanOnlyIfIdleEnabled
```

Pour plus d'informations et les paramètres autorisés, voir les informations suivantes :
- [Windows Defender API WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

<a id="remed"></a>
## <a name="configure-when-full-scans-should-be-run-to-complete-remediation"></a>Configurer le moment où les analyses complètes doivent être exécutés pour terminer la correction

Certaines menaces peuvent nécessiter une analyse complète pour terminer leur suppression et leur correction. Vous pouvez planifier à quel moment ces analyses doivent se produire avec la stratégie de groupe, PowerShell ou WMI.

### <a name="use-group-policy-to-schedule-remediation-required-scans"></a>Utiliser la stratégie de groupe pour planifier des analyses nécessaires à la correction

| Emplacement | Paramètre | Description | Paramètre par défaut (s'il n'est pas configuré) |
|---|---|---|---|
|Correction | Spécifier le jour de la semaine pour exécuter une analyse complète programmée afin de terminer la correction | Spécifiez le jour (ou jamais) d'exécuter une analyse. | Jamais |
|Correction | Spécifier l'heure de la journée pour exécuter une analyse complète programmée afin de terminer la correction | Spécifiez le nombre de minutes après minuit (par exemple, entrez **60** pour 1 h 00) | 2 h 00 |

### <a name="use-powershell-cmdlets"></a>Utiliser les cmdlets PowerShell

Utilisez les cmdlets suivantes :

```PowerShell
Set-MpPreference -RemediationScheduleDay
Set-MpPreference -RemediationScheduleTime
```

Pour [plus d'informations](use-powershell-cmdlets-microsoft-defender-antivirus.md) sur l'utilisation de PowerShell avec l'Antivirus Microsoft Defender, voir les [cmdlets](/powershell/module/defender/) Utiliser PowerShell pour configurer et exécuter l'Antivirus Microsoft Defender.

### <a name="use-windows-management-instruction-wmi"></a>Utiliser Windows Management Instruction (WMI)

Utilisez la [ **méthode Set** de la **classe MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) pour les propriétés suivantes :

```WMI
RemediationScheduleDay
RemediationScheduleTime
```

Pour plus d'informations et les paramètres autorisés, voir les informations suivantes :
- [Windows Defender API WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)




## <a name="set-up-daily-quick-scans"></a>Configurer des analyses rapides quotidiennes

Vous pouvez activer une analyse rapide quotidienne qui peut être exécuté en plus de vos autres analyses programmées avec la stratégie de groupe, PowerShell ou WMI.


### <a name="use-group-policy-to-schedule-daily-scans"></a>Utiliser une stratégie de groupe pour planifier des analyses quotidiennes


|Emplacement | Paramètre | Description | Paramètre par défaut (s'il n'est pas configuré) |
|:---|:---|:---|:---|
|Analyser | Spécifier l'intervalle pour exécuter des analyses rapides par jour | Spécifiez le nombre d'heures devant s'écoulée avant la prochaine analyse rapide. Par exemple, pour exécuter toutes les deux heures, entrez **2**, pour une fois par jour, **entrez 24**. Entrez **0 pour** ne jamais exécuter une analyse rapide quotidienne. | Jamais |
|Analyser | Spécifier l'heure d'une analyse rapide quotidienne | Spécifiez le nombre de minutes après minuit (par exemple, entrez **60** pour 1 h 00) | 2 h 00 |

### <a name="use-powershell-cmdlets-to-schedule-daily-scans"></a>Utiliser les cmdlets PowerShell pour planifier des analyses quotidiennes

Utilisez les cmdlets suivantes :

```PowerShell
Set-MpPreference -ScanScheduleQuickScanTime
```

Pour [plus d'informations](use-powershell-cmdlets-microsoft-defender-antivirus.md) sur l'utilisation de PowerShell avec l'Antivirus Microsoft Defender, voir les cmdlets Utiliser PowerShell pour configurer et exécuter les [cmdlets](/powershell/module/defender/) Antivirus Microsoft Defender et Defender.

### <a name="use-windows-management-instruction-wmi-to-schedule-daily-scans"></a>Utiliser Windows Management Instruction (WMI) pour planifier des analyses quotidiennes

Utilisez la [ **méthode Set** de la **classe MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) pour les propriétés suivantes :

```WMI
ScanScheduleQuickScanTime
```

Pour plus d'informations et les paramètres autorisés, voir les informations suivantes :
- [Windows Defender API WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)


## <a name="enable-scans-after-protection-updates"></a>Activer les analyses après les mises à jour de la protection

Vous pouvez forcer une analyse à se produire après chaque mise à jour [de protection](manage-protection-updates-microsoft-defender-antivirus.md) avec la stratégie de groupe.

### <a name="use-group-policy-to-schedule-scans-after-protection-updates"></a>Utiliser la stratégie de groupe pour planifier des analyses après les mises à jour de la protection

|Emplacement | Paramètre | Description | Paramètre par défaut (s'il n'est pas configuré)|
|:---|:---|:---|:---|
|Mises à jour des signatures | Activer l'analyse après la mise à jour des informations de sécurité | Une analyse se produit immédiatement après le téléchargement d'une nouvelle mise à jour de la protection | Activé |

## <a name="see-also"></a>Voir aussi
- [Empêcher ou autoriser les utilisateurs à modifier localement les paramètres de stratégie](configure-local-policy-overrides-microsoft-defender-antivirus.md)
- [Configurer et exécuter des analyses de l'Antivirus Microsoft Defender à la demande](run-scan-microsoft-defender-antivirus.md)
- [Configurer les options d'analyse de l'Antivirus Microsoft Defender](configure-advanced-scan-types-microsoft-defender-antivirus.md)
- [Gérer les mises à jour de l'Antivirus Microsoft Defender et appliquer les lignes de base](manage-updates-baselines-microsoft-defender-antivirus.md)
- [Gérer le moment où les mises à jour de protection doivent être téléchargées et appliquées](manage-protection-update-schedule-microsoft-defender-antivirus.md) 
- [Antivirus Microsoft Defender dans Windows 10](microsoft-defender-antivirus-in-windows-10.md)