---
title: Examiner des événements de connexion qui se produisent d’arrière vers l’avant des proxys
description: Découvrez comment utiliser la surveillance avancée au niveau HTTP par le biais de la protection réseau dans Microsoft Defender ATP, qui utilise une cible réelle, au lieu d’un proxy.
keywords: proxy, protection réseau, proxy avant, événements réseau, audit, bloc, noms de domaine, domaine
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 28d8a113ed77e9624bd914571b1af4a7ece2aa5c
ms.sourcegitcommit: 987f70e44e406ab6b1dd35f336a9d0c228032794
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2021
ms.locfileid: "51587562"
---
# <a name="investigate-connection-events-that-occur-behind-forward-proxies"></a>Examiner des événements de connexion qui se produisent d’arrière vers l’avant des proxys

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez faire l’expérience de Defender pour point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-investigatemachines-abovefoldlink)

Defender pour le point de terminaison prend en charge la surveillance des connexions réseau à partir de différents niveaux de la pile réseau. Un cas difficile est celui où le réseau utilise un proxy avant comme passerelle vers Internet.

Le proxy agit comme s’il s’agissait du point de terminaison cible.  Dans ce cas, les moniteurs de connexion réseau simples auditent les connexions avec le proxy, ce qui est correct mais qui a une valeur d’investigation inférieure. 

Defender pour le point de terminaison prend en charge la surveillance avancée au niveau HTTP via la protection réseau. Lorsqu’il est allumé, un nouveau type d’événement est exposé, qui expose les noms de domaine cibles réels.

## <a name="use-network-protection-to-monitor-network-connection-behind-a-firewall"></a>Utiliser la protection réseau pour surveiller la connexion réseau derrière un pare-feu
La surveillance de la connexion réseau derrière un proxy avant est possible en raison d’événements réseau supplémentaires qui proviennent de la protection du réseau. Pour les voir sur une chronologie d’appareil, activer la protection réseau (au minimum en mode audit). 

La protection réseau peut être contrôlée à l’aide des modes suivants :

- **Bloquer** <br> Les utilisateurs ou les applications ne pourront pas se connecter à des domaines dangereux. Vous pourrez voir cette activité dans le Centre de sécurité Microsoft Defender.
- **Audit** <br> La connexion à des domaines dangereux ne sera pas bloquée pour les utilisateurs ou les applications. Toutefois, vous verrez toujours cette activité dans le Centre de sécurité Microsoft Defender.


Si vous désactiver la protection réseau, les utilisateurs ou les applications ne seront pas bloqués pour se connecter à des domaines dangereux. Vous ne verrez aucune activité réseau dans le Centre de sécurité Microsoft Defender.

Si vous ne la configurez pas, le blocage du réseau est désactivé par défaut.

Pour plus d’informations, voir [Activer la protection réseau.](enable-network-protection.md)

## <a name="investigation-impact"></a>Impact de l’examen
Lorsque la protection réseau est allumée, vous verrez que, sur la chronologie d’un appareil, l’adresse IP continuera à représenter le proxy, tandis que l’adresse cible réelle s’affiche.

![Image des événements réseau sur la chronologie de l’appareil](images/atp-proxy-investigation.png)

D’autres événements déclenchés par la couche de protection réseau sont désormais disponibles pour faire surface des noms de domaine réels, même derrière un proxy.

Informations sur l’événement :

![Image d’un événement réseau unique](images/atp-proxy-investigation-event.png)



## <a name="hunt-for-connection-events-using-advanced-hunting"></a>Recherche des événements de connexion à l’aide de la recherche avancée 
Tous les nouveaux événements de connexion sont également disponibles pour la recherche avancée. Étant donné que ces événements sont des événements de connexion, vous pouvez les trouver sous la table DeviceNetworkEvents sous le `ConnecionSuccess` type d’action.

L’utilisation de cette requête simple vous montre tous les événements pertinents :

```
DeviceNetworkEvents
| where ActionType == "ConnectionSuccess" 
| take 10
```

![Image d’une requête de recherche avancée](images/atp-proxy-investigation-ah.png)

Vous pouvez également filtrer les événements liés à la connexion au proxy lui-même. 

Utilisez la requête suivante pour filtrer les connexions au proxy :

```
DeviceNetworkEvents
| where ActionType == "ConnectionSuccess" and RemoteIP != "ProxyIP"  
| take 10
```



## <a name="related-topics"></a>Voir aussi
- [Application de la protection réseau avec la stratégie de groupe - CSP de stratégie](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-enablenetworkprotection)
