---
title: Utiliser la protection réseau pour empêcher les connexions à des sites défectueux
description: Protéger votre réseau en empêchant les utilisateurs d’accéder à des adresses réseau malveillantes et suspectes connues
keywords: Protection réseau, exploits, site web malveillant, ip, domaine, domaines, commande et contrôle, SmartScreen, notification toast
ms.service: microsoft-365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
ms.date: 10/20/2022
audience: ITPro
author: denisebmsft
ms.author: deniseb
ms.reviewer: oogunrinde
manager: dansimp
ms.custom: asr
ms.subservice: mde
ms.topic: overview
ms.collection:
- m365-security
- tier2
search.appverid: met150
ms.openlocfilehash: 99d1d4bfbbce6a010f9823071b2c3be8920aa409
ms.sourcegitcommit: ab45f2963e0635ff2cb9670f6f7b4c784f6a250e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/02/2022
ms.locfileid: "68815548"
---
# <a name="protect-your-network"></a>Protéger votre réseau

**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- Antivirus Microsoft Defender

**Plateformes**

- Windows
- macOS
- Linux

Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

## <a name="overview-of-network-protection"></a>Vue d’ensemble de la protection réseau

La protection réseau permet de protéger les appareils contre les événements Basés sur Internet. La protection réseau est une fonctionnalité de réduction de la surface d’attaque. Il permet d’empêcher les employés d’accéder à des domaines dangereux par le biais d’applications. Les domaines qui hébergent des escroqueries par hameçonnage, des attaques et d’autres contenus malveillants sur Internet sont considérés comme dangereux. La protection réseau étend l’étendue de [Microsoft Defender SmartScreen](/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-overview) pour bloquer tout le trafic HTTP sortant qui tente de se connecter à des sources de mauvaise réputation (en fonction du domaine ou du nom d’hôte).

La protection réseau étend la protection dans la [protection web](web-protection-overview.md) au niveau du système d’exploitation et est un composant principal pour le filtrage de contenu web (WCF). Il fournit la fonctionnalité de protection web de Microsoft Edge à d’autres navigateurs pris en charge et applications non-navigateur. La protection réseau offre également une visibilité et un blocage des indicateurs de compromission (ICS) lorsqu’ils sont utilisés avec la [détection et la réponse des points de terminaison](overview-endpoint-detection-response.md). Par exemple, la protection réseau fonctionne avec vos [indicateurs personnalisés](manage-indicators.md) que vous pouvez utiliser pour bloquer des domaines ou des noms d’hôtes spécifiques.

### <a name="network-protection-coverage"></a>Couverture de la protection réseau

Le tableau suivant récapitule les zones de protection réseau de couverture.

| Fonctionnalité | Microsoft Edge | Navigateurs tiers | Processus non-navigateur <br> (par exemple, PowerShell) |
|:---|:---|:---|:---|
| Protection contre les menaces web | SmartScreen doit être activé | Np doit être en mode bloc | Np doit être en mode bloc |
| Indicateurs personnalisés | SmartScreen doit être activé | Np doit être en mode bloc | Np doit être en mode bloc |
| Filtrage de contenu web | SmartScreen doit être activé | Np doit être en mode bloc | Non pris en charge |

> [!NOTE]
> La protection réseau ne surveille pas msedge.exe sur les appareils Windows.
> Pour Mac et Linux, vous devez disposer d’une protection réseau en mode bloc pour obtenir la prise en charge de ces fonctionnalités dans Edge.
> Pour les processus autres que Microsoft Edge et Internet Explorer, les scénarios de protection web tirent parti de la protection réseau pour l’inspection et l’application :
> - L’adresse IP est prise en charge pour les trois protocoles (TCP, HTTP et HTTPS (TLS)).
> - Seules les adresses IP uniques sont prises en charge (aucun bloc CIDR ou plage d’adresses IP) dans les indicateurs personnalisés.
> - Les URL chiffrées (chemin d’accès complet) ne peuvent être bloquées que sur les navigateurs internes (Internet Explorer, Edge).
> - Les URL chiffrées (FQDN uniquement) peuvent être bloquées dans les navigateurs tiers (c’est-à-dire autres qu’Internet Explorer, Edge).
> - Les blocs de chemin d’URL complets peuvent être appliqués pour les URL non chiffrées.
>
> Il peut y avoir jusqu’à 2 heures de latence (généralement moins) entre le moment où l’action est effectuée et le blocage de l’URL et de l’adresse IP.

Regardez cette vidéo pour découvrir comment la protection réseau permet de réduire la surface d’attaque de vos appareils contre les escroqueries par hameçonnage, les attaques et d’autres contenus malveillants.
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4r4yZ]

## <a name="requirements-for-network-protection"></a>Configuration requise pour la protection du réseau

La protection réseau nécessite Windows 10 ou 11 (Professionnel ou Entreprise), Windows Server version 1803 ou ultérieure, macOS version 11 ou ultérieure, ou les versions Linux prises en charge par Defender, et Microsoft Defender protection antivirus en temps réel.

| Version de Windows | Antivirus Microsoft Defender |
|:---|:---|
| Windows 10 version 1709 ou ultérieure, Windows 11, Windows Server 1803 ou version ultérieure | [Assurez-vous que la protection en temps réel Microsoft Defender Antivirus](configure-real-time-protection-microsoft-defender-antivirus.md) et la [protection fournie par le cloud](enable-cloud-protection-microsoft-defender-antivirus.md) sont activées (actives) |
| Windows Server 2012 R2 et Windows Server 2016 avec l’agent unifié | Mise à jour de la plateforme version 4.18.2001.x.x ou ultérieure |

## <a name="why-network-protection-is-important"></a>Pourquoi la protection réseau est importante

La protection réseau fait partie du groupe de solutions de réduction de la surface d’attaque dans Microsoft Defender pour point de terminaison. La protection réseau permet de superposer la couche réseau d’URL de blocage et d’adresses IP. La protection réseau peut empêcher l’accès aux URL à l’aide de certains navigateurs et connexions réseau standard. Par défaut, la protection réseau protège vos ordinateurs contre les URL malveillantes connues à l’aide du flux SmartScreen, qui bloque les URL malveillantes d’une manière similaire à SmartScreen dans le navigateur Microsoft Edge. La fonctionnalité de protection réseau peut être étendue à :

- Bloquer les adresses IP/URL de votre propre renseignement sur les menaces ([indicateurs](indicator-ip-domain.md))
- Bloquer les services non approuvés de [Microsoft Defender for Cloud Apps](/defender-cloud-apps/what-is-defender-for-cloud-apps)
- Bloquer les sites en fonction de la catégorie ([filtrage de contenu web](web-content-filtering.md))

La protection réseau est une partie essentielle de la pile de protection et de réponse Microsoft.

> [!TIP]
> Pour plus d’informations sur la protection réseau pour Windows Server, Linux, MacOS et Mobile Threat Defense (MTD), consultez [La chasse proactive aux menaces avec la chasse avancée](advanced-hunting-overview.md).

### <a name="block-command-and-control-attacks"></a>Bloquer les attaques de commande et de contrôle

Les ordinateurs serveur de commande et de contrôle (C2) sont utilisés par des utilisateurs malveillants pour envoyer des commandes à des systèmes compromis par des programmes malveillants, puis exercer un certain type de contrôle sur les systèmes compromis. Les attaques C2 se cachent généralement dans les services cloud tels que le partage de fichiers et les services de messagerie web, ce qui permet aux serveurs C2 d’éviter la détection en se mêlant au trafic classique.

Les serveurs C2 peuvent être utilisés pour lancer des commandes qui peuvent :

- Voler des données (par exemple, par hameçonnage)
- Contrôler les ordinateurs compromis dans un botnet
- Interrompre les applications légitimes
- Diffuser des programmes malveillants, tels que des rançongiciels

Le composant de protection réseau de Defender pour point de terminaison identifie et bloque les connexions aux infrastructures C2 utilisées dans les attaques par ransomware gérées par l’homme, à l’aide de techniques telles que l’apprentissage automatique et l’identification intelligente des indicateurs de compromission (IoC).

#### <a name="network-protection-c2-detection-and-remediation"></a>Protection réseau : détection et correction C2

Dans sa forme initiale, le ransomware est une menace de base, préprogrammée et axée sur des résultats limités et spécifiques (par exemple, le chiffrement d’un ordinateur). Toutefois, les rançongiciels ont évolué en une menace sophistiquée pilotée par l’homme, adaptative et axée sur des résultats à plus grande échelle et plus répandus, comme la conservation des ressources ou des données d’une organisation entière contre rançon.

La prise en charge des serveurs de commande et de contrôle (C2) est un élément clé de cette évolution des ransomwares et permet à ces attaques de s’adapter à l’environnement qu’elles ciblent. La rupture du lien avec l’infrastructure de commande et de contrôle arrête la progression d’une attaque à l’étape suivante. Pour plus d’informations sur la détection et la correction de C2, consultez [Détection et correction des attaques de commande et de contrôle au niveau de la couche réseau](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/detecting-and-remediating-command-and-control-attacks-at-the/ba-p/3650607).

#### <a name="network-protection-new-toast-notifications"></a>Protection réseau : nouvelles notifications toast

| Nouveau mappage  | Catégorie de réponse  | Sources |
| :--- | :--- | :--- |
| hameçonnage | Hameçonnage | Smartscreen |
| Malveillants | Malveillant | Smartscreen |
| commande et contrôle | C2 | Smartscreen |
| commande et contrôle | COCO | Smartscreen |
| Malveillants | Non approuvé | Smartscreen |
| par votre administrateur informatique | CustomBlockList |   |
| par votre administrateur informatique | CustomPolicy |   |

> [!NOTE]
> **customAllowList** ne génère pas de notifications sur les points de terminaison.

### <a name="new-notifications-for-network-protection-determination"></a>Nouvelles notifications pour la détermination de la protection réseau

Une nouvelle fonctionnalité de protection réseau disponible publiquement utilise des fonctions dans SmartScreen pour bloquer les activités d’hameçonnage à partir de sites de commande et de contrôle malveillants.

Lorsqu’un utilisateur final tente de visiter un site web dans un environnement dans lequel la protection réseau est activée, trois scénarios sont possibles :

- L’URL a une **bonne réputation connue** : dans ce cas, l’accès est autorisé à l’utilisateur sans obstruction, et aucune notification toast n’est présentée sur le point de terminaison. En effet, le domaine ou l’URL est défini sur _Autorisé_.
- L’URL a une **réputation inconnue ou incertaine** : l’accès de l’utilisateur est bloqué, mais avec la possibilité de contourner (débloquer) le bloc. En effet, le domaine ou l’URL est défini sur _Audit_.
- L’URL a une **mauvaise réputation connue (malveillante)** : l’utilisateur n’est pas autorisé à y accéder. En effet, le domaine ou l’URL est défini sur _Bloquer_.

#### <a name="warn-experience"></a>Expérience d’avertissement

Un utilisateur visite un site web :

- Si l’URL a une réputation inconnue ou incertaine, une notification toast présente à l’utilisateur les options suivantes :

  - **OK** : la notification toast est publiée (supprimée) et la tentative d’accès au site est terminée.
  - **Débloquer** : l’utilisateur n’a pas besoin d’accéder au portail Windows Defender Security Intelligence (WDSI) pour accéder au site. L’utilisateur aura accès au site pendant 24 heures; à ce moment-là, le bloc est réactivé pendant 24 heures supplémentaires. L’utilisateur peut continuer à utiliser **Unblock** pour accéder au site jusqu’à ce que l’administrateur interdise (bloque) le site, supprimant ainsi l’option **Deblock**.
  - **Commentaires** : la notification toast présente à l’utilisateur un lien pour envoyer un ticket, que l’utilisateur peut utiliser pour envoyer des commentaires à l’administrateur dans le but de justifier l’accès au site.

    :::image type="content" source="images/network-protection-phishing-warn-2.png" alt-text="Affiche une notification d’avertissement de contenu d’hameçonnage de protection réseau.":::

  > [!NOTE]
  > Les images présentées ici pour l’expérience d’avertissement et l’expérience de blocage (ci-dessous) répertorient « **URL bloquée »** comme exemple de texte d’espace réservé ; dans un environnement fonctionnel, l’URL ou le domaine réel est répertorié.  

#### <a name="block-experience"></a>Expérience de blocage

Un utilisateur visite un site web :

- Si l’URL a une mauvaise réputation, une notification toast présente à l’utilisateur les options suivantes :
  - **D'accord** La notification toast est publiée (supprimée) et la tentative d’accès au site est terminée.
  - **Commentaires** La notification toast présente à l’utilisateur un lien pour envoyer un ticket, que l’utilisateur peut utiliser pour envoyer des commentaires à l’administrateur dans le but de justifier l’accès au site.

    :::image type="content" source="images/network-protection-phishing-blocked.png" alt-text="Affiche une notification de blocage du contenu d’hameçonnage connu de protection réseau." lightbox="images/network-protection-phishing-blocked.png":::

## <a name="smartscreen-unblock"></a>Déblocage SmartScreen

Avec les indicateurs dans Defender pour point de terminaison, les administrateurs peuvent autoriser les utilisateurs finaux à contourner les avertissements générés pour certaines URL et adresses IP. Selon la raison pour laquelle l’URL a été bloquée, lorsqu’un bloc SmartScreen est rencontré, il peut offrir aux administrateurs la possibilité de débloquer le site pendant 24 heures maximum. Dans ce cas, une notification toast Sécurité Windows s’affiche, permettant à l’utilisateur final de **débloquer** l’URL ou l’adresse IP pendant la période définie.  

:::image type="content" source="images/network-protection-smart-screen-block-notification.png" alt-text="notification Sécurité Windows pour la protection réseau.":::

Microsoft Defender pour point de terminaison administrateurs peuvent configurer la fonctionnalité de déblocage SmartScreen dans le [portail Microsoft 365 Defender](https://security.microsoft.com) à l’aide d’un indicateur « autoriser » pour les adresses IP, les URL et les domaines.

:::image type="content" source="images/network-protection-smart-screen-block-configuration.png" alt-text="Formulaire ULR et IP de configuration de la protection réseau SmartScreen.":::

Consultez [Créer des indicateurs pour les adresses IP et les URL/domaines](indicator-ip-domain.md).

## <a name="using-network-protection"></a>Utilisation de la protection réseau

La protection réseau est activée par appareil, ce qui est généralement effectué à l’aide de votre infrastructure de gestion. Pour connaître les méthodes prises en charge, consultez [Activer la protection réseau](enable-network-protection.md).

> [!NOTE]
> Microsoft Defender Antivirus doit être actif pour activer la protection réseau.

Vous pouvez activer la protection réseau en mode **Audit** ou **En mode Bloc** . Si vous souhaitez évaluer l’impact de l’activation de la protection réseau avant de bloquer réellement les adresses IP ou les URL, vous pouvez activer la protection réseau en mode Audit pendant un certain temps pour collecter des données sur ce qui serait bloqué. Journaux du mode Audit lorsque les utilisateurs finaux se sont connectés à une adresse ou à un site qui aurait autrement été bloqué par la protection réseau. Notez que pour que les indicateurs de compromission (IoC) ou de filtrage de contenu Web (WCF) fonctionnent, la protection réseau doit être en « mode Bloc ».

Pour plus d’informations sur la protection réseau pour Linux et macOS, consultez Protection [réseau pour Linux](network-protection-linux.md) et [Protection réseau pour macOS](network-protection-macos.md).

## <a name="advanced-hunting"></a>Recherche avancée de menaces

Si vous utilisez la chasse avancée pour identifier les événements d’audit, vous aurez jusqu’à 30 jours d’historique disponible à partir de la console. Voir [Repérage avancé](advanced-hunting-overview.md).

Vous trouverez les données d’audit dans **Repérage avancé** dans le portail Defender pour point de terminaison ([https://security.microsoft.com](https://security.microsoft.com)).  

Les événements se trouvent dans DeviceEvents avec un ActionType de `ExploitGuardNetworkProtectionAudited`. Les blocs sont affichés par `ExploitGuardNetworkProtectionBlocked`.  

L’exemple suivant inclut les actions bloquées :

```kusto

DeviceEvents
|where ActionType in ('ExploitGuardNetworkProtectionAudited','ExploitGuardNetworkProtectionBlocked')

```

:::image type="content" source="images/network-protection-advanced-hunting.png" alt-text="Repérage avancé pour l’audit et l’identification des événements." lightbox="images/network-protection-advanced-hunting.png":::

> [!TIP]
> Ces entrées contiennent des données dans la colonne **AdditionalFields** , ce qui vous donne d’excellentes informations sur l’action. Si vous développez **AdditionalFields** , vous pouvez également obtenir les champs : **IsAudit**, **ResponseCategory** et **DisplayName**.

Voici un autre exemple :

```kusto

DeviceEvents:

|where ActionType contains "ExploitGuardNetworkProtection"
|extend ParsedFields=parse_json(AdditionalFields)
|project DeviceName, ActionType, Timestamp, RemoteUrl, InitiatingProcessFileName, IsAudit=tostring(ParsedFields.IsAudit), ResponseCategory=tostring(ParsedFields.ResponseCategory), DisplayName=tostring(ParsedFields.DisplayName)
|sort by Timestamp desc

```

La catégorie Réponse vous indique la cause de l’événement, par exemple :

| ResponseCategory | Fonctionnalité responsable de l’événement |
|:---|:---|
| CustomPolicy |  Wcf  |
| CustomBlockList  |   Indicateurs personnalisés   |
| CasbPolicy   |   Defender for Cloud Apps   |
| Malveillant   |   Menaces web  |
| Hameçonnage  |   Menaces web  |

Pour plus d’informations, consultez [Résoudre les problèmes liés aux blocs de point de terminaison](web-protection-overview.md#troubleshoot-endpoint-blocks).

Vous pouvez utiliser la liste des URL et adresses IP obtenue pour déterminer ce qui aurait été bloqué si l’appareil était en mode bloc et quelle fonctionnalité les a bloqués. Passez en revue chaque élément de la liste pour identifier les URL ou les adresses IP nécessaires à votre environnement. Si vous trouvez des entrées auditées qui sont critiques pour votre environnement, créez un indicateur pour les autoriser dans votre réseau. Autoriser les indicateurs URL/IP sont prioritaires sur n’importe quel bloc.

Une fois que vous avez créé un indicateur, vous pouvez examiner la résolution du problème sous-jacent :

- SmartScreen : demande de révision
- Indicateur : modifier l’indicateur existant
- MCA : passer en revue l’application non approuvée
- WCF : recatégorisation des demandes

À l’aide de ces données, vous pouvez prendre une décision éclairée sur l’activation de la protection réseau en mode Bloc. Consultez [Ordre de priorité pour les blocs de protection réseau](web-protection-overview.md#order-of-precedence).

> [!NOTE]
> Comme il s’agit d’un paramètre par appareil s’il existe des appareils qui ne peuvent pas passer en mode Bloquer, vous pouvez simplement les laisser sur audit jusqu’à ce que vous puissiez corriger le défi et recevoir les événements d’audit.

Pour plus d’informations sur la façon de signaler les faux positifs, consultez [Signaler des faux positifs](web-protection-overview.md#report-false-positives).

Pour plus d’informations sur la création de vos propres rapports Power BI, consultez [Créer des rapports personnalisés à l’aide de Power BI](api-power-bi.md).

## <a name="configuring-network-protection"></a>Configuration de la protection réseau

Pour plus d’informations sur l’activation de la protection réseau, consultez **[Activer la protection réseau](enable-network-protection.md)**. Utilisez stratégie de groupe, PowerShell ou les fournisseurs de services de configuration GPM pour activer et gérer la protection réseau dans votre réseau.

Une fois que vous avez activé les services, vous devrez peut-être configurer votre réseau ou votre pare-feu pour autoriser les connexions entre les services et vos appareils (également appelés points de terminaison).

- `.smartscreen.microsoft.com`
- `.smartscreen-prod.microsoft.com`

## <a name="viewing-network-protection-events"></a>Affichage des événements de protection réseau

La protection réseau fonctionne mieux avec [Microsoft Defender pour point de terminaison](microsoft-defender-endpoint.md), qui vous donne des rapports détaillés sur les événements et les blocages de protection contre les attaques dans le cadre de [scénarios d’investigation d’alerte](investigate-alerts.md).

Lorsque la protection réseau bloque une connexion, une notification s’affiche à partir du Centre de notifications. Votre équipe des opérations de sécurité peut [personnaliser la notification](attack-surface-reduction-rules-deployment-implement.md#customize-attack-surface-reduction-rules) avec les détails et les informations de contact de votre organisation. En outre, des règles individuelles de réduction de la surface d’attaque peuvent être activées et personnalisées pour s’adapter à certaines techniques à surveiller.

Vous pouvez également utiliser le [mode audit](audit-windows-defender.md) pour évaluer l’impact de la protection réseau sur votre organisation si elle était activée.

## <a name="review-network-protection-events-in-the-microsoft-365-defender-portal"></a>Passer en revue les événements de protection réseau dans le portail Microsoft 365 Defender

Defender pour point de terminaison fournit des rapports détaillés sur les événements et les blocs dans le cadre de ses [scénarios d’investigation des alertes](investigate-alerts.md). Vous pouvez afficher ces détails dans le portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) dans la [file d’attente des alertes](review-alerts.md) ou en utilisant la [chasse avancée](advanced-hunting-overview.md). Si vous utilisez le [mode audit](audit-windows-defender.md), vous pouvez utiliser la chasse avancée pour voir comment les paramètres de protection réseau affectent votre environnement s’ils étaient activés.

Voici un exemple de requête pour la chasse avancée :

```kusto

DeviceNetworkEvents
|where ActionType in ('ExploitGuardNetworkProtectionAudited','ExploitGuardNetworkProtectionBlocked')

```

## <a name="review-network-protection-events-in-windows-event-viewer"></a>Passer en revue les événements de protection réseau dans Windows observateur d'événements

Vous pouvez consulter le journal des événements Windows pour voir les événements créés lorsque la protection réseau bloque (ou audite) l’accès à une adresse IP ou à un domaine malveillant :

1. [Copiez directement le code XML](event-views.md).

2. Sélectionnez **OK**.

Cette procédure crée une vue personnalisée qui filtre pour afficher uniquement les événements suivants liés à la protection réseau :

|ID d’événement|Description|
|---|---|
|5007|Événement lorsque les paramètres sont modifiés|
|1125|Événement lors du déclenchement de la protection réseau en mode audit|
|1126|Événement lorsque la protection réseau se déclenche en mode bloc|

## <a name="network-protection-and-the-tcp-three-way-handshake"></a>Protection réseau et établissement d’une liaison tcp triple

Avec la protection réseau, la détermination de l’autorisation ou du blocage de l’accès à un site est effectuée après la fin de l’établissement [d’une liaison triple via TCP/IP](/troubleshoot/windows-server/networking/three-way-handshake-via-tcpip). Ainsi, lorsqu’un site est bloqué par la protection réseau, vous pouvez voir un type d’action sous `ConnectionSuccess` `NetworkConnectionEvents` dans le portail Microsoft 365 Defender, même si le site a été bloqué. `NetworkConnectionEvents` sont signalés à partir de la couche TCP, et non à partir de la protection réseau. Une fois la négociation triple terminée, l’accès au site est autorisé ou bloqué par la protection réseau.

Voici un exemple de fonctionnement :

1. Supposons qu’un utilisateur tente d’accéder à un site web sur son appareil. Le site est hébergé sur un domaine dangereux et doit être bloqué par la protection réseau.  

2. L’établissement d’une liaison triple via TCP/IP commence. Avant qu’elle ne se termine, une `NetworkConnectionEvents` action est journalisée et son `ActionType` est répertorié en tant que `ConnectionSuccess`. Toutefois, dès que le processus de négociation triple est terminé, la protection réseau bloque l’accès au site. Tout cela se produit rapidement. Un processus similaire se produit avec [Microsoft Defender SmartScreen](/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-overview) ; c’est lorsque la négociation tridirectionnel se termine qu’une détermination est effectuée et que l’accès à un site est bloqué ou autorisé.

3. Dans le portail Microsoft 365 Defender, une alerte est répertoriée dans la [file d’attente des alertes](alerts-queue.md). Les détails de cette alerte incluent à la fois `NetworkConnectionEvents` et `AlertEvents`. Vous pouvez voir que le site a été bloqué, même si vous avez également un `NetworkConnectionEvents` élément avec l’ActionType de `ConnectionSuccess`.

## <a name="considerations-for-windows-virtual-desktop-running-windows-10-enterprise-multi-session"></a>Considérations relatives au bureau virtuel Windows exécuté Windows 10 Entreprise multisession

En raison de la nature multi-utilisateur de Windows 10 Entreprise, gardez les points suivants à l’esprit :

1. La protection réseau est une fonctionnalité à l’échelle de l’appareil qui ne peut pas être ciblée sur des sessions utilisateur spécifiques.

2. Les stratégies de filtrage de contenu web sont également à l’échelle de l’appareil.

3. Si vous devez différencier les groupes d’utilisateurs, envisagez de créer des pools d’hôtes Windows Virtual Desktop distincts et des affectations.

4. Testez la protection réseau en mode audit pour évaluer son comportement avant le déploiement.

5. Envisagez de redimensionner votre déploiement si vous avez un grand nombre d’utilisateurs ou un grand nombre de sessions multi-utilisateurs.

### <a name="alternative-option-for-network-protection"></a>Autre option pour la protection réseau

Pour le client MDE unifié Windows Server 2012R2/2016, Windows Server version 1803 ou ultérieure, Windows Server 2019 ou version ultérieure, et Windows 10 Entreprise multisession 1909 et versions ultérieures, utilisées dans Windows Virtual Desktop sur Azure, la protection réseau pour Microsoft Edge peut être activée à l’aide de la méthode suivante :

1. Utilisez [Activer la protection réseau](enable-network-protection.md) et suivez les instructions pour appliquer votre stratégie.

2. Exécutez les commandes PowerShell suivantes :

   - `Set-MpPreference -EnableNetworkProtection Enabled`
   - `Set-MpPreference -AllowNetworkProtectionOnWinServer 1`
   - `Set-MpPreference -AllowNetworkProtectionDownLevel 1`
   - `Set-MpPreference -AllowDatagramProcessingOnWinServer 1`

> [!NOTE]
> Dans certains cas, en fonction de votre infrastructure, du volume de trafic et d’autres conditions, `Set-MpPreference -AllowDatagramProcessingOnWinServer 1` peut avoir un effet sur les performances du réseau.

### <a name="network-protection-for-windows-servers"></a>Protection réseau pour les serveurs Windows

Voici des informations spécifiques aux serveurs Windows.

#### <a name="verify-that-network-protection-is-enabled"></a>Vérifier que la protection réseau est activée

Vérifiez si la protection réseau est activée sur un appareil local à l’aide de l’Éditeur du Registre.

1. Sélectionnez le bouton **Démarrer** dans la barre des tâches et tapez **regedit** pour ouvrir l’Éditeur du Registre.
1. Sélectionnez **HKEY_LOCAL_MACHINE** dans le menu latéral.
1. Naviguez dans les menus imbriqués jusqu’à **Stratégies LOGICIELLEs** >  >  **Microsoft** > **Windows defender** >  **Windows Defender Exploit Guard** > **Network Protection**.

   (Si la clé n’est pas présente, accédez à **LOGICIEL** >  **Microsoft** >   >  Windows Defender **Windows Defender Exploit Guard** > **Network Protection**)

4. Sélectionnez **ActiverRéseauProtection** pour voir l’état actuel de la protection réseau sur l’appareil :

   - 0 = Désactivé
   - 1 = Activé (activé)
   - 2 = mode Audit

Pour plus d’informations, consultez : [Activer la protection réseau](enable-network-protection.md)

##### <a name="network-protection-suggestion"></a>Suggestion de protection réseau

Pour le client MDE unifié Windows Server 2012/2016, Windows Server version 1803 ou ultérieure, Windows Server 2019 ou version ultérieure, et Windows 10 Entreprise multisession 1909 et versions ultérieures (utilisées dans Windows Virtual Desktop sur Azure), des clés de Registre supplémentaires doivent être activées :

**HKEY_LOCAL_MACHINE**\* *LOGICIEL**\** Stratégies **\**Microsoft**\* *Windows Defender**\** Windows Defender Exploit Guard **\**Protection réseau**

**AllowNetworkProtectionDownLevel** (dword) 1 (hex) **AllowNetworkProtectionOnWinServer** (dword) 1 (hex) **EnableNetworkProtection** (dword) 1 (hex)

> [!NOTE]
> En fonction de votre infrastructure, du volume de trafic et d’autres conditions, **HKEY_LOCAL_MACHINE**\\ les **stratégies**\\**LOGICIELLEs**\\**Microsoft**\\ **Windows Defender** \\**NIS****Consumers**\\**IPS** - \\**AllowDatagramProcessingOnWinServer (dword) 1 (hex)** peuvent avoir un effet sur les performances du réseau.

Pour plus d’informations, consultez : [Activer la protection réseau](enable-network-protection.md)

#### <a name="windows-servers-and-windows-multi-session-configuration-requires-powershell"></a>La configuration des serveurs Windows et windows multisession nécessite PowerShell

Pour les serveurs Windows et Windows Multisession, vous devez activer des éléments supplémentaires à l’aide des applets de commande PowerShell. Pour le client MDE unifié Windows Server 2012/2016, Windows Server version 1803 ou ultérieure, Windows Server 2019 ou version ultérieure, et Windows 10 Entreprise multisession 1909 et versions ultérieures, utilisés dans Windows Virtual Desktop sur Azure.

1. Set-MpPreference -EnableNetworkProtection Enabled
1. Set-MpPreference -AllowNetworkProtectionOnWinServer 1
1. Set-MpPreference -AllowNetworkProtectionDownLevel 1
1. Set-MpPreference -AllowDatagramProcessingOnWinServer 1

> [!NOTE]
> Dans certains cas, en fonction de votre infrastructure, du volume de trafic et d’autres conditions, **Set-MpPreference -AllowDatagramProcessingOnWinServer 1** peut avoir un effet sur les performances du réseau.


## <a name="network-protection-troubleshooting"></a>Résolution des problèmes de protection réseau

En raison de l’environnement dans lequel la protection réseau s’exécute, Microsoft peut ne pas être en mesure de détecter les paramètres de proxy du système d’exploitation. Dans certains cas, les clients de protection réseau ne peuvent pas atteindre le service cloud. Pour résoudre le problème de connectivité, [configurez un proxy statique pour Microsoft Defender Antivirus](configure-proxy-internet.md#configure-a-static-proxy-for-microsoft-defender-antivirus).

## <a name="optimizing-network-protection-performance"></a>Optimisation des performances de protection réseau

La protection réseau dispose désormais d’une optimisation des performances qui permet au mode Bloc de commencer à inspecter de façon asynchrone les connexions longues une fois qu’elles ont été validées et autorisées par SmartScreen, ce qui peut offrir une réduction potentielle du coût de l’inspection sur la bande passante et peut également aider à résoudre les problèmes de compatibilité des applications. Cette fonctionnalité d’optimisation est activée par défaut. Vous pouvez désactiver cette fonctionnalité à l’aide de l’applet de commande PowerShell suivante :

`Set-MpPreference -AllowSwitchToAsyncInspection $false`

## <a name="see-also"></a>Voir aussi

- [Évaluer les | de protection réseau](evaluate-network-protection.md) Exécutez un scénario rapide qui montre comment la fonctionnalité fonctionne et quels événements seraient généralement créés.
- [Activer la protection réseau](enable-network-protection.md) | Utilisez stratégie de groupe, PowerShell ou les fournisseurs de services de configuration GPM pour activer et gérer la protection réseau dans votre réseau.
- [Configuration des fonctionnalités de réduction de la surface d’attaque dans Microsoft Intune](/mem/intune/protect/endpoint-security-asr-policy)
- [Protection réseau pour les | Linux](network-protection-linux.md) Pour en savoir plus sur l’utilisation de la protection réseau Microsoft pour les appareils Linux.
- [Protection réseau pour les | macOS](network-protection-macos.md) Pour en savoir plus sur la protection réseau Microsoft pour macOS
