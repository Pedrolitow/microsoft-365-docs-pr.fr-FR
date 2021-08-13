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
ms.reviewer: tewchen, pahuijbr
manager: dansimp
ms.technology: mde
ms.date: 07/06/2021
ms.openlocfilehash: b7584a7e8165b11e334d004736df4b3868a1f172d2c5d1d0d7127cde311fee67
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53800041"
---
# <a name="microsoft-defender-antivirus-compatibility"></a>Antivirus Microsoft Defender compatibilité

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/)

## <a name="summary"></a>Résumé

Antivirus Microsoft Defender est automatiquement activé et installé sur les points de terminaison et les appareils qui s’exécutent Windows 10. Mais que se passe-t-il lorsqu’une autre solution antivirus/anti-programme malveillant (non Microsoft) est utilisée ? Pouvez-vous exécuter Antivirus Microsoft Defender avec un autre produit antivirus ? Les réponses dépendent de plusieurs facteurs, tels que le système d’exploitation et si vous utilisez [Microsoft Defender pour Endpoint](microsoft-defender-endpoint.md) avec votre protection antivirus. 

## <a name="important-points-to-keep-in-mind"></a>Points importants à garder à l’esprit

- En mode actif, Antivirus Microsoft Defender est utilisé comme application antivirus sur l’ordinateur. Paramètres à l’aide de Configuration Manager, d’une stratégie de groupe, Microsoft Intune ou d’autres produits de gestion s’appliquent. Les fichiers sont analysés, les menaces sont corrigés et les informations de détection sont signalées dans votre outil de configuration (par exemple, Configuration Manager ou l’application Antivirus Microsoft Defender sur le point de terminaison lui-même).

- En mode passif, Antivirus Microsoft Defender n’est pas utilisé comme  application antivirus et les menaces ne sont pas corrigés par Antivirus Microsoft Defender. Les fichiers sont analysés et des rapports sont fournis pour détecter les menaces qui sont partagées avec le service Microsoft Defender for Endpoint. Des alertes peuvent [](microsoft-defender-security-center.md) s’afficher dans le centre de sécurité indiquant Antivirus Microsoft Defender comme source, même si Antivirus Microsoft Defender est en mode passif.

- Lorsque PEPT en [mode](edr-in-block-mode.md) blocage est allumé et que Antivirus Microsoft Defender n’est pas la solution antivirus principale, PEPT en mode blocage détecte et remédie aux éléments malveillants détectés sur l’appareil (après violation). PEPT en mode bloc Antivirus Microsoft Defender être activé en mode actif ou passif.

- Lorsqu’elle est désactivée, Antivirus Microsoft Defender n’est pas utilisé comme application antivirus. Les fichiers ne sont pas analysés et les menaces ne sont pas corrigés. La désactivation ou la désinstallation Antivirus Microsoft Defender est déconseillée en général ; si possible, conservez Antivirus Microsoft Defender en mode passif si vous utilisez une solution anti-programme malveillant/antivirus non Microsoft.

- Si vous êtes inscrit à Microsoft Defender pour le point de terminaison et que vous utilisez un produit antivirus/anti-programme malveillant non Microsoft, Antivirus Microsoft Defender est activé en mode passif. Defender pour le point de terminaison nécessite le partage d’informations courantes à partir de Antivirus Microsoft Defender afin de surveiller correctement vos appareils et votre réseau pour les tentatives d’intrusion et les attaques. Pour en savoir plus, [voir Antivirus Microsoft Defender compatibilité avec Microsoft Defender pour Endpoint.](defender-compatibility.md) 

- Lorsque Antivirus Microsoft Defender est en mode passif, vous pouvez toujours gérer les mises à jour pour [Antivirus Microsoft Defender](manage-updates-baselines-microsoft-defender-antivirus.md); toutefois, vous ne pouvez pas déplacer Antivirus Microsoft Defender en mode actif si vos appareils ont un produit antivirus non Microsoft qui fournit une protection en temps réel contre les programmes malveillants. Pour une protection par couches de sécurité et une détection optimales, veillez à obtenir vos mises à jour antivirus et anti-programme malveillant, même si Antivirus Microsoft Defender est en cours d’exécution en mode passif. Voir [Gérer Antivirus Microsoft Defender mises à jour et appliquer les lignes de base.](manage-updates-baselines-microsoft-defender-antivirus.md)

- Lorsque Antivirus Microsoft Defender est désactivé automatiquement, il peut être réactivé automatiquement si le produit antivirus/anti-programme malveillant non-Microsoft expire ou s’il cesse de fournir une protection en temps réel contre les virus, les programmes malveillants ou d’autres menaces. La réactivé automatique des Antivirus Microsoft Defender permet de garantir que la protection antivirus est conservée sur vos points de terminaison. Vous pouvez également activer l’analyse périodique [limitée,](limited-periodic-scanning-microsoft-defender-antivirus.md)qui utilise le moteur Antivirus Microsoft Defender pour vérifier régulièrement les menaces si vous utilisez une application antivirus non Microsoft.

## <a name="microsoft-defender-antivirus-and-non-microsoft-antivirusantimalware-solutions"></a>Antivirus Microsoft Defender solutions antivirus/anti-programme malveillant non Microsoft

Le système d’exploitation, le produit antivirus et Defender pour le point de terminaison affectent si Antivirus Microsoft Defender est en mode actif, passif ou désactivé. Le tableau suivant récapitule ce qui se passe avec Antivirus Microsoft Defender lorsque des solutions antivirus/anti-programme malveillant non Microsoft sont utilisées ensemble ou sans Microsoft Defender for Endpoint. 

| Version de Windows   | Solution antivirus/anti-programme malveillant  | Intégré à <br/> Defender pour le point de terminaison ? | Antivirus Microsoft Defender’état     |
|------|------|-------|-------|
| Windows 10  | Antivirus Microsoft Defender | Oui  | Mode actif | 
| Windows 10  | Antivirus Microsoft Defender | Non   | Mode actif |
| Windows 10  | Une solution antivirus/anti-programme malveillant non-Microsoft | Oui  | Mode passif (automatiquement) |
| Windows 10  | Une solution antivirus/anti-programme malveillant non-Microsoft | Non   | Mode désactivé (automatiquement)    |
| Windows Serveur, version 1803 ou plus récente <p> Windows Server 2019 | Antivirus Microsoft Defender  | Oui |         Mode actif  |
| Windows Serveur, version 1803 ou plus récente <p> Windows Server 2019 | Antivirus Microsoft Defender | Non  | Mode actif |
| Windows Serveur, version 1803 ou plus récente <p> Windows Server 2019 | Une solution antivirus/anti-programme malveillant non-Microsoft | Oui  | Antivirus Microsoft Defender doit être définie en mode passif (manuellement) <sup> [[1](#fn1)]<sup>  | 
| Windows Serveur, version 1803 ou plus récente <p> Windows Server 2019 | Une solution antivirus/anti-programme malveillant non-Microsoft | Non  | Antivirus Microsoft Defender doit être désactivé (manuellement) <sup> [[2](#fn2)]<sup></sup>  |
| Windows Server 2016 | Antivirus Microsoft Defender | Oui | Mode actif |
| Windows Server 2016 | Antivirus Microsoft Defender | Non | Mode actif |
| Windows Server 2016 | Une solution antivirus/anti-programme malveillant non-Microsoft | Oui | Antivirus Microsoft Defender doit être désactivé (manuellement) <sup> [[2](#fn2)]<sup> |
| Windows Server 2016 | Une solution antivirus/anti-programme malveillant non-Microsoft | Non | Antivirus Microsoft Defender doit être désactivé (manuellement) <sup> [[2](#fn2)]<sup> |

(<a id="fn1">1</a>) Sur Windows Server, version 1803 ou plus récente, ou Windows Server 2019, Antivirus Microsoft Defender n’entre pas en mode passif automatiquement lorsque vous installez un produit antivirus non Microsoft. Dans ce cas, [définissez Antivirus Microsoft Defender](microsoft-defender-antivirus-on-windows-server.md#need-to-set-microsoft-defender-antivirus-to-passive-mode) en mode passif pour éviter les problèmes causés par l’installation de plusieurs produits antivirus sur un serveur. Vous pouvez définir Antivirus Microsoft Defender mode passif à l’aide de PowerShell, d’une stratégie de groupe ou d’une clé de Registre.

Si vous utilisez Windows Server, version 1803 ou plus récente, ou Windows Server 2019, vous pouvez définir Antivirus Microsoft Defender en mode passif en réglant la clé de Registre suivante :
- Chemin d’accès : `HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection`
- Nom : `ForceDefenderPassiveMode`
- Type : `REG_DWORD`
- Valeur : `1`

> [!NOTE]
> Le mode passif n’est pas pris en charge Windows Server 2016. La clé de Registre peut être utilisée sur `ForceDefenderPassiveMode` Windows Server, version 1803 ou plus récente, ou Windows Server 2019, mais pas Windows Server 2016. 

(<a id="fn2">2</a>) Sur Windows Server 2016, si vous utilisez un produit antivirus non Microsoft, vous ne pouvez pas exécuter Antivirus Microsoft Defender en mode passif ou actif. Dans ce cas, [désactivez/désinstallez](microsoft-defender-antivirus-on-windows-server.md#are-you-using-windows-server-2016) Antivirus Microsoft Defender manuellement pour éviter les problèmes causés par l’installation de plusieurs produits antivirus sur un serveur.

Voir [Antivirus Microsoft Defender sur Windows Server pour](microsoft-defender-antivirus-on-windows-server.md) les principales différences et les options de gestion pour les installations Windows Server.

> [!IMPORTANT]
> Antivirus Microsoft Defender est disponible uniquement sur les appareils exécutant Windows 10, Windows Server 2016, Windows Server, version 1803 ou ultérieure et Windows Server 2019.
>
> Dans Windows 8.1 et Windows Server 2012, la protection antivirus de point de terminaison au niveau de l’entreprise est proposée sous [la](/previous-versions/system-center/system-center-2012-R2/hh508760(v=technet.10))System Center Endpoint Protection, qui est gérée via Microsoft Endpoint Configuration Manager.
>
> Windows Defender est également proposé pour les appareils grand public sur Windows 8.1 et [Windows Server 2012,](/previous-versions/windows/it-pro/windows-8.1-and-8/dn344918(v=ws.11)#BKMK_WindowsDefender)bien qu’il ne fournisse pas de gestion au niveau de l’entreprise (ou une interface sur les installations Windows Server 2012 Server Core).

## <a name="how-microsoft-defender-antivirus-affects-defender-for-endpoint-functionality"></a>Impact Antivirus Microsoft Defender fonctionnalités de Defender for Endpoint

Le tableau de cette section récapitule les fonctionnalités et fonctionnalités disponibles dans chaque état. Le tableau est conçu pour être uniquement d’information. Il est destiné à décrire les fonctionnalités & qui fonctionnent activement ou non, selon que Antivirus Microsoft Defender est en mode actif, en mode passif ou est désactivé/désinstallé. 

> [!IMPORTANT]
> Ne pas désactiver les fonctionnalités, telles que la protection en temps réel, la protection cloud ou l’analyse périodique limitée, si vous utilisez Antivirus Microsoft Defender en mode passif ou si vous utilisez PEPT en mode blocage. 

|Protection |Mode actif |Mode passif |PEPT en mode blocage |Désactivé ou désinstallé |
|:---|:---|:---|:---|:---|
| [Protection en temps réel](configure-real-time-protection-microsoft-defender-antivirus.md) et [protection cloud](enable-cloud-protection-microsoft-defender-antivirus.md) | Oui | Non <sup> [[3](#fn3)]<sup> | Non | Non |
| [Disponibilité limitée de l’analyse périodique](limited-periodic-scanning-microsoft-defender-antivirus.md) | Non | Non | Non | Oui |
| [Informations sur l’analyse et la détection des fichiers](customize-run-review-remediate-scans-microsoft-defender-antivirus.md) | Oui | Oui | Oui | Non |
|  [Correction des menaces](configure-remediation-microsoft-defender-antivirus.md) | Oui | Voir la remarque <sup> [[4](#fn4)]<sup> | Oui | Non |
| [Mises à jour de l’intelligence de la sécurité](manage-updates-baselines-microsoft-defender-antivirus.md) | Oui | Oui | Oui | Non |

(<a id="fn3">3</a>) En général, lorsque Antivirus Microsoft Defender est en mode passif, la protection en temps réel ne fournit aucun blocage ou application, même si elle est activée et en mode passif. 

(<a id="fn4">4</a>) Lorsque Antivirus Microsoft Defender est en mode passif, les fonctionnalités de correction des menaces ne sont actives que lors d’analyses programmées ou à la demande.

> [!NOTE]
> [Microsoft 365 protection contre](/microsoft-365/compliance/endpoint-dlp-learn-about) la perte de données de point de terminaison continue de fonctionner normalement lorsque Antivirus Microsoft Defender est en mode actif ou passif.

## <a name="why-defender-for-endpoint-matters"></a>Pourquoi Defender pour le point de terminaison a-t-il de l’importance ?

Envisagez d’intégrer vos points de terminaison à Defender for Endpoint, même si vous utilisez une solution antivirus/anti-programme malveillant non-Microsoft. Dans la plupart des cas, lorsque vous intégrerez vos appareils à Defender for Endpoint, vous pouvez utiliser Antivirus Microsoft Defender avec votre solution antivirus non Microsoft pour une protection supplémentaire. Par exemple, vous pouvez utiliser PEPT en [mode](edr-in-block-mode.md)blocage, qui bloque et remédie les artefacts malveillants que votre solution antivirus principale a peut-être manquées. 

Voici le principe de fonctionnement :

- Si les appareils clients de votre organisation sont protégés par une solution antivirus/anti-programme malveillant non Microsoft, lorsque ces appareils sont intégrés à Defender pour endpoint, Antivirus Microsoft Defender passe automatiquement en mode passif. Dans ce cas, les détections de menaces se produisent, mais la protection en temps réel et les menaces ne sont pas corrigés par Antivirus Microsoft Defender.
   
   > [!NOTE]
   > Ce scénario particulier ne s’applique pas aux points de terminaison exécutant Windows Server.

- Si les appareils clients de votre organisation sont protégés par une solution antivirus/anti-programme malveillant non Microsoft et que ces appareils ne sont pas intégrés à Microsoft Defender pour endpoint, Antivirus Microsoft Defender passe en mode désactivé automatiquement. Dans ce cas, les menaces ne sont ni détectées ni corrigés par les Antivirus Microsoft Defender.
   
   > [!NOTE]
   > Ce scénario particulier ne s’applique pas aux points de terminaison exécutant Windows Server.

- Si les points de terminaison de votre organisation exécutent Windows Server et que ces points de terminaison sont protégés par une solution antivirus/anti-programme malveillant non Microsoft, lorsque ces points de terminaison sont intégrés à Defender pour le point de terminaison, Antivirus Microsoft Defender ne passe pas en mode passif ou désactivé automatiquement. Dans ce scénario particulier, vous devez configurer vos points de terminaison Windows serveur de manière appropriée. 

   - Sur Windows Server, version 1803 ou plus récente et Windows Server 2019, vous pouvez configurer Antivirus Microsoft Defender pour qu’il s’exécute en mode passif. 
   - Sur Windows Server 2016, Antivirus Microsoft Defender doit être désactivé (le mode passif n’est pas pris en charge sur Windows Server 2016).

- Si les points de terminaison de votre organisation sont protégés par une solution antivirus/anti-programme malveillant non-Microsoft, lorsque ces appareils sont intégrés à Defender for Endpoint avec PEPT activé en [mode](/microsoft-365/security/defender-endpoint/edr-in-block-mode) bloc, Defender for Endpoint bloque et remédie aux artefacts malveillants.
   
   > [!NOTE]
   > Ce scénario particulier ne s’applique pas aux Windows Server 2016. PEPT en mode bloc Antivirus Microsoft Defender être activé en mode actif ou passif.


> [!WARNING]
> Ne désactivez, n’arrêtez ni ne modifiez aucun des services associés utilisés par Antivirus Microsoft Defender, Microsoft Defender pour le point de terminaison ou l Sécurité Windows appl. Cette recommandation inclut les services et processus *wscsvc,* *SecurityHealthService,* *MsSense,* *Sense,* *WinDefend* ou *MsMpEng.* La modification manuelle de ces services peut entraîner une instabilité grave sur vos appareils et rendre votre réseau vulnérable. La désactivation, l’arrêt ou la modification de ces services peut également provoquer des problèmes lors de l’utilisation de solutions antivirus non Microsoft et la façon dont leurs informations sont affichées dans [l’application Sécurité Windows.](microsoft-defender-security-center-antivirus.md)


## <a name="see-also"></a>Voir aussi

- [Antivirus Microsoft Defender dans Windows 10](microsoft-defender-antivirus-in-windows-10.md)
- [Antivirus Microsoft Defender sur Windows Server](microsoft-defender-antivirus-on-windows-server.md)
- [PEPT en mode blocage](edr-in-block-mode.md)
- [Configurer Endpoint Protection](/mem/configmgr/protect/deploy-use/endpoint-protection-configure)
- [Résoudre des faux négatifs/positifs dans Microsoft Defender pour point de terminaison](defender-endpoint-false-positives-negatives.md)
- [Découvrir la protection contre la perte de données des point de terminaison de Microsoft 365](/microsoft-365/compliance/endpoint-dlp-learn-about)
