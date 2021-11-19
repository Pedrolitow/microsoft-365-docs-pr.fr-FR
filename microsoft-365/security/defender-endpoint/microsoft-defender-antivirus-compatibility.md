---
title: Antivirus Microsoft Defender compatibilité avec d’autres produits de sécurité
description: Découvrez les Antivirus Microsoft Defender avec d’autres produits de sécurité et les systèmes d’exploitation.
keywords: windows defender, defender pour le point de terminaison, nouvelle génération, antivirus, compatibilité, mode passif
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
ms.date: 10/26/2021
ms.collection: M365-security-compliance
ms.openlocfilehash: 6a2faec5ec3dca1fcd346aecc73edbbcd2cfa583
ms.sourcegitcommit: 1ef176c79a0e6dbb51834fe30807409d4e94847c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2021
ms.locfileid: "61110090"
---
# <a name="microsoft-defender-antivirus-compatibility-with-other-security-products"></a>Antivirus Microsoft Defender compatibilité avec d’autres produits de sécurité

**S’applique à :**

- Antivirus Microsoft Defender
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)

[!include[Prerelease information](../../includes/prerelease.md)]

Antivirus Microsoft Defender est automatiquement installé sur les points de terminaison exécutant les versions suivantes de Windows :

- Windows 10 ou plus nouveau
- Windows Server 2022
- Windows Server 2019
- Windows Server, version 1803 ou plus récente
- Windows Server 2016

Que se passe-t-il lorsqu’une autre solution antivirus/anti-programme malveillant non-Microsoft est utilisée ? Pouvez-vous exécuter Antivirus Microsoft Defender avec un autre produit antivirus ? Les réponses dépendent de plusieurs facteurs, tels que votre système d’exploitation et si vous utilisez [Microsoft Defender](microsoft-defender-endpoint.md) pour point de terminaison (Defender pour point de terminaison) avec votre protection antivirus.

Cet article décrit ce qui se passe avec Antivirus Microsoft Defender et une solution antivirus/anti-programme malveillant non Microsoft, avec ou sans Defender for Endpoint.

> [!IMPORTANT]
> Antivirus Microsoft Defender est disponible uniquement sur les appareils exécutant Windows 10 et 11, Windows Server 2022, Windows Server 2019, Windows Server, version 1803 ou plus récente, Windows Server 2016 et Windows Server 2012 R2.
>
> Dans Windows 8.1, la protection antivirus de point de terminaison au niveau de l’entreprise est proposée sous [la](/previous-versions/system-center/system-center-2012-R2/hh508760(v=technet.10))System Center Endpoint Protection , qui est gérée via Microsoft Endpoint Configuration Manager.
>
> Windows Defender est également proposé pour les appareils grand public sur [Windows 8.1,](/previous-versions/windows/it-pro/windows-8.1-and-8/dn344918(v=ws.11)#BKMK_WindowsDefender)bien que Windows Defender ne fournisse pas de gestion au niveau de l’entreprise.

## <a name="antivirus-protection-without-defender-for-endpoint"></a>Protection antivirus sans Defender for Endpoint

Cette section décrit ce qui se passe avec Antivirus Microsoft Defender et les produits antivirus/anti-programme malveillant non Microsoft sur les points de terminaison qui ne sont pas intégrés à Defender for Endpoint. Le tableau suivant récapitule ce à quoi vous pouvez vous attendre :

<br/><br/>

|Version de Windows|Solution antivirus/anti-programme malveillant principale|Antivirus Microsoft Defender’état|
|---|---|---|
|Windows 10 <p> Windows 11|Antivirus Microsoft Defender|Mode actif|
|Windows 10 <p> Windows 11|Une solution antivirus/anti-programme malveillant non-Microsoft|Mode désactivé (se produit automatiquement)|
|Windows Server 2022 <p> Windows Server 2019<p> Windows Server, version 1803 ou plus récente <p> Windows Server 2016 |Antivirus Microsoft Defender|Mode actif|
|Windows Server 2022<p>Windows Server 2019<p>Windows Server, version 1803 ou plus récente <p> Windows Server 2016 <p>  |Une solution antivirus/anti-programme malveillant non-Microsoft|Désactivé (définie manuellement) <sup>[[1](#fn1)]</sup>|

(<a id="fn1">1</a>) Sur Windows Server, si vous exécutez un produit antivirus non Microsoft, vous pouvez désactiver Antivirus Microsoft Defender à l’aide de la stratégie de groupe pour désactiver Antivirus Microsoft Defender ou à l’aide de la clé de Registre [DisableAntiSpyware.](/windows-hardware/customize/desktop/unattend/security-malware-windows-defender-disableantispyware) Pour utiliser la clé de Registre, accédez `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender` à , et définissez ou créez une entrée DWORD appelée `DisableAntiSpyware` . Définissez sa valeur sur (qui définit la valeur de la clé de Registre sur true), puis sélectionnez `1` **Hexadécimal** pour sa base. 

> [!TIP]
> Voir [Antivirus Microsoft Defender sur Windows Server pour](microsoft-defender-antivirus-on-windows-server.md) les principales différences et les options de gestion pour les installations Windows Server. Sur Windows Server 2016, vous pouvez voir *Antivirus Windows Defender* au lieu de *Antivirus Microsoft Defender*.

## <a name="microsoft-defender-antivirus-and-non-microsoft-antivirusantimalware-solutions"></a>Antivirus Microsoft Defender solutions antivirus/anti-programme malveillant non Microsoft

Le tableau suivant récapitule ce qui se passe avec Antivirus Microsoft Defender lorsque des solutions antivirus/anti-programme malveillant non Microsoft sont utilisées ensemble ou sans Microsoft Defender for Endpoint. 

| Version de Windows   | Solution antivirus/anti-programme malveillant  | Intégré à <br/> Defender pour le point de terminaison ? | Antivirus Microsoft Defender’état     |
|------|------|-------|-------|
| Windows 10 <p> Windows 11| Antivirus Microsoft Defender | Oui  | Mode actif | 
| Windows 10 <p> Windows 11 | Antivirus Microsoft Defender | Non   | Mode actif |
| Windows 10 <p> Windows 11  | Une solution antivirus/anti-programme malveillant non-Microsoft | Oui  | Mode passif (automatiquement) |
| Windows 10 <p> Windows 11  | Une solution antivirus/anti-programme malveillant non-Microsoft | Non   | Mode désactivé (automatiquement)    |
| Windows Server 2019 <p>Windows Server, version 1803 ou plus récente  | Antivirus Microsoft Defender  | Oui |         Mode actif  |
| Windows Server 2019 <p> Windows Server, version 1803 ou plus récente   | Antivirus Microsoft Defender | Non  | Mode actif |
| Windows Server 2019 <p> Windows Server, version 1803 ou plus récente  | Une solution antivirus/anti-programme malveillant non-Microsoft | Oui  | Antivirus Microsoft Defender doit être définie en mode passif (manuellement) <sup> [[2](#fn2)]<sup>  | 
| Windows Server 2019 <p> Windows Server, version 1803 ou plus récente  | Une solution antivirus/anti-programme malveillant non-Microsoft | Non  | Antivirus Microsoft Defender être désactivé (manuellement) <sup> [[3](#fn3)]<sup></sup>  |
| Windows Server 2016 <br><br> Windows Server 2012 R2   | Antivirus Microsoft Defender | Oui | Mode actif |
|Windows Server 2016 <br><br> Windows Server 2012 R2  | Antivirus Microsoft Defender | Non | Mode actif |
| Windows Server 2016 <br><br> Windows Server 2012 R2  | Une solution antivirus/anti-programme malveillant non-Microsoft | Oui | Antivirus Microsoft Defender doit être définie en mode passif (manuellement) <sup> [[2](#fn2)]<sup> |
|Windows Server 2016 <br><br> Windows Server 2012 R2  | Une solution antivirus/anti-programme malveillant non-Microsoft | Non | Antivirus Microsoft Defender être désactivé (manuellement) <sup> [[3](#fn3)]<sup> |

(<a id="fn2">2</a>) Sur Windows Server 2019, Windows Server, version 1803 ou plus récente, Windows Server 2016 ou Windows Server 2012 R2, Antivirus Microsoft Defender n’entre pas en mode passif automatiquement lorsque vous installez un non-Microsoft produit antivirus. Dans ce cas, [définissez Antivirus Microsoft Defender](microsoft-defender-antivirus-on-windows-server.md) en mode passif pour éviter les problèmes causés par l’installation de plusieurs produits antivirus sur un serveur. Vous pouvez définir Antivirus Microsoft Defender mode passif à l’aide de PowerShell, d’une stratégie de groupe ou d’une clé de Registre. 

  Vous pouvez définir Antivirus Microsoft Defender en mode passif en réglant la clé de Registre suivante :
- Chemin d’accès : `HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection`
- Nom : `ForceDefenderPassiveMode`
- Type : `REG_DWORD`
- Valeur : `1`

 > [!NOTE]
 > Pour que le mode passif fonctionne sur les points de terminaison exécutant Windows Server 2016 et Windows Server 2012 R2, ces points de terminaison doivent être intégrés à l’aide des instructions des serveurs Windows [intégrés.](configure-server-endpoints.md#windows-server-2012-r2-and-windows-server-2016) 

(<a id="fn3">3</a>) Sur Windows Server 2016 ou Windows Server 2012 R2, si vous utilisez un produit antivirus non Microsoft et que ce point de terminaison n’est pas intégré à Microsoft Defender pour le point de terminaison, [désactivez/désinstallez](microsoft-defender-antivirus-on-windows-server.md#are-you-using-windows-server-2012-r2-or-windows-server-2016) Antivirus Microsoft Defender manuellement  pour éviter les problèmes causés par l’installation de plusieurs produits antivirus sur un serveur.

> [!TIP]
> Voir [Antivirus Microsoft Defender sur Windows Server pour](microsoft-defender-antivirus-on-windows-server.md) les principales différences et les options de gestion pour les installations Windows Server. Sur Windows Server 2016, vous pouvez voir *Antivirus Windows Defender* au lieu de *Antivirus Microsoft Defender*.

> [!IMPORTANT]
> Antivirus Microsoft Defender est disponible uniquement sur les appareils exécutant Windows 10 et 11, Windows Server 2022, Windows Server 2019, Windows Server, version 1803 ou plus récente, Windows Server 2016 et Windows Server 2012 R2.
>
> Dans Windows 8.1, la protection antivirus de point de terminaison au niveau de l’entreprise est proposée sous [la](/previous-versions/system-center/system-center-2012-R2/hh508760(v=technet.10))System Center Endpoint Protection , qui est gérée via Microsoft Endpoint Configuration Manager.
>
> Windows Defender est également proposé pour les appareils grand public sur [Windows 8.1,](/previous-versions/windows/it-pro/windows-8.1-and-8/dn344918(v=ws.11)#BKMK_WindowsDefender)bien que Windows Defender ne fournisse pas de gestion au niveau de l’entreprise.

Defender pour le point de terminaison inclut des fonctionnalités qui étendent davantage la protection antivirus installée sur votre point de terminaison. Vous pouvez tirer parti de l’exécution Antivirus Microsoft Defender avec une autre solution antivirus.

Par exemple, la détection et la réponse des points de terminaison [(PEPT)](edr-in-block-mode.md) en mode blocage offrent une protection supplémentaire contre les artefacts malveillants, même si Antivirus Microsoft Defender n’est pas le produit antivirus principal. De telles fonctionnalités Antivirus Microsoft Defender être installées et en cours d’exécution en mode passif ou actif.

### <a name="requirements-for-microsoft-defender-antivirus-to-run-in-passive-mode"></a>Conditions requises Antivirus Microsoft Defender’exécuter en mode passif

Pour que les Antivirus Microsoft Defender s’exécutent en mode passif, les points de terminaison doivent respecter les conditions suivantes :

- Système d’exploitation : Windows 10 ou plus nouveau ; Windows Server 2022, Windows Server 2019 ou Windows Server, version 1803 ou plus récente
- Antivirus Microsoft Defender doit être installé
- Un autre produit antivirus/anti-programme malveillant non-Microsoft doit être installé et utilisé comme solution antivirus principale
- Les points de terminaison doivent être intégrés à Defender for Endpoint

## <a name="how-microsoft-defender-antivirus-affects-defender-for-endpoint-functionality"></a>Impact Antivirus Microsoft Defender fonctionnalités de Defender for Endpoint

Defender pour le point de terminaison a une incidence sur Antivirus Microsoft Defender’exécuter en mode passif. Antivirus Microsoft Defender peuvent également affecter certaines fonctionnalités de Defender for Endpoint. Par exemple, la protection en temps réel fonctionne lorsque Antivirus Microsoft Defender est en mode actif ou passif, mais pas lorsque Antivirus Microsoft Defender est désactivé ou désinstallé.

Le tableau de cette section récapitule les fonctionnalités qui fonctionnent activement ou non, selon que Antivirus Microsoft Defender est en mode actif, passif ou désactivé/désinstallé.

> [!IMPORTANT]
> Le tableau suivant est conçu pour être uniquement d’information. Ne pas désactiver les fonctionnalités, telles que la protection en temps réel, la protection livrée par le cloud ou l’analyse périodique limitée si vous utilisez Antivirus Microsoft Defender en mode passif, ou si vous utilisez PEPT en [mode](edr-in-block-mode.md)blocage, qui fonctionne en arrière-plan pour détecter et corriger les artefacts malveillants détectés après la violation.

<br/><br/>

 | Protection | Antivirus Microsoft Defender <br/>(*Mode actif*) | Antivirus Microsoft Defender <br/>(*Mode passif*) | Antivirus Microsoft Defender <br/>(*Désactivé ou désinstallé*) | [PEPT en mode blocage](edr-in-block-mode.md) | 
 |---|---|---|---|---| 
 | [Protection en temps réel](configure-real-time-protection-microsoft-defender-antivirus.md) | Oui | Non <sup>[[4](#fn4)]</sup> | Non | Non | 
 | [Protection cloud](enable-cloud-protection-microsoft-defender-antivirus.md) | Oui | Non  | Non | Non | 
 | [Protection du réseau](network-protection.md)  | Oui | Non | Non | Non | 
 | [Règles de réduction de la surface d’attaque](attack-surface-reduction.md)  | Oui | Non | Non  | Non | 
 | [Disponibilité limitée de l’analyse périodique](limited-periodic-scanning-microsoft-defender-antivirus.md) | Non | Non | Oui | Non | 
 | [Informations sur l’analyse et la détection des fichiers](review-scan-results-microsoft-defender-antivirus.md) | Oui | Oui | Non | Oui | 
 | [Correction des menaces](configure-remediation-microsoft-defender-antivirus.md) | Oui | Voir la remarque <sup>[[5](#fn5)]</sup> | Non | Oui | 
 | [Mises à jour de l’intelligence de la sécurité](manage-updates-baselines-microsoft-defender-antivirus.md) | Oui | Oui | Non | Oui | 

(<a id="fn4">4</a>) En général, lorsque Antivirus Microsoft Defender est en mode passif, la protection en temps réel ne fournit aucun blocage ou application, même si elle est activée et en mode passif.

(<a id="fn5">5</a>) Lorsque Antivirus Microsoft Defender est en mode passif, les fonctionnalités de correction des menaces ne sont actives que lors d’analyses programmées ou à la demande.

> [!NOTE]
> [Microsoft 365 protection contre](/microsoft-365/compliance/endpoint-dlp-learn-about) la perte de données de point de terminaison continue de fonctionner normalement lorsque Antivirus Microsoft Defender est en mode actif ou passif.

## <a name="important-notes"></a>Remarques importantes

- Ne désactivez, n’arrêtez ni ne modifiez aucun des services associés utilisés par Antivirus Microsoft Defender, Defender pour le point de terminaison ou l Sécurité Windows appl. Cette recommandation inclut les services et processus *wscsvc,* *SecurityHealthService,* *MsSense,* *Sense,* *WinDefend* ou *MsMpEng.* La modification manuelle de ces services peut entraîner une instabilité grave sur vos appareils et rendre votre réseau vulnérable. La désactivation, l’arrêt ou la modification de ces services peut également provoquer des problèmes lors de l’utilisation de solutions antivirus non Microsoft et la façon dont leurs informations sont affichées dans [l’application Sécurité Windows.](microsoft-defender-security-center-antivirus.md)

- Dans Defender pour le point de terminaison, PEPT en mode blocage, même si Antivirus Microsoft Defender n’est pas votre solution antivirus principale. PEPT en mode blocage détecte et remédie aux éléments malveillants détectés sur l’appareil (après violation). Pour plus d’informations, [voir PEPT en mode bloc.](edr-in-block-mode.md)

## <a name="how-to-confirm-the-state-of-microsoft-defender-antivirus"></a>Comment confirmer l’état du Antivirus Microsoft Defender

Vous pouvez utiliser l’une des méthodes suivantes pour confirmer l’état de Antivirus Microsoft Defender, comme décrit dans le tableau suivant :

<br/><br/>

 | Méthode | Procedure | 
 |---|---| 
 | Sécurité Windows application |  1. Sur un appareil Windows, ouvrez l’Sécurité Windows’application.<br/>2. Sélectionnez **Protection contre & virus**.<br/>3. Under **Qui’s protecting me?** select **Manage providers**.<br/>4. Dans la page **Fournisseurs de sécurité,** sous **Antivirus,** vous devez voir Antivirus Microsoft Defender **est allumé.** | 
 | Gestionnaire des tâches |  1. Sur un appareil Windows, ouvrez l’application Gestionnaire des tâches.<br/>2. Sélectionnez **l’onglet Détails.**<br/>3. Recherchez les **MsMpEng.exe** dans la liste. | 
 | Windows PowerShell <br/><br/> (Pour confirmer qu’Antivirus Microsoft Defender est en cours d’exécution) |  1. Sur un appareil Windows, ouvrez Windows PowerShell. <br/>2. Exécutez l’cmdlet PowerShell suivante `Get-Process` :<br/>3. Examinez les résultats. Vous devriez voir **MsMpEng.exe** si Antivirus Microsoft Defender est activé. | 
 | Windows PowerShell <br/><br/> (Pour vérifier que la protection antivirus est en place) |  Vous pouvez utiliser [l’cmdlet PowerShell Get-MpComputerStatus.](/powershell/module/defender/get-mpcomputerstatus) <br/><br/>1. Sur un appareil Windows, ouvrez Windows PowerShell.<br/>2. Exécutez l’cmdlet PowerShell suivante `Get-MpComputerStatus | select AMRunningMode` : .<br/>3. Examinez les résultats. Vous devez voir **normal** ou **passif** si Antivirus Microsoft Defender est activé sur le point de terminaison.  | 
 | Invite de commandes |  1. Sur un Windows, ouvrez l’invite de commandes.<br/>2. `sc query windefend` Tapez, puis appuyez sur Entrée.<br/>3. Examinez les résultats pour vérifier que Antivirus Microsoft Defender est en cours d’exécution en mode passif.  | 

## <a name="more-details-about-microsoft-defender-antivirus-states"></a>Plus d’informations sur Antivirus Microsoft Defender états

Le tableau de cette section décrit les différents états que vous pouvez voir avec Antivirus Microsoft Defender.

<br/><br/>

 |  État  |  Action exécutée  | 
 |---|---| 
 |  Mode actif  |  En mode actif, Antivirus Microsoft Defender est utilisé comme application antivirus sur l’ordinateur. Paramètres configurés à l’aide de Configuration Manager, d’une stratégie de groupe, Microsoft Intune d’autres produits de gestion s’appliquent. Les fichiers sont analysés, les menaces sont corrigés et les informations de détection sont signalées dans votre outil de configuration (par exemple, Configuration Manager ou l’application Antivirus Microsoft Defender sur le point de terminaison lui-même).  | 
 |  Mode passif  |  En mode passif, Antivirus Microsoft Defender n’est pas utilisé comme  application antivirus et les menaces ne sont pas corrigés par Antivirus Microsoft Defender. Toutefois, les menaces peuvent être corrigés par la détection et la réponse des points de terminaison [(PEPT) en mode blocage.](edr-in-block-mode.md) <br/><br/> Les fichiers sont analysés et des rapports sont fournis pour détecter les menaces qui sont partagées avec le service Defender for Endpoint. Il se peut que des alertes s’affichent dans [Defender pour le cloud](microsoft-defender-security-center.md) Antivirus Microsoft Defender en tant que source, même lorsque Antivirus Microsoft Defender est en mode passif. <br/><br/> Lorsque Antivirus Microsoft Defender est en mode passif, vous pouvez toujours gérer les mises à jour pour [Antivirus Microsoft Defender](manage-updates-baselines-microsoft-defender-antivirus.md); toutefois, vous ne pouvez pas déplacer Antivirus Microsoft Defender  en mode actif si vos appareils ont un produit antivirus non Microsoft qui fournit une protection en temps réel contre les programmes malveillants. <br/><br/> Pour une protection par couches de sécurité et une détection optimales, veillez à obtenir vos mises à jour antivirus et anti-programme malveillant, même si Antivirus Microsoft Defender est en cours d’exécution en mode passif. Voir [Gérer Antivirus Microsoft Defender mises à jour et appliquer les lignes de base.](manage-updates-baselines-microsoft-defender-antivirus.md) <br/><br/> **REMARQUE**: le mode passif n’est pas pris en charge Windows Server 2016.  | 
 |  Désactivé <br/><br/> ou <br/><br/> Désinstallé  |  Lorsqu’il est désactivé ou désinstallé, Antivirus Microsoft Defender n’est pas utilisé comme application antivirus. Les fichiers ne sont pas analysés et les menaces ne sont pas corrigés. <br/><br/> La désactivation ou la désinstallation de Antivirus Microsoft Defender n’est pas recommandée en général ; si possible, conservez les Antivirus Microsoft Defender en mode passif si vous utilisez une solution anti-programme malveillant/antivirus non Microsoft. <br/><br/> Dans les cas où Antivirus Microsoft Defender est automatiquement désactivé, il peut être réactivé automatiquement si le produit antivirus/anti-programme malveillant non-Microsoft expire ou cesse de fournir une protection en temps réel contre les virus, les programmes malveillants ou d’autres menaces. La réactivé automatique des Antivirus Microsoft Defender vous permet de vous assurer que la protection antivirus est conservée sur vos points de terminaison. <br/><br/> Vous pouvez également utiliser une analyse périodique [limitée,](limited-periodic-scanning-microsoft-defender-antivirus.md)qui fonctionne avec le moteur Antivirus Microsoft Defender pour vérifier régulièrement les menaces si vous utilisez une application antivirus non Microsoft.  | 


## <a name="see-also"></a>Voir aussi

- [Antivirus Microsoft Defender dans Windows 10](microsoft-defender-antivirus-in-windows-10.md)
- [Antivirus Microsoft Defender sur Windows Server](microsoft-defender-antivirus-on-windows-server.md)
- [PEPT en mode blocage](edr-in-block-mode.md)
- [Découvrir la protection contre la perte de données des point de terminaison de Microsoft 365](/microsoft-365/compliance/endpoint-dlp-learn-about)
