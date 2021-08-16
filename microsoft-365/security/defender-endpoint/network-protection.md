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
ms.topic: how-to
ms.openlocfilehash: 6fb72c68d69c6844c981c7575bcfed3811a8d20e55a51485d78e26ec447becfe
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53867978"
---
# <a name="protect-your-network"></a>Protéger votre réseau

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

La protection réseau permet de réduire la surface d’attaque de vos appareils à partir d’événements Basés sur Internet. Elle empêche les employés d’utiliser n’importe quelle application pour accéder à des domaines dangereux qui peuvent héberger des tentatives d’hameçonnage, des attaques et d’autres contenus malveillants sur Internet. La protection du réseau étend l’étendue des [Microsoft Defender SmartScreen](/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-overview) pour bloquer tout le trafic HTTP sortant qui tente de se connecter à des sources de faible réputation (en fonction du domaine ou du nom d’hôte).

La protection réseau est prise en charge Windows, à partir Windows 10 version 1709. La protection réseau n’est pas encore prise en charge sur d’autres systèmes d’exploitation, mais la protection web est prise en charge à l’aide du nouveau Microsoft Edge basé sur Chromium. Pour en savoir plus, consultez [La protection Web.](web-protection-overview.md)

La protection du réseau étend la protection dans [la protection Web](web-protection-overview.md) au niveau du système d’exploitation. Il fournit des fonctionnalités de protection web dans Edge à d’autres navigateurs et applications non-navigateur pris en charge. En outre, la protection réseau offre une visibilité et un blocage des indicateurs de compromission (IOCs) lorsqu’elle est utilisée avec la détection et la réponse des [points de terminaison.](overview-endpoint-detection-response.md) Par exemple, la protection du réseau fonctionne avec vos [indicateurs personnalisés.](manage-indicators.md)

Pour plus d’informations sur la façon d’activer la protection réseau, voir [Activer la protection réseau.](enable-network-protection.md) Utilisez une stratégie de groupe, PowerShell ou des CSP de gestion des stratégies de groupe pour activer et gérer la protection réseau dans votre réseau.

> [!TIP]
> Consultez le site testground de Microsoft Defender for Endpoint [demo.wd.microsoft.com](https://demo.wd.microsoft.com?ocid=cx-wddocs-testground) pour voir comment fonctionne la protection réseau.

La protection réseau fonctionne mieux avec [Microsoft Defender pour point](microsoft-defender-endpoint.md)de terminaison, qui vous fournit des rapports détaillés sur les événements et les blocs Exploit Protection dans le cadre de scénarios d’investigation [d’alerte.](investigate-alerts.md)

Lorsque la protection réseau bloque une connexion, une notification s’affiche à partir du centre de notifications. Votre équipe des opérations de sécurité [peut personnaliser la notification](customize-attack-surface-reduction.md#customize-the-notification) avec les détails et les informations de contact de votre organisation. En outre, les règles de réduction de la surface d’attaque individuelles peuvent être activées et personnalisées en fonction de certaines techniques à surveiller.

Vous pouvez également utiliser le [mode audit](audit-windows-defender.md) pour évaluer l’impact de la protection réseau sur votre organisation si elle était activée.

## <a name="requirements"></a>Configuration requise

La protection réseau nécessite Windows 10 Professionnel ou Enterprise, et Antivirus Microsoft Defender protection en temps réel.

| Version de Windows | Antivirus Microsoft Defender |
|:---|:---|
| Windows 10 version 1709 ou ultérieure <p>Windows Serveur 1803 ou ultérieur | [Antivirus Microsoft Defender protection en temps réel](configure-real-time-protection-microsoft-defender-antivirus.md) et la [protection](enable-cloud-protection-microsoft-defender-antivirus.md) cloud doivent être activées |

Après avoir activé les services, vous devrez peut-être configurer votre réseau ou votre pare-feu pour autoriser les connexions entre les services et vos appareils (également appelés points de terminaison).  

- `.smartscreen.microsoft.com`
- `.smartscreen-prod.microsoft.com`

## <a name="review-network-protection-events-in-the-microsoft-defender-for-endpoint-security-center"></a>Passer en revue les événements de protection réseau dans le Centre de sécurité Microsoft Defender pour points de terminaison

Microsoft Defender pour le point de terminaison fournit des rapports détaillés sur les événements et les blocages dans le cadre de ses [scénarios d’investigation d’alerte.](investigate-alerts.md)

Vous pouvez interroger Microsoft Defender pour obtenir des données de point de terminaison à l’aide de [la recherche avancée.](advanced-hunting-overview.md) Si vous utilisez le [mode audit,](audit-windows-defender.md)vous pouvez utiliser la recherche avancée pour voir l’impact des paramètres de protection réseau sur votre environnement s’ils étaient activés.

Voici un exemple de requête

```kusto
DeviceEvents
| where ActionType in ('ExploitGuardNetworkProtectionAudited','ExploitGuardNetworkProtectionBlocked')
```

## <a name="review-network-protection-events-in-windows-event-viewer"></a>Passer en revue les événements de protection réseau dans Windows’observateur d’événements

Vous pouvez consulter le journal des Windows pour voir les événements créés lorsque la protection réseau bloque (ou audite) l’accès à une adresse IP ou un domaine malveillant :

1. [Copiez le XML directement.](event-views.md)

2. Sélectionnez **OK**.

Cette procédure crée un affichage personnalisé qui filtre pour afficher uniquement les événements suivants liés à la protection du réseau :

| ID d’événement | Description |
|:---|:---|
| 5007 | Événement lorsque les paramètres sont modifiés |
| 1125 | Événement lorsque la protection du réseau se déclenche en mode audit |
| 1126 | Événement lorsque la protection réseau se déclenche en mode blocage |

## <a name="considerations-for-windows-virtual-desktop-running-windows-10-enterprise-multi-session"></a>Considérations à prendre en compte Windows de bureau virtuel s’exécutant Windows 10 Entreprise multisess session

En raison de la nature multi-utilisateur de Windows 10 Entreprise, gardez les points suivants à l’esprit :

1. La protection réseau est une fonctionnalité à l’échelle de l’appareil qui ne peut pas être ciblée sur des sessions utilisateur spécifiques.

2. Les stratégies de filtrage de contenu Web sont également à l’échelle de l’appareil.

3. Si vous devez différencier les groupes d’utilisateurs, envisagez de créer des Windows et des affectations d’hôtes Virtual Desktop distincts.

4. Testez la protection réseau en mode audit pour évaluer son comportement avant de le déployer. 

5. Envisagez de re resserger votre déploiement si vous avez un grand nombre d’utilisateurs ou un grand nombre de sessions multi-utilisateurs.

### <a name="alternative-option-for-network-protection"></a>Autre option pour la protection du réseau

Pour Windows 10 Entreprise multisession 1909 et plus, utilisé dans Windows Virtual Desktop sur Azure, la protection réseau pour Microsoft Edge peut être activée à l’aide de la méthode suivante :

1. Utilisez [Activer la protection réseau et](enable-network-protection.md) suivez les instructions pour appliquer votre stratégie.

2. Exécutez la commande PowerShell suivante : `Set-MpPreference -AllowNetworkProtectionOnWinServer 1`

## <a name="network-protection-troubleshooting"></a>Résolution des problèmes de protection du réseau

En raison de l’environnement dans lequel la Protection du réseau s’exécute, Microsoft peut ne pas être en mesure de détecter les paramètres proxy du système d’exploitation. Dans certains cas, les clients de protection réseau ne peuvent pas accéder au service Cloud. Pour résoudre le problème de connectivité, les clients titulaires d’une licence E5 doivent configurer l’une des clés de Registre Defender suivantes :

```console
reg add "HKLM\Software\Microsoft\Windows Defender" /v ProxyServer /d "<proxy IP address: Port>" /f
reg add "HKLM\Software\Microsoft\Windows Defender" /v ProxyPacUrl /d "<Proxy PAC url>" /f

```

## <a name="related-articles"></a>Articles connexes

- [Évaluer les niveaux de protection](evaluate-network-protection.md) | Entreprendre un scénario rapide qui illustre le fonctionnement de la fonctionnalité et les événements qui seraient généralement créés.

- [Activer la protection réseau](enable-network-protection.md) | Utilisez une stratégie de groupe, PowerShell ou des CSP de gestion des stratégies de groupe pour activer et gérer la protection réseau dans votre réseau.
