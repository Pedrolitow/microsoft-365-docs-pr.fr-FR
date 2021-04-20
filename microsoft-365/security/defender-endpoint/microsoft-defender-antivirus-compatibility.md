---
title: Compatibilité de l'Antivirus Microsoft Defender avec d'autres produits de sécurité
description: Ce qu'il faut attendre de l'Antivirus Microsoft Defender avec d'autres produits de sécurité et les systèmes d'exploitation que vous utilisez.
keywords: windows defender, nouvelle génération, antivirus, compatibilité, mode passif
search.product: eADQiWindows 10XVcnh
ms.pagetype: security
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
localization_priority: normal
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: tewchen, pahuijbr, shwjha
manager: dansimp
ms.technology: mde
ms.openlocfilehash: 8e179135f12ad6f4ea765eaf975a40534446b51f
ms.sourcegitcommit: 55791ddab9ae484f76b30f0470eec8a4cf7b46d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2021
ms.locfileid: "51893388"
---
# <a name="microsoft-defender-antivirus-compatibility"></a>Compatibilité de l'Antivirus Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/)

## <a name="overview"></a>Vue d’ensemble

L'Antivirus Microsoft Defender est automatiquement activé et installé sur les points de terminaison et les appareils exécutant Windows 10. Mais que se passe-t-il lorsqu'une autre solution antivirus/anti-programme malveillant est utilisée ? Cela dépend de l'utilisation ou non de [Microsoft Defender pour Endpoint](microsoft-defender-endpoint.md) avec votre protection antivirus.
- Si les points de terminaison et les appareils de votre organisation sont protégés par une solution antivirus/anti-programme malveillant non Microsoft et que Microsoft Defender pour le point de terminaison n'est pas utilisé, l'Antivirus Microsoft Defender passe automatiquement en mode désactivé.
- Si votre organisation utilise Microsoft Defender pour endpoint avec une solution antivirus/anti-programme malveillant non Microsoft, l'Antivirus Microsoft Defender passe automatiquement en mode passif. (La protection en temps réel et les menaces ne sont pas corrigés par l'Antivirus Microsoft Defender.)
- Si votre organisation utilise Microsoft Defender pour le point de terminaison avec une solution antivirus/anti-programme malveillant non Microsoft et que [l'EDR](/microsoft-365/security/defender-endpoint/edr-in-block-mode) est activé en mode blocage, chaque fois qu'un artefact malveillant est détecté, Microsoft Defender pour le point de terminaison prend des mesures pour bloquer et corriger l'artefact.

## <a name="antivirus-and-microsoft-defender-for-endpoint"></a>Antivirus et Microsoft Defender pour point de terminaison

Le tableau suivant récapitule ce qui se produit avec l'Antivirus Microsoft Defender lorsque des produits antivirus tiers sont utilisés ensemble ou sans Microsoft Defender for Endpoint. 


| Version de Windows   | Protection anti-programme malveillant  | Inscription de Microsoft Defender pour les points de terminaison | État de l'Antivirus Microsoft Defender     |
|------|------|-------|-------|
| Windows 10  | Un produit tiers qui n'est pas proposé ou développé par Microsoft | Oui  | Mode passif  |
| Windows 10  | Un produit tiers qui n'est pas proposé ou développé par Microsoft | Non   | Mode désactivé automatiquement     |
| Windows 10  | Antivirus Microsoft Defender | Oui  | Mode actif | 
| Windows 10  | Antivirus Microsoft Defender | Non   | Mode actif |
| Windows Server, version 1803 ou plus récente, ou Windows Server 2019 | Un produit tiers qui n'est pas proposé ou développé par Microsoft | Oui  | Doit être définie sur le mode passif (manuellement) <sup> [[1](#fn1)]<sup>  | 
| Windows Server, version 1803 ou plus récente, ou Windows Server 2019 | Un produit tiers qui n'est pas proposé ou développé par Microsoft | Non  | Doit être désactivé (manuellement) <sup> [[2](#fn2)]<sup></sup>  |
| Windows Server, version 1803 ou plus récente, ou Windows Server 2019 | Antivirus Microsoft Defender  | Oui |         Mode actif  |
| Windows Server, version 1803 ou plus récente, ou Windows Server 2019 | Antivirus Microsoft Defender | Non  | Mode actif |
| Windows Server 2016 | Antivirus Microsoft Defender | Oui | Mode actif |
| Windows Server 2016 | Antivirus Microsoft Defender | Non | Mode actif |
| Windows Server 2016 | Un produit tiers qui n'est pas proposé ou développé par Microsoft | Oui | Doit être désactivé (manuellement) <sup> [[2](#fn2)]<sup> |
| Windows Server 2016 | Un produit tiers qui n'est pas proposé ou développé par Microsoft | Non | Doit être désactivé (manuellement) <sup> [[2](#fn2)]<sup> |

(<a id="fn1">1</a>) Sur Windows Server, version 1803 ou plus récente, ou Windows Server 2019, l'Antivirus Microsoft Defender n'entre pas en mode passif automatiquement lorsque vous installez un produit antivirus non Microsoft. Dans ce cas, [définissez l'Antivirus Microsoft Defender](microsoft-defender-antivirus-on-windows-server.md#need-to-set-microsoft-defender-antivirus-to-passive-mode) sur le mode passif pour éviter les problèmes causés par l'installation de plusieurs produits antivirus sur un serveur.

Si vous utilisez Windows Server, version 1803 ou plus récente, ou Windows Server 2019, vous pouvez définir l'Antivirus Microsoft Defender sur le mode passif en réglant la clé de Registre suivante :
- Chemin d'accès : `HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection`
- Nom : `ForceDefenderPassiveMode`
- Type : `REG_DWORD`
- Valeur : `1`

> [!NOTE]
> La `ForcePassiveMode` clé de Registre n'est pas prise en charge sur Windows Server 2016.

(<a id="fn2">2</a>) Sur Windows Server 2016, l'Antivirus Microsoft Defender n'entre pas en mode passif automatiquement lorsque vous installez un produit antivirus non Microsoft. En outre, l'Antivirus Microsoft Defender n'est pas pris en charge en mode passif. Dans ce cas, [désactivez/désinstallez manuellement l'Antivirus Microsoft Defender](microsoft-defender-antivirus-on-windows-server.md#are-you-using-windows-server-2016) pour éviter les problèmes causés par l'installation de plusieurs produits antivirus sur un serveur.

Consultez [l'Antivirus Microsoft Defender sur Windows Server pour obtenir](microsoft-defender-antivirus-on-windows-server.md) les principales différences et les options de gestion pour les installations de Windows Server.

> [!IMPORTANT]
> L'Antivirus Microsoft Defender est disponible uniquement sur les appareils exécutant Windows 10, Windows Server 2016, Windows Server, version 1803 ou ultérieure et Windows Server 2019.
>
> Dans Windows 8.1 et Windows Server 2012, la protection antivirus de point de terminaison au niveau de l'entreprise est proposée en tant que [System Center Endpoint Protection](/previous-versions/system-center/system-center-2012-R2/hh508760(v=technet.10)), qui est gérée par le biais de Microsoft Endpoint Configuration Manager.
>
> Windows Defender est également proposé pour les appareils grand public sur [Windows 8.1 et Windows Server 2012,](/previous-versions/windows/it-pro/windows-8.1-and-8/dn344918(v=ws.11)#BKMK_WindowsDefender)bien qu'il ne fournisse pas de gestion au niveau de l'entreprise (ou une interface sur les installations Windows Server 2012 Server Core).

## <a name="functionality-and-features-available-in-each-state"></a>Fonctionnalités et fonctionnalités disponibles dans chaque état

Le tableau de cette section récapitule les fonctionnalités et fonctionnalités disponibles dans chaque état. Le tableau est conçu pour être uniquement d'information. Il est destiné à décrire les fonctionnalités & qui fonctionnent activement ou non, selon que l'Antivirus Microsoft Defender est en mode actif, en mode passif ou est désactivé/désinstallé. 

> [!IMPORTANT]
> Ne pas désactiver les fonctionnalités, telles que la protection en temps réel, la protection cloud ou l'analyse périodique limitée, si vous utilisez l'Antivirus Microsoft Defender en mode passif ou si vous utilisez EDR en mode blocage. 

|Protection |Mode actif |Mode passif |PEPT en mode blocage |Désactivé ou désinstallé |
|:---|:---|:---|:---|:---|
| [Protection en temps réel](./configure-real-time-protection-microsoft-defender-antivirus.md) et [protection cloud](./enable-cloud-protection-microsoft-defender-antivirus.md) | Oui | Non <sup> [[3](#fn3)]<sup> | Non | Non |
| [Disponibilité limitée de l'analyse périodique](./limited-periodic-scanning-microsoft-defender-antivirus.md) | Non | Non | Non | Oui |
| [Informations sur l'analyse et la détection des fichiers](./customize-run-review-remediate-scans-microsoft-defender-antivirus.md) | Oui | Oui | Oui | Non |
|  [Correction des menaces](./configure-remediation-microsoft-defender-antivirus.md) | Oui | Voir la remarque <sup> [[4](#fn4)]<sup> | Oui | Non |
| [Mises à jour de l'intelligence de la sécurité](./manage-updates-baselines-microsoft-defender-antivirus.md) | Oui | Oui | Oui | Non |

(<a id="fn3">3</a>) En général, lorsque l'Antivirus Microsoft Defender est en mode passif, la protection en temps réel ne fournit aucun blocage ou application, même si elle est activée et en mode passif. 

(<a id="fn4">4</a>) Lorsque l'Antivirus Microsoft Defender est en mode passif, les fonctionnalités de correction des menaces ne sont actives que lors d'analyses programmées ou à la demande.

> [!NOTE]
> La protection contre la perte de données de point de terminaison [Microsoft 365](/microsoft-365/compliance/endpoint-dlp-learn-about) continue de fonctionner normalement lorsque l'Antivirus Microsoft Defender est en mode actif ou passif.

## <a name="keep-the-following-points-in-mind"></a>Gardez les points suivants à l'esprit

- En mode actif, l'Antivirus Microsoft Defender est utilisé comme application antivirus sur l'ordinateur. Toutes les configurations réalisées avec Configuration Manager, la stratégie de groupe, Intune ou d'autres produits de gestion s'appliquent. Les fichiers sont analysés et les menaces sont corrigés, et des informations de détection sont signalées dans votre outil de configuration (par exemple, Configuration Manager ou l'application Antivirus Microsoft Defender sur l'ordinateur lui-même).

- En mode passif, l'Antivirus Microsoft Defender n'est pas utilisé comme application antivirus et les menaces ne sont pas corrigés par l'Antivirus Microsoft Defender. Les fichiers sont analysés et des rapports sont fournis pour détecter les menaces qui sont partagées avec le service Microsoft Defender for Endpoint. Par conséquent, vous pouvez rencontrer des alertes dans la console du Centre de sécurité avec l'Antivirus Microsoft Defender comme source, même lorsque l'Antivirus Microsoft Defender est en mode passif.

- Lorsque [l'EDR](/microsoft-365/security/defender-endpoint/edr-in-block-mode) en mode blocage est allumé et que l'Antivirus Microsoft Defender n'est pas la solution antivirus principale, il peut toujours détecter et corriger les éléments malveillants.

- Lorsqu'il est désactivé, l'Antivirus Microsoft Defender n'est pas utilisé comme application antivirus. Les fichiers ne sont pas analysés et les menaces ne sont pas corrigés. La désactivation/désinstallation de l'Antivirus Microsoft Defender n'est généralement pas recommandée . Si possible, conservez l'Antivirus Microsoft Defender en mode passif si vous utilisez une solution anti-programme malveillant/antivirus non Microsoft.

- Si vous êtes inscrit à Microsoft Defender pour endpoint et que vous utilisez un produit anti-programme malveillant tiers, le mode passif est activé. [Le service nécessite le partage d'informations](/microsoft-365/security/defender-endpoint/defender-compatibility) courantes à partir du service Antivirus Microsoft Defender afin de surveiller correctement vos appareils et votre réseau pour les tentatives d'intrusion et les attaques.

- Lorsque l'Antivirus Microsoft Defender est désactivé automatiquement, il peut être réactivé automatiquement si la protection offerte par un produit antivirus non-Microsoft expire ou cesse de fournir une protection en temps réel contre les virus, les programmes malveillants ou d'autres menaces. La réactiver automatique permet de s'assurer que la protection antivirus est conservée sur vos appareils. Il vous permet également d'activer l'analyse périodique [limitée,](limited-periodic-scanning-microsoft-defender-antivirus.md)qui utilise le moteur antivirus Microsoft Defender pour vérifier régulièrement les menaces en plus de votre application antivirus principale.

- Lorsque l'Antivirus Microsoft Defender est en mode passif, vous pouvez toujours gérer les mises à jour de [l'Antivirus Microsoft Defender](manage-updates-baselines-microsoft-defender-antivirus.md). Toutefois, vous ne pouvez pas déplacer l'Antivirus Microsoft Defender en mode actif si vos appareils ont un produit antivirus non Microsoft à jour fournissant une protection en temps réel contre les programmes malveillants. Pour une protection par couches de sécurité et une détection optimales, veillez à mettre à jour la protection de [l'Antivirus Microsoft Defender (mise](./manage-updates-baselines-microsoft-defender-antivirus.md) à jour de l'intelligence de sécurité, moteur et plateforme) même si l'Antivirus Microsoft Defender s'exécute en mode passif.

   Si vous désinstallez le produit antivirus non Microsoft et que vous utilisez l'Antivirus Microsoft Defender pour protéger vos appareils, l'Antivirus Microsoft Defender revient automatiquement à son mode d'activité normal.

> [!WARNING]
> Ne désactivez, n'arrêtez ni ne modifiez aucun des services associés utilisés par l'Antivirus Microsoft Defender, Microsoft Defender pour le point de terminaison ou l'application Sécurité Windows. Cette recommandation inclut les services et processus *wscsvc,* *SecurityHealthService,* *MsSense,* *Sense,* *WinDefend* ou *MsMpEng.* La modification manuelle de ces services peut entraîner une instabilité grave sur vos appareils et rendre votre réseau vulnérable. La désactivation, l'arrêt ou la modification de ces services peut également provoquer des problèmes lors de l'utilisation de solutions antivirus non Microsoft et la façon dont leurs informations sont affichées dans l'application [Sécurité Windows.](microsoft-defender-security-center-antivirus.md)


## <a name="see-also"></a>Voir aussi

- [Antivirus Microsoft Defender dans Windows 10](microsoft-defender-antivirus-in-windows-10.md)
- [Antivirus Microsoft Defender sur Windows Server](microsoft-defender-antivirus-on-windows-server.md)
- [PEPT en mode blocage](edr-in-block-mode.md)
- [Configurer Endpoint Protection](/mem/configmgr/protect/deploy-use/endpoint-protection-configure)
- [Résoudre des faux négatifs/positifs dans Microsoft Defender pour point de terminaison](defender-endpoint-false-positives-negatives.md)
- [Découvrir la protection contre la perte de données des point de terminaison de Microsoft 365](/microsoft-365/compliance/endpoint-dlp-learn-about)
