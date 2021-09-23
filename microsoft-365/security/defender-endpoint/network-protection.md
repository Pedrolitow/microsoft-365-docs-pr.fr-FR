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
ms.reviewer: oogunrinde
manager: dansimp
ms.custom: asr
ms.technology: mde
ms.topic: overview
ms.collection: M365-security-compliance
ms.openlocfilehash: ab658009d5459093477dede8fdab5e8da4186eb6
ms.sourcegitcommit: 6968594dc8cf8b30a4c958df6d65dfd0cd2cfae1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2021
ms.locfileid: "59491156"
---
# <a name="protect-your-network"></a>Protéger votre réseau

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

## <a name="overview-of-network-protection"></a>Vue d’ensemble de la protection du réseau

La protection du réseau permet de protéger les appareils contre les événements Basés sur Internet. La protection réseau est une fonctionnalité de réduction de la surface d’attaque. Cela permet d’empêcher les employés d’accéder à des domaines dangereux par le biais d’applications. Les domaines qui hébergent des tentatives de hameçonnage, des attaques et d’autres contenus malveillants sur Internet sont considérés comme dangereux. La protection du réseau étend l’étendue des [Microsoft Defender SmartScreen](/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-overview) pour bloquer tout le trafic HTTP sortant qui tente de se connecter à des sources de faible réputation (en fonction du domaine ou du nom d’hôte).

La protection du réseau étend la protection dans [la protection Web](web-protection-overview.md) au niveau du système d’exploitation. Il fournit des fonctionnalités de protection web dans Edge à d’autres navigateurs et applications non-navigateur pris en charge. En outre, la protection réseau offre une visibilité et un blocage des indicateurs de compromission (IOCs) lorsqu’elle est utilisée avec la détection et la réponse des [points de terminaison.](overview-endpoint-detection-response.md) Par exemple, la protection du réseau fonctionne avec vos indicateurs [personnalisés que](manage-indicators.md) vous pouvez utiliser pour bloquer des domaines ou des noms d’hôte spécifiques.

> [!TIP]
> Consultez le site testground de Microsoft Defender for Endpoint [demo.wd.microsoft.com](https://demo.wd.microsoft.com?ocid=cx-wddocs-testground) pour voir comment fonctionne la protection réseau.

## <a name="requirements-for-network-protection"></a>Conditions requises pour la protection du réseau

La protection réseau nécessite Windows 10 Professionnel ou Enterprise, et Antivirus Microsoft Defender protection en temps réel.

<br>

****

|Version de Windows|Antivirus Microsoft Defender|
|---|---|
|Windows 10 version 1709 ou ultérieure <p> Windows Serveur 1803 ou ultérieur|[Antivirus Microsoft Defender protection en temps réel](configure-real-time-protection-microsoft-defender-antivirus.md) et la [protection](enable-cloud-protection-microsoft-defender-antivirus.md) cloud doivent être activées|
|

Après avoir activé les services, vous devrez peut-être configurer votre réseau ou votre pare-feu pour autoriser les connexions entre les services et vos appareils (également appelés points de terminaison).

- `.smartscreen.microsoft.com`
- `.smartscreen-prod.microsoft.com`

## <a name="configuring-network-protection"></a>Configuration de la protection réseau

Pour plus d’informations sur la façon d’activer la protection réseau, voir **[Activer la protection réseau.](enable-network-protection.md)** Utilisez une stratégie de groupe, PowerShell ou des CSP de gestion des stratégies de groupe pour activer et gérer la protection réseau dans votre réseau.

## <a name="viewing-network-protection-events"></a>Affichage des événements de protection réseau

La protection du réseau fonctionne mieux avec [Microsoft Defender pour point](microsoft-defender-endpoint.md)de terminaison, qui vous fournit des rapports détaillés sur les événements et les blocs Exploit Protection dans le cadre de scénarios d’investigation [d’alerte.](investigate-alerts.md)

Lorsque la protection réseau bloque une connexion, une notification s’affiche à partir du centre de notifications. Votre équipe des opérations de sécurité [peut personnaliser la notification](customize-attack-surface-reduction.md#customize-the-notification) avec les détails et les informations de contact de votre organisation. En outre, les règles de réduction de la surface d’attaque individuelles peuvent être activées et personnalisées en fonction de certaines techniques à surveiller.

Vous pouvez également utiliser le [mode audit pour](audit-windows-defender.md) évaluer l’impact de la protection réseau sur votre organisation si elle était activée.

## <a name="review-network-protection-events-in-the-microsoft-365-defender-portal"></a>Passer en revue les événements de protection réseau dans le Microsoft 365 Defender web

Microsoft Defender pour le point de terminaison fournit des rapports détaillés sur les événements et les blocages dans le cadre de ses [scénarios d’investigation d’alerte.](investigate-alerts.md) Vous pouvez afficher ces détails dans le portail Microsoft 365 Defender ( ) dans la file d’attente des alertes ou à l’aide de [https://security.microsoft.com](https://security.microsoft.com) [la recherche avancée.](advanced-hunting-overview.md) [](review-alerts.md) Si vous utilisez le [mode audit,](audit-windows-defender.md)vous pouvez utiliser la recherche avancée pour voir l’impact des paramètres de protection réseau sur votre environnement s’ils étaient activés.

Voici un exemple de requête de recherche avancée :

```kusto
DeviceEvents
|where ActionType in ('ExploitGuardNetworkProtectionAudited','ExploitGuardNetworkProtectionBlocked')
```

## <a name="review-network-protection-events-in-windows-event-viewer"></a>Passer en revue les événements de protection réseau dans Windows’observateur d’événements

Vous pouvez consulter le journal des Windows pour voir les événements créés lorsque la protection réseau bloque (ou audite) l’accès à une adresse IP ou un domaine malveillant :

1. [Copiez le XML directement.](event-views.md)

2. Sélectionnez **OK**.

Cette procédure crée un affichage personnalisé qui filtre pour afficher uniquement les événements suivants liés à la protection du réseau :

<br>

****

|ID d’événement|Description|
|---|---|
|5007|Événement lorsque les paramètres sont modifiés|
|1125|Événement lorsque la protection du réseau se déclenche en mode audit|
|1126|Événement lorsque la protection réseau se déclenche en mode blocage|
|

## <a name="network-protection-and-the-tcp-three-way-handshake"></a>Protection du réseau et protocole d’handshake triple TCP

Avec la protection du réseau, la décision d’autoriser ou de bloquer l’accès à un site est prise après la fin de l’accord triple [via TCP/IP](/troubleshoot/windows-server/networking/three-way-handshake-via-tcpip). Par conséquent, lorsqu’un site est bloqué par la protection réseau, vous pouvez voir un type d’action en dessous dans le portail Microsoft 365 Defender, même si le `ConnectionSuccess` site a été réellement `NetworkConnectionEvents` bloqué. `NetworkConnectionEvents` sont signalés à partir de la couche TCP, et non à partir de la protection réseau. Une fois l’handshake triple terminée, l’accès au site est autorisé ou bloqué par la protection du réseau.

Voici un exemple de fonctionnement :

1. Supposons qu’un utilisateur tente d’accéder à un site web sur son appareil. Le site est hébergé sur un domaine dangereux et il doit être bloqué par la protection du réseau.  

2. La négociation triple via TCP/IP commence. Avant qu’elle ne se termine, une action est enregistrée `NetworkConnectionEvents` et est `ActionType` répertoriée comme `ConnectionSuccess` . Toutefois, dès que le processus d’handshake triple se termine, la protection du réseau bloque l’accès au site. Tout cela se produit très rapidement. Un processus similaire se produit avec [Microsoft Defender SmartScreen](/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-overview); C’est lorsque l’poignée de main triple est terminée qu’une détermination est prise et que l’accès à un site est bloqué ou autorisé.

3. Dans le portail Microsoft 365 Defender, une alerte est répertoriée dans la file [d’attente des alertes.](alerts-queue.md) Les détails de cette alerte sont les deux `NetworkConnectionEvents` et `AlertEvents` . Vous pouvez voir que le site a été bloqué, même si vous avez également un élément `NetworkConnectionEvents` avec l’actionType de `ConnectionSuccess` .

## <a name="considerations-for-windows-virtual-desktop-running-windows-10-enterprise-multi-session"></a>Considérations à prendre en compte Windows de bureau virtuel exécutant Windows 10 Entreprise multisess session

En raison de la nature multi-utilisateur de Windows 10 Entreprise, gardez les points suivants à l’esprit :

1. La protection réseau est une fonctionnalité à l’échelle de l’appareil qui ne peut pas être ciblée sur des sessions utilisateur spécifiques.

2. Les stratégies de filtrage de contenu Web sont également à l’échelle de l’appareil.

3. Si vous devez différencier les groupes d’utilisateurs, envisagez de créer des Windows et des affectations d’hôtes Virtual Desktop distincts.

4. Testez la protection réseau en mode audit pour évaluer son comportement avant de le déployer.

5. Envisagez de re resserger votre déploiement si vous avez un grand nombre d’utilisateurs ou un grand nombre de sessions multi-utilisateurs.

### <a name="alternative-option-for-network-protection"></a>Autre option pour la protection du réseau

Pour Windows 10 Entreprise multisession 1909 et plus, utilisée dans Windows Virtual Desktop sur Azure, la protection réseau pour Microsoft Edge peut être activée à l’aide de la méthode suivante :

1. Utilisez [Activer la protection réseau et](enable-network-protection.md) suivez les instructions pour appliquer votre stratégie.

2. Exécutez la commande PowerShell suivante : `Set-MpPreference -AllowNetworkProtectionOnWinServer 1`

## <a name="network-protection-troubleshooting"></a>Résolution des problèmes de protection du réseau

En raison de l’environnement dans lequel la protection réseau s’exécute, Microsoft peut ne pas être en mesure de détecter les paramètres proxy du système d’exploitation. Dans certains cas, les clients de protection réseau ne peuvent pas accéder au service Cloud. Pour résoudre le problème de connectivité, les clients titulaires d’une licence E5 doivent configurer l’une des clés de Registre Defender suivantes :

```console
reg add "HKLM\Software\Microsoft\Windows Defender" /v ProxyServer /d "<proxy IP address: Port>" /f
reg add "HKLM\Software\Microsoft\Windows Defender" /v ProxyPacUrl /d "<Proxy PAC url>" /f

```

## <a name="see-also"></a>Voir aussi

- [Évaluer les niveaux de protection](evaluate-network-protection.md) | Entreprendre un scénario rapide qui illustre le fonctionnement de la fonctionnalité et les événements qui seraient généralement créés.
- [Activer la protection réseau](enable-network-protection.md) | Utilisez une stratégie de groupe, PowerShell ou des CSP de gestion des stratégies de groupe pour activer et gérer la protection réseau dans votre réseau.
- [Configuration des fonctionnalités de réduction de la surface d’attaque dans Microsoft Intune](/mem/intune/protect/endpoint-security-asr-policy)
