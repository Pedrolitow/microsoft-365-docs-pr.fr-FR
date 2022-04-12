---
title: Utiliser la protection réseau pour empêcher les connexions à des sites incorrects
description: Protéger votre réseau en empêchant les utilisateurs d’accéder à des adresses réseau malveillantes et suspectes connues
keywords: Protection réseau, exploits, site web malveillant, ip, domaine, domaines
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
audience: ITPro
author: denisebmsft
ms.author: deniseb
ms.reviewer: oogunrinde
manager: dansimp
ms.custom: asr
ms.technology: mde
ms.topic: overview
ms.collection:
- m365initiative-m365-defender
- M365-security-compliance
ms.date: ''
ms.openlocfilehash: f58c7afe9c6f532f7f6420d58bcd681778483680
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/12/2022
ms.locfileid: "64789335"
---
# <a name="protect-your-network"></a>Protéger votre réseau

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- Antivirus Microsoft Defender

**Plateformes**
- Windows

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

## <a name="overview-of-network-protection"></a>Vue d’ensemble de la protection réseau

La protection réseau permet de protéger les appareils contre les événements Basés sur Internet. La protection réseau est une fonctionnalité de réduction de la surface d’attaque. Il permet d’empêcher les employés d’accéder à des domaines dangereux par le biais d’applications. Les domaines qui hébergent des escroqueries, des exploits et d’autres contenus malveillants sur Internet sont considérés comme dangereux. La protection réseau étend l’étendue des [Microsoft Defender SmartScreen](/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-overview) pour bloquer tout le trafic HTTP sortant qui tente de se connecter à des sources de faible réputation (en fonction du domaine ou du nom d’hôte).

La protection réseau étend la protection dans la [protection Web](web-protection-overview.md) au niveau du système d’exploitation. Il fournit des fonctionnalités de protection web dans Edge à d’autres navigateurs et applications non-navigateurs pris en charge. En outre, la protection réseau offre une visibilité et un blocage des indicateurs de compromission (E/S) lorsqu’ils sont utilisés avec la [détection et la réponse](overview-endpoint-detection-response.md) des points de terminaison. Par exemple, la protection réseau fonctionne avec vos [indicateurs personnalisés](manage-indicators.md) que vous pouvez utiliser pour bloquer des domaines ou des noms d’hôte spécifiques.

> [!TIP]
> Consultez le site Microsoft Defender pour point de terminaison testground sur [demo.wd.microsoft.com](https://demo.wd.microsoft.com?ocid=cx-wddocs-testground) pour voir comment fonctionne la protection réseau.

> [!NOTE]
> Le site de démonstration Defender pour point de terminaison sur demo.wd.microsoft.com est déconseillé et sera supprimé à l’avenir.

## <a name="requirements-for-network-protection"></a>Configuration requise pour la protection réseau

La protection réseau nécessite Windows 10 Professionnel ou Enterprise, et Antivirus Microsoft Defender protection en temps réel.

<br>

****

|Version de Windows|Antivirus Microsoft Defender|
|---|---|
|Windows 10 version 1709 ou ultérieure <p> Windows 11 <p> Windows Server 1803 ou version ultérieure|[Antivirus Microsoft Defender protection en temps réel](configure-real-time-protection-microsoft-defender-antivirus.md) et [la protection fournie par le cloud](enable-cloud-protection-microsoft-defender-antivirus.md) doivent être activées|
|

Une fois que vous avez activé les services, vous devrez peut-être configurer votre réseau ou pare-feu pour autoriser les connexions entre les services et vos appareils (également appelés points de terminaison).

- `.smartscreen.microsoft.com`
- `.smartscreen-prod.microsoft.com`

## <a name="configuring-network-protection"></a>Configuration de la protection réseau

Pour plus d’informations sur l’activation de la protection réseau, consultez **[Activer la protection réseau](enable-network-protection.md)**. Utilisez stratégie de groupe, PowerShell ou MDM CSP pour activer et gérer la protection réseau dans votre réseau.

## <a name="viewing-network-protection-events"></a>Affichage des événements de protection réseau

La protection réseau fonctionne mieux avec [Microsoft Defender pour point de terminaison](microsoft-defender-endpoint.md), ce qui vous permet de générer des rapports détaillés sur les événements et les blocs de protection contre les attaques dans le cadre de [scénarios d’investigation d’alerte](investigate-alerts.md).

Lorsque la protection réseau bloque une connexion, une notification s’affiche à partir du Centre d’actions. Votre équipe des opérations de sécurité peut [personnaliser la notification](attack-surface-reduction-rules-deployment-implement.md#customize-attack-surface-reduction-rules) avec les détails et les informations de contact de votre organisation. En outre, les règles individuelles de réduction de la surface d’attaque peuvent être activées et personnalisées en fonction de certaines techniques à surveiller.

Vous pouvez également utiliser le [mode audit](audit-windows-defender.md) pour évaluer l’impact de la protection réseau sur votre organisation si elle était activée.

## <a name="review-network-protection-events-in-the-microsoft-365-defender-portal"></a>Passer en revue les événements de protection réseau dans le portail Microsoft 365 Defender

Microsoft Defender pour point de terminaison fournit des rapports détaillés sur les événements et les blocs dans le cadre de ses [scénarios d’investigation des alertes](investigate-alerts.md). Vous pouvez afficher ces détails dans le portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) dans la [file d’attente des alertes](review-alerts.md) ou à l’aide de la [chasse avancée](advanced-hunting-overview.md). Si vous utilisez le [mode audit](audit-windows-defender.md), vous pouvez utiliser la chasse avancée pour voir comment les paramètres de protection réseau affecteraient votre environnement s’ils étaient activés.

Voici un exemple de requête pour la chasse avancée :

```kusto
DeviceNetworkEvents
|where ActionType in ('ExploitGuardNetworkProtectionAudited','ExploitGuardNetworkProtectionBlocked', 'ConnectionSuccess')
```

## <a name="review-network-protection-events-in-windows-event-viewer"></a>Passer en revue les événements de protection réseau dans Windows observateur d'événements

Vous pouvez consulter le journal des événements Windows pour voir les événements créés lorsque la protection réseau bloque (ou audite) l’accès à une adresse IP ou un domaine malveillant :

1. [Copiez le code XML directement](event-views.md).

2. Sélectionnez **OK**.

Cette procédure crée une vue personnalisée qui filtre pour afficher uniquement les événements suivants liés à la protection réseau :

<br>

****

|ID d’événement|Description|
|---|---|
|5007|Événement lorsque les paramètres sont modifiés|
|1125|Événement lorsque la protection réseau se déclenche en mode audit|
|1126|Événement lorsque la protection réseau se déclenche en mode bloc|
|

## <a name="network-protection-and-the-tcp-three-way-handshake"></a>Protection réseau et liaison TCP triple

Avec la protection réseau, la détermination de l’autorisation ou du blocage de l’accès à un site est effectuée après la fin de l’établissement de la [liaison triple via TCP/IP](/troubleshoot/windows-server/networking/three-way-handshake-via-tcpip). Ainsi, lorsqu’un site est bloqué par la protection réseau, vous pouvez voir un type d’action `ConnectionSuccess` sous `NetworkConnectionEvents` le portail Microsoft 365 Defender, même si le site a été bloqué. `NetworkConnectionEvents` sont signalés à partir de la couche TCP et non de la protection réseau. Une fois la négociation triple terminée, l’accès au site est autorisé ou bloqué par la protection réseau.

Voici un exemple de fonctionnement :

1. Supposons qu’un utilisateur tente d’accéder à un site web sur son appareil. Le site est hébergé sur un domaine dangereux et doit être bloqué par la protection réseau.  

2. L’établissement d’une liaison triple via TCP/IP commence. Avant de se terminer, une `NetworkConnectionEvents` action est journalisée et est `ActionType` répertoriée comme `ConnectionSuccess`. Toutefois, dès que le processus de négociation triple est terminé, la protection réseau bloque l’accès au site. Tout cela se produit très rapidement. Un processus similaire se produit avec [Microsoft Defender SmartScreen](/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-overview) ; c’est lorsque l’établissement d’une liaison à trois est terminé qu’une décision est prise et que l’accès à un site est bloqué ou autorisé.

3. Dans le portail Microsoft 365 Defender, une alerte est répertoriée dans la [file d’attente des alertes](alerts-queue.md). Les détails de cette alerte incluent à la fois `NetworkConnectionEvents` et `AlertEvents`. Vous pouvez voir que le site a été bloqué, même si vous avez également un `NetworkConnectionEvents` élément avec l’ActionType de `ConnectionSuccess`.

## <a name="considerations-for-windows-virtual-desktop-running-windows-10-enterprise-multi-session"></a>Considérations relatives à Windows bureau virtuel exécutant Windows 10 Entreprise multisession

En raison de la nature multi-utilisateur de Windows 10 Entreprise, gardez à l’esprit les points suivants :

1. La protection réseau est une fonctionnalité à l’échelle de l’appareil et ne peut pas être ciblée sur des sessions utilisateur spécifiques.

2. Les stratégies de filtrage de contenu web sont également à l’échelle de l’appareil.

3. Si vous devez faire la distinction entre les groupes d’utilisateurs, envisagez de créer des Windows pools d’hôtes virtual desktop et des affectations distinctes.

4. Testez la protection réseau en mode audit pour évaluer son comportement avant de le déployer.

5. Envisagez de redimensionner votre déploiement si vous avez un grand nombre d’utilisateurs ou un grand nombre de sessions multi-utilisateurs.

### <a name="alternative-option-for-network-protection"></a>Autre option pour la protection réseau

Pour Windows 10 Entreprise multisession 1909 et versions ultérieures, utilisées dans Windows Virtual Desktop sur Azure, la protection réseau pour Microsoft Edge peut être activée à l’aide de la méthode suivante :

1. Utilisez [Activer la protection réseau](enable-network-protection.md) et suivez les instructions pour appliquer votre stratégie.

2. Exécutez les commandes PowerShell suivantes :
  - `Set-MpPreference -EnableNetworkProtection Enabled`
  - `Set-MpPreference -AllowNetworkProtectionOnWinServer 1`
  - `Set-MpPreference -AllowNetworkProtectionDownLevel 1`
  - `Set-MpPreference -AllowDatagramProcessingOnWinServer 1`

## <a name="network-protection-troubleshooting"></a>Résolution des problèmes de protection réseau

En raison de l’environnement dans lequel la protection réseau s’exécute, Microsoft peut ne pas être en mesure de détecter les paramètres de proxy du système d’exploitation. Dans certains cas, les clients de protection réseau ne peuvent pas accéder au service cloud. Pour résoudre le problème de connectivité, les clients disposant de licences E5 doivent configurer l’une des clés de Registre suivantes :

```console
reg add "HKLM\Software\Microsoft\Windows Defender" /v ProxyServer /d "<proxy IP address: Port>" /f
reg add "HKLM\Software\Microsoft\Windows Defender" /v ProxyPacUrl /d "<Proxy PAC url>" /f

```

## <a name="see-also"></a>Voir aussi

- [Évaluer les | de protection réseau](evaluate-network-protection.md) Effectuez un scénario rapide qui illustre le fonctionnement de la fonctionnalité et les événements qui sont généralement créés.
- [Activer la protection réseau](enable-network-protection.md) | Utilisez stratégie de groupe, PowerShell ou MDM CSP pour activer et gérer la protection réseau dans votre réseau.
- [Configuration des fonctionnalités de réduction de la surface d’attaque dans Microsoft Intune](/mem/intune/protect/endpoint-security-asr-policy)
