---
title: Antivirus Microsoft Defender compatibilité avec d’autres produits de sécurité
description: Découvrez les Antivirus Microsoft Defender avec d’autres produits de sécurité et les systèmes d’exploitation.
keywords: windows defender, defender pour le point de terminaison, nouvelle génération, antivirus, compatibilité, mode passif
search.product: eADQiWindows 10XVcnh
ms.pagetype: security
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
localization_priority: normal
ms.topic: article
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: mkaminska, pahuijbr
manager: dansimp
ms.technology: mde
ms.date: 08/11/2021
ms.openlocfilehash: be816488ebe930da2f757ed192a12d81c0a222ef
ms.sourcegitcommit: c41e3f48451e2d7b45901faee21b1e1d19a16688
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2021
ms.locfileid: "58823755"
---
# <a name="microsoft-defender-antivirus-compatibility-with-other-security-products"></a>Antivirus Microsoft Defender compatibilité avec d’autres produits de sécurité

**S’applique à :**

- Antivirus Microsoft Defender
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)


Antivirus Microsoft Defender est automatiquement installé sur les points de terminaison exécutant les versions suivantes de Windows :

- Windows 10 ou ultérieure
- Windows Server 2016
- Windows Serveur, version 1803 ou ultérieure
- Windows Server 2019

Que se passe-t-il lorsqu’une autre solution antivirus/anti-programme malveillant non-Microsoft est utilisée ? Pouvez-vous exécuter Antivirus Microsoft Defender avec un autre produit antivirus ? Les réponses dépendent de plusieurs facteurs, tels que votre système d’exploitation et si vous utilisez [Microsoft Defender](microsoft-defender-endpoint.md) pour point de terminaison (Defender pour point de terminaison) avec votre protection antivirus.

Cet article décrit ce qui se passe avec Antivirus Microsoft Defender et une solution antivirus/anti-programme malveillant non Microsoft, avec ou sans Defender for Endpoint.

## <a name="antivirus-protection-without-defender-for-endpoint"></a>Protection antivirus sans Defender pour le point de terminaison

Cette section décrit ce qui se passe avec Antivirus Microsoft Defender et les produits antivirus/anti-programme malveillant non-Microsoft sur les points de terminaison qui ne sont pas intégrés à Defender for Endpoint. Le tableau suivant récapitule ce à quoi vous pouvez vous attendre :

<br>

****

|Version de Windows|Solution antivirus/anti-programme malveillant principale|Antivirus Microsoft Defender’état|
|---|---|---|---|
|Windows 10|Antivirus Microsoft Defender|Mode actif|
|Windows 10|Une solution antivirus/anti-programme malveillant non-Microsoft|Mode désactivé (se produit automatiquement)|
|Windows Server 2016 <p> Windows Serveur, version 1803 ou plus récente <p> Windows Server 2019|Antivirus Microsoft Defender|Mode actif|
|Windows Server 2016 <p> Windows Serveur, version 1803 ou plus récente <p> Windows Server 2019|Une solution antivirus/anti-programme malveillant non-Microsoft|Désactivé (définie manuellement) <sup> [[1](#fn1)]<sup></sup>|

(<a id="fn1">1</a>) Sur Windows Server, si vous exécutez un produit antivirus non Microsoft, vous pouvez désactiver Antivirus Microsoft Defender à l’aide de la stratégie de groupe pour désactiver Antivirus Microsoft Defender ou à l’aide de la clé de Registre [DisableAntiSpyware.](/windows-hardware/customize/desktop/unattend/security-malware-windows-defender-disableantispyware) Pour utiliser la clé de Registre, accédez `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender` à , et définissez ou créez une entrée DWORD appelée `DisableAntiSpyware` . Définissez sa valeur sur (qui définit la valeur de la clé de Registre sur true), puis sélectionnez `1` **Hexadécimal** pour sa base. 

> [!TIP]
> Voir [Antivirus Microsoft Defender sur Windows Server pour](microsoft-defender-antivirus-on-windows-server.md) les principales différences et les options de gestion pour les installations Windows Server. On Windows Server 2016, you might see *Antivirus Windows Defender* instead of *Antivirus Microsoft Defender*.

## <a name="antivirus-protection-with-defender-for-endpoint"></a>Protection antivirus avec Defender pour le point de terminaison

Si votre organisation utilise une solution antivirus/anti-programme malveillant non Microsoft avec Defender for Endpoint, Antivirus Microsoft Defender peut, en fonction de votre système d’exploitation, s’exécuter en mode passif.

<br>

****

|Version de Windows|Solution antivirus/anti-programme malveillant principale|Antivirus Microsoft Defender’état|
|---|---|---|---|
|Windows 10 ou ultérieure|Antivirus Microsoft Defender|Mode actif|
|Windows 10 ou ultérieure|Une solution antivirus/anti-programme malveillant non-Microsoft|Mode passif (se produit automatiquement)|
|Windows Server 2016 <p> Windows Serveur, version 1803 ou plus récente <p> Windows Server 2019|Antivirus Microsoft Defender|Mode actif|
|Windows Serveur, version 1803 ou plus récente <p> Windows Server 2019|Une solution antivirus/anti-programme malveillant non-Microsoft|Mode passif (définir manuellement) <sup> [[2](#fn2)]<sup></sup>|
|Windows Server 2016|Une solution antivirus/anti-programme malveillant non-Microsoft|Désactivé (définie manuellement) <sup> [[3](#fn3)]<sup>|

(<a id="fn2">2</a>) Sur Windows Server, version 1803 ou plus récente, ou Windows Server 2019, lorsque vous installez un produit antivirus non Microsoft, définissez Antivirus Microsoft Defender en mode passif manuellement. Vous pouvez utiliser la **clé de Registre ForceDefenderPassiveMode** pour effectuer cette tâche. Pour utiliser la clé de Registre, accédez `HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection` à , et définissez ou créez une entrée DWORD appelée `ForceDefenderPassiveMode` . Définissez sa valeur sur (qui définit la valeur de la clé de Registre sur true), puis sélectionnez `1` **Hexadécimal** pour sa base.  Pour plus d’informations, [voir Mode passif et Windows Server.](microsoft-defender-antivirus-on-windows-server.md#passive-mode-and-windows-server)

(<a id="fn3">3</a>) Sur Windows Server 2016, vous pouvez désactiver Antivirus Microsoft Defender à l’aide de la stratégie de groupe pour désactiver Antivirus Windows Defender ou à l’aide de la clé de Registre [DisableAntiSpyware.](/windows-hardware/customize/desktop/unattend/security-malware-windows-defender-disableantispyware) Pour utiliser la clé de Registre, accédez `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender` à , et définissez ou créez une entrée DWORD appelée `DisableAntiSpyware` . Définissez sa valeur sur (qui définit la valeur de la clé de Registre sur true), puis sélectionnez `1` **Hexadécimal** pour sa base. 

> [!TIP]
> Voir [Antivirus Microsoft Defender sur Windows Server pour](microsoft-defender-antivirus-on-windows-server.md) les principales différences et les options de gestion pour les installations Windows Server. On Windows Server 2016, you might see *Antivirus Windows Defender* instead of *Antivirus Microsoft Defender*.

### <a name="why-run-microsoft-defender-antivirus-in-passive-mode"></a>Pourquoi exécuter Antivirus Microsoft Defender en mode passif ?

Defender pour le point de terminaison inclut des fonctionnalités qui étendent davantage la protection antivirus installée sur votre point de terminaison. Vous pouvez tirer parti de l’exécution de Antivirus Microsoft Defender avec une autre solution antivirus.

Par exemple, la détection et la réponse des points de terminaison [(PEPT)](edr-in-block-mode.md) en mode blocage offrent une protection supplémentaire contre les artefacts malveillants, même si Antivirus Microsoft Defender n’est pas le produit antivirus principal. De telles fonctionnalités Antivirus Microsoft Defender être installées et en cours d’exécution en mode passif ou actif.

### <a name="requirements-for-microsoft-defender-antivirus-to-run-in-passive-mode"></a>Conditions requises Antivirus Microsoft Defender’exécuter en mode passif

Pour que les Antivirus Microsoft Defender s’exécutent en mode passif, les points de terminaison doivent respecter les conditions suivantes :

- Système d’exploitation : Windows 10 ou ultérieure ; Windows Serveur, version 1803 ou plus récente ; ou Windows Server 2019
- Antivirus Microsoft Defender doit être installé
- Un autre produit antivirus/anti-programme malveillant non-Microsoft doit être installé et utilisé comme solution antivirus principale
- Les points de terminaison doivent être intégrés à Defender for Endpoint

## <a name="how-microsoft-defender-antivirus-affects-defender-for-endpoint-functionality"></a>Impact Antivirus Microsoft Defender fonctionnalités de Defender for Endpoint

Defender pour le point de terminaison a une incidence sur Antivirus Microsoft Defender’exécuter en mode passif. Antivirus Microsoft Defender peuvent également affecter certaines fonctionnalités de Defender pour Endpoint. Par exemple, la protection en temps réel fonctionne lorsque Antivirus Microsoft Defender est en mode actif ou passif, mais pas lorsque Antivirus Microsoft Defender est désactivé ou désinstallé.

Le tableau de cette section récapitule les fonctionnalités qui fonctionnent activement ou non, selon que Antivirus Microsoft Defender est en mode actif, passif ou désactivé/désinstallé.

> [!IMPORTANT]
> Le tableau suivant est conçu pour être uniquement d’information. Ne pas désactiver les fonctionnalités, telles que la protection en temps réel, la protection livrée par le cloud ou l’analyse périodique limitée si vous utilisez Antivirus Microsoft Defender en mode passif, ou si vous utilisez PEPT en [mode](edr-in-block-mode.md)blocage, qui fonctionne en arrière-plan pour détecter et corriger les artefacts malveillants détectés après la violation.

<br>

****

|Protection|Antivirus Microsoft Defender <p> Mode actif|Antivirus Microsoft Defender <p> Mode passif|Antivirus Microsoft Defender <p> Désactivé ou désinstallé|[PEPT en mode blocage](edr-in-block-mode.md)|
|---|---|---|---|---|
|[Protection en temps réel](configure-real-time-protection-microsoft-defender-antivirus.md) et [protection cloud](enable-cloud-protection-microsoft-defender-antivirus.md)|Oui|Non <sup> [[5](#fn5)]<sup>|Non|Non|
|[Disponibilité limitée de l’analyse périodique](limited-periodic-scanning-microsoft-defender-antivirus.md)|Non|Non|Oui|Non|
|[Informations sur l’analyse et la détection des fichiers](review-scan-results-microsoft-defender-antivirus.md)|Oui|Oui|Non|Oui|
|[Correction des menaces](configure-remediation-microsoft-defender-antivirus.md)|Oui|Voir la remarque <sup> [[6](#fn6)]<sup>|Non|Oui|
|[Mises à jour de l’intelligence de la sécurité](manage-updates-baselines-microsoft-defender-antivirus.md)|Oui|Oui|Non|Oui|
||||||

(<a id="fn5">5</a>) En général, lorsque Antivirus Microsoft Defender est en mode passif, la protection en temps réel ne fournit aucun blocage ou application, même si elle est activée et en mode passif.

(<a id="fn6">6</a>) Lorsque Antivirus Microsoft Defender est en mode passif, les fonctionnalités de correction des menaces ne sont actives que lors d’analyses programmées ou à la demande.

> [!NOTE]
> [Microsoft 365 protection contre](/microsoft-365/compliance/endpoint-dlp-learn-about) la perte de données de point de terminaison continue de fonctionner normalement lorsque Antivirus Microsoft Defender est en mode actif ou passif.

## <a name="important-notes"></a>Remarques importantes

- Ne désactivez, n’arrêtez ni ne modifiez aucun des services associés utilisés par Antivirus Microsoft Defender, Defender pour le point de terminaison ou l Sécurité Windows appl. Cette recommandation inclut les services et processus *wscsvc,* *SecurityHealthService,* *MsSense,* *Sense,* *WinDefend* ou *MsMpEng.* La modification manuelle de ces services peut entraîner une instabilité grave sur vos appareils et rendre votre réseau vulnérable. La désactivation, l’arrêt ou la modification de ces services peut également provoquer des problèmes lors de l’utilisation de solutions antivirus non Microsoft et la façon dont leurs informations sont affichées dans [l’application Sécurité Windows.](microsoft-defender-security-center-antivirus.md)

- Dans Defender pour le point de terminaison, PEPT en mode blocage, même si Antivirus Microsoft Defender n’est pas votre solution antivirus principale. PEPT en mode blocage détecte et remédie aux éléments malveillants détectés sur l’appareil (après violation). Pour plus d’informations, [voir PEPT en mode bloc.](edr-in-block-mode.md)

## <a name="how-to-confirm-the-state-of-microsoft-defender-antivirus"></a>Comment confirmer l’état du Antivirus Microsoft Defender

Vous pouvez utiliser l’une des méthodes suivantes pour confirmer l’état Antivirus Microsoft Defender, comme décrit dans le tableau suivant :

<br>

****

|Méthode|Procedure|
|---|---|
|Sécurité Windows application|<ol><li>Sur un Windows, ouvrez l’Sécurité Windows app.</li><li>Sélectionnez **Protection contre les virus et les menaces**.</li><li>Under **Qui’s protecting me?** select **Manage providers**.</li><li>Dans la page **Fournisseurs de sécurité,** sous **Antivirus,** vous devriez voir Antivirus Microsoft Defender **est allumé.**</li></ol>|
|Gestionnaire des tâches|<ol><li>Sur un Windows, ouvrez l’application Gestionnaire des tâches.</li><li>Sélectionnez **l’onglet Détails.**</li><li>Recherchez **lesMsMpEng.exe** dans la liste.</li></ol>|
|Windows PowerShell <p> (Pour confirmer que le Antivirus Microsoft Defender est en cours d’exécution)|<ol><li>Sur un Windows, ouvrez Windows PowerShell</li><li>Exécutez l’cmdlet PowerShell suivante : `Get-Process` .</li><li>Passez en revue les résultats. Vous devriez voir **MsMpEng.exe** si Antivirus Microsoft Defender est activé.</li></ol>|
|Windows PowerShell <p> (Pour vérifier que la protection antivirus est en place)|Vous pouvez utiliser [l’cmdlet PowerShell Get-MpComputerStatus.](/powershell/module/defender/get-mpcomputerstatus) <ol><li>Sur un Windows, ouvrez Windows PowerShell.</li><li>Exécutez l’cmdlet PowerShell suivante `Get-MpComputerStatus|select AMRunningMode` : .</li><li>Passez en revue les résultats. Vous devez voir **normal** ou **passif** si Antivirus Microsoft Defender est activé sur le point de terminaison.</li></ol>|
|Invite de commandes|<ol><li>Sur un Windows, ouvrez l’invite de commandes.</li><li>`sc query windefend`Tapez, puis appuyez sur Entrée.</li><li>Examinez les résultats pour vérifier que Antivirus Microsoft Defender est en cours d’exécution en mode passif.</li></ol>|
|||

## <a name="more-details-about-microsoft-defender-antivirus-states"></a>Plus d’informations sur Antivirus Microsoft Defender états

Le tableau de cette section décrit les différents états que vous pouvez voir avec Antivirus Microsoft Defender.

<br>

****

|Antivirus Microsoft Defender’état|Action exécutée|
|---|---|
|Mode actif|En mode actif, Antivirus Microsoft Defender est utilisé comme application antivirus sur l’ordinateur. Paramètres configurés à l’aide de Configuration Manager, d’une stratégie de groupe, Microsoft Intune ou d’autres produits de gestion s’appliquent. Les fichiers sont analysés, les menaces sont corrigés et les informations de détection sont signalées dans votre outil de configuration (par exemple, Configuration Manager ou l’application Antivirus Microsoft Defender sur le point de terminaison lui-même).|
|Mode passif|En mode passif, Antivirus Microsoft Defender n’est pas utilisé comme  application antivirus et les menaces ne sont pas corrigés par Antivirus Microsoft Defender. Toutefois, les menaces peuvent être corrigés par la détection et la réponse des points [de terminaison (PEPT) en mode blocage.](edr-in-block-mode.md) <p> Les fichiers sont analysés et des rapports sont fournis pour détecter les menaces qui sont partagées avec le service Defender for Endpoint. Des alertes peuvent [](microsoft-defender-security-center.md) s’afficher dans le centre de sécurité indiquant Antivirus Microsoft Defender comme source, même si Antivirus Microsoft Defender est en mode passif. <p> Lorsque Antivirus Microsoft Defender est en mode passif, vous pouvez toujours gérer les mises à jour pour [Antivirus Microsoft Defender](manage-updates-baselines-microsoft-defender-antivirus.md); toutefois, vous ne pouvez pas déplacer Antivirus Microsoft Defender en mode actif si vos appareils ont un produit antivirus non Microsoft qui fournit une protection en temps réel contre les programmes malveillants. <p> Pour une protection par couches de sécurité et une détection optimales, veillez à obtenir vos mises à jour antivirus et anti-programme malveillant, même si Antivirus Microsoft Defender est en cours d’exécution en mode passif. Voir [Gérer Antivirus Microsoft Defender mises à jour et appliquer les lignes de base.](manage-updates-baselines-microsoft-defender-antivirus.md) <p> **REMARQUE**: le mode passif n’est pas pris en charge Windows Server 2016.|
|Désactivé <p> ou <p> Désinstallé|Lorsqu’il est désactivé ou désinstallé, Antivirus Microsoft Defender n’est pas utilisé comme application antivirus. Les fichiers ne sont pas analysés et les menaces ne sont pas corrigés. <p> La désactivation ou la désinstallation Antivirus Microsoft Defender est déconseillée en général ; si possible, conservez Antivirus Microsoft Defender en mode passif si vous utilisez une solution anti-programme malveillant/antivirus non Microsoft. <p> Dans les cas où Antivirus Microsoft Defender est automatiquement désactivé, il peut être réactivé automatiquement si le produit antivirus/anti-programme malveillant non-Microsoft expire ou cesse de fournir une protection en temps réel contre les virus, les programmes malveillants ou d’autres menaces. La réactivé automatique des Antivirus Microsoft Defender permet de garantir que la protection antivirus est conservée sur vos points de terminaison. <p> Vous pouvez également utiliser une analyse périodique [limitée,](limited-periodic-scanning-microsoft-defender-antivirus.md)qui fonctionne avec le moteur Antivirus Microsoft Defender pour vérifier régulièrement les menaces si vous utilisez une application antivirus non Microsoft.|
|||

## <a name="see-also"></a>Voir aussi

- [Antivirus Microsoft Defender dans Windows 10](microsoft-defender-antivirus-in-windows-10.md)
- [Antivirus Microsoft Defender sur Windows Server](microsoft-defender-antivirus-on-windows-server.md)
- [PEPT en mode blocage](edr-in-block-mode.md)
- [Découvrir la protection contre la perte de données des point de terminaison de Microsoft 365](/microsoft-365/compliance/endpoint-dlp-learn-about)
