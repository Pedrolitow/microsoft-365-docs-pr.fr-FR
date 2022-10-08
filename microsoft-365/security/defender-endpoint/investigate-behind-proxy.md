---
title: Examiner des événements de connexion qui se produisent d’arrière vers l’avant des proxys
description: Découvrez comment utiliser la surveillance avancée au niveau HTTP via la protection réseau dans Microsoft Defender pour point de terminaison, qui expose une cible réelle, au lieu d’un proxy.
keywords: proxy, protection réseau, proxy de transfert, événements réseau, audit, bloc, noms de domaine, domaine
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- tier2
ms.topic: article
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: cd733e56133b4aa16f167fac2b20be93bdac615e
ms.sourcegitcommit: 4e42bafee965446f44f7f57d1defed2b9b24fce8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2022
ms.locfileid: "68232361"
---
# <a name="investigate-connection-events-that-occur-behind-forward-proxies"></a>Examiner des événements de connexion qui se produisent d’arrière vers l’avant des proxys

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigatemachines-abovefoldlink)

Defender pour point de terminaison prend en charge la surveillance des connexions réseau à partir de différents niveaux de la pile réseau. Un cas difficile est lorsque le réseau utilise un proxy de transfert comme passerelle vers Internet.

Le proxy agit comme s’il s’agissait du point de terminaison cible. Dans ce cas, les moniteurs de connexion réseau simples auditent les connexions avec le proxy qui est correct, mais qui a une valeur d’investigation inférieure.

Defender pour point de terminaison prend en charge la surveillance avancée au niveau HTTP via la protection réseau. Lorsqu’il est activé, un nouveau type d’événement est exposé, qui expose les noms de domaine cibles réels.

## <a name="use-network-protection-to-monitor-network-connection-behind-a-firewall"></a>Utiliser la protection réseau pour surveiller la connexion réseau derrière un pare-feu

La surveillance de la connexion réseau derrière un proxy de transfert est possible en raison d’autres événements réseau qui proviennent de la protection réseau. Pour les afficher sur une chronologie d’appareil, activez la protection réseau (au minimum en mode audit).

La protection réseau peut être contrôlée à l’aide des modes suivants :

- **Bloc** : les utilisateurs ou les applications ne peuvent pas se connecter à des domaines dangereux. Vous pourrez voir cette activité dans Microsoft 365 Defender.
- **Audit** : les utilisateurs ou les applications ne seront pas bloqués pour se connecter à des domaines dangereux. Toutefois, vous verrez toujours cette activité dans Microsoft 365 Defender.


Si vous désactivez la protection réseau, les utilisateurs ou les applications ne seront pas empêchés de se connecter à des domaines dangereux. Aucune activité réseau ne s’affiche dans Microsoft 365 Defender.

Si vous ne le configurez pas, le blocage du réseau est désactivé par défaut.

Pour plus d’informations, consultez [Activer la protection réseau](enable-network-protection.md).

## <a name="investigation-impact"></a>Impact de l’examen

Lorsque la protection réseau est activée, vous voyez que dans la chronologie d’un appareil, l’adresse IP continue à représenter le proxy, tandis que l’adresse cible réelle s’affiche.

:::image type="content" source="images/atp-proxy-investigation.png" alt-text="Événements réseau sur la chronologie de l’appareil" lightbox="images/atp-proxy-investigation.png":::

D’autres événements déclenchés par la couche de protection réseau sont désormais disponibles pour exposer les noms de domaine réels, même derrière un proxy.

Informations de l’événement :

:::image type="content" source="images/atp-proxy-investigation-event.png" alt-text="URL d’un événement réseau unique" lightbox="images/atp-proxy-investigation-event.png":::

## <a name="hunt-for-connection-events-using-advanced-hunting"></a>Rechercher des événements de connexion à l’aide d’une chasse avancée

Tous les nouveaux événements de connexion sont également disponibles pour vous permettre d’effectuer une chasse avancée. Étant donné que ces événements sont des événements de connexion, vous pouvez les trouver sous la table DeviceNetworkEvents sous le type d’action `ConnecionSuccess` .

L’utilisation de cette requête simple vous montre tous les événements pertinents :

```console
DeviceNetworkEvents
| where ActionType == "ConnectionSuccess"
| take 10
```

:::image type="content" source="images/atp-proxy-investigation-ah.png" alt-text="Requête de repérage avancée" lightbox="images/atp-proxy-investigation-ah.png":::

Vous pouvez également filtrer les événements liés à la connexion au proxy lui-même.

Utilisez la requête suivante pour filtrer les connexions au proxy :

```console
DeviceNetworkEvents
| where ActionType == "ConnectionSuccess" and RemoteIP != "ProxyIP"
| take 10
```

## <a name="related-topics"></a>Voir aussi

- [Application de la protection réseau avec gp - fournisseur de solutions cloud de stratégie](/windows/client-management/mdm/policy-csp-defender#defender-enablenetworkprotection)
