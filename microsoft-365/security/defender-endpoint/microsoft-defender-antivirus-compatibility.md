---
title: Microsoft Defender Compatibilité de l’antivirus avec d’autres produits de sécurité
description: Découvrez Microsoft Defender Antivirus avec d’autres produits de sécurité et les systèmes d’exploitation.
keywords: windows defender, defender pour point de terminaison, nouvelle génération, antivirus, compatibilité, mode passif
ms.pagetype: security
ms.service: microsoft-365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
ms.date: 10/20/2022
ms.topic: conceptual
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: mkaminska, pahuijbr
manager: dansimp
ms.subservice: mde
ms.collection:
- m365-security
- tier2
search.appverid: met150
ms.openlocfilehash: 2f9f9b65804d5218f2439e85af1c888b012c9a62
ms.sourcegitcommit: 87283bb02ca750286f7c069f811b788730ed5832
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2022
ms.locfileid: "68661652"
---
# <a name="microsoft-defender-antivirus-compatibility-with-other-security-products"></a>Microsoft Defender Compatibilité de l’antivirus avec d’autres produits de sécurité

**S’applique à :**

- Antivirus Microsoft Defender
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

**Plateformes**
- Windows

Microsoft Defender Antivirus est automatiquement installé sur les points de terminaison exécutant les versions suivantes de Windows :

- Windows 10 ou version ultérieure
- Windows Server 2022
- Windows Server 2019
- Windows Server, version 1803 ou ultérieure
- Windows Server 2016

Que se passe-t-il quand une autre solution antivirus/anti-programme malveillant non-Microsoft est utilisée ? Pouvez-vous exécuter Microsoft Defender Antivirus avec un autre produit antivirus ? Les réponses dépendent de plusieurs facteurs, tels que votre système d’exploitation et si vous utilisez [Microsoft Defender pour point de terminaison](microsoft-defender-endpoint.md) avec votre protection antivirus.

Cet article décrit ce qui se passe avec Microsoft Defender Antivirus et une solution antivirus/anti-programme malveillant non-Microsoft, avec et sans Defender pour point de terminaison.

> [!IMPORTANT]
> - Microsoft Defender Antivirus est disponible sur les appareils exécutant Windows 10 et 11, Windows Server 2022, Windows Server 2019, Windows Server, version 1803 ou ultérieure, et Windows Server 2016. 
> - Microsoft Defender Antivirus est également disponible sur Windows Server 2012 R2 lorsqu’il est intégré à l’aide de la [solution moderne et unifiée](/microsoft-365/security/defender-endpoint/configure-server-endpoints).
> - Sur Windows 8.1, la protection antivirus de point de terminaison au niveau de [l’entreprise](/previous-versions/system-center/system-center-2012-R2/hh508760(v=technet.10)) est proposée en tant que System Center Endpoint Protection, qui est gérée via Microsoft Endpoint Configuration Manager.
> - Windows Defender est également proposé pour [les appareils grand public sur Windows 8.1](/previous-versions/windows/it-pro/windows-8.1-and-8/dn344918(v=ws.11)#BKMK_WindowsDefender), bien que Windows Defender ne fournisse pas de gestion au niveau de l’entreprise.

## <a name="antivirus-protection-without-defender-for-endpoint"></a>Protection antivirus sans Defender pour point de terminaison

Cette section décrit ce qui se passe lorsque vous utilisez Microsoft Defender Antivirus avec des produits antivirus/anti-programme malveillant non-Microsoft sur des points de terminaison qui ne sont pas intégrés à Defender pour point de terminaison. 

> [!NOTE]
> En règle générale, Microsoft Defender Antivirus ne s’exécute pas en mode passif sur les appareils qui ne sont pas intégrés à Defender pour point de terminaison.

Le tableau suivant récapitule ce à quoi vous devez vous attendre :

|Version de Windows|Solution antivirus/anti-programme malveillant principale|état de l’antivirus Microsoft Defender|
|:---|:---|:---|
|Windows 10 <br/> Windows 11|Antivirus Microsoft Defender|Mode actif|
|Windows 10 <br/> Windows 11|Une solution antivirus/anti-programme malveillant non-Microsoft|Mode désactivé (se produit automatiquement)|
|Windows Server 2022 <br/> Windows Server 2019<br/> Windows Server, version 1803 ou ultérieure <br/> Windows Server 2016 <br/> Windows Server 2012 R2 |Antivirus Microsoft Defender|Mode actif|
|Windows Server 2022<br/>Windows Server 2019<br/>Windows Server, version 1803 ou ultérieure <br/> Windows Server 2016 |Une solution antivirus/anti-programme malveillant non-Microsoft|Désactivé (défini manuellement) <sup>[[1](#fn1)]</sup>|

(<a id="fn1">1</a>) Sur Windows Server, si vous exécutez un produit antivirus non-Microsoft, vous pouvez désinstaller Microsoft Defender Antivirus pour éviter les conflits. Si l’appareil est intégré à Microsoft Defender pour point de terminaison, vous pouvez utiliser Microsoft Defender Antivirus en mode passif (voir ci-dessous).

> [!TIP]
> Sur Windows Server 2016, vous pouvez voir *Windows Defender Antivirus* au lieu de *Microsoft Defender Antivirus*.

## <a name="microsoft-defender-antivirus-and-non-microsoft-antivirusantimalware-solutions"></a>Microsoft Defender antivirus et solutions antivirus/anti-programme malveillant non-Microsoft

> [!NOTE]
> En général, Microsoft Defender Antivirus peut être défini en mode passif uniquement sur les points de terminaison intégrés à Defender pour point de terminaison.

Le fait que Microsoft Defender antivirus s’exécute en mode actif, passif ou désactivé dépend de plusieurs facteurs, tels que :

- Quelle version de Windows est installée sur un point de terminaison
- Indique si Microsoft Defender Antivirus est la solution antivirus/anti-programme malveillant principale sur le point de terminaison
- Si le point de terminaison est intégré à Defender pour point de terminaison

Le tableau suivant récapitule l’état de Microsoft Defender Antivirus dans plusieurs scénarios. 

| Version de Windows   | Solution antivirus/anti-programme malveillant  | Intégré à <br/> Defender pour point de terminaison ? | état de l’antivirus Microsoft Defender     |
|:------|:------|:-------|:-------|
| Windows 10 <br/> Windows 11| Antivirus Microsoft Defender | Oui  | Mode actif | 
| Windows 10 <br/> Windows 11 | Antivirus Microsoft Defender | Non   | Mode actif |
| Windows 10 <br/> Windows 11  | Une solution antivirus/anti-programme malveillant non-Microsoft | Oui  | Mode passif (automatiquement) |
| Windows 10 <br/> Windows 11  | Une solution antivirus/anti-programme malveillant non-Microsoft | Non   | Mode désactivé (automatiquement)    |
| Windows Server 2022 <br/> Windows Server 2019 <br/>Windows Server, version 1803 ou ultérieure  | Antivirus Microsoft Defender  | Oui |         Mode actif  |
| Windows Server 2022 <br/> Windows Server 2019 <br/> Windows Server, version 1803 ou ultérieure   | Antivirus Microsoft Defender | Non  | Mode actif |
| Windows Server 2022 <br/> Windows Server 2019 <p> Windows Server, version 1803 ou ultérieure  | Une solution antivirus/anti-programme malveillant non-Microsoft | Oui  | Microsoft Defender Antivirus doit être défini sur le mode passif (manuellement) <sup>[[2](#fn2)]<sup>  | 
| Windows Server 2022 <br/> Windows Server 2019 <p> Windows Server, version 1803 ou ultérieure  | Une solution antivirus/anti-programme malveillant non-Microsoft | Non  | Microsoft Defender Antivirus doit être désactivé (manuellement) <sup>[[3](#fn3)]<sup></sup>  |
| Windows Server 2016 <br/> Windows Server 2012 R2   | Antivirus Microsoft Defender | Oui | Mode actif |
|Windows Server 2016 <br/> Windows Server 2012 R2  | Antivirus Microsoft Defender | Non | Mode actif |
| Windows Server 2016 <br/> Windows Server 2012 R2  | Une solution antivirus/anti-programme malveillant non-Microsoft | Oui | Microsoft Defender Antivirus doit être défini sur le mode passif (manuellement) <sup>[[2](#fn2)]<sup> |
|Windows Server 2016 <br/> Windows Server 2012 R2  | Une solution antivirus/anti-programme malveillant non-Microsoft | Non | Microsoft Defender Antivirus doit être désactivé (manuellement) <sup>[[3](#fn3)]<sup> |

(<a id="fn2">2</a>) Sur Windows Server 2019, Windows Server, version 1803 ou ultérieure, Windows Server 2016 ou Windows Server 2012 R2, Microsoft Defender Antivirus n’entre pas automatiquement en mode passif lorsque vous installez un produit antivirus non-Microsoft. Dans ce cas, définissez Microsoft Defender Antivirus en mode passif pour éviter les problèmes causés par l’installation de plusieurs produits antivirus sur un serveur. Vous pouvez définir Microsoft Defender Antivirus en mode passif à l’aide d’une clé de Registre comme suit :
- Chemin: `HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection`
- Nom : `ForceDefenderPassiveMode`
- Type: `REG_DWORD`
- Valeur : `1`

Vous pouvez afficher l’état de votre protection dans PowerShell à l’aide de la commande [Get-MpComputerStatus](/powershell/module/defender/get-mpcomputerstatus). Vérifiez la valeur de `AMRunningMode`. Vous devez voir **le mode de blocage Normal**, **Passif** ou **EDR** si Microsoft Defender Antivirus est activé sur le point de terminaison. 

 > [!NOTE]
 > Pour que le mode passif fonctionne sur des points de terminaison exécutant Windows Server 2016 et Windows Server 2012 R2, ces points de terminaison doivent être intégrés à la solution moderne et unifiée décrite dans [Intégrer des serveurs Windows](configure-server-endpoints.md#windows-server-2012-r2-and-windows-server-2016). 

(<a id="fn3">3</a>) Sur Windows Server 2016, Windows Server 2012 R2, Windows Server version 1803 ou ultérieure, Windows Server 2019 et Windows Server 2022, si vous utilisez un produit antivirus non-Microsoft sur un point de terminaison qui *n’est pas* intégré à Microsoft Defender pour point de terminaison, désactivez/désinstallez Microsoft Defender Antivirus manuellement pour éviter les problèmes causés par l’installation de plusieurs produits antivirus sur un serveur.

> [!TIP]
> Sur Windows Server 2016, vous pouvez voir *Windows Defender Antivirus* au lieu de *Microsoft Defender Antivirus*.

Defender pour point de terminaison inclut des fonctionnalités qui étendent davantage la protection antivirus installée sur votre point de terminaison. Vous pouvez tirer parti de l’exécution de Microsoft Defender Antivirus en même temps qu’une autre solution antivirus.

Par exemple, [la détection et la réponse de point de terminaison (EDR) en mode bloc](edr-in-block-mode.md) offre une protection supplémentaire contre les artefacts malveillants, même si Microsoft Defender Antivirus n’est pas le produit antivirus principal. Ces fonctionnalités nécessitent Microsoft Defender Antivirus pour être installé et s’exécuter en mode passif ou actif.

## <a name="requirements-for-microsoft-defender-antivirus-to-run-in-passive-mode"></a>Configuration requise pour Microsoft Defender Antivirus pour s’exécuter en mode passif

Pour que Microsoft Defender Antivirus s’exécute en mode passif, les points de terminaison doivent répondre aux exigences suivantes :

- Système d’exploitation : Windows 10 ou plus récent; Windows Server 2022, Windows Server 2019 ou Windows Server, version 1803 ou ultérieure <br/>(Windows Server 2012 R2 et Windows Server 2016 si elles sont intégrées à l’aide de la [solution unifiée moderne](/microsoft-365/security/defender-endpoint/configure-server-endpoints)). 
- Microsoft Defender Antivirus doit être installé. 
- Un autre produit antivirus/anti-programme malveillant non-Microsoft doit être installé et utilisé comme solution antivirus principale. 
- Les points de terminaison doivent être intégrés à Defender pour point de terminaison. 

> [!IMPORTANT]
> - antivirus Microsoft Defender est disponible uniquement sur les appareils exécutant Windows 10 et 11, Windows Server 2022, Windows Server 2016, Windows Server 2019, Windows Server, version 1803 ou ultérieure, Windows Server 2016 et Windows Server 2012 R2.
> - Le mode passif n’est pris en charge que sur Windows Server 2012 R2 & 2016 lorsque l’appareil est intégré à l’aide de la [solution unifiée moderne](/microsoft-365/security/defender-endpoint/configure-server-endpoints). 
> - Dans Windows 8.1, la protection antivirus de point de terminaison au niveau de l’entreprise est proposée en tant que [System Center Endpoint Protection](/previous-versions/system-center/system-center-2012-R2/hh508760(v=technet.10)), qui est gérée via Microsoft Endpoint Configuration Manager.
> - Windows Defender est également proposé pour [les appareils grand public sur Windows 8.1](/previous-versions/windows/it-pro/windows-8.1-and-8/dn344918(v=ws.11)#BKMK_WindowsDefender), bien que Windows Defender ne fournisse pas de gestion au niveau de l’entreprise.

## <a name="how-microsoft-defender-antivirus-affects-defender-for-endpoint-functionality"></a>Comment Microsoft Defender Antivirus affecte les fonctionnalités de Defender pour point de terminaison

Defender pour point de terminaison détermine si Microsoft Defender Antivirus peut s’exécuter en mode passif. De plus, l’état de Microsoft Defender Antivirus peut affecter certaines fonctionnalités de Defender pour point de terminaison. Par exemple, la protection en temps réel fonctionne quand Microsoft Defender Antivirus est en mode actif ou passif, mais pas quand Microsoft Defender Antivirus est désactivé ou désinstallé.

> [!IMPORTANT]
> - Le tableau de cette section récapitule les fonctionnalités qui fonctionnent activement ou non, selon qu’Microsoft Defender Antivirus est en mode actif, passif ou désactivé/désinstallé. Cette table a été conçue pour être à information uniquement.   
> - **Ne désactivez pas les fonctionnalités**, telles que la protection en temps réel, la protection fournie par le cloud ou l’analyse périodique limitée si vous utilisez Microsoft Defender Antivirus en mode passif, ou si vous utilisez [EDR en mode bloc](edr-in-block-mode.md), qui fonctionne en arrière-plan pour détecter et corriger les artefacts malveillants détectés après la violation.

| Protection | Antivirus Microsoft Defender <br/>(*Mode actif*) | Antivirus Microsoft Defender <br/>(*Mode passif*) | Antivirus Microsoft Defender <br/>(*Désactivé ou désinstallé*) | [PEPT en mode blocage](edr-in-block-mode.md) | 
|:---|:---|:---|:---|:---| 
| [Protection en temps réel](configure-real-time-protection-microsoft-defender-antivirus.md) | Oui | Voir <sup>la note [[4](#fn4)]</sup> | Non | Non | 
| [Protection fournie par le cloud](enable-cloud-protection-microsoft-defender-antivirus.md) | Oui | Non  | Non | Non | 
| [Protection du réseau](network-protection.md)  | Oui | Non | Non | Non | 
| [Règles de réduction de la surface d’attaque](attack-surface-reduction.md)  | Oui | Non | Non  | Non | 
| [Disponibilité de l’analyse périodique limitée](limited-periodic-scanning-microsoft-defender-antivirus.md) | Non | Non | Oui | Non | 
| [Informations sur l’analyse et la détection des fichiers](review-scan-results-microsoft-defender-antivirus.md) | Oui | Oui <sup>[[5](#fn5)]</sup> | Non | Oui | 
| [Correction des menaces](configure-remediation-microsoft-defender-antivirus.md) | Oui | Voir <sup>la note [[6](#fn6)]</sup> | Non | Oui | 
| [Mises à jour de la veille de sécurité](manage-updates-baselines-microsoft-defender-antivirus.md) | Oui | Oui <sup>[[7](#fn7)]</sup> | Non | Oui <sup>[[7](#fn7)]</sup> | 
| [Protection contre la perte de données](../../compliance/endpoint-dlp-learn-about.md) | Oui | Oui | Non | Non |
| [Accès contrôlé aux dossiers](controlled-folders.md) | Oui |Non | Non | Non |
| [Filtrage du contenu web](web-content-filtering.md) | Oui | Voir <sup>la note [[8](#fn8)]</sup> | Non | Non |
| [Contrôle des appareils](device-control-report.md) | Oui | Oui | Non | Non |
| [Protection PUA](detect-block-potentially-unwanted-apps-microsoft-defender-antivirus.md) | Oui | Non | Non | Non |

(<a id="fn4">4</a>) En général, quand Microsoft Defender Antivirus est en mode passif, la protection en temps réel n’offre aucun blocage ou application, même si elle est activée et en mode passif.

(<a id="fn5">5</a>) Lorsque Microsoft Defender Antivirus est en mode passif, les analyses ne sont pas planifiées.

(<a id="fn6">6</a>) Quand Microsoft Defender Antivirus est en mode passif, il ne corrige pas les menaces. Toutefois, les menaces peuvent être corrigées par [la détection et la réponse de point de terminaison (EDR) en mode bloc](edr-in-block-mode.md). Dans ce cas, vous pouvez voir des alertes affichant Microsoft Defender Antivirus en tant que source, même quand Microsoft Defender Antivirus est en mode passif.

(<a id="fn7">7</a>) La cadence des mises à jour du renseignement de sécurité est contrôlée par les paramètres Windows Update uniquement. Les planificateurs de mise à jour spécifiques à Defender (quotidiens/hebdomadaires à une heure spécifique, basés sur des intervalles) fonctionnent uniquement lorsque Microsoft Defender Antivirus est en mode actif. Ils sont ignorés en mode passif.

(<a id="fn8">8</a>) Lorsque Microsoft Defender Antivirus est en mode passif, le filtrage de contenu web fonctionne uniquement avec le navigateur Microsoft Edge. 

> [!IMPORTANT]
> - [La protection contre la perte de données de point de terminaison](/microsoft-365/compliance/endpoint-dlp-learn-about) continue de fonctionner normalement quand Microsoft Defender Antivirus est en mode actif ou passif.
>
> - Ne désactivez pas, n’arrêtez pas ou ne modifiez aucun des services associés utilisés par Microsoft Defender Antivirus, Defender pour point de terminaison ou l’application Sécurité Windows. Cette recommandation inclut les services et processus *wscsvc*, *SecurityHealthService*, *MsSense*, *Sense*, *WinDefend* ou *MsMpEng* . La modification manuelle de ces services peut entraîner une instabilité grave sur vos appareils et rendre votre réseau vulnérable. La désactivation, l’arrêt ou la modification de ces services peuvent également entraîner des problèmes lors de l’utilisation de solutions antivirus non-Microsoft et de la façon dont leurs informations sont affichées dans [l’application Sécurité Windows](microsoft-defender-security-center-antivirus.md).
>
> - Dans Defender pour point de terminaison, vous pouvez activer EDR en mode bloc, même si Microsoft Defender Antivirus n’est pas votre solution antivirus principale. EDR en mode bloc détecte et corrige les éléments malveillants détectés sur l’appareil (après une violation). Pour en savoir plus, consultez [EDR en mode bloc](edr-in-block-mode.md).

## <a name="how-to-confirm-the-state-of-microsoft-defender-antivirus"></a>Comment confirmer l’état de Microsoft Defender Antivirus

Vous pouvez utiliser l’une des méthodes suivantes pour confirmer l’état de Microsoft Defender Antivirus. Vous pouvez :

- [Utilisez l’application Sécurité Windows pour identifier votre application antivirus](#use-the-windows-security-app-to-identify-your-antivirus-app).
- [Utilisez le Gestionnaire des tâches pour confirmer que Microsoft Defender’antivirus est en cours d’exécution](#use-task-manager-to-confirm-that-microsoft-defender-antivirus-is-running).
- [Utilisez Windows PowerShell pour vérifier que Microsoft Defender Antivirus est en cours d’exécution](#use-windows-powershell-to-confirm-that-microsoft-defender-antivirus-is-running).
- [Utilisez Windows PowerShell pour vérifier que la protection antivirus est en cours d’exécution](#use-windows-powershell-to-confirm-that-antivirus-protection-is-running).

> [!IMPORTANT]
> À compter de la [version de plateforme 4.18.2208.0 et versions ultérieures](manage-updates-baselines-microsoft-defender-antivirus.md#monthly-platform-and-engine-versions) : si un serveur a été intégré à Microsoft Defender pour point de terminaison, le paramètre de stratégie de [groupe](configure-endpoints-gp.md#update-endpoint-protection-configuration) « Désactiver Windows Defender » ne désactive plus complètement Windows Defender Antivirus sur Windows Server 2012 R2 et versions ultérieures. Au lieu de cela, il le place en mode passif. En outre, la fonctionnalité de [protection contre les falsifications](prevent-changes-to-security-settings-with-tamper-protection.md) permet de passer en mode actif, mais pas en mode passif.
> 
> - Si l’option « Désactiver Windows Defender » est déjà en place avant l’intégration à Microsoft Defender pour point de terminaison, aucune modification n’est apportée et l’antivirus Defender reste désactivé.
> - Pour passer de l’antivirus Defender en mode passif, même s’il a été désactivé avant l’intégration, vous pouvez appliquer la [configuration ForceDefenderPassiveMode](switch-to-mde-phase-2.md#set-microsoft-defender-antivirus-to-passive-mode-on-windows-server) avec la valeur `1`. Pour la placer en mode actif, basculez cette valeur sur à la `0` place.
> 
> Notez la logique modifiée pour `ForceDefenderPassiveMode` l’activation de la protection contre les falsifications : une fois Microsoft Defender Antivirus basculé en mode actif, la protection contre les falsifications l’empêche de revenir en mode passif, même lorsque `ForceDefenderPassiveMode` est défini sur `1`.

### <a name="use-the-windows-security-app-to-identify-your-antivirus-app"></a>Utiliser l’application Sécurité Windows pour identifier votre application antivirus

1. Sur un appareil Windows, ouvrez l’application Sécurité Windows.

2. Sélectionnez **Protection contre les virus et les menaces**.

3. Sous **Qui me protège ?** sélectionnez **Gérer les fournisseurs**.

4. Dans la page **Fournisseurs de sécurité**, sous **Antivirus**, vous devez voir **Microsoft Defender Antivirus est activé**.

### <a name="use-task-manager-to-confirm-that-microsoft-defender-antivirus-is-running"></a>Utiliser le Gestionnaire des tâches pour vérifier que Microsoft Defender Antivirus est en cours d’exécution

1. Sur un appareil Windows, ouvrez l’application Gestionnaire des tâches.

2. Sélectionnez l’onglet **Détails** .

3. Recherchez **MsMpEng.exe** dans la liste.

### <a name="use-windows-powershell-to-confirm-that-microsoft-defender-antivirus-is-running"></a>Utiliser Windows PowerShell pour vérifier que Microsoft Defender Antivirus est en cours d’exécution

> [!NOTE]
> Utilisez cette procédure uniquement pour vérifier si Microsoft Defender Antirivus s’exécute sur un point de terminaison.

1. Sur un appareil Windows, ouvrez Windows PowerShell. 

2. Exécutez l’applet de commande PowerShell suivante : `Get-Process`.

3. Passez en revue les résultats. Vous devriez voir **MsMpEng.exe** si Microsoft Defender Antivirus est activé.

### <a name="use-windows-powershell-to-confirm-that-antivirus-protection-is-running"></a>Utiliser Windows PowerShell pour vérifier que la protection antivirus est en cours d’exécution

> [!NOTE]
> Utilisez cette procédure uniquement pour vérifier si la protection antivirus est activée sur un point de terminaison.

1. Sur un appareil Windows, ouvrez Windows PowerShell.

2. Exécutez l’applet de commande PowerShell suivante : `Get-MpComputerStatus | select AMRunningMode`.

3. Passez en revue les résultats. Vous devez voir **le mode de blocage Normal**, **Passif** ou **EDR** si la protection antivirus est activée sur le point de terminaison. 

> [!NOTE]
> Notez que cette procédure vise uniquement à vérifier si la protection antivirus est activée sur un point de terminaison.

## <a name="more-details-about-microsoft-defender-antivirus-states"></a>Plus d’informations sur les états de l’antivirus Microsoft Defender

Les sections suivantes décrivent à quoi s’attendre quand Microsoft Defender Antivirus est :

- [En mode actif](#active-mode)
- [En mode passif, ou quand EDR en mode bloc est activé](#passive-mode-or-edr-block-mode)
- [Désactivé ou désinstallé](#disabled-or-uninstalled)

### <a name="active-mode"></a>Mode actif

En mode actif, Microsoft Defender Antivirus est utilisé comme application antivirus sur l’ordinateur. Les paramètres configurés à l’aide de Configuration Manager, stratégie de groupe, Microsoft Intune ou d’autres produits de gestion s’appliquent. Les fichiers sont analysés, les menaces sont corrigées et les informations de détection sont signalées dans votre outil de configuration (par exemple, dans le centre d’administration Microsoft Endpoint Manager ou l’application antivirus Microsoft Defender sur le point de terminaison).  

### <a name="passive-mode-or-edr-block-mode"></a>Mode passif ou mode bloc EDR

En mode passif, Microsoft Defender Antivirus n’est pas utilisé comme application antivirus, et les menaces *ne sont pas* corrigées par Microsoft Defender Antivirus. Toutefois, les menaces peuvent être corrigées par [la détection et la réponse de point de terminaison (EDR) en mode bloc](edr-in-block-mode.md). Les fichiers sont analysés par EDR et des rapports sont fournis pour les détections de menaces partagées avec le service Defender pour point de terminaison. Vous pouvez voir des alertes indiquant Microsoft Defender Antivirus en tant que source, même quand Microsoft Defender Antivirus est en mode passif. 

Lorsque Microsoft Defender Antivirus est en mode passif, vous pouvez toujours [gérer les mises à jour de Microsoft Defender Antivirus](manage-updates-baselines-microsoft-defender-antivirus.md). Toutefois, vous ne pouvez pas déplacer Microsoft Defender Antivirus en mode actif si vos appareils disposent d’un produit antivirus non-Microsoft qui fournit une protection en temps réel contre les programmes malveillants.

**Veillez à obtenir vos mises à jour antivirus et anti-programme malveillant, même si Microsoft Defender Antivirus s’exécute en mode passif**. Consultez [Gérer les mises à jour de l’antivirus Microsoft Defender et appliquer des bases de référence](manage-updates-baselines-microsoft-defender-antivirus.md).<br/><br/>Notez que le mode passif n’est pris en charge que sur Windows Server 2012 R2 & 2016 lorsque la machine est intégrée à l’aide de la [solution unifiée moderne](/microsoft-365/security/defender-endpoint/configure-server-endpoints). 

### <a name="disabled-or-uninstalled"></a>Désactivé ou désinstallé

Lorsqu’il est désactivé ou désinstallé, Microsoft Defender Antivirus n’est pas utilisé comme application antivirus. Les fichiers ne sont pas analysés et les menaces ne sont pas corrigées. La désactivation ou la désinstallation de Microsoft Defender Antivirus n’est pas recommandée en général. Si possible, conservez Microsoft Defender Antivirus en mode passif si vous utilisez une solution anti-programme malveillant/antivirus non-Microsoft.

Dans les cas où Microsoft Defender Antivirus est désactivé automatiquement, il peut être réactivé automatiquement si le produit antivirus/anti-programme malveillant non-Microsoft expire, est désinstallé ou cesse de fournir une protection en temps réel contre les virus, les programmes malveillants ou d’autres menaces. La réactivation automatique de Microsoft Defender Antivirus permet de garantir que la protection antivirus est conservée sur vos points de terminaison.

Vous pouvez également utiliser une [analyse périodique limitée](limited-periodic-scanning-microsoft-defender-antivirus.md), qui fonctionne avec le moteur antivirus Microsoft Defender pour rechercher régulièrement les menaces si vous utilisez une application antivirus non-Microsoft.  | 

## <a name="what-about-non-windows-devices"></a>Qu’en est-il des appareils non Windows ?

 Si vous recherchez des informations relatives à l’antivirus pour d’autres plateformes, consultez :

- [Définir les préférences pour Microsoft Defender pour point de terminaison sur macOS](mac-preferences.md)
- [Microsoft Defender pour point de terminaison sur Mac](microsoft-defender-endpoint-mac.md)
- [Paramètres de stratégie antivirus macOS pour Antivirus Microsoft Defender pour Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
- [Définir les préférences pour Microsoft Defender pour point de terminaison sur Linux](linux-preferences.md)
- [Microsoft Defender pour point de terminaison Linux](microsoft-defender-endpoint-linux.md)
- [Configurer Defender pour point de terminaison pour des fonctionnalités Android](android-configure.md)
- [configurer Microsoft Defender pour point de terminaison sur les fonctionnalités iOS](ios-configure-features.md)

## <a name="see-also"></a>Voir aussi

- [Antivirus Microsoft Defender sur les clients Windows](microsoft-defender-antivirus-in-windows-10.md)
- [PEPT en mode blocage](edr-in-block-mode.md)
- [Découvrir la protection contre la perte de données de point de terminaison](/microsoft-365/compliance/endpoint-dlp-learn-about)
