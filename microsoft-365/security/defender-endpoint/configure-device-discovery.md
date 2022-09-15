---
title: Configurer la découverte d’appareils
description: Découvrez comment configurer la découverte d’appareils dans Microsoft 365 Defender à l’aide de la découverte de base ou standard
keywords: de base, standard, configurer la découverte de points de terminaison, la découverte d’appareils
ms.service: microsoft-365-security
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
ms.custom: admindeeplinkDEFENDER
ms.topic: conceptual
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: 9fbff594d65ef51d351f9810764821914206be53
ms.sourcegitcommit: 9b133379196da2b3a4bb311b07ff274f43780f68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2022
ms.locfileid: "67702421"
---
# <a name="configure-device-discovery"></a>Configurer la découverte d’appareils

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


La découverte peut être configurée pour être en mode standard ou de base. Utilisez l’option standard pour rechercher activement des appareils dans votre réseau, ce qui permettra de mieux garantir la découverte des points de terminaison et de fournir une classification plus riche des appareils.

Vous pouvez personnaliser la liste des appareils utilisés pour effectuer la découverte standard. Vous pouvez activer la découverte standard sur tous les appareils intégrés qui prennent également en charge cette fonctionnalité (actuellement Windows 10 ou version ultérieure et les appareils Windows Server 2019 ou ultérieurs uniquement) ou sélectionner un sous-ensemble ou des sous-ensembles de vos appareils en spécifiant leurs balises d’appareil.

## <a name="set-up-device-discovery"></a>Configurer la découverte d’appareils

Pour configurer la découverte d’appareils, effectuez les étapes de configuration suivantes dans <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portail</a> :

Accéder à **La découverte des paramètres** > **de l’appareil**

1. Si vous souhaitez configurer Basic en tant que mode de découverte à utiliser sur vos appareils intégrés, sélectionnez **De base** , puis **Sélectionnez Enregistrer**
2. Si vous avez choisi d’utiliser la découverte standard, sélectionnez les appareils à utiliser pour la détection active : tous les appareils ou sur un sous-ensemble en spécifiant leurs balises d’appareil, puis **sélectionnez Enregistrer**

> [!NOTE]
>La découverte standard utilise différents scripts PowerShell pour sonder activement les appareils du réseau. Ces scripts PowerShell sont signés Par Microsoft et exécutés à partir de l’emplacement suivant : `C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\Downloads\*.ps`. Par exemple : `C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\Downloads\UnicastScannerV1.1.0.ps1`.

## <a name="exclude-devices-from-being-actively-probed-in-standard-discovery"></a>Exclure les appareils d’une sonde active dans la découverte standard

S’il existe des appareils sur votre réseau qui ne doivent pas être analysés activement (par exemple, des appareils utilisés comme honeypots pour un autre outil de sécurité), vous pouvez également définir une liste d’exclusions pour les empêcher d’être analysés. Notez que les appareils peuvent toujours être découverts à l’aide du mode de découverte de base et peuvent également être découverts par le biais de tentatives de découverte de multidiffusion. Ces appareils seront découverts passivement, mais ne seront pas analysés activement.

Vous pouvez configurer les appareils à exclure dans la page **Exclusions** .

## <a name="select-networks-to-monitor"></a>Sélectionner des réseaux à surveiller

Microsoft Defender pour point de terminaison analyse un réseau et détermine s’il s’agit d’un réseau d’entreprise qui doit être surveillé ou d’un réseau autre qu’un réseau d’entreprise qui peut être ignoré. Pour identifier un réseau en tant qu’entreprise, nous mettons en corrélation les identificateurs réseau entre tous les clients du locataire et si la majorité des appareils de l’organisation indiquent qu’ils sont connectés au même nom de réseau, avec la même passerelle par défaut et la même adresse de serveur DHCP, nous partons du principe qu’il s’agit d’un réseau d’entreprise. Les réseaux d’entreprise sont généralement choisis pour être surveillés. Toutefois, vous pouvez remplacer cette décision en choisissant de surveiller les réseaux non d’entreprise où se trouvent les appareils intégrés.

Vous pouvez configurer l’emplacement où la découverte d’appareils peut être effectuée en spécifiant les réseaux à surveiller. Lorsqu’un réseau est surveillé, la découverte d’appareil peut être effectuée sur celui-ci.

La liste des réseaux sur lesquels la découverte d’appareils peut être effectuée s’affiche dans la page **Réseaux surveillés** .

> [!NOTE]
> La liste répertorie les réseaux qui ont été identifiés comme réseaux d’entreprise. Si moins de 50 réseaux sont identifiés comme réseaux d’entreprise, la liste affiche jusqu’à 50 réseaux avec les appareils les plus intégrés.

La liste des réseaux surveillés est triée en fonction du nombre total d’appareils affichés sur le réseau au cours des 7 derniers jours.

Vous pouvez appliquer un filtre pour afficher l’un des états de découverte réseau suivants :

- **Réseaux surveillés** : réseaux où la découverte d’appareils est effectuée.
- **Réseaux ignorés** : ce réseau est ignoré et la découverte des appareils n’est pas effectuée sur celui-ci.
- **Tous : les** réseaux surveillés et ignorés s’affichent.

### <a name="configure-the-network-monitor-state"></a>Configurer l’état du moniteur réseau

Vous contrôlez l’emplacement de découverte des appareils. Les réseaux surveillés sont l’endroit où la découverte des appareils est effectuée et sont généralement des réseaux d’entreprise. Vous pouvez également choisir d’ignorer les réseaux ou de sélectionner la classification de découverte initiale après avoir modifié un état.

Le choix de la classification de découverte initiale implique l’application de l’état par défaut du moniteur réseau créé par le système. La sélection de l’état par défaut du moniteur réseau fait par le système signifie que les réseaux qui ont été identifiés comme étant d’entreprise, seront surveillés et que les réseaux identifiés comme non professionnels seront ignorés automatiquement.

1. Sélectionnez **Paramètres > découverte d’appareil**.
2. Sélectionnez **Réseaux surveillés**.
3. Affichez la liste des réseaux.
4. Sélectionnez les trois points en regard du nom du réseau.
5. Choisissez si vous souhaitez surveiller, ignorer ou utiliser la classification de découverte initiale.

    > [!WARNING]
    >
    > - Le choix de surveiller un réseau qui n’a pas été identifié par Microsoft Defender pour point de terminaison en tant que réseau d’entreprise peut entraîner la découverte d’appareils en dehors de votre réseau d’entreprise et peut donc détecter les appareils domestiques ou autres appareils non professionnels.
    > - Le choix d’ignorer un réseau arrête la surveillance et la découverte des appareils de ce réseau. Les appareils qui ont déjà été découverts ne seront pas supprimés de l’inventaire, mais ne seront plus mis à jour et les détails seront conservés jusqu’à l’expiration de la période de conservation des données de Defender pour point de terminaison.
    > - Avant de choisir de surveiller les réseaux autres que les réseaux d’entreprise, vous devez vous assurer que vous êtes autorisé à le faire. <br>

6. Vérifiez que vous souhaitez apporter la modification.

## <a name="explore-devices-in-the-network"></a>Explorer les appareils dans le réseau

Vous pouvez utiliser la requête de repérage avancée suivante pour obtenir plus de contexte sur chaque nom de réseau décrit dans la liste des réseaux. La requête répertorie tous les appareils intégrés qui ont été connectés à un certain réseau au cours des 7 derniers jours.

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

Vous pouvez utiliser la requête de chasse avancée suivante pour obtenir les dernières informations complètes sur un appareil spécifique.

```kusto
DeviceInfo
| where DeviceName == "<device name here>" and isnotempty(OSPlatform)
| summarize arg_max(Timestamp, *) by DeviceId
```

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble de la découverte d’appareils](device-discovery.md)
- [FAQ sur la découverte d’appareils](device-discovery-faq.md)
