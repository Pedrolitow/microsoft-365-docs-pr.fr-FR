---
title: Configurer la découverte d’appareils
description: Découvrez comment configurer la découverte d’appareils dans Microsoft 365 Defender à l’aide de la découverte standard ou de base
keywords: de base, standard, configurer la découverte de point de terminaison, la découverte d’appareils
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: c1dfbc1fb953a83c3854e7059bba30a069a37c83
ms.sourcegitcommit: 3140e2866de36d57a27d27f70d47e8167c9cc907
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2021
ms.locfileid: "60555211"
---
# <a name="configure-device-discovery"></a>Configurer la découverte d’appareils

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2146631)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!include[Prerelease information](../../includes/prerelease.md)]

La découverte peut être configurée pour être en mode standard ou de base. Utilisez l’option standard pour rechercher activement des appareils dans votre réseau, ce qui garantit mieux la découverte des points de terminaison et fournit une classification plus riche des appareils.


Vous pouvez personnaliser la liste des appareils utilisés pour effectuer une découverte standard. Vous pouvez activer la découverte standard sur tous les appareils intégrés qui également prendre en charge cette fonctionnalité (actuellement - appareils Windows 10 uniquement) ou sélectionner un sous-ensemble ou des sous-ensembles de vos appareils en spécifiant leurs balises d’appareil.

> [!IMPORTANT]
> Pour la prévisualisation, vous devez d’abord activer les fonctionnalités d’aperçu dans Microsoft 365 Defender.
> Vous pouvez ensuite accéder à la configuration de découverte d’appareils Microsoft 365 centre de sécurité. La liste des appareils non utilisés et les recommandations de sécurité seront disponibles dans le centre de sécurité Microsoft 365 Defender et Microsoft 365, tandis que les vignettes de tableau de bord ne seront disponibles que dans Microsoft 365 centre de sécurité.

Prenez les étapes de configuration suivantes dans Microsoft 365 de sécurité :

1. Accédez à **Paramètres > détection d’appareil.**
2. Sélectionnez le mode de découverte à utiliser sur vos appareils intégrés.
3. Si vous avez choisi d’utiliser la découverte standard, sélectionnez les appareils à utiliser pour l’analyse active : tous les appareils ou sur un sous-ensemble en spécifiant leurs balises d’appareil.
4. Cliquez sur **Enregistrer**.

## <a name="exclude-devices-from-being-actively-probed-in-standard-discovery"></a>Exclure les appareils d’être activement sondés dans la découverte standard

S’il existe des appareils sur votre réseau qui ne doivent pas être analysés activement (par exemple, les appareils utilisés comme des honeypots pour un autre outil de sécurité), vous pouvez également définir une liste d’exclusions pour les empêcher d’être analysés. Notez que les appareils peuvent toujours être découverts à l’aide du mode de découverte de base et peuvent également être découverts par le biais de tentatives de découverte multidiffusion. Ces appareils seront découverts passivement, mais ne seront pas activement sondés.   

## <a name="select-networks-to-monitor"></a>Sélectionner les réseaux à surveiller

 Microsoft Defender pour point de terminaison analyse un réseau et détermine s’il s’agit d’un réseau d’entreprise qui doit être surveillé ou d’un réseau non professionnel qui peut être ignoré. Les réseaux d’entreprise sont généralement choisis pour être surveillés. Toutefois, vous pouvez remplacer cette décision en choisissant de surveiller les réseaux autres que ceux de l’entreprise où se trouvent les appareils intégrés.

Vous pouvez configurer l’endroit où la découverte d’appareils peut être effectuée en spécifiant les réseaux à surveiller. Lorsqu’un réseau est surveillé, la découverte d’appareils peut être effectuée sur ce réseau.

La liste des réseaux sur lequel la découverte d’appareils peut être effectuée s’affiche dans la page **Réseaux surveillés.**

> [!NOTE]
> La liste affiche les réseaux identifiés comme réseaux d’entreprise. Si moins de 50 réseaux sont identifiés comme réseaux d’entreprise, la liste affiche jusqu’à 50 réseaux avec le plus d’appareils intégrés. 

La liste des réseaux surveillés est triée en fonction du nombre total d’appareils observés sur le réseau au cours des 7 derniers jours.

Vous pouvez appliquer un filtre pour afficher l’un des états de découverte réseau suivants :

- **Réseaux surveillés** : réseaux où la découverte d’appareils est effectuée.
- **Réseaux ignorés** : ce réseau sera ignoré et la découverte d’appareils ne sera pas effectuée sur celui-ci.
- **Tous** : les réseaux surveillés et ignorés s’affichent.

### <a name="configure-the-network-monitor-state"></a>Configurer l’état du moniteur réseau

Vous contrôlez l’endroit où la découverte d’appareils a lieu. Les réseaux surveillés sont l’endroit où la découverte des appareils est effectuée et qui sont généralement des réseaux d’entreprise. Vous pouvez également choisir d’ignorer les réseaux ou de sélectionner la classification de découverte initiale après avoir modifié un état.

Le choix de la classification de découverte initiale implique l’application de l’état du moniteur réseau par défaut. Si vous sélectionnez l’état du moniteur réseau par défaut, les réseaux identifiés comme étant des réseaux d’entreprise seront surveillés et ceux identifiés comme non professionnels seront ignorés automatiquement.

1. Sélectionnez **Paramètres > détection d’appareil.**
2. Sélectionnez **Réseaux surveillés.**
3. Afficher la liste des réseaux.
4. Sélectionnez les trois points à côté du nom du réseau.
5. Choisissez si vous souhaitez surveiller, ignorer ou utiliser la classification de découverte initiale.

    > [!WARNING]
    >
    > - Le choix de surveiller un réseau qui n’a pas été identifié par Microsoft Defender pour Endpoint comme réseau d’entreprise peut entraîner la découverte d’appareils en dehors de votre réseau d’entreprise et peut donc détecter des appareils d’entreprise ou d’autres appareils.
    > - Choisir d’ignorer un réseau arrête la surveillance et la découverte d’appareils dans ce réseau. Les appareils qui ont déjà été découverts ne seront pas supprimés de l’inventaire, mais ne seront plus mis à jour et les détails seront conservés jusqu’à l’expiration de la période de rétention des données de Defender for Endpoint.
    > - Avant de choisir de surveiller les réseaux non professionnels, vous devez vous assurer que vous êtes autorisé à le faire. <br>

6. Confirmez que vous souhaitez apporter la modification.

## <a name="explore-devices-in-the-network"></a>Explorer les appareils du réseau

Vous pouvez utiliser la requête de recherche avancée suivante pour obtenir plus de contexte sur chaque nom de réseau décrit dans la liste des réseaux. La requête répertorie tous les appareils intégrés qui ont été connectés à un certain réseau au cours des 7 derniers jours.

```kusto
DeviceNetworkInfo
| where Timestamp > ago(7d)
| where ConnectedNetworks  != ""
| extend ConnectedNetworksExp = parse_json(ConnectedNetworks)
| mv-expand bagexpansion = array ConnectedNetworks=ConnectedNetworksExp
| extend NetworkName = tostring(ConnectedNetworks ["Name"]), Description = tostring(ConnectedNetworks ["Description"]), NetworkCategory = tostring(ConnectedNetworks ["Category"])
| where NetworkName == "<your network name here>"
| summarize arg_max(Timestamp, *) by DeviceId
```

## <a name="get-information-on-device"></a>Obtenir des informations sur l’appareil

Vous pouvez utiliser la requête de recherche avancée suivante pour obtenir les dernières informations complètes sur un appareil spécifique.

```kusto
DeviceInfo
| where DeviceName == "<device name here>" and isnotempty(OSPlatform)
| summarize arg_max(Timestamp, *) by DeviceId
```

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble de la découverte d’appareils](device-discovery.md)
- [FAQ sur la découverte d’appareils](device-discovery-faq.md)
