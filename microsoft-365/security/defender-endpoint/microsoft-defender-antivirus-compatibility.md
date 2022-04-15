---
title: Antivirus Microsoft Defender compatibilité avec d’autres produits de sécurité
description: Découvrez Antivirus Microsoft Defender avec d’autres produits de sécurité et les systèmes d’exploitation.
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
ms.date: 04/14/2022
ms.collection:
- M365-security-compliance
- m365initiative-defender-endpoint
ms.openlocfilehash: 4f579d3d22b553b764149c8b13538ceae1da44d8
ms.sourcegitcommit: e3bc6563037bd2cce2abf108b3d1bcc2ccf538f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/15/2022
ms.locfileid: "64862881"
---
# <a name="microsoft-defender-antivirus-compatibility-with-other-security-products"></a>Antivirus Microsoft Defender compatibilité avec d’autres produits de sécurité

**S’applique à :**

- Antivirus Microsoft Defender
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

**Plateformes**
- Windows

[!include[Prerelease information](../../includes/prerelease.md)]

Antivirus Microsoft Defender est installé automatiquement sur les points de terminaison exécutant les versions suivantes de Windows :

- Windows 10 ou plus récent
- Windows Server 2022
- Windows Server 2019
- Windows Server, version 1803 ou ultérieure
- Windows Server 2016

Que se passe-t-il quand une autre solution antivirus/anti-programme malveillant non Microsoft est utilisée ? Pouvez-vous exécuter Antivirus Microsoft Defender avec un autre produit antivirus ? Les réponses dépendent de plusieurs facteurs, tels que votre système d’exploitation et si vous utilisez [Microsoft Defender pour point de terminaison](microsoft-defender-endpoint.md) avec votre protection antivirus.

Cet article décrit ce qui se passe avec Antivirus Microsoft Defender et une solution antivirus/anti-programme malveillant non Microsoft, avec et sans Defender pour point de terminaison.

> [!IMPORTANT]
> - Antivirus Microsoft Defender est disponible sur les appareils exécutant Windows 10 et 11, Windows Server 2022, Windows Server 2019, Windows Server, version 1803 ou ultérieure et Windows Server 2016. 
> - Antivirus Microsoft Defender est également disponible sur Windows Server 2012 R2 lors de l’intégration à l’aide de la [solution unifiée moderne](/microsoft-365/security/defender-endpoint/configure-server-endpoints).
> - Sur Windows 8.1, la protection antivirus de point de terminaison au niveau de l’entreprise est proposée en tant que [System Center Endpoint Protection](/previous-versions/system-center/system-center-2012-R2/hh508760(v=technet.10), qui est gérée via Microsoft Endpoint Configuration Manager.
> - Windows Defender est également proposé pour [les appareils grand public sur Windows 8.1](/previous-versions/windows/it-pro/windows-8.1-and-8/dn344918(v=ws.11)#BKMK_WindowsDefender), bien que Windows Defender n’assure pas la gestion au niveau de l’entreprise.

## <a name="antivirus-protection-without-defender-for-endpoint"></a>Protection antivirus sans Defender pour point de terminaison

Cette section décrit ce qui se passe lorsque vous utilisez Antivirus Microsoft Defender avec des produits antivirus/anti-programme malveillant non Microsoft sur des points de terminaison qui ne sont pas intégrés à Defender pour point de terminaison. 

> [!NOTE]
> En général, Antivirus Microsoft Defender ne s’exécute pas en mode passif sur les appareils qui ne sont pas intégrés à Defender pour point de terminaison.

Le tableau suivant récapitule les attentes :

|Version de Windows|Solution antivirus/anti-programme malveillant principale|état Antivirus Microsoft Defender|
|:---|:---|:---|
|Windows 10 <br/> Windows 11|Antivirus Microsoft Defender|Mode actif|
|Windows 10 <br/> Windows 11|Une solution antivirus/anti-programme malveillant non Microsoft|Mode désactivé (se produit automatiquement)|
|Windows Server 2022 <br/> Windows Server 2019<br/> Windows Server, version 1803 ou ultérieure <br/> Windows Server 2016 |Antivirus Microsoft Defender|Mode actif|
|Windows Server 2022<br/>Windows Server 2019<br/>Windows Server, version 1803 ou ultérieure <br/> Windows Server 2016  |Une solution antivirus/anti-programme malveillant non Microsoft|Désactivé (défini manuellement) <sup>[[1](#fn1)]</sup>|

(<a id="fn1">1</a>) Sur Windows Server, si vous exécutez un produit antivirus non Microsoft, vous pouvez désinstaller Antivirus Microsoft Defender pour éviter tout conflit. Si l’appareil est intégré à Microsoft Defender pour point de terminaison, vous pouvez utiliser Antivirus Microsoft Defender en mode passif (voir ci-dessous).

> [!TIP]
> Sur Windows Server 2016, vous pouvez voir *Antivirus Windows Defender* au lieu de *Antivirus Microsoft Defender*.

## <a name="microsoft-defender-antivirus-and-non-microsoft-antivirusantimalware-solutions"></a>Antivirus Microsoft Defender et solutions antivirus/anti-programme malveillant non Microsoft

> [!NOTE]
> En général, Antivirus Microsoft Defender ne peut être défini en mode passif que sur les points de terminaison intégrés à Defender pour point de terminaison.

Le fait que Antivirus Microsoft Defender s’exécute en mode actif, en mode passif ou est désactivé dépend de plusieurs facteurs, tels que :

- Quelle version de Windows est installée sur un point de terminaison ?
- Indique si Antivirus Microsoft Defender est la solution antivirus/anti-programme malveillant principale sur le point de terminaison
- Indique si le point de terminaison est intégré à Defender pour point de terminaison

Le tableau suivant récapitule l’état de Antivirus Microsoft Defender dans plusieurs scénarios. 

| Version de Windows   | Solution antivirus/anti-programme malveillant  | Intégré à <br/> Defender pour point de terminaison ? | état Antivirus Microsoft Defender     |
|:------|:------|:-------|:-------|
| Windows 10 <br/> Windows 11| Antivirus Microsoft Defender | Oui  | Mode actif | 
| Windows 10 <br/> Windows 11 | Antivirus Microsoft Defender | Non   | Mode actif |
| Windows 10 <br/> Windows 11  | Une solution antivirus/anti-programme malveillant non Microsoft | Oui  | Mode passif (automatiquement) |
| Windows 10 <br/> Windows 11  | Une solution antivirus/anti-programme malveillant non Microsoft | Non   | Mode désactivé (automatiquement)    |
| Windows Server 2022 <br/> Windows Server 2019 <br/>Windows Server, version 1803 ou ultérieure  | Antivirus Microsoft Defender  | Oui |         Mode actif  |
| Windows Server 2022 <br/> Windows Server 2019 <br/> Windows Server, version 1803 ou ultérieure   | Antivirus Microsoft Defender | Non  | Mode actif |
| Windows Server 2022 <br/> Windows Server 2019 <p> Windows Server, version 1803 ou ultérieure  | Une solution antivirus/anti-programme malveillant non Microsoft | Oui  | Antivirus Microsoft Defender doit être défini en mode passif (manuellement) <sup>[[2](#fn2)]<sup>  | 
| Windows Server 2022 <br/> Windows Server 2019 <p> Windows Server, version 1803 ou ultérieure  | Une solution antivirus/anti-programme malveillant non Microsoft | Non  | Antivirus Microsoft Defender doit être désactivé (manuellement) <sup>[[3](#fn3)]<sup></sup>  |
| Windows Server 2016 <br/> Windows Server 2012 R2   | Antivirus Microsoft Defender | Oui | Mode actif |
|Windows Server 2016 <br/> Windows Server 2012 R2  | Antivirus Microsoft Defender | Non | Mode actif |
| Windows Server 2016 <br/> Windows Server 2012 R2  | Une solution antivirus/anti-programme malveillant non Microsoft | Oui | Antivirus Microsoft Defender doit être défini en mode passif (manuellement) <sup>[[2](#fn2)]<sup> |
|Windows Server 2016 <br/> Windows Server 2012 R2  | Une solution antivirus/anti-programme malveillant non Microsoft | Non | Antivirus Microsoft Defender doit être désactivé (manuellement) <sup>[[3](#fn3)]<sup> |

(<a id="fn2">2</a>) Sur Windows Server 2019, Windows Server, version 1803 ou ultérieure, Windows Server 2016 ou Windows Server 2012 R2, Antivirus Microsoft Defender n’entre pas automatiquement en mode passif lorsque vous installez un non-Microsoft antivirus. Dans ce cas, définissez Antivirus Microsoft Defender en mode passif pour éviter les problèmes causés par l’installation de plusieurs produits antivirus sur un serveur. Vous pouvez définir Antivirus Microsoft Defender en mode passif à l’aide de PowerShell, d’stratégie de groupe ou d’une clé de Registre. 

  Vous pouvez définir Antivirus Microsoft Defender en mode passif en définissant la clé de Registre suivante :
- Chemin: `HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection`
- Nom : `ForceDefenderPassiveMode`
- Type: `REG_DWORD`
- Valeur : `1`

 > [!NOTE]
 > Pour que le mode passif fonctionne sur des points de terminaison exécutant Windows Server 2016 et Windows Server 2012 R2, ces points de terminaison doivent être intégrés à la solution unifiée moderne décrite dans [Intégrer Windows serveurs](configure-server-endpoints.md#windows-server-2012-r2-and-windows-server-2016). 

(<a id="fn3">3</a>) Sur Windows Server 2016, Windows Server 2012 R2, Windows Server version 1803 ou ultérieure, Windows Server 2019 et Windows Server 2022, si vous utilisez un produit antivirus non Microsoft sur un point de terminaison qui *n’est pas* intégré à Microsoft Defender pour point de terminaison, désactivez/désinstallez manuellement Antivirus Microsoft Defender pour éviter les problèmes liés à l’installation de plusieurs produits antivirus sur un serveur.

> [!TIP]
> Sur Windows Server 2016, vous pouvez voir *Antivirus Windows Defender* au lieu de *Antivirus Microsoft Defender*.

> [!IMPORTANT]
> Antivirus Microsoft Defender est disponible uniquement sur les appareils exécutant Windows 10 et 11, Windows Server 2022, Windows Server 2019, Windows Server, version 1803 ou ultérieure, Windows Server 2016 et Windows Server 2012 R2.
>
> Dans Windows 8.1, la protection antivirus de point de terminaison au niveau de l’entreprise est proposée en tant que [System Center Endpoint Protection](/previous-versions/system-center/system-center-2012-R2/hh508760(v=technet.10)), qui est gérée via Microsoft Endpoint Configuration Manager.
>
> Windows Defender est également proposé pour [les appareils grand public sur Windows 8.1](/previous-versions/windows/it-pro/windows-8.1-and-8/dn344918(v=ws.11)#BKMK_WindowsDefender), bien que Windows Defender n’assure pas la gestion au niveau de l’entreprise.

Defender pour point de terminaison inclut des fonctionnalités qui étendent davantage la protection antivirus installée sur votre point de terminaison. Vous pouvez tirer parti de l’exécution de Antivirus Microsoft Defender avec une autre solution antivirus.

Par exemple, la [détection et la réponse des points de terminaison (PEPT) en mode bloc](edr-in-block-mode.md) offrent une protection supplémentaire contre les artefacts malveillants, même si Antivirus Microsoft Defender n’est pas le produit antivirus principal. De telles fonctionnalités nécessitent l’installation et l’exécution de Antivirus Microsoft Defender en mode passif ou actif.

### <a name="requirements-for-microsoft-defender-antivirus-to-run-in-passive-mode"></a>Configuration requise pour que Antivirus Microsoft Defender s’exécute en mode passif

Pour que Antivirus Microsoft Defender s’exécutent en mode passif, les points de terminaison doivent répondre aux exigences suivantes :

- Système d’exploitation : Windows 10 ou plus récent ; Windows Server 2022, Windows Server 2019 ou Windows Server, version 1803 ou ultérieure
- Antivirus Microsoft Defender doit être installé
- Un autre produit antivirus/anti-programme malveillant non Microsoft doit être installé et utilisé comme solution antivirus principale
- Les points de terminaison doivent être intégrés à Defender pour point de terminaison

## <a name="how-microsoft-defender-antivirus-affects-defender-for-endpoint-functionality"></a>Comment Antivirus Microsoft Defender affecte les fonctionnalités de Defender pour point de terminaison

Defender pour point de terminaison détermine si Antivirus Microsoft Defender peuvent s’exécuter en mode passif. Antivirus Microsoft Defender peuvent également affecter certaines fonctionnalités de Defender pour point de terminaison. Par exemple, la protection en temps réel fonctionne quand Antivirus Microsoft Defender est en mode actif ou passif, mais pas quand Antivirus Microsoft Defender est désactivé ou désinstallé.

Le tableau de cette section récapitule les fonctionnalités qui fonctionnent activement ou non, selon que Antivirus Microsoft Defender est en mode actif, en mode passif ou désactivé/désinstallé.

> [!IMPORTANT]
> Le tableau suivant est conçu pour être informatif uniquement. **Ne désactivez pas les fonctionnalités**, telles que la protection en temps réel, la protection fournie par le cloud ou l’analyse périodique limitée si vous utilisez Antivirus Microsoft Defender en mode passif, ou si vous utilisez [PEPT en mode bloc](edr-in-block-mode.md), qui fonctionne en arrière-plan pour détecter et corriger les artefacts malveillants détectés après la violation.

| Protection | Antivirus Microsoft Defender <br/>(*Mode actif*) | Antivirus Microsoft Defender <br/>(*Mode passif*) | Antivirus Microsoft Defender <br/>(*Désactivé ou désinstallé*) | [PEPT en mode blocage](edr-in-block-mode.md) | 
|:---|:---|:---|:---|:---| 
| [Protection en temps réel](configure-real-time-protection-microsoft-defender-antivirus.md) | Oui | Voir la note <sup>[[4](#fn4)]</sup> | Non | Non | 
| [Protection fournie par le cloud](enable-cloud-protection-microsoft-defender-antivirus.md) | Oui | Non  | Non | Non | 
| [Protection du réseau](network-protection.md)  | Oui | Non | Non | Non | 
| [Règles de réduction de la surface d’attaque](attack-surface-reduction.md)  | Oui | Non | Non  | Non | 
| [Disponibilité d’analyse périodique limitée](limited-periodic-scanning-microsoft-defender-antivirus.md) | Non | Non | Oui | Non | 
| [Informations sur l’analyse et la détection des fichiers](review-scan-results-microsoft-defender-antivirus.md) | Oui | Oui<sup>[[5](#fn5)]</sup> | Non | Oui | 
| [Correction des menaces](configure-remediation-microsoft-defender-antivirus.md) | Oui | Voir la note <sup>[[6](#fn6)]</sup> | Non | Oui | 
| [Mises à jour de la veille de sécurité](manage-updates-baselines-microsoft-defender-antivirus.md) | Oui | Oui <sup>[[7](#fn7)]</sup> | Non | Oui <sup>[[7](#fn7)]</sup> | 
| [Protection contre la perte de données](../../compliance/endpoint-dlp-learn-about.md) | Oui | Oui | Non | Non |
| [Accès contrôlé aux dossiers](controlled-folders.md) | Oui |Non | Non | Non |
| [Filtrage du contenu web](web-content-filtering.md) | Oui | Voir la note <sup>[[8](#fn8)]</sup> | Non | Non |
| [Contrôle des appareils](device-control-report.md) | Oui | Oui | Non | Non |
| [Protection PUA](detect-block-potentially-unwanted-apps-microsoft-defender-antivirus.md) | Oui | Non | Non | Non |

(<a id="fn4">4</a>) En général, lorsque Antivirus Microsoft Defender est en mode passif, la protection en temps réel n’offre aucun blocage ou application, même si elle est activée et en mode passif.

(<a id="fn5">5</a>) Lorsque Antivirus Microsoft Defender est en mode passif, les analyses ne sont pas planifiées.

(<a id="fn6">6</a>) Lorsque Antivirus Microsoft Defender est en mode passif, il ne corrige pas les menaces. Toutefois, les menaces peuvent être corrigées par [la détection et la réponse des points de terminaison (PEPT) en mode bloc](edr-in-block-mode.md). Dans ce cas, des alertes peuvent s’afficher Antivirus Microsoft Defender en tant que source, même lorsque Antivirus Microsoft Defender est en mode passif.

(<a id="fn7">7</a>) La cadence de mise à jour du renseignement de sécurité est contrôlée uniquement par Windows Update paramètres. Les planificateurs de mises à jour spécifiques à Defender (quotidiens/hebdomadaires à une heure spécifique, basés sur des intervalles) fonctionnent uniquement lorsque Antivirus Microsoft Defender est en mode actif. Ils sont ignorés en mode passif.

(<a id="fn8">8</a>) Lorsque Antivirus Microsoft Defender est en mode passif, le filtrage de contenu web fonctionne uniquement avec le navigateur Microsoft Edge. 

> [!NOTE]
> [Microsoft 365 protection contre la perte de données](/microsoft-365/compliance/endpoint-dlp-learn-about) de point de terminaison continue de fonctionner normalement lorsque Antivirus Microsoft Defender est en mode actif ou passif.

## <a name="important-notes"></a>Remarques importantes

- Ne désactivez pas, arrêtez ou ne modifiez aucun des services associés utilisés par Antivirus Microsoft Defender, Defender pour point de terminaison ou l’application Sécurité Windows. Cette recommandation inclut les services et processus *wscsvc*, *SecurityHealthService*, *MsSense*, *Sense*, *WinDefend* ou *MsMpEng* . La modification manuelle de ces services peut entraîner une instabilité grave sur vos appareils et rendre votre réseau vulnérable. La désactivation, l’arrêt ou la modification de ces services peuvent également entraîner des problèmes lors de l’utilisation de solutions antivirus non Microsoft et de la façon dont leurs informations sont affichées dans [l’application Sécurité Windows](microsoft-defender-security-center-antivirus.md).

- Dans Defender pour point de terminaison, activez PEPT en mode bloc, même si Antivirus Microsoft Defender n’est pas votre solution antivirus principale. PEPT en mode bloc détecte et corrige les éléments malveillants détectés sur l’appareil (après la violation). Pour en savoir plus, consultez [PEPT en mode bloc](edr-in-block-mode.md).

## <a name="how-to-confirm-the-state-of-microsoft-defender-antivirus"></a>Comment confirmer l’état de Antivirus Microsoft Defender

Vous pouvez utiliser l’une des méthodes suivantes pour confirmer l’état de Antivirus Microsoft Defender, comme décrit dans le tableau suivant :

 | Méthode | Procedure | 
 |:---|:---| 
 | application Sécurité Windows |  1. Sur un appareil Windows, ouvrez l’application Sécurité Windows.<br/>2. Sélectionnez **Virus & protection contre les menaces**.<br/>3. Sous **Qui me protège ?** sélectionnez **Gérer les fournisseurs**.<br/>4. Dans la page **Fournisseurs de sécurité**, sous **Antivirus**, vous devez voir **Antivirus Microsoft Defender est activé**. | 
 | Gestionnaire des tâches |  1. Sur un appareil Windows, ouvrez l’application Gestionnaire de tâches.<br/>2. Sélectionnez l’onglet **Détails** .<br/>3. Recherchez **MsMpEng.exe** dans la liste. | 
 | Windows PowerShell <br/> (Pour confirmer que Antivirus Microsoft Defender est en cours d’exécution) |  1. Sur un appareil Windows, ouvrez Windows PowerShell. <br/>2. Exécutez l’applet de commande PowerShell suivante : `Get-Process`.<br/>3. Passez en revue les résultats. Vous devez voir **MsMpEng.exe** si Antivirus Microsoft Defender est activé. | 
 | Windows PowerShell <br/>(Pour confirmer que la protection antivirus est en place) |  Vous pouvez utiliser [l’applet de commande PowerShell Get-MpComputerStatus](/powershell/module/defender/get-mpcomputerstatus).<br/>1. Sur un appareil Windows, ouvrez Windows PowerShell.<br/>2. Exécutez l’applet de commande PowerShell suivante :<br/> \|Get-MpComputerStatus sélectionner AMRunningMode <br/>3. Passez en revue les résultats. Vous devez voir **normal** ou **passif** si Antivirus Microsoft Defender est activé sur le point de terminaison.  | 
 | Invite de commandes |  1. Sur un appareil Windows, ouvrez l’invite de commandes.<br/>2. Tapez `sc query windefend`, puis appuyez sur Entrée.<br/>3. Passez en revue les résultats pour vérifier que Antivirus Microsoft Defender s’exécute en mode passif.  | 

## <a name="more-details-about-microsoft-defender-antivirus-states"></a>Plus d’informations sur les états Antivirus Microsoft Defender

Le tableau de cette section décrit les différents états que vous pouvez voir avec Antivirus Microsoft Defender.

 |  État  |  Action exécutée  | 
 |:---|:---| 
 |  Mode actif  |  En mode actif, Antivirus Microsoft Defender est utilisé comme application antivirus sur l’ordinateur. Paramètres configurés à l’aide de Configuration Manager, de stratégie de groupe, de Microsoft Intune ou d’autres produits de gestion s’appliquent. Les fichiers sont analysés, les menaces sont corrigées et les informations de détection sont signalées dans votre outil de configuration (par exemple, Configuration Manager ou l’application Antivirus Microsoft Defender sur le point de terminaison lui-même).  | 
 |  Mode passif  |  En mode passif, Antivirus Microsoft Defender n’est pas utilisé comme application antivirus et les menaces ne sont *pas* corrigées par Antivirus Microsoft Defender. Toutefois, les menaces peuvent être corrigées par [la détection et la réponse des points de terminaison (PEPT) en mode bloc](edr-in-block-mode.md). <br/><br/> Les fichiers sont analysés par PEPT et des rapports sont fournis pour les détections de menaces partagées avec le service Defender pour point de terminaison. Vous pouvez voir des alertes montrant Antivirus Microsoft Defender en tant que source, même lorsque Antivirus Microsoft Defender est en mode passif. <br/><br/> Quand Antivirus Microsoft Defender est en mode passif, vous pouvez toujours [gérer les mises à jour pour Antivirus Microsoft Defender](manage-updates-baselines-microsoft-defender-antivirus.md) ; toutefois, vous ne pouvez pas déplacer Antivirus Microsoft Defender  en mode actif si vos appareils disposent d’un produit antivirus non Microsoft qui fournit une protection en temps réel contre les programmes malveillants. <br/><br/> Pour optimiser l’efficacité de la protection et de la détection en couches de sécurité, veillez à obtenir vos mises à jour antivirus et anti-programme malveillant, même si Antivirus Microsoft Defender s’exécute en mode passif. Consultez [Gérer les mises à jour Antivirus Microsoft Defender et appliquer des lignes de base](manage-updates-baselines-microsoft-defender-antivirus.md). <br/><br/> Notez que le mode passif est pris en charge uniquement sur Windows Server 2012 R2 & 2016 lorsque l’ordinateur est intégré à l’aide de la [solution unifiée moderne](/microsoft-365/security/defender-endpoint/configure-server-endpoints).  | 
 |  Désactivé <br/><br/> ou <br/><br/> Désinstallé  |  Lorsqu’elle est désactivée ou désinstallée, Antivirus Microsoft Defender n’est pas utilisée comme application antivirus. Les fichiers ne sont pas analysés et les menaces ne sont pas corrigées. <br/><br/> La désactivation ou la désinstallation de Antivirus Microsoft Defender n’est pas recommandée en général ; si possible, conservez Antivirus Microsoft Defender en mode passif si vous utilisez une solution antivirus/logiciel anti-programme malveillant non Microsoft. <br/><br/> Dans les cas où Antivirus Microsoft Defender est désactivé automatiquement, il peut être réactivé automatiquement si le produit antivirus/anti-programme malveillant non Microsoft expire ou cesse de fournir une protection en temps réel contre les virus, les programmes malveillants ou d’autres menaces. La réactivation automatique de Antivirus Microsoft Defender permet de garantir que la protection antivirus est maintenue sur vos points de terminaison. <br/><br/> Vous pouvez également utiliser une [analyse périodique limitée](limited-periodic-scanning-microsoft-defender-antivirus.md), qui fonctionne avec le moteur Antivirus Microsoft Defender pour vérifier régulièrement les menaces si vous utilisez une application antivirus non Microsoft.  | 

> [!TIP]
> Si vous recherchez des informations relatives à l’antivirus pour d’autres plateformes, consultez :
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur macOS](mac-preferences.md)
> - [Microsoft Defender pour point de terminaison sur Mac](microsoft-defender-endpoint-mac.md)
> - [Paramètres de stratégie antivirus macOS pour Antivirus Microsoft Defender pour Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur Linux](linux-preferences.md)
> - [Microsoft Defender pour point de terminaison Linux](microsoft-defender-endpoint-linux.md)
> - [Configurer Defender pour point de terminaison pour des fonctionnalités Android](android-configure.md)
> - [configurer Microsoft Defender pour point de terminaison sur les fonctionnalités iOS](ios-configure-features.md)

## <a name="see-also"></a>Voir aussi

- [Antivirus Microsoft Defender sur les clients Windows](microsoft-defender-antivirus-in-windows-10.md)
- [Antivirus Microsoft Defender sur Windows Server](microsoft-defender-antivirus-on-windows-server.md)
- [PEPT en mode blocage](edr-in-block-mode.md)
- [Découvrir la protection contre la perte de données des point de terminaison de Microsoft 365](/microsoft-365/compliance/endpoint-dlp-learn-about)
