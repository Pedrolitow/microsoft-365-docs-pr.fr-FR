---
title: Compatibilité de l’antivirus Microsoft Defender avec d’autres produits de sécurité
description: Découvrez l’Antivirus Microsoft Defender avec d’autres produits de sécurité et les systèmes d’exploitation.
keywords: windows defender, defender pour point de terminaison, nouvelle génération, antivirus, compatibilité, mode passif
ms.pagetype: security
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
ms.topic: article
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: mkaminska, pahuijbr
manager: dansimp
ms.technology: mde
ms.collection:
- M365-security-compliance
- m365initiative-defender-endpoint
ms.openlocfilehash: 860c1cd36568705b2646cf14b6fea071af4a19a5
ms.sourcegitcommit: aa9e1bceb661df894f66d5dd5f4ab692c870fc71
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/13/2022
ms.locfileid: "66756602"
---
# <a name="microsoft-defender-antivirus-compatibility-with-other-security-products"></a>Compatibilité de l’antivirus Microsoft Defender avec d’autres produits de sécurité

**S’applique à :**

- Antivirus Microsoft Defender
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

**Plateformes**
- Windows

L’Antivirus Microsoft Defender est installé automatiquement sur les points de terminaison exécutant les versions suivantes de Windows :

- Windows 10 ou plus récent
- Windows Server 2022
- Windows Server 2019
- Windows Server, version 1803 ou ultérieure
- Windows Server 2016

Que se passe-t-il quand une autre solution antivirus/anti-programme malveillant non Microsoft est utilisée ? Pouvez-vous exécuter l’Antivirus Microsoft Defender avec un autre produit antivirus ? Les réponses dépendent de plusieurs facteurs, tels que votre système d’exploitation et si vous utilisez [Microsoft Defender pour point de terminaison](microsoft-defender-endpoint.md) avec votre protection antivirus.

Cet article décrit ce qui se passe avec l’antivirus Microsoft Defender et une solution antivirus/anti-programme malveillant non Microsoft, avec et sans Defender pour point de terminaison.

> [!IMPORTANT]
> - L’Antivirus Microsoft Defender est disponible sur les appareils exécutant Windows 10 et 11, Windows Server 2022, Windows Server 2019, Windows Server, version 1803 ou ultérieure, et Windows Server 2016. 
> - L’antivirus Microsoft Defender est également disponible sur Windows Server 2012 R2 lors de l’intégration à l’aide de la [solution moderne et unifiée](/microsoft-365/security/defender-endpoint/configure-server-endpoints).
> - Sur Windows 8.1, la protection antivirus de point de terminaison au niveau de l’entreprise est proposée en [tant que System Center Endpoint Protection](/previous-versions/system-center/system-center-2012-R2/hh508760(v=technet.10)), qui est gérée par le biais de Microsoft Endpoint Configuration Manager.
> - Windows Defender est également proposé pour [les appareils grand public sur Windows 8.1](/previous-versions/windows/it-pro/windows-8.1-and-8/dn344918(v=ws.11)#BKMK_WindowsDefender), bien que Windows Defender n’assure pas la gestion au niveau de l’entreprise.

## <a name="antivirus-protection-without-defender-for-endpoint"></a>Protection antivirus sans Defender pour point de terminaison

Cette section décrit ce qui se passe lorsque vous utilisez l’antivirus Microsoft Defender avec des produits antivirus/anti-programme malveillant non Microsoft sur des points de terminaison qui ne sont pas intégrés à Defender pour point de terminaison. 

> [!NOTE]
> En général, l’Antivirus Microsoft Defender ne s’exécute pas en mode passif sur les appareils qui ne sont pas intégrés à Defender pour point de terminaison.

Le tableau suivant récapitule les attentes :

|Version de Windows|Solution antivirus/anti-programme malveillant principale|État de l’antivirus Microsoft Defender|
|:---|:---|:---|
|Windows 10 <br/> Windows 11|Antivirus Microsoft Defender|Mode actif|
|Windows 10 <br/> Windows 11|Une solution antivirus/anti-programme malveillant non Microsoft|Mode désactivé (se produit automatiquement)|
|Windows Server 2022 <br/> Windows Server 2019<br/> Windows Server, version 1803 ou ultérieure <br/> Windows Server 2016 <br/> Windows Server 2012 R2 |Antivirus Microsoft Defender|Mode actif|
|Windows Server 2022<br/>Windows Server 2019<br/>Windows Server, version 1803 ou ultérieure <br/> Windows Server 2016 |Une solution antivirus/anti-programme malveillant non Microsoft|Désactivé (défini manuellement) <sup>[[1](#fn1)]</sup>|

(<a id="fn1">1</a>) Sur Windows Server, si vous exécutez un produit antivirus non-Microsoft, vous pouvez désinstaller l’antivirus Microsoft Defender pour éviter tout conflit. Si l’appareil est intégré à Microsoft Defender pour point de terminaison, vous pouvez utiliser l’antivirus Microsoft Defender en mode passif (voir ci-dessous).

> [!TIP]
> Sur Windows Server 2016, vous pouvez voir *Antivirus Windows Defender* au lieu de *l’antivirus Microsoft Defender*.

## <a name="microsoft-defender-antivirus-and-non-microsoft-antivirusantimalware-solutions"></a>Antivirus Microsoft Defender et solutions antivirus/anti-programme malveillant non Microsoft

> [!NOTE]
> En général, l’Antivirus Microsoft Defender peut être défini en mode passif uniquement sur les points de terminaison intégrés à Defender pour point de terminaison.

Le fait que l’Antivirus Microsoft Defender s’exécute en mode actif, en mode passif ou est désactivé dépend de plusieurs facteurs, tels que :

- Version de Windows installée sur un point de terminaison
- Indique si l’antivirus Microsoft Defender est la solution antivirus/anti-programme malveillant principale sur le point de terminaison
- Indique si le point de terminaison est intégré à Defender pour point de terminaison

Le tableau suivant récapitule l’état de l’antivirus Microsoft Defender dans plusieurs scénarios. 

| Version de Windows   | Solution antivirus/anti-programme malveillant  | Intégré à <br/> Defender pour point de terminaison ? | État de l’antivirus Microsoft Defender     |
|:------|:------|:-------|:-------|
| Windows 10 <br/> Windows 11| Antivirus Microsoft Defender | Oui  | Mode actif | 
| Windows 10 <br/> Windows 11 | Antivirus Microsoft Defender | Non   | Mode actif |
| Windows 10 <br/> Windows 11  | Une solution antivirus/anti-programme malveillant non Microsoft | Oui  | Mode passif (automatiquement) |
| Windows 10 <br/> Windows 11  | Une solution antivirus/anti-programme malveillant non Microsoft | Non   | Mode désactivé (automatiquement)    |
| Windows Server 2022 <br/> Windows Server 2019 <br/>Windows Server, version 1803 ou ultérieure  | Antivirus Microsoft Defender  | Oui |         Mode actif  |
| Windows Server 2022 <br/> Windows Server 2019 <br/> Windows Server, version 1803 ou ultérieure   | Antivirus Microsoft Defender | Non  | Mode actif |
| Windows Server 2022 <br/> Windows Server 2019 <p> Windows Server, version 1803 ou ultérieure  | Une solution antivirus/anti-programme malveillant non Microsoft | Oui  | L’antivirus Microsoft Defender doit être défini en mode passif (manuellement) <sup>[[2](#fn2)]<sup>  | 
| Windows Server 2022 <br/> Windows Server 2019 <p> Windows Server, version 1803 ou ultérieure  | Une solution antivirus/anti-programme malveillant non Microsoft | Non  | L’antivirus Microsoft Defender doit être désactivé (manuellement) <sup>[[3](#fn3)]<sup></sup>  |
| Windows Server 2016 <br/> Windows Server 2012 R2   | Antivirus Microsoft Defender | Oui | Mode actif |
|Windows Server 2016 <br/> Windows Server 2012 R2  | Antivirus Microsoft Defender | Non | Mode actif |
| Windows Server 2016 <br/> Windows Server 2012 R2  | Une solution antivirus/anti-programme malveillant non Microsoft | Oui | L’antivirus Microsoft Defender doit être défini en mode passif (manuellement) <sup>[[2](#fn2)]<sup> |
|Windows Server 2016 <br/> Windows Server 2012 R2  | Une solution antivirus/anti-programme malveillant non Microsoft | Non | L’antivirus Microsoft Defender doit être désactivé (manuellement) <sup>[[3](#fn3)]<sup> |

(<a id="fn2">2</a>) Sur Windows Server 2019, Windows Server, version 1803 ou ultérieure, Windows Server 2016 ou Windows Server 2012 R2, l’antivirus Microsoft Defender n’entre pas automatiquement en mode passif lorsque vous installez un produit antivirus non Microsoft. Dans ce cas, définissez l’antivirus Microsoft Defender en mode passif pour éviter les problèmes causés par l’installation de plusieurs produits antivirus sur un serveur. Vous pouvez définir l’antivirus Microsoft Defender en mode passif à l’aide d’une clé de Registre comme suit :
- Chemin: `HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection`
- Nom : `ForceDefenderPassiveMode`
- Type: `REG_DWORD`
- Valeur : `1`

Vous pouvez afficher votre état de protection dans PowerShell à l’aide de la commande [Get-MpComputerStatus](/powershell/module/defender/get-mpcomputerstatus). Vérifiez la valeur de `AMRunningMode`. Le mode bloc **Normal**, **Passif** ou **EDR** doit s’afficher si l’antivirus Microsoft Defender est activé sur le point de terminaison. 

 > [!NOTE]
 > Pour que le mode passif fonctionne sur des points de terminaison exécutant Windows Server 2016 et Windows Server 2012 R2, ces points de terminaison doivent être intégrés à la solution unifiée moderne décrite dans [les serveurs Windows intégrés](configure-server-endpoints.md#windows-server-2012-r2-and-windows-server-2016). 

(<a id="fn3">3</a>) Sur Windows Server 2016, Windows Server 2012 R2, Windows Server version 1803 ou ultérieure, Windows Server 2019 et Windows Server 2022, si vous utilisez un produit antivirus non Microsoft sur un point de terminaison qui *n’est pas* intégré à Microsoft Defender pour point de terminaison, désactivez/désinstallez manuellement l’Antivirus Microsoft Defender pour éviter les problèmes causés par l’installation de plusieurs produits antivirus sur un serveur.

> [!TIP]
> Sur Windows Server 2016, vous pouvez voir *Antivirus Windows Defender* au lieu de *l’antivirus Microsoft Defender*.

Defender pour point de terminaison inclut des fonctionnalités qui étendent davantage la protection antivirus installée sur votre point de terminaison. Vous pouvez tirer parti de l’exécution de l’Antivirus Microsoft Defender avec une autre solution antivirus.

Par exemple, la [détection et la réponse des points de terminaison (EDR) en mode bloc](edr-in-block-mode.md) offrent une protection supplémentaire contre les artefacts malveillants, même si l’Antivirus Microsoft Defender n’est pas le produit antivirus principal. Ces fonctionnalités nécessitent l’installation et l’exécution de l’antivirus Microsoft Defender en mode passif ou actif.

## <a name="requirements-for-microsoft-defender-antivirus-to-run-in-passive-mode"></a>Configuration requise pour que l’antivirus Microsoft Defender s’exécute en mode passif

Pour que l’Antivirus Microsoft Defender s’exécute en mode passif, les points de terminaison doivent répondre aux exigences suivantes :

- Système d’exploitation : Windows 10 ou plus récent ; Windows Server 2022, Windows Server 2019 ou Windows Server, version 1803 ou ultérieure
- L’antivirus Microsoft Defender doit être installé
- Un autre produit antivirus/anti-programme malveillant non Microsoft doit être installé et utilisé comme solution antivirus principale
- Les points de terminaison doivent être intégrés à Defender pour point de terminaison

> [!IMPORTANT]
> - L’Antivirus Microsoft Defender est disponible uniquement sur les appareils exécutant Windows 10 et 11, Windows Server 2022, Windows Server 2019, Windows Server, version 1803 ou ultérieure, Windows Server 2016 et Windows Server 2012 R2.
> - Dans Windows 8.1, la protection antivirus de point de terminaison au niveau de l’entreprise est proposée en tant que [System Center Endpoint Protection](/previous-versions/system-center/system-center-2012-R2/hh508760(v=technet.10)), qui est gérée par le biais de Microsoft Endpoint Configuration Manager.
> - Windows Defender est également proposé pour [les appareils grand public sur Windows 8.1](/previous-versions/windows/it-pro/windows-8.1-and-8/dn344918(v=ws.11)#BKMK_WindowsDefender), bien que Windows Defender n’assure pas la gestion au niveau de l’entreprise.

## <a name="how-microsoft-defender-antivirus-affects-defender-for-endpoint-functionality"></a>Comment l’antivirus Microsoft Defender affecte les fonctionnalités de Defender pour point de terminaison

Defender pour point de terminaison détermine si l’Antivirus Microsoft Defender peut s’exécuter en mode passif. De plus, l’état de l’antivirus Microsoft Defender peut affecter certaines fonctionnalités de Defender pour point de terminaison. Par exemple, la protection en temps réel fonctionne lorsque l’Antivirus Microsoft Defender est en mode actif ou passif, mais pas lorsque l’antivirus Microsoft Defender est désactivé ou désinstallé.

> [!IMPORTANT]
> - Le tableau de cette section récapitule les fonctionnalités qui fonctionnent activement ou non, selon que l’Antivirus Microsoft Defender est en mode actif, en mode passif ou désactivé/désinstallé. Ce tableau est conçu pour être informatif uniquement.   
> - **Ne désactivez pas les fonctionnalités**, telles que la protection en temps réel, la protection fournie par le cloud ou l’analyse périodique limitée si vous utilisez l’Antivirus Microsoft Defender en mode passif, ou si vous utilisez [EDR en mode bloc](edr-in-block-mode.md), qui fonctionne en arrière-plan pour détecter et corriger les artefacts malveillants détectés après la violation.

| Protection | Antivirus Microsoft Defender <br/>(*Mode actif*) | Antivirus Microsoft Defender <br/>(*Mode passif*) | Antivirus Microsoft Defender <br/>(*Désactivé ou désinstallé*) | [PEPT en mode blocage](edr-in-block-mode.md) | 
|:---|:---|:---|:---|:---| 
| [Protection en temps réel](configure-real-time-protection-microsoft-defender-antivirus.md) | Oui | Voir la note <sup>[[4](#fn4)]</sup> | Non | Non | 
| [Protection fournie par le cloud](enable-cloud-protection-microsoft-defender-antivirus.md) | Oui | Non  | Non | Non | 
| [Protection du réseau](network-protection.md)  | Oui | Non | Non | Non | 
| [Règles de réduction de la surface d’attaque](attack-surface-reduction.md)  | Oui | Non | Non  | Non | 
| [Disponibilité d’analyse périodique limitée](limited-periodic-scanning-microsoft-defender-antivirus.md) | Non | Non | Oui | Non | 
| [Informations sur l’analyse et la détection des fichiers](review-scan-results-microsoft-defender-antivirus.md) | Oui | Oui <sup>[[5](#fn5)]</sup> | Non | Oui | 
| [Correction des menaces](configure-remediation-microsoft-defender-antivirus.md) | Oui | Voir la note <sup>[[6](#fn6)]</sup> | Non | Oui | 
| [Mises à jour de la veille de sécurité](manage-updates-baselines-microsoft-defender-antivirus.md) | Oui | Oui <sup>[[7](#fn7)]</sup> | Non | Oui <sup>[[7](#fn7)]</sup> | 
| [Protection contre la perte de données](../../compliance/endpoint-dlp-learn-about.md) | Oui | Oui | Non | Non |
| [Accès contrôlé aux dossiers](controlled-folders.md) | Oui |Non | Non | Non |
| [Filtrage du contenu web](web-content-filtering.md) | Oui | Voir la note <sup>[[8](#fn8)]</sup> | Non | Non |
| [Contrôle des appareils](device-control-report.md) | Oui | Oui | Non | Non |
| [Protection PUA](detect-block-potentially-unwanted-apps-microsoft-defender-antivirus.md) | Oui | Non | Non | Non |

(<a id="fn4">4</a>) En général, lorsque l’Antivirus Microsoft Defender est en mode passif, la protection en temps réel ne fournit aucun blocage ou application, même si elle est activée et en mode passif.

(<a id="fn5">5</a>) Lorsque l’Antivirus Microsoft Defender est en mode passif, les analyses ne sont pas planifiées.

(<a id="fn6">6</a>) Lorsque l’Antivirus Microsoft Defender est en mode passif, il ne corrige pas les menaces. Toutefois, les menaces peuvent être corrigées par [la détection et la réponse des points de terminaison (EDR) en mode bloc](edr-in-block-mode.md). Dans ce cas, vous pouvez voir des alertes montrant l’Antivirus Microsoft Defender comme source, même lorsque l’Antivirus Microsoft Defender est en mode passif.

(<a id="fn7">7</a>) La cadence de mise à jour du renseignement de sécurité est contrôlée uniquement par Windows Update paramètres. Les planificateurs de mises à jour spécifiques à Defender (quotidiens/hebdomadaires à un moment spécifique, basés sur des intervalles) fonctionnent uniquement lorsque l’Antivirus Microsoft Defender est en mode actif. Ils sont ignorés en mode passif.

(<a id="fn8">8</a>) Lorsque l’Antivirus Microsoft Defender est en mode passif, le filtrage de contenu web fonctionne uniquement avec le navigateur Microsoft Edge. 

> [!IMPORTANT]
> - [La protection contre la perte de données](/microsoft-365/compliance/endpoint-dlp-learn-about) de point de terminaison continue de fonctionner normalement lorsque l’antivirus Microsoft Defender est en mode actif ou passif.
>
> - Ne désactivez pas, arrêtez ou ne modifiez aucun des services associés utilisés par l’Antivirus Microsoft Defender, Defender pour point de terminaison ou l’application Sécurité Windows. Cette recommandation inclut les services et processus *wscsvc*, *SecurityHealthService*, *MsSense*, *Sense*, *WinDefend* ou *MsMpEng* . La modification manuelle de ces services peut entraîner une instabilité grave sur vos appareils et rendre votre réseau vulnérable. La désactivation, l’arrêt ou la modification de ces services peuvent également entraîner des problèmes lors de l’utilisation de solutions antivirus non Microsoft et de la façon dont leurs informations sont affichées dans [l’application Sécurité Windows](microsoft-defender-security-center-antivirus.md).
>
> - Dans Defender pour point de terminaison, vous pouvez activer EDR en mode bloc, même si l’antivirus Microsoft Defender n’est pas votre solution antivirus principale. EDR en mode bloc détecte et corrige les éléments malveillants qui se trouvent sur l’appareil (après la violation). Pour en savoir plus, consultez [EDR en mode bloc](edr-in-block-mode.md).

## <a name="how-to-confirm-the-state-of-microsoft-defender-antivirus"></a>Comment confirmer l’état de l’antivirus Microsoft Defender

Vous pouvez utiliser l’une des plusieurs méthodes pour confirmer l’état de l’antivirus Microsoft Defender. Vous pouvez :

- [Utilisez l’application Sécurité Windows pour identifier votre application antivirus](#use-the-windows-security-app-to-identify-your-antivirus-app).
- [Utilisez le Gestionnaire des tâches pour confirmer que l’antivirus Microsoft Defender est en cours d’exécution](#use-task-manager-to-confirm-that-microsoft-defender-antivirus-is-running).
- [Utilisez Windows PowerShell pour confirmer que l’antivirus Microsoft Defender est en cours d’exécution](#use-windows-powershell-to-confirm-that-microsoft-defender-antivirus-is-running).
- [Utilisez Windows PowerShell pour confirmer que la protection antivirus est en cours d’exécution](#use-windows-powershell-to-confirm-that-antivirus-protection-is-running).

### <a name="use-the-windows-security-app-to-identify-your-antivirus-app"></a>Utiliser l’application Sécurité Windows pour identifier votre application antivirus

1. Sur un appareil Windows, ouvrez l’application Sécurité Windows.

2. Sélectionnez **Protection contre les virus et les menaces**.

3. Sous **Qui me protège ?** **Sélectionnez Gérer les fournisseurs**.

4. Dans la page **Fournisseurs de sécurité** , sous **Antivirus**, vous devriez voir que **l’antivirus Microsoft Defender est activé**.

### <a name="use-task-manager-to-confirm-that-microsoft-defender-antivirus-is-running"></a>Utiliser le Gestionnaire des tâches pour confirmer que l’antivirus Microsoft Defender est en cours d’exécution

1. Sur un appareil Windows, ouvrez l’application Gestionnaire de tâches.

2. Sélectionnez l’onglet **Détails** .

3. Recherchez **MsMpEng.exe** dans la liste.

### <a name="use-windows-powershell-to-confirm-that-microsoft-defender-antivirus-is-running"></a>Utilisez Windows PowerShell pour confirmer que l’antivirus Microsoft Defender est en cours d’exécution

> [!NOTE]
> Utilisez cette procédure uniquement pour confirmer si Microsoft Defender Antirivus s’exécute sur un point de terminaison.

1. Sur un appareil Windows, ouvrez Windows PowerShell. 

2. Exécutez l’applet de commande PowerShell suivante : `Get-Process`.

3. Passez en revue les résultats. Vous devriez voir **MsMpEng.exe** si l’Antivirus Microsoft Defender est activé.

### <a name="use-windows-powershell-to-confirm-that-antivirus-protection-is-running"></a>Utiliser Windows PowerShell pour confirmer que la protection antivirus est en cours d’exécution

> [!NOTE]
> Utilisez cette procédure uniquement pour confirmer si la protection antivirus est activée sur un point de terminaison.

1. Sur un appareil Windows, ouvrez Windows PowerShell.

2. Exécutez l’applet de commande PowerShell suivante : `Get-MpComputerStatus | select AMRunningMode`.

3. Passez en revue les résultats. Vous devez voir **le** **mode de blocage** Normal, **Passif** ou EDR si la protection antivirus est activée sur le point de terminaison. 

> [!NOTE]
> Notez que cette procédure vise uniquement à confirmer si la protection antivirus est activée sur un point de terminaison.

## <a name="more-details-about-microsoft-defender-antivirus-states"></a>Plus d’informations sur les états de l’antivirus Microsoft Defender

Les sections suivantes décrivent à quoi s’attendre quand l’Antivirus Microsoft Defender est :

- [En mode actif](#active-mode)
- [En mode passif, ou lorsque l’EDR en mode bloc est activé](#passive-mode-or-edr-block-mode)
- [Désactivé ou désinstallé](#disabled-or-uninstalled)

### <a name="active-mode"></a>Mode actif

En mode actif, l’Antivirus Microsoft Defender est utilisé comme application antivirus sur l’ordinateur. Les paramètres configurés à l’aide de Configuration Manager, stratégie de groupe, Microsoft Intune ou d’autres produits de gestion s’appliquent. Les fichiers sont analysés, les menaces sont corrigées et les informations de détection sont signalées dans votre outil de configuration (par exemple, dans le Centre d’administration Microsoft Endpoint Manager ou l’application Antivirus Microsoft Defender sur le point de terminaison).  

### <a name="passive-mode-or-edr-block-mode"></a>Mode passif ou mode bloc EDR

En mode passif, l’Antivirus Microsoft Defender n’est pas utilisé comme application antivirus et les menaces *ne sont pas* corrigées par l’Antivirus Microsoft Defender. Toutefois, les menaces peuvent être corrigées par [la détection et la réponse des points de terminaison (EDR) en mode bloc](edr-in-block-mode.md). Les fichiers sont analysés par EDR et des rapports sont fournis pour les détections de menaces partagées avec le service Defender pour point de terminaison. Vous pouvez voir des alertes montrant l’Antivirus Microsoft Defender comme source, même lorsque l’Antivirus Microsoft Defender est en mode passif. 

Lorsque l’Antivirus Microsoft Defender est en mode passif, vous pouvez toujours [gérer les mises à jour pour l’antivirus Microsoft Defender](manage-updates-baselines-microsoft-defender-antivirus.md) ; Toutefois, vous ne pouvez pas déplacer l’antivirus Microsoft Defender en mode actif si vos appareils disposent d’un produit antivirus non-Microsoft qui fournit une protection en temps réel contre les programmes malveillants.

**Veillez à obtenir vos mises à jour antivirus et anti-programme malveillant, même si l’antivirus Microsoft Defender s’exécute en mode passif**. Consultez [Gérer les mises à jour de l’Antivirus Microsoft Defender et appliquer les lignes de base](manage-updates-baselines-microsoft-defender-antivirus.md).<br/><br/>Notez que le mode passif est pris en charge uniquement sur Windows Server 2012 R2 & 2016 lorsque l’ordinateur est intégré à l’aide de la [solution unifiée moderne](/microsoft-365/security/defender-endpoint/configure-server-endpoints). 

### <a name="disabled-or-uninstalled"></a>Désactivé ou désinstallé

Lorsqu’il est désactivé ou désinstallé, l’Antivirus Microsoft Defender n’est pas utilisé comme application antivirus. Les fichiers ne sont pas analysés et les menaces ne sont pas corrigées. La désactivation ou la désinstallation de l’antivirus Microsoft Defender n’est pas recommandée en général ; si possible, conservez l’antivirus Microsoft Defender en mode passif si vous utilisez une solution anti-programme malveillant/antivirus non Microsoft.

Dans les cas où l’antivirus Microsoft Defender est désactivé automatiquement, il peut être réactivé automatiquement si le produit antivirus/anti-programme malveillant non Microsoft expire, est désinstallé ou cesse de fournir une protection en temps réel contre les virus, les programmes malveillants ou d’autres menaces. La réactivation automatique de l’antivirus Microsoft Defender permet de garantir que la protection antivirus est maintenue sur vos points de terminaison.

Vous pouvez également utiliser une [analyse périodique limitée](limited-periodic-scanning-microsoft-defender-antivirus.md), qui fonctionne avec le moteur antivirus Microsoft Defender pour vérifier régulièrement les menaces si vous utilisez une application antivirus non Microsoft.  | 

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
