---
title: Vue d’ensemble de la découverte d’appareils
description: Découvrez comment tirer parti de la découverte de points de terminaison dans Microsoft 365 Defender pour rechercher des appareils non utilisés dans votre réseau
keywords: détection d’appareils, découverte, passif, proactif, réseau, visibilité, serveur, station de travail, intégration, appareils non utilisés
ms.prod: m365-security
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
ms.technology: m365d
ms.openlocfilehash: 926d23cb4e9abcecd9d34e976dee60851471613b
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64472922"
---
# <a name="device-discovery-overview"></a>Vue d’ensemble de la découverte d’appareils

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

La protection de votre environnement nécessite d’inventorier les appareils qui se sont connectés à votre réseau. Toutefois, le mappage d’appareils dans un réseau peut souvent être coûteux, difficile et chronophage.

Microsoft Defender pour point de terminaison fournit une fonctionnalité de découverte d’appareils qui vous permet de trouver des appareils non utilisés connectés à votre réseau d’entreprise sans avoir besoin d’appliances supplémentaires ou de modifications de processus fastidieuses. La découverte d’appareils utilise des points de terminaison intégrés, dans votre réseau, pour collecter, sonder ou analyser votre réseau afin de découvrir les appareils non utilisés. La fonctionnalité de découverte d’appareils vous permet de découvrir :

- Enterprise de terminaison (stations de travail, serveurs et appareils mobiles) qui ne sont pas encore intégrés à Microsoft Defender pour endpoint
- Périphériques réseau tels que les routeurs et commutateurs
- Appareils IoT tels que les imprimantes et les appareils photo

Les appareils inconnus et non utilisés présentent des risques importants pour votre réseau , qu’il s’agit d’une imprimante non filée, d’appareils réseau avec des configurations de sécurité faibles ou d’un serveur sans contrôle de sécurité. Une fois les appareils détectés, vous pouvez :

- Intégrer des points de terminaison nonmanagés au service, ce qui augmente la visibilité de la sécurité sur ces derniers.
- Réduisez la surface d’attaque en identifiant et en évaluant les vulnérabilités et en détectant les lacunes de configuration.

Regardez cette vidéo pour obtenir une vue d’ensemble rapide de la découverte d’appareils :

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWORdQ]

Parallèlement à cette fonctionnalité, une recommandation de sécurité pour intégrer des appareils à Microsoft Defender for Endpoint est disponible dans le cadre de l’expérience Gestion des menaces et des vulnérabilités existante.

## <a name="discovery-methods"></a>Méthodes de découverte

Vous pouvez choisir le mode de découverte à utiliser par vos appareils intégrés. Le mode contrôle le niveau de visibilité que vous pouvez obtenir pour les appareils non utilisés dans votre réseau d’entreprise.

Deux modes de découverte sont disponibles :

- **Découverte de base** : dans ce mode, les points de terminaison collectent passivement des événements dans votre réseau et extraient les informations de l’appareil. La découverte de base utilise SenseNDR.exe binaire pour la collecte de données réseau passives et aucun trafic réseau n’est initié. Les points de terminaison extraient simplement les données de chaque trafic réseau visible par un appareil intégré. Avec la découverte de base, vous n’aurez qu’une visibilité limitée des points de terminaison nonmanagés dans votre réseau.

- **Découverte standard** (recommandée) : ce mode permet aux points de terminaison de rechercher activement des appareils dans votre réseau pour enrichir les données collectées et découvrir d’autres appareils, ce qui vous aide à créer un inventaire fiable et cohérent des appareils. Outre les appareils observés à l’aide de la méthode passive, le mode standard exploite également les protocoles de découverte courants qui utilisent des requêtes multidiffusion dans le réseau pour trouver encore plus d’appareils. Le mode standard utilise l’analyse intelligente et active pour découvrir des informations supplémentaires sur les appareils observés afin d’enrichir les informations d’appareil existantes. Lorsque le mode Standard est activé, l’activité réseau minime et négligeable générée par le capteur de découverte peut être observée par les outils de surveillance réseau de votre organisation.

Vous pouvez modifier et personnaliser vos paramètres de découverte. Pour plus d’informations, voir [Configurer la découverte d’appareils](configure-device-discovery.md).

> [!IMPORTANT]
> La découverte standard est le mode par défaut pour tous les clients à partir du 19 juillet 2021. Vous pouvez choisir de modifier cette configuration pour qu’elle soit de base via la page paramètres. Si vous choisissez le mode de base, vous n’aurez qu’une visibilité limitée des points de terminaison nonmanagés dans votre réseau.

> [!NOTE]
> Le moteur de découverte fait la distinction entre les événements réseau reçus dans le réseau d’entreprise et en dehors du réseau d’entreprise. Les appareils qui ne sont pas connectés à des réseaux d’entreprise ne seront pas découverts ni répertoriés dans l’inventaire des appareils.

## <a name="device-inventory"></a>Inventaire des appareils

Les appareils qui ont été découverts mais qui n’ont pas encore été intégrés et sécurisés par Microsoft Defender pour le point de terminaison sont répertoriés dans l’inventaire des appareils sous l’onglet Ordinateurs et appareils mobiles.

Pour évaluer ces appareils, vous pouvez utiliser un filtre dans la liste d’inventaire des appareils appelé état d’intégration, qui peut avoir l’une des valeurs suivantes :

- Intégré : le point de terminaison est intégré à Microsoft Defender pour le point de terminaison.
- Peut être intégré : le point de terminaison a été découvert dans le réseau et le système d’exploitation a été identifié comme étant pris en charge par Microsoft Defender pour le point de terminaison, mais il n’est pas actuellement intégré. Nous vous recommandons vivement d’intégrer ces appareils.
- Non pris en charge : le point de terminaison a été découvert dans le réseau, mais n’est pas pris en charge par Microsoft Defender pour endpoint.
- Informations insuffisantes : le système n’a pas pu déterminer la prise en charge de l’appareil. L’activation de la découverte standard sur d’autres appareils du réseau peut enrichir les attributs découverts.

:::image type="content" source="images/2b62255cd3a9dd42f3219e437b956fb9.png" alt-text="Tableau de bord d’inventaire des appareils" lightbox="images/2b62255cd3a9dd42f3219e437b956fb9.png":::

> [!TIP]
> Vous pouvez toujours appliquer des filtres pour exclure les appareils nonmanagés de la liste d’inventaire des appareils. Vous pouvez également utiliser la colonne d’état d’intégration sur les requêtes API pour filtrer les appareils nonmanagés.

Pour plus d’informations, voir [Inventaire des appareils](machines-view-overview.md).

## <a name="network-device-discovery"></a>Découverte de périphériques réseau

Le grand nombre de périphériques réseau non utilisés déployés dans une organisation crée une zone d’attaque de grande surface et représente un risque significatif pour l’ensemble de l’entreprise. Les fonctionnalités de découverte réseau de Microsoft Defender pour points de terminaison vous permettent de vous assurer que les périphériques réseau sont découverts, classés avec précision et ajoutés à l’inventaire des biens.

Les périphériques réseau ne sont pas gérés en tant que points de terminaison standard, car Defender pour point de terminaison ne comprend pas de capteur intégré aux périphériques réseau eux-mêmes. Ces types d’appareils nécessitent une approche sans agent dans laquelle une analyse à distance obtient les informations nécessaires des appareils. Pour ce faire, un appareil Microsoft Defender for Endpoint désigné sera utilisé sur chaque segment réseau pour effectuer des analyses authentifiées périodiques des périphériques réseau préconfigurés. Une fois découvertes, les fonctionnalités Gestion des menaces et des vulnérabilités de Defender for Endpoint fournissent des flux de travail intégrés pour sécuriser les commutateurs découverts, les routeurs, les contrôleurs WLAN, les pare-feu et les passerelles VPN.

Pour plus d’informations, voir [Périphériques réseau](network-devices.md).

## <a name="device-discovery-integrations"></a>Intégrations de découverte d’appareils

Pour relever le défi de gagner suffisamment de visibilité pour localiser, identifier et sécuriser votre inventaire complet des ressources OT/IOT, Microsoft Defender pour endpoint prend désormais en charge les intégrations suivantes :

- **Corelight** : Microsoft s’est associé à Corelight pour recevoir des données à partir d’appliances réseau Corelight. Cela permet Microsoft 365 Defender une meilleure visibilité sur les activités réseau des appareils nonmanagés, notamment la communication avec d’autres appareils nonmanagés ou des réseaux externes. Pour plus d’informations, voir [Activer l’intégration des données Corelight](corelight-integration.md).

- **Microsoft Defender pour IoT** : cette intégration combine les fonctionnalités de découverte d’appareils de Microsoft Defender pour Endpoint, avec les fonctionnalités de surveillance sans agent de Microsoft Defender pour IoT, pour sécuriser les appareils IoT d’entreprise connectés à un réseau informatique (par exemple, VoIP, imprimantes et téléviseurs intelligents). Pour plus d’informations, voir [Activer Microsoft Defender pour l’intégration IoT](enable-microsoft-defender-for-iot-integration.md).

## <a name="vulnerability-assessment-on-discovered-devices"></a>Évaluation de la vulnérabilité sur les appareils détectés

Les vulnérabilités et les risques sur vos appareils, ainsi que d’autres périphériques non utilisés détectés dans le réseau font partie des flux TVM actuels sous « Recommandations de sécurité » et représentés dans les pages d’entité sur le portail.
Recherchez les recommandations de sécurité « SSH » pour rechercher les vulnérabilités SSH liées aux appareils non gérés et gérés.

:::image type="content" source="images/1156c82ffadd356ce329d1cf551e806c.png" alt-text="Tableau de bord recommandations en matière de sécurité" lightbox="images/1156c82ffadd356ce329d1cf551e806c.png":::


## <a name="use-advanced-hunting-on-discovered-devices"></a>Utiliser le service de recherche avancée sur les appareils détectés

Vous pouvez utiliser des requêtes de recherche avancée pour obtenir une visibilité sur les appareils détectés.
Recherchez des détails sur les points de terminaison détectés dans la table DeviceInfo ou des informations réseau sur ces appareils dans la table DeviceNetworkInfo.

:::image type="content" source="images/f48ba1779eddee9872f167453c24e5c9.png" alt-text="Page de recherche avancée sur laquelle les requêtes peuvent être utilisées" lightbox="images/f48ba1779eddee9872f167453c24e5c9.png":::

La découverte d’appareils tire parti de Microsoft Defender pour les appareils intégrés au point de terminaison en tant que source de données réseau pour attribuer des activités à des appareils non intégrés. Cela signifie que si un appareil intégré De Microsoft Defender pour point de terminaison a communiqué avec un appareil non intégré, les activités sur l’appareil non intégré peuvent être visibles sur la chronologie et via la table DeviceNetworkEvents de recherche avancée.

Les nouveaux événements sont basés sur les connexions TCP (Transmission Control Protocol) et s’adaptent au schéma DeviceNetworkEvents actuel. L’entrée TCP vers l’appareil Microsoft Defender pour point de terminaison activé à partir d’un autre que Microsoft Defender pour point de terminaison est activée.

Les types d’action suivants ont également été ajoutés :

- ConnectionAttempt : tentative d’établissement d’une connexion TCP (syn)
- ConnectionAcknowledged : accusé de réception de l’acceptation d’une connexion TCP (syn\ack)

Vous pouvez essayer cette requête d’exemple :

```text
DeviceNetworkEvents
| where ActionType == "ConnectionAcknowledged" or ActionType == "ConnectionAttempt"
| take 10
```

## <a name="next-steps"></a>Étapes suivantes

- [Configurer la découverte d’appareils](configure-device-discovery.md)
- [FAQ sur la découverte d’appareils](device-discovery-faq.md)
