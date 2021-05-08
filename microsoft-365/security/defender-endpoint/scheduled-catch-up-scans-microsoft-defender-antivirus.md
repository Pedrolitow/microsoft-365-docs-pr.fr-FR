---
title: Planifier des analyses rapides et complètes régulières avec Antivirus Microsoft Defender
description: Configurer des analyses périodiques (programmées), notamment quand elles doivent s’exécuter et s’ils s’exécutent en tant qu’analyses complètes ou rapides
keywords: analyse rapide, analyse complète, rapide ou complète, analyse de planification, quotidienne, hebdomadaire, heure, programmée, périodique, régulière
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
localization_priority: Normal
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 05/05/2021
ms.reviewer: pauhijbr, ksarens
manager: dansimp
ms.technology: mde
ms.topic: how-to
ms.openlocfilehash: 1748a33be2c27123eb0437784dcdb2cb7905616a
ms.sourcegitcommit: 51b316c23e070ab402a687f927e8fa01cb719c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2021
ms.locfileid: "52274687"
---
# <a name="configure-scheduled-quick-or-full-microsoft-defender-antivirus-scans"></a>Configurer des analyses antivirus Microsoft Defender rapides ou complètes

**S’applique à :**

- [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/)


> [!NOTE]
> Par défaut, Antivirus Microsoft Defender recherche une mise à jour 15 minutes avant l’heure des analyses programmées. Vous pouvez [gérer la planification du téléchargement](manage-protection-update-schedule-microsoft-defender-antivirus.md) et de l’application des mises à jour de la protection pour remplacer cette valeur par défaut. 

Outre la protection en temps réel [](run-scan-microsoft-defender-antivirus.md) toujours en cours et les analyses à la demande, vous pouvez configurer des analyses régulières et programmées. 

Vous pouvez configurer le type d’analyse, le moment où l’analyse doit se produire et si l’analyse doit se produire après une mise à jour de [la protection](manage-protection-updates-microsoft-defender-antivirus.md) ou si le point de terminaison est utilisé. Vous pouvez également spécifier à quel moment des analyses spéciales doivent être nécessaires pour terminer la correction.

Cet article explique comment configurer des analyses programmées avec la stratégie de groupe, les cmdlets PowerShell et WMI. Vous pouvez également configurer des analyses de planifications [avec Microsoft Endpoint Configuration Manager](/configmgr/protect/deploy-use/endpoint-antimalware-policies#scheduled-scans-settings) ou [Microsoft Intune](/mem/intune/configuration/device-restrictions-windows-10).

## <a name="to-configure-the-group-policy-settings-described-in-this-article"></a>Pour configurer les paramètres de stratégie de groupe décrits dans cet article

1. Sur votre ordinateur de gestion des stratégies de groupe, dans l’Éditeur de stratégie de groupe, allez à Modèles d’administration de **configuration** ordinateur  >    >  **Windows composants**  >    >  **Antivirus Microsoft Defender’analyse.**

2. Cliquez avec le bouton droit sur l’objet de stratégie de groupe à configurer, puis sélectionnez **Modifier.**

3. Spécifiez les paramètres de l’objet de stratégie de groupe, puis sélectionnez **OK**. 

4. Répétez les étapes 1 à 4 pour chaque paramètre à configurer.

5. Déployez votre objet de stratégie de groupe comme vous le faites normalement. Si vous avez besoin d’aide sur les objets de stratégie de groupe, voir [Créer un objet de stratégie de groupe.](/windows/security/threat-protection/windows-firewall/create-a-group-policy-object)

Consultez également la rubrique Gérer quand les mises à jour de [la protection](manage-protection-update-schedule-microsoft-defender-antivirus.md) doivent être téléchargées et appliquées, et empêcher ou autoriser les utilisateurs à modifier localement les [paramètres de](configure-local-policy-overrides-microsoft-defender-antivirus.md) stratégie.

## <a name="quick-scan-versus-full-scan-and-custom-scan"></a>Analyse rapide par rapport à l’analyse complète et à l’analyse personnalisée

Lorsque vous définissez des analyses programmées, vous pouvez définir si l’analyse doit être une analyse complète ou rapide.


|Analyse rapide  |Analyse complète  | Analyse personnalisée |
|---------|---------|---------|
|Une analyse rapide examine tous les emplacements où des programmes malveillants peuvent être enregistrés pour démarrer avec le système, tels que les clés de Registre et les dossiers de démarrage Windows connus. <p>Dans la plupart des cas, une analyse rapide est suffisante et est recommandée pour les analyses programmées. |Une analyse complète commence par l’exécution d’une analyse rapide, puis se poursuit avec une analyse séquentielle de tous les disques fixes montés et lecteurs amovibles/réseau (si l’analyse complète est configurée pour le faire). <p>L’analyse complète peut prendre quelques heures ou jours, en fonction de la quantité et du type de données à analyser.<p>Une fois l’analyse complète terminée, de nouvelles informations de sécurité sont disponibles et une nouvelle analyse est nécessaire pour s’assurer qu’aucune autre menace n’est détectée avec la nouvelle intelligence de sécurité.   | Une analyse personnalisée est une analyse rapide qui s’exécute sur les fichiers et dossiers que vous spécifiez. Par exemple, vous pouvez choisir d’analyser un lecteur USB ou un dossier spécifique sur le lecteur local de votre appareil. <p> | 

>[!NOTE]
>Par défaut, les analyses rapides s’exécutent sur des appareils amovibles montés, tels que des lecteurs USB.

### <a name="how-do-i-know-which-scan-type-to-choose"></a>Comment savoir quel type d’analyse choisir ?

Utilisez le tableau suivant pour choisir un type d’analyse.


|Scénario  |Type d’analyse recommandé  |
|---------|---------|
|Vous souhaitez configurer des analyses régulières et programmées     | Analyse rapide <p>Une analyse rapide vérifie les processus, la mémoire, les profils et certains emplacements de l’appareil. Combinée à [une protection en](configure-real-time-protection-microsoft-defender-antivirus.md)temps réel toujours en cours, une analyse rapide permet d’assurer une couverture forte à la fois pour les programmes malveillants qui commencent par le système et les programmes malveillants au niveau du noyau. La protection en temps réel examine les fichiers lorsqu’ils sont ouverts et fermés, et chaque fois qu’un utilisateur navigue vers un dossier.         |
|Les menaces, telles que les programmes malveillants, sont détectées sur un appareil     | Analyse complète <p>Une analyse complète peut aider à identifier s’il existe des composants inactifs qui nécessitent un nettoyage plus approfondi.         |
|Vous souhaitez exécuter une [analyse à la demande](run-scan-microsoft-defender-antivirus.md)     | Analyse complète  <p>Une analyse complète examine tous les fichiers sur le disque de l’appareil, y compris les fichiers obsolètes, archivés et qui ne sont pas accessibles quotidiennement.      |
| Vous souhaitez vous assurer qu’un appareil portable, tel qu’un lecteur USB, ne contient pas de programmes malveillants. | Analyse personnalisée <p>Une analyse personnalisée vous permet de sélectionner des emplacements, dossiers ou fichiers spécifiques et exécute une analyse rapide. |

### <a name="what-else-do-i-need-to-know-about-quick-and-full-scans"></a>Que dois-je savoir d’autre sur les analyses rapides et complètes ?

- Les fichiers malveillants peuvent être stockés dans des emplacements qui ne sont pas inclus dans une analyse rapide. Toutefois, la protection en temps réel toujours en cours examine tous les fichiers ouverts et fermés, ainsi que tous les fichiers qui se contiennent dans des dossiers accessibles par un utilisateur. La combinaison d’une protection en temps réel et d’une analyse rapide permet de fournir une protection forte contre les programmes malveillants.

- La protection à l’accès avec une protection assurée par le [cloud](cloud-protection-microsoft-defender-antivirus.md) permet de s’assurer que tous les fichiers accessibles sur le système sont analysés avec les derniers modèles d’intelligence de sécurité et d’apprentissage automatique dans le Cloud.

- Lorsque la protection en temps réel détecte des programmes malveillants et que l’étendue des fichiers affectés n’est pas déterminée initialement, Antivirus Microsoft Defender lance une analyse complète dans le cadre du processus de correction.

- Une analyse complète peut détecter des fichiers malveillants qui n’ont pas été détectés par d’autres analyses, telles qu’une analyse rapide. Toutefois, une analyse complète peut prendre un certain temps et utiliser des ressources système précieuses pour se terminer.

- Si un appareil est hors connexion pendant une période prolongée, une analyse complète peut prendre plus de temps. 

## <a name="set-up-scheduled-scans"></a>Configurer des analyses programmées

Les analyses programmées s’exécutent le jour et l’heure que vous spécifiez. Vous pouvez utiliser la stratégie de groupe, PowerShell et WMI pour configurer des analyses programmées.

> [!NOTE]
> Si un appareil est débranché et s’exécute sur batterie pendant une analyse complète programmée, l’analyse programmée s’arrête avec l’événement 1002, qui indique que l’analyse s’est arrêtée avant la fin. Antivirus Microsoft Defender exécutera une analyse complète à l’heure prévue suivante.

### <a name="use-group-policy-to-schedule-scans"></a>Utiliser une stratégie de groupe pour planifier des analyses

|Lieu | Paramètre | Description | Paramètre par défaut (s’il n’est pas configuré) |
|:---|:---|:---|:---|
|Analyser | Spécifier le type d’analyse à utiliser pour une analyse programmée | Analyse rapide |
|Analyser | Spécifier le jour de la semaine pour exécuter une analyse programmée | Spécifiez le jour (ou jamais) d’exécuter une analyse. | Jamais |
|Analyser | Spécifier l’heure de la journée pour exécuter une analyse programmée | Spécifiez le nombre de minutes après minuit (par exemple, entrez **60** pour 1 heure du matin). | 2 h 00 |
|Root | Randomize scheduled task times |In Antivirus Microsoft Defender, randomize the start time of the scan to any interval from 0 to 4 hours. <p>Dans [SCEP](/mem/intune/protect/certificates-scep-configure), rendre aléatoires les analyses à n’importe quel intervalle plus ou moins 30 minutes. Cela peut être utile dans les machines virtuelles ou les déploiements VDI. | Activé |


### <a name="use-powershell-cmdlets-to-schedule-scans"></a>Utiliser les cmdlets PowerShell pour planifier des analyses

Utilisez les cmdlets suivantes :

```PowerShell
Set-MpPreference -ScanParameters
Set-MpPreference -ScanScheduleDay
Set-MpPreference -ScanScheduleTime
Set-MpPreference -RandomizeScheduleTaskTimes

```

Pour plus d’informations, voir Utiliser les [cmdlets PowerShell](use-powershell-cmdlets-microsoft-defender-antivirus.md) pour configurer et exécuter des [cmdlets](/powershell/module/defender/) Antivirus Microsoft Defender et Defender pour plus d’informations sur l’utilisation de PowerShell avec Antivirus Microsoft Defender.

### <a name="use-windows-management-instruction-wmi-to-schedule-scans"></a>Utiliser Windows Management Instruction (WMI) pour planifier des analyses

Utilisez la [ **méthode Set** de la **classe MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) pour les propriétés suivantes :

```WMI
ScanParameters
ScanScheduleDay
ScanScheduleTime
RandomizeScheduleTaskTimes
```

Pour plus d’informations et des paramètres autorisés, [voir Windows Defender API WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)


## <a name="start-scheduled-scans-only-when-the-endpoint-is-not-in-use"></a>Démarrer des analyses programmées uniquement lorsque le point de terminaison n’est pas en cours d’utilisation

Vous pouvez définir l’analyse programmée de façon à ce qu’elle se produise uniquement lorsque le point de terminaison est allumé mais qu’il n’est pas utilisé avec la stratégie de groupe, PowerShell ou WMI.

> [!NOTE]
> Ces analyses ne respectent pas la configuration de limitation du processeur et tirez pleinement parti des ressources disponibles pour effectuer l’analyse aussi rapidement que possible.

### <a name="use-group-policy-to-schedule-scans"></a>Utiliser une stratégie de groupe pour planifier des analyses

|Lieu | Paramètre | Description | Paramètre par défaut (s’il n’est pas configuré) |
|:---|:---|:---|:---|
|Analyser | Démarrer l’analyse programmée uniquement lorsque l’ordinateur est en cours d’utilisation | Les analyses programmées ne s’exécutent pas, sauf si l’ordinateur est en cours d’utilisation | Activé |

### <a name="use-powershell-cmdlets"></a>Utiliser les cmdlets PowerShell

Utilisez les cmdlets suivantes :

```PowerShell
Set-MpPreference -ScanOnlyIfIdleEnabled
```

Pour plus d’informations, [voir Utiliser les cmdlets PowerShell](use-powershell-cmdlets-microsoft-defender-antivirus.md) pour configurer et exécuter les [cmdlets](/powershell/module/defender/)Antivirus Microsoft Defender et Defender.

### <a name="use-windows-management-instruction-wmi"></a>Utiliser Windows Management Instruction (WMI)

Utilisez la [ **méthode Set** de la **classe MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) pour les propriétés suivantes :

```WMI
ScanOnlyIfIdleEnabled
```

Pour plus d’informations sur les API et les paramètres autorisés, [voir Windows Defender API WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal).

<a id="remed"></a>
## <a name="configure-when-full-scans-should-be-run-to-complete-remediation"></a>Configurer le moment où les analyses complètes doivent être exécutés pour terminer la correction

Certaines menaces peuvent nécessiter une analyse complète pour terminer leur suppression et leur correction. Vous pouvez spécifier quand ces analyses doivent se produire avec la stratégie de groupe, PowerShell ou WMI.

### <a name="use-group-policy-to-schedule-remediation-required-scans"></a>Utiliser une stratégie de groupe pour planifier des analyses requises pour la correction

| Lieu | Paramètre | Description | Paramètre par défaut (s’il n’est pas configuré) |
|---|---|---|---|
|Correction | Spécifier le jour de la semaine pour exécuter une analyse complète programmée afin de terminer la correction | Spécifiez le jour (ou jamais) d’exécuter une analyse. | Jamais |
|Correction | Spécifier l’heure de la journée pour exécuter une analyse complète programmée afin de terminer la correction | Spécifiez le nombre de minutes après minuit (par exemple, entrez **60** pour 1 h 00) | 2 h 00 |

### <a name="use-powershell-cmdlets"></a>Utiliser les cmdlets PowerShell

Utilisez les cmdlets suivantes :

```PowerShell
Set-MpPreference -RemediationScheduleDay
Set-MpPreference -RemediationScheduleTime
```

Pour plus d’informations sur l’utilisation de PowerShell avec Antivirus Microsoft Defender, voir utiliser les [cmdlets PowerShell](use-powershell-cmdlets-microsoft-defender-antivirus.md) pour configurer et exécuter des [cmdlets](/powershell/module/defender/) Antivirus Microsoft Defender et Defender.

### <a name="use-windows-management-instruction-wmi"></a>Utiliser Windows Management Instruction (WMI)

Utilisez la [ **méthode Set** de la **classe MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) pour les propriétés suivantes :

```WMI
RemediationScheduleDay
RemediationScheduleTime
```

Pour plus d’informations et les paramètres autorisés, [voir Windows Defender API WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal).


## <a name="set-up-daily-quick-scans"></a>Configurer des analyses rapides quotidiennes

Vous pouvez activer une analyse rapide quotidienne qui peut être exécuté en plus de vos autres analyses programmées avec la stratégie de groupe, PowerShell ou WMI.

### <a name="use-group-policy-to-schedule-daily-scans"></a>Utiliser une stratégie de groupe pour planifier des analyses quotidiennes

|Lieu | Paramètre | Description | Paramètre par défaut (s’il n’est pas configuré) |
|:---|:---|:---|:---|
|Analyser | Spécifier l’intervalle pour exécuter des analyses rapides par jour | Spécifiez le nombre d’heures devant s’écoulée avant la prochaine analyse rapide. Par exemple, pour exécuter toutes les deux heures, entrez **2**, pour une fois par jour, **entrez 24**. Entrez **0 pour** ne jamais exécuter une analyse rapide quotidienne. | Jamais |
|Analyser | Spécifier l’heure d’une analyse rapide quotidienne | Spécifiez le nombre de minutes après minuit (par exemple, entrez **60** pour 1 h 00) | 2 h 00 |

### <a name="use-powershell-cmdlets-to-schedule-daily-scans"></a>Utiliser les cmdlets PowerShell pour planifier des analyses quotidiennes

Utilisez les cmdlets suivantes :

```PowerShell
Set-MpPreference -ScanScheduleQuickScanTime
```

Pour plus d’informations sur l’utilisation de PowerShell avec Antivirus Microsoft Defender, voir Utiliser les [cmdlets PowerShell](use-powershell-cmdlets-microsoft-defender-antivirus.md) pour configurer et exécuter des [cmdlets](/powershell/module/defender/)Antivirus Microsoft Defender et Defender.

### <a name="use-windows-management-instruction-wmi-to-schedule-daily-scans"></a>Utiliser Windows Management Instruction (WMI) pour planifier des analyses quotidiennes

Utilisez la [ **méthode Set** de la **classe MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) pour les propriétés suivantes :

```WMI
ScanScheduleQuickScanTime
```

Pour plus d’informations et les paramètres autorisés, [voir Windows Defender API WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal).


## <a name="enable-scans-after-protection-updates"></a>Activer les analyses après les mises à jour de la protection

Vous pouvez forcer l’analyse après chaque mise à jour [de la protection](manage-protection-updates-microsoft-defender-antivirus.md) avec la stratégie de groupe.

### <a name="use-group-policy-to-schedule-scans-after-protection-updates"></a>Utiliser la stratégie de groupe pour planifier des analyses après les mises à jour de la protection

|Lieu | Paramètre | Description | Paramètre par défaut (s’il n’est pas configuré)|
|:---|:---|:---|:---|
|Mises à jour des signatures | Activer l’analyse après la mise à jour des informations de sécurité | Une analyse se produit immédiatement après le téléchargement d’une nouvelle mise à jour de la protection | Activé |

## <a name="see-also"></a>Voir aussi

- [Empêcher ou autoriser les utilisateurs à modifier localement les paramètres de stratégie](configure-local-policy-overrides-microsoft-defender-antivirus.md)
- [Configurer et exécuter des analyses à la demande avec l’antivirus Microsoft Defender](run-scan-microsoft-defender-antivirus.md).
- [Configurer les options d’analyse de l’antivirus Microsoft Defender](configure-advanced-scan-types-microsoft-defender-antivirus.md)
- [Gérer les mises Antivirus Microsoft Defender jour et appliquer les lignes de base](manage-updates-baselines-microsoft-defender-antivirus.md)
- [Gérer le moment où les mises à jour de protection doivent être téléchargées et appliquées](manage-protection-update-schedule-microsoft-defender-antivirus.md) 
- [Antivirus Microsoft Defender dans Windows 10](microsoft-defender-antivirus-in-windows-10.md)