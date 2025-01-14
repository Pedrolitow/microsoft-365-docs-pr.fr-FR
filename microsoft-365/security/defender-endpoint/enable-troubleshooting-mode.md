---
title: Prise en main du mode de résolution des problèmes dans Microsoft Defender pour point de terminaison
description: Activez le mode de résolution des problèmes Microsoft Defender pour point de terminaison pour résoudre différents problèmes antivirus.
keywords: antivirus, résolution des problèmes, mode de résolution des problèmes, protection contre les falsifications, compatibilité
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.service: microsoft-365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- tier2
ms.topic: conceptual
ms.subservice: mde
ms.openlocfilehash: bc93ecda200dc207f39c95a2e2ce3f3f97c2251c
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68628288"
---
# <a name="get-started-with-troubleshooting-mode-in-microsoft-defender-for-endpoint"></a>Prise en main du mode de résolution des problèmes dans Microsoft Defender pour point de terminaison 

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-configureendpointsscript-abovefoldlink)

Microsoft Defender pour point de terminaison mode de résolution des problèmes vous permet de résoudre les différents Microsoft Defender fonctionnalités antivirus en les activant à partir de l’appareil et en testant différents scénarios, même s’ils sont contrôlés par la stratégie d’organisation. Le mode de résolution des problèmes est désactivé par défaut et vous oblige à l’activer pour un appareil (et/ou un groupe d’appareils) pendant une durée limitée. Notez qu’il s’agit exclusivement d’une fonctionnalité d’entreprise et nécessite un accès Microsoft 365 Defender.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Utilisez le mode de dépannage pour désactiver/modifier le paramètre de protection contre les falsifications à effectuer :

  - Microsoft Defender résolution des problèmes fonctionnels de l’antivirus /compatibilité des applications (blocs d’application faux positifs).
  - Microsoft Defender résolution des problèmes de performances de l’antivirus en utilisant le mode de résolution des problèmes et en manipulant la protection contre les falsifications et d’autres paramètres antivirus.

- Si un événement de falsification se produit (par exemple, l’instantané est modifié ou supprimé), le `MpPreference` mode de résolution des problèmes se termine et la protection contre les falsifications est activée sur l’appareil.

- Les administrateurs locaux, avec les autorisations appropriées, peuvent modifier les configurations sur des points de terminaison individuels qui sont généralement verrouillés par la stratégie. Le fait d’avoir un appareil en mode de dépannage peut être utile lors du diagnostic de Microsoft Defender scénarios de performances et de compatibilité de l’antivirus.

  - Les administrateurs locaux ne pourront pas désactiver Microsoft Defender Antivirus ou le désinstaller.
  - Les administrateurs locaux pourront configurer tous les autres paramètres de sécurité dans la suite antivirus Microsoft Defender (par exemple, protection cloud, protection contre les falsifications).

- Les administrateurs disposant des autorisations « Gérer les paramètres de sécurité » ont accès au mode de résolution des problèmes.

- Microsoft Defender pour point de terminaison collecte les journaux et les données d’investigation tout au long du processus de résolution des problèmes.

  - `MpPreference` La capture instantanée sera prise avant le début du mode de dépannage.
  - La deuxième capture instantanée est effectuée juste avant l’expiration du mode de dépannage.
  - Les journaux opérationnels à partir du mode de résolution des problèmes seront également collectés.

  - Tous les journaux et instantanés ci-dessus seront collectés et seront disponibles pour qu’un administrateur puisse les collecter à l’aide de la fonctionnalité [Collecter le package d’enquête](respond-machine-alerts.md#collect-investigation-package-from-devices) sur la page de l’appareil. Notez que Microsoft ne supprimera pas ces données de l’appareil tant qu’un administrateur ne les aura pas collectées.

- Les administrateurs peuvent également passer en revue les modifications apportées aux paramètres qui ont lieu pendant le mode de résolution des problèmes dans **observateur d'événements** sur la page de l’appareil.

- Le mode de résolution des problèmes se désactive automatiquement après avoir atteint l’heure d’expiration (il dure 3 heures). Après l’expiration, toutes les configurations gérées par la stratégie redeviennent en lecture seule et reviennent à ce qu’elles étaient avant de définir le mode de résolution des problèmes.

- Il peut prendre jusqu’à 15 minutes entre le moment où la commande est envoyée à partir de Microsoft 365 Defender et le moment où elle devient active sur l’appareil.

- La notification est envoyée à l’utilisateur final lorsque le mode de résolution des problèmes commence et lorsque le mode de résolution des problèmes se termine. Un avertissement sera également envoyé pour l’informer qu’il se terminera bientôt.

- Le début et la fin du mode de résolution des problèmes sont identifiés dans la **chronologie** de l’appareil sur la page de l’appareil.

- Vous pouvez interroger tous les événements de mode de dépannage dans la chasse avancée.

> [!NOTE]
> Les modifications apportées à la gestion des stratégies sont appliquées à la machine lorsqu’elle est activement en mode de résolution des problèmes. Toutefois, les modifications n’entreront pas en vigueur tant que le mode de résolution des problèmes n’aura pas expiré. En outre, Microsoft Defender mises à jour de la plateforme antivirus ne seront pas appliquées pendant le mode de résolution des problèmes. Les mises à jour de plateforme seront appliquées une fois le mode de résolution des problèmes terminé par une mise à jour Windows.

## <a name="prerequisites"></a>Configuration requise

- Appareil exécutant Windows 10 (version 19044.1618 ou ultérieure), Windows 11, Windows Server 2019 ou Windows Server 2022.

  Semestre/Redstone|Version du système d'exploitation|Débloquer
  :---|:---|:---
  21H2/SV1|>=22000.593|[KB5011563 : Catalogue Microsoft Update](https://www.catalog.update.microsoft.com/Search.aspx?q=KB5011563)
  20H1/20H2/21H1|>=19042.1620<br/> >=19041.1620<br/> >=19043.1620|[KB5011543 : Catalogue Microsoft Update](https://www.catalog.update.microsoft.com/Search.aspx?q=KB5011543)
  Windows Server 2022|>=20348.617|[KB5011558 : Catalogue Microsoft Update](https://www.catalog.update.microsoft.com/Search.aspx?q=KB5011558)
  Windows Server 2019 (RS5)|>=17763.2746|[KB5011551 : Catalogue Microsoft Update](https://www.catalog.update.microsoft.com/Search.aspx?q=KB5011551)

- Le mode de résolution des problèmes est également disponible pour les machines exécutant la solution unifiée moderne pour Windows Server 2012 R2 et Windows Server 2016. Pendant le mode de dépannage, utilisez-le `Set-MPPreference -DisableTamperProtection $true` pour désactiver temporairement la protection contre les falsifications sur votre appareil et apporter les modifications de configuration nécessaires. Avant d’utiliser le mode de résolution des problèmes, vérifiez que tous les composants suivants sont à jour :

  - Sense version 10.8049.22439.1084 ou ultérieure ([KB5005292 : Catalogue Microsoft Update](https://www.catalog.update.microsoft.com/Search.aspx?q=KB5005292))

  - Antivirus Defender - Plateforme : 4.18.2207.7 ou version ultérieure ([KB4052623 : Catalogue Microsoft Update](https://www.catalog.update.microsoft.com/Search.aspx?q=KB4052623))

  - Antivirus Defender - Moteur : 1.1.19500.2 ou version ultérieure ([KB2267602 : Catalogue Microsoft Update](https://www.microsoft.com/en-us/wdsi/defenderupdates))

- Pour que le mode de dépannage soit appliqué, Microsoft Defender pour point de terminaison doit être inscrit par le locataire et actif sur l’appareil.

- L’appareil doit exécuter activement Microsoft Defender Antivirus, version 4.18.2203 ou ultérieure.

## <a name="enable-the-troubleshooting-mode"></a>Activer le mode de résolution des problèmes

1. Accédez au portail Microsoft 365 Defender (<https://security.microsoft.com>) et connectez-vous.

2. Accédez à la page de l’appareil/machine pour l’appareil que vous souhaitez activer le mode de résolution des problèmes. Sélectionnez **Activer le mode de résolution des problèmes**. Notez que cela nécessite des autorisations « Gérer les paramètres de sécurité dans Security Center » pour Microsoft Defender pour point de terminaison.

   :::image type="content" source="../../media/ts-mode-menu.png" alt-text="Activer le mode de résolution des problèmes" lightbox="../../media/ts-mode-menu.png":::

3. Vérifiez que vous souhaitez activer le mode de résolution des problèmes pour l’appareil.

   :::image type="content" source="../../media/ts-mode-conf-flyout.png" alt-text="Menu volant de configuration" lightbox="../../media/ts-mode-conf-flyout.png":::

4. La page de l’appareil indique que l’appareil est maintenant en mode de dépannage.

   :::image type="content" source="../../media/ts-mode-option-greyed-out.png" alt-text="L’appareil est maintenant en mode de dépannage" lightbox="../../media/ts-mode-option-greyed-out.png":::

## <a name="advanced-hunting-queries"></a>Requêtes de repérage avancées

Voici quelques requêtes de chasse avancées prédéfinies pour vous donner une visibilité sur les événements de dépannage qui se produisent dans votre environnement. Vous pouvez également utiliser ces requêtes pour [créer des règles de détection](/defender/custom-detection-rules.md#create-a-custom-detection-rule) qui vous alertent lorsque les appareils sont en mode de dépannage.

### <a name="get-troubleshooting-events-for-a-particular-device"></a>Obtenir des événements de dépannage pour un appareil particulier

Effectuez une recherche par deviceId ou deviceName en commentant les lignes respectives. 
 
```kusto
//let deviceName = "<deviceName>";   // update with device name
let deviceId = "<deviceID>";   // update with device id
DeviceEvents
| where DeviceId == deviceId
//| where DeviceName  == deviceName
| where ActionType == "AntivirusTroubleshootModeEvent"
| extend _tsmodeproperties = parse_json(AdditionalFields)
| project Timestamp,DeviceId, DeviceName, _tsmodeproperties,
 _tsmodeproperties.TroubleshootingState, _tsmodeproperties.TroubleshootingPreviousState, _tsmodeproperties.TroubleshootingStartTime,
 _tsmodeproperties.TroubleshootingStateExpiry, _tsmodeproperties.TroubleshootingStateRemainingMinutes,
 _tsmodeproperties.TroubleshootingStateChangeReason, _tsmodeproperties.TroubleshootingStateChangeSource
```

### <a name="devices-currently-in-troubleshooting-mode"></a>Appareils actuellement en mode de dépannage  

```kusto
DeviceEvents
| where ActionType == "AntivirusTroubleshootModeEvent"
| extend _tsmodeproperties = parse_json(AdditionalFields)
| where _tsmodeproperties.TroubleshootingStateChangeReason contains "started"
|summarize (Timestamp, ReportId)=arg_max(Timestamp, ReportId), count() by DeviceId
| order by Timestamp desc
```

### <a name="count-of-troubleshooting-mode-instances-by-device"></a>Nombre d’instances de mode de dépannage par appareil

```kusto
DeviceEvents
| where ActionType == "AntivirusTroubleshootModeEvent"
| extend _tsmodeproperties = parse_json(AdditionalFields)
| where Timestamp > ago(30d)  // choose the date range you want
| where _tsmodeproperties.TroubleshootingStateChangeReason contains "started"
| summarize (Timestamp, ReportId)=arg_max(Timestamp, ReportId), count() by DeviceId
| sort by count_
```

### <a name="total-count"></a>Nombre total

```kusto
DeviceEvents
| where ActionType == "AntivirusTroubleshootModeEvent"
| extend _tsmodeproperties = parse_json(AdditionalFields)
| where Timestamp > ago(2d) //beginning of time range
| where Timestamp < ago(1d) //end of time range
| where _tsmodeproperties.TroubleshootingStateChangeReason contains "started"
| summarize (Timestamp, ReportId)=arg_max(Timestamp, ReportId), count()
| where count_ > 5          // choose your max # of TS mode instances for your time range
```

## <a name="related-topic"></a>Rubrique connexe

- [Scénarios de mode de dépannage](troubleshooting-mode-scenarios.md)
- [Protéger les paramètres de sécurité avec la protection contre la falsifiation](prevent-changes-to-security-settings-with-tamper-protection.md)
