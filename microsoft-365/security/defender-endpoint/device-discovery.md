---
title: Vue d’ensemble de la découverte d’appareils
description: Découvrez comment tirer parti de la découverte de points de terminaison dans Microsoft 365 Defender pour rechercher des appareils non gérés dans votre réseau
keywords: détection d’appareil, détection, passif, proactif, réseau, visibilité, serveur, station de travail, appareils intégrés, appareils non gérés
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: siosulli
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
- m365-initiative-defender-endpoint
ms.custom: admindeeplinkDEFENDER
ms.topic: conceptual
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: a3bb9420773c61258a53a547ec9181c652a6e526
ms.sourcegitcommit: c29af68260ba8676083674b3c70209bff2c2e362
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/16/2022
ms.locfileid: "67739837"
---
# <a name="device-discovery-overview"></a>Vue d’ensemble de la découverte d’appareils

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

La protection de votre environnement nécessite l’inventaire des appareils qui se trouvent dans votre réseau. Toutefois, le mappage des appareils d’un réseau peut souvent être coûteux, difficile et fastidieux.

Pertahanan Microsoft untuk Titik Akhir fournit une fonctionnalité de découverte d’appareils qui vous permet de trouver des appareils non gérés connectés à votre réseau d’entreprise sans avoir besoin d’appliances supplémentaires ou de modifications de processus fastidieuses. La découverte d’appareils utilise des points de terminaison intégrés, dans votre réseau, pour collecter, sonder ou analyser votre réseau pour découvrir les appareils non gérés. La fonctionnalité de découverte d’appareils vous permet de découvrir :

- Points de terminaison d’entreprise (stations de travail, serveurs et appareils mobiles) qui ne sont pas encore intégrés à Pertahanan Microsoft untuk Titik Akhir
- Appareils réseau tels que les routeurs et les commutateurs
- Appareils IoT tels que les imprimantes et les caméras

Les appareils inconnus et non gérés présentent des risques significatifs pour votre réseau, qu’il s’agisse d’une imprimante non modifiée, d’appareils réseau avec des configurations de sécurité faibles ou d’un serveur sans contrôle de sécurité. Une fois les appareils découverts, vous pouvez :

- Intégrer des points de terminaison non managés au service, ce qui augmente la visibilité de la sécurité sur ces derniers.
- Réduisez la surface d’attaque en identifiant et en évaluant les vulnérabilités, et en détectant les lacunes de configuration.

Regardez cette vidéo pour obtenir une vue d’ensemble rapide de l’évaluation et de l’intégration d’appareils non gérés qui Pertahanan Microsoft untuk Titik Akhir découverts.
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4RwQz]

Conjointement à cette fonctionnalité, une recommandation de sécurité pour intégrer des appareils à Pertahanan Microsoft untuk Titik Akhir est disponible dans le cadre de l’expérience de Gestion des vulnérabilités Microsoft Defender existante.

## <a name="discovery-methods"></a>Méthodes de découverte

Vous pouvez choisir le mode de découverte à utiliser par vos appareils intégrés. Le mode contrôle le niveau de visibilité que vous pouvez obtenir pour les appareils non gérés dans votre réseau d’entreprise.

Deux modes de découverte sont disponibles :

- **Découverte de base** : dans ce mode, les points de terminaison collectent passivement les événements de votre réseau et en extraient les informations de l’appareil. La découverte de base utilise le binaire SenseNDR.exe pour la collecte de données réseau passives et aucun trafic réseau n’est lancé. Les points de terminaison extraient simplement les données de chaque trafic réseau qui est vu par un appareil intégré. Avec la découverte de base, vous bénéficiez uniquement d’une visibilité limitée des points de terminaison non managés dans votre réseau.

- **Découverte standard** (recommandée) : ce mode permet aux points de terminaison de rechercher activement des appareils dans votre réseau pour enrichir les données collectées et découvrir d’autres appareils, ce qui vous permet de créer un inventaire fiable et cohérent des appareils. Outre les appareils qui ont été observés à l’aide de la méthode passive, le mode standard tire également parti des protocoles de découverte courants qui utilisent des requêtes de multidiffusion dans le réseau pour rechercher encore plus d’appareils. Le mode Standard utilise une détection active et intelligente pour découvrir des informations supplémentaires sur les appareils observés afin d’enrichir les informations existantes sur les appareils. Lorsque le mode Standard est activé, l’activité réseau minimale et négligeable générée par le capteur de découverte peut être observée par les outils de surveillance réseau de votre organisation.

Vous pouvez modifier et personnaliser vos paramètres de découverte. Pour plus d’informations, consultez [Configurer la découverte d’appareils](configure-device-discovery.md).

> [!IMPORTANT]
> La découverte standard est le mode par défaut pour tous les clients à compter du 19 juillet 2021. Vous pouvez choisir de remplacer cette configuration par une configuration de base via la page des paramètres. Si vous choisissez le mode de base, vous ne bénéficiez que d’une visibilité limitée des points de terminaison non managés dans votre réseau.

> [!NOTE]
> Le moteur de découverte fait la distinction entre les événements réseau reçus dans le réseau d’entreprise et en dehors du réseau d’entreprise. Les appareils qui ne sont pas connectés aux réseaux d’entreprise ne seront pas découverts ou répertoriés dans l’inventaire des appareils.

## <a name="device-inventory"></a>Inventaire des appareils

Les appareils qui ont été découverts mais qui n’ont pas encore été intégrés et sécurisés par Pertahanan Microsoft untuk Titik Akhir sont répertoriés dans l’inventaire des appareils sous l’onglet Ordinateurs et appareils mobiles.

Pour évaluer ces appareils, vous pouvez utiliser un filtre dans la liste d’inventaire des appareils appelé État d’intégration, qui peut avoir l’une des valeurs suivantes :

- Intégré : le point de terminaison est intégré à Pertahanan Microsoft untuk Titik Akhir.
- Peut être intégré : le point de terminaison a été découvert dans le réseau et le système d’exploitation a été identifié comme étant pris en charge par Pertahanan Microsoft untuk Titik Akhir, mais il n’est pas actuellement intégré. Nous vous recommandons vivement d’intégrer ces appareils.
- Non pris en charge : le point de terminaison a été découvert dans le réseau, mais n’est pas pris en charge par Pertahanan Microsoft untuk Titik Akhir.
- Informations insuffisantes : le système n’a pas pu déterminer la prise en charge de l’appareil. L’activation de la découverte standard sur plus d’appareils du réseau peut enrichir les attributs découverts.

:::image type="content" source="images/2b62255cd3a9dd42f3219e437b956fb9.png" alt-text="Tableau de bord de l’inventaire des appareils" lightbox="images/2b62255cd3a9dd42f3219e437b956fb9.png":::

> [!TIP]
> Vous pouvez toujours appliquer des filtres pour exclure les appareils non gérés de la liste d’inventaire des appareils. Vous pouvez également utiliser la colonne d’état d’intégration sur les requêtes d’API pour filtrer les appareils non gérés.

Pour plus d’informations, consultez [l’inventaire des appareils](machines-view-overview.md).

## <a name="network-device-discovery"></a>Découverte d’appareils réseau

Le grand nombre d’appareils réseau non managés déployés dans une organisation crée une grande surface d’attaque et représente un risque significatif pour l’ensemble de l’entreprise. Pertahanan Microsoft untuk Titik Akhir fonctionnalités de découverte du réseau vous permettent de vous assurer que les appareils réseau sont découverts, classés avec précision et ajoutés à l’inventaire des ressources.

Les appareils réseau ne sont pas gérés en tant que points de terminaison standard, car Defender pour point de terminaison n’a pas de capteur intégré aux appareils réseau eux-mêmes. Ces types d’appareils nécessitent une approche sans agent dans laquelle une analyse à distance obtient les informations nécessaires auprès des appareils. Pour ce faire, un appareil Pertahanan Microsoft untuk Titik Akhir désigné sera utilisé sur chaque segment réseau pour effectuer des analyses périodiques authentifiées des appareils réseau préconfigurés. Une fois découvertes, les fonctionnalités de gestion des vulnérabilités de Defender pour point de terminaison fournissent des workflows intégrés pour sécuriser les commutateurs détectés, les routeurs, les contrôleurs WLAN, les pare-feu et les passerelles VPN.

Pour plus d’informations, consultez [Périphériques réseau](network-devices.md).

## <a name="device-discovery-integrations"></a>Intégrations de découverte d’appareils

Pour relever le défi d’obtenir suffisamment de visibilité pour localiser, identifier et sécuriser votre inventaire complet des ressources OT/IOT Pertahanan Microsoft untuk Titik Akhir prend désormais en charge les intégrations suivantes :

- **Corelight** : Microsoft s’est associé à Corelight pour recevoir des données des appliances réseau Corelight. Cela offre Microsoft 365 Defender avec une visibilité accrue sur les activités réseau des appareils non managés, y compris la communication avec d’autres appareils non gérés ou des réseaux externes. Pour plus d’informations, consultez [Activer l’intégration des données Corelight](corelight-integration.md).

- **Microsoft Defender pour IoT** : cette intégration combine les fonctionnalités de découverte d’appareils de Pertahanan Microsoft untuk Titik Akhir, avec les fonctionnalités de surveillance sans agent de Microsoft Defender pour IoT, pour sécuriser les appareils IoT d’entreprise connectés à un réseau informatique (par exemple, VoIP (Voice over Internet Protocol), les imprimantes et les téléviseurs intelligents). Pour plus d’informations, consultez [Activer l’intégration de Microsoft Defender pour IoT](enable-microsoft-defender-for-iot-integration.md).

## <a name="vulnerability-assessment-on-discovered-devices"></a>Évaluation des vulnérabilités sur les appareils découverts

Les vulnérabilités et les risques sur vos appareils, ainsi que sur d’autres appareils non gérés détectés dans le réseau, font partie des flux de gestion des vulnérabilités Defender actuels sous « Recommandations de sécurité » et sont représentés dans les pages d’entité sur le portail.
Recherchez les recommandations de sécurité liées à « SSH » pour rechercher les vulnérabilités SSH liées aux appareils non gérés et gérés.

:::image type="content" source="images/1156c82ffadd356ce329d1cf551e806c.png" alt-text="Tableau de bord des recommandations de sécurité" lightbox="images/1156c82ffadd356ce329d1cf551e806c.png":::

## <a name="use-advanced-hunting-on-discovered-devices"></a>Utiliser la chasse avancée sur les appareils découverts

Vous pouvez utiliser des requêtes de chasse avancées pour obtenir une visibilité sur les appareils découverts. Recherchez des détails sur les appareils découverts dans la table DeviceInfo, ou des informations relatives au réseau sur ces appareils, dans la table DeviceNetworkInfo.

:::image type="content" source="images/f48ba1779eddee9872f167453c24e5c9.png" alt-text="Page De repérage avancé sur laquelle les requêtes peuvent être utilisées" lightbox="images/f48ba1779eddee9872f167453c24e5c9.png":::

### <a name="query-discovered-devices-details"></a>Détails de la requête sur les appareils découverts

Exécutez cette requête sur la table DeviceInfo pour retourner tous les appareils découverts, ainsi que les détails les plus récents pour chaque appareil :

```query
DeviceInfo
| summarize arg_max(Timestamp, *) by DeviceId  // Get latest known good per device Id
| where isempty(MergedToDeviceId) // Remove invalidated/merged devices
| where OnboardingStatus != "Onboarded"
```

En appelant la fonction **SeenBy** , dans votre requête de repérage avancée, vous pouvez obtenir des détails sur l’appareil intégré sur lequel un appareil découvert a été vu. Ces informations peuvent vous aider à déterminer l’emplacement réseau de chaque appareil découvert et, par la suite, à l’identifier dans le réseau.

```query
DeviceInfo
| where OnboardingStatus != "Onboarded"
| summarize arg_max(Timestamp, *) by DeviceId 
| where isempty(MergedToDeviceId) 
| limit 100
| invoke SeenBy()
| project DeviceId, DeviceName, DeviceType, SeenBy
```

Pour plus d’informations, consultez la fonction [SeenBy().](/microsoft-365/security/defender/advanced-hunting-seenby-function)

### <a name="query-network-related-information"></a>Interroger les informations relatives au réseau

La découverte d’appareils tire parti Pertahanan Microsoft untuk Titik Akhir appareils intégrés en tant que source de données réseau pour attribuer des activités à des appareils non intégrés. Le capteur réseau sur l’appareil intégré Pertahanan Microsoft untuk Titik Akhir identifie deux nouveaux types de connexion :

- ConnectionAttempt : tentative d’établissement d’une connexion TCP (syn)
- ConnectionAcknowledged - Un accusé de réception indiquant qu’une connexion TCP a été acceptée (syn\ack)

Cela signifie que lorsqu’un appareil non intégré tente de communiquer avec un appareil Pertahanan Microsoft untuk Titik Akhir intégré, la tentative génère un DeviceNetworkEvent et les activités d’appareil non intégrées peuvent être affichées dans la chronologie de l’appareil intégré et via la table DeviceNetworkEvents de repérage avancé.

Vous pouvez essayer cet exemple de requête :

```text
DeviceNetworkEvents
| where ActionType == "ConnectionAcknowledged" or ActionType == "ConnectionAttempt"
| take 10
```

## <a name="next-steps"></a>Prochaines étapes

- [Configurer la découverte d’appareils](configure-device-discovery.md)
- [FAQ sur la découverte d’appareils](device-discovery-faq.md)
