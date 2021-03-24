---
title: Utiliser la protection réseau pour empêcher les connexions à des sites malveillants
description: Protéger votre réseau en empêchant les utilisateurs d’accéder aux adresses réseau malveillantes et suspectes connues
keywords: Protection du réseau, attaques, site web malveillant, ip, domaine, domaines
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
localization_priority: Normal
audience: ITPro
author: denisebmsft
ms.author: deniseb
ms.reviewer: ''
manager: dansimp
ms.custom: asr
ms.technology: mde
ms.date: 03/08/2021
ms.openlocfilehash: b6069d392da1b8610d018908d172dc27044baffc
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2021
ms.locfileid: "51061342"
---
# <a name="protect-your-network"></a>Protéger votre réseau

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2146631)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez découvrir Microsoft Defender pour le point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink)

La protection réseau permet de réduire la surface d’attaque de vos appareils à partir d’événements Basés sur Internet. Elle empêche les employés d’utiliser n’importe quelle application pour accéder à des domaines dangereux qui peuvent héberger des tentatives d’hameçonnage, des attaques et d’autres contenus malveillants sur Internet. La protection du réseau étend l’étendue de [Microsoft Defender SmartScreen](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-overview) pour bloquer tout le trafic HTTP sortant qui tente de se connecter à des sources de faible réputation (en fonction du domaine ou du nom d’hôte).

La protection réseau est prise en charge sur Windows, à partir de Windows 10, version 1709. 

Pour plus d’informations sur la façon d’activer la protection réseau, voir [Activer la protection réseau.](enable-network-protection.md) Utilisez une stratégie de groupe, PowerShell ou des CSP de gestion des stratégies de groupe pour activer et gérer la protection réseau dans votre réseau.

> [!TIP]
> Consultez le site testground de Microsoft Defender ATP [demo.wd.microsoft.com](https://demo.wd.microsoft.com?ocid=cx-wddocs-testground) pour voir comment fonctionne la protection réseau.

La protection du réseau fonctionne mieux avec [Microsoft Defender pour point](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/microsoft-defender-advanced-threat-protection)de terminaison, qui vous fournit des rapports détaillés sur les événements et les blocs Exploit Protection dans le cadre de scénarios d’investigation [d’alerte.](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/investigate-alerts)

Lorsque la protection réseau bloque une connexion, une notification s’affiche à partir du centre de notifications. Votre équipe des opérations de sécurité [peut personnaliser la notification](customize-attack-surface-reduction.md#customize-the-notification) avec les détails et les informations de contact de votre organisation. En outre, les règles de réduction de la surface d’attaque individuelles peuvent être activées et personnalisées en fonction de certaines techniques à surveiller.

Vous pouvez également utiliser le [mode audit pour](audit-windows-defender.md) évaluer l’impact de la protection réseau sur votre organisation si elle était activée.

## <a name="requirements"></a>Configuration requise

La protection du réseau nécessite Windows 10 Professionnel ou Entreprise et la protection en temps réel de l’Antivirus Microsoft Defender.

| Version de Windows | Antivirus Microsoft Defender |
|:---|:---|
| Windows 10 version 1709 ou ultérieure <p>Windows Server 1803 ou une ultérieure | [La protection en temps réel](https://docs.microsoft.com/windows/security/threat-protection/configure-real-time-protection-microsoft-defender-antivirus.md) et la protection [cloud](https://docs.microsoft.com/windows/security/threat-protection/enable-cloud-protection-microsoft-defender-antivirus.md) de l’Antivirus Microsoft Defender doivent être activées |

Après avoir activé les services, vous devrez peut-être configurer votre réseau ou votre pare-feu pour autoriser les connexions entre les services et vos appareils (également appelés points de terminaison).  

- .smartscreen.microsoft.com
- .smartscreen-prod.microsoft.com

## <a name="review-network-protection-events-in-the-microsoft-defender-for-endpoint-security-center"></a>Passer en revue les événements de protection réseau dans le Centre de sécurité Microsoft Defender pour points de terminaison

Microsoft Defender pour le point de terminaison fournit des rapports détaillés sur les événements et les blocages dans le cadre de ses [scénarios d’investigation d’alerte.](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/investigate-alerts)

Vous pouvez interroger Microsoft Defender pour obtenir des données de point de terminaison à l’aide [de la recherche avancée.](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-windows-defender-advanced-threat-protection) Si vous utilisez le [mode audit,](audit-windows-defender.md)vous pouvez utiliser la recherche avancée pour voir l’impact des paramètres de protection réseau sur votre environnement s’ils étaient activés.

Voici un exemple de requête

```kusto
DeviceEvents
| where ActionType in ('ExploitGuardNetworkProtectionAudited','ExploitGuardNetworkProtectionBlocked')
```

## <a name="review-network-protection-events-in-windows-event-viewer"></a>Passer en revue les événements de protection réseau dans l’Observateur d’événements Windows

Vous pouvez consulter le journal des événements Windows pour voir les événements créés lorsque la protection réseau bloque (ou audite) l’accès à une adresse IP ou un domaine malveillant :

1. [Copiez le XML directement.](event-views.md)

2. Sélectionnez **OK**.

Cette procédure crée un affichage personnalisé qui filtre pour afficher uniquement les événements suivants liés à la protection du réseau :

| ID de l'événement | Description |
|:---|:---|
| 5007 | Événement lorsque les paramètres sont modifiés |
| 1125 | Événement lorsque la protection du réseau se déclenche en mode audit |
| 1126 | Événement lorsque la protection réseau se déclenche en mode blocage |

## <a name="related-articles"></a>Articles connexes

- [Évaluer les niveaux de protection](evaluate-network-protection.md) | Entreprendre un scénario rapide qui illustre le fonctionnement de la fonctionnalité et les événements qui seraient généralement créés.

- [Activer la protection réseau](enable-network-protection.md) | Utilisez une stratégie de groupe, PowerShell ou des CSP de gestion des stratégies de groupe pour activer et gérer la protection réseau dans votre réseau.
