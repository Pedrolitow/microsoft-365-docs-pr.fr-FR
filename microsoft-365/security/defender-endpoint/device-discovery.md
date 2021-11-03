---
title: Vue d’ensemble de la découverte d’appareils
description: Découvrez comment tirer parti de la découverte de points de terminaison dans Microsoft 365 Defender pour rechercher des appareils non utilisés dans votre réseau
keywords: détection d’appareils, découverte, passif, proactif, réseau, visibilité, serveur, station de travail, intégration, appareils non utilisés
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
ms.openlocfilehash: c1a76bb0a82562a7c2a2f96e87b087f6fd09fcea
ms.sourcegitcommit: bf3965b46487f6f8cf900dd9a3af8b213a405989
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2021
ms.locfileid: "60701002"
---
# <a name="device-discovery-overview"></a>Vue d’ensemble de la découverte d’appareils

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2146631)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


La protection de votre environnement nécessite d’inventorier les appareils qui se sont connectés à votre réseau. Toutefois, le mappage d’appareils dans un réseau peut souvent être coûteux, difficile et chronophage.

Microsoft Defender pour point de terminaison fournit une fonctionnalité de découverte d’appareils qui vous permet de trouver des appareils non utilisés connectés à votre réseau d’entreprise sans avoir besoin d’appliances supplémentaires ou de modifications de processus fastidieuses.

La fonctionnalité de découverte d’appareils vous permet de :

- **Découvrir les points de terminaison d’entreprise connectés à votre réseau d’entreprise**

  À l’aide des options de découverte standard ou de base, vous pouvez découvrir les stations de travail, les serveurs et les points de terminaison mobiles qui ne sont pas encore intégrés à Microsoft Defender pour endpoint.

- **Intégrer les points de terminaison découverts**

  Les points de terminaison non pris en compte dans votre réseau introduisent des vulnérabilités et des risques pour votre réseau. Leur intégration au service peut accroître leur visibilité sur la sécurité.

Parallèlement à cette fonctionnalité, une nouvelle recommandation de sécurité pour intégrer des appareils à Microsoft Defender pour le point de terminaison sera disponible dans le cadre de l’expérience de gestion des menaces et des vulnérabilités existante.

## <a name="discovery-methods"></a>Méthodes de découverte

Il existe deux modes de découverte :

- Découverte de base
- Découverte standard (recommandé)

> [!IMPORTANT]
> La découverte est définie sur le mode de base. Vous pouvez choisir de conserver cette configuration via la page paramètres. La découverte standard sera le mode par défaut pour tous les clients à partir du 19 juillet 2021, sauf modification via la page des paramètres avant cette date.


Seuls les appareils observés par le mode de découverte de base seront activement sondés en mode standard.


### <a name="basic-discovery"></a>Découverte de base

Dans ce mode, les points de terminaison collectent passivement des événements dans votre réseau et en extraient les informations de l’appareil. La découverte de base utilise SenseNDR.exe binaire pour la collecte de données réseau passives et aucun trafic réseau n’est initié. Les points de terminaison extraient simplement les données de chaque trafic réseau visible par un appareil intégré.

### <a name="standard-discovery"></a>Découverte standard

Ce mode permet aux points de terminaison de sonder activement les appareils observés dans le réseau pour enrichir les données collectées et découvrir d’autres appareils, ce qui vous aide à créer un inventaire fiable et cohérent des appareils. Le mode standard utilise l’analyse intelligente et active pour découvrir encore plus d’informations sur les appareils observés afin d’enrichir les informations d’appareil existantes. Le mode standard exploite également les protocoles de découverte courants qui utilisent des requêtes multidiffusion dans le réseau pour trouver encore plus d’appareils, en plus de ceux qui ont été ovationné à l’aide de la méthode passive.

Lorsque le mode Standard est activé, une activité réseau minime et négligeable générée par le capteur de découverte peut être observée par les outils de surveillance réseau de votre organisation.

 Si vous choisissez de ne pas activer ce mode, vous n’aurez qu’une visibilité limitée des points de terminaison nonmanagés dans votre réseau.

La découverte standard utilise divers scripts PowerShell pour sonder activement des périphériques dans le réseau. Ces scripts PowerShell sont signés par Microsoft et sont exécutés à partir de l’emplacement suivant `C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\Downloads\*.ps` : Par exemple, `C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\Downloads\UnicastScannerV1.1.0.ps1`.

Vous pouvez modifier et personnaliser vos paramètres de découverte, pour plus d’informations, voir [Configurer la découverte d’appareils.](configure-device-discovery.md)

> [!NOTE]
> Le moteur de découverte fait la distinction entre les événements réseau reçus dans le réseau d’entreprise et en dehors du réseau d’entreprise. Les appareils qui ne sont pas connectés à des réseaux d’entreprise ne seront pas découverts ni répertoriés dans l’inventaire des appareils.

## <a name="device-inventory"></a>Inventaire des appareils

Les appareils qui ont été découverts mais qui n’ont pas encore été intégrés et sécurisés par Microsoft Defender pour le point de terminaison sont répertoriés dans l’inventaire des appareils dans l’onglet Points de terminaison. Vous pouvez désormais utiliser un nouveau filtre dans la liste d’inventaire des appareils appelé État d’intégration, qui peut avoir l’une des valeurs suivantes :

- Intégré : le point de terminaison est intégré à Microsoft Defender pour le point de terminaison.
- Peut être intégré : le point de terminaison a été découvert dans le réseau et le système d’exploitation a été identifié comme étant pris en charge par Microsoft Defender pour le point de terminaison, mais il n’est pas actuellement intégré. Nous vous recommandons vivement d’intégrer ces appareils.
- Non pris en charge : le point de terminaison a été découvert dans le réseau, mais n’est pas pris en charge par Microsoft Defender pour endpoint.
- Informations insuffisantes : le système n’a pas pu déterminer la prise en charge de l’appareil. L’activation de la découverte standard sur d’autres appareils du réseau peut enrichir les attributs découverts.

![Image du tableau de bord d’inventaire des appareils.](images/2b62255cd3a9dd42f3219e437b956fb9.png)

> [!TIP]
> Vous pouvez toujours appliquer des filtres pour exclure les appareils nonmanagés de la liste d’inventaire des appareils. Vous pouvez également utiliser la colonne d’état d’intégration sur les requêtes API pour filtrer les appareils nonmanagés.

## <a name="vulnerability-assessment-on-discovered-devices"></a>Évaluation de la vulnérabilité sur les appareils détectés

Les vulnérabilités et les risques sur vos appareils, ainsi que d’autres périphériques non utilisés détectés dans le réseau font partie des flux TVM actuels sous « Security Recommandations » et représentés dans les pages d’entité sur le portail.
Recherchez les recommandations de sécurité « SSH » pour rechercher les vulnérabilités SSH liées aux appareils non gérés et gérés.

![Image du tableau de bord recommandations en matière de sécurité.](images/1156c82ffadd356ce329d1cf551e806c.png)

## <a name="use-advanced-hunting-on-discovered-devices"></a>Utiliser le service de recherche avancée sur les appareils détectés

Vous pouvez utiliser des requêtes de recherche avancée pour obtenir une visibilité sur les appareils détectés.
Recherchez des détails sur les points de terminaison détectés dans la table DeviceInfo ou des informations réseau sur ces appareils dans la table DeviceNetworkInfo.

![Image de l’utilisation avancée du chasse.](images/f48ba1779eddee9872f167453c24e5c9.png)

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

## <a name="changed-behavior"></a>Comportement modifié

La section suivante répertorie les modifications que vous observerez dans Microsoft Defender pour le point de terminaison et/ou Microsoft 365 centre de sécurité lorsque cette fonctionnalité est activée.

1. Les appareils qui ne sont pas intégrés à Microsoft Defender pour le point de terminaison sont censés apparaître dans les requêtes d’inventaire, de recherche avancée et d’API. Cela peut augmenter considérablement la taille des résultats de la requête.
    1. Les tables « DeviceInfo » et « DeviceNetworkInfo » dans la recherche avancée vont maintenant contenir l’appareil détecté. Vous pouvez filtrer ces appareils à l’aide de l’attribut « OnboardingStatus ».
    2. Les appareils détectés sont censés apparaître dans les résultats de requête de l’API de diffusion en continu. Vous pouvez filtrer ces appareils à l’aide `OnboardingStatus` du filtre dans votre requête.
2. Les appareils non utilisés seront affectés à des groupes d’appareils existants en fonction des critères définis.
3. Dans de rares cas, la découverte standard peut déclencher des alertes sur les moniteurs réseau ou les outils de sécurité. Veuillez nous faire part de vos commentaires, si vous faites l’expérience de tels événements, afin d’éviter que ces problèmes ne se répètent. Vous pouvez exclure explicitement des cibles spécifiques ou des sous-réseaux entiers d’être activement sondés par la découverte standard.

## <a name="next-steps"></a>Prochaines étapes

- [Configurer la découverte d’appareils](configure-device-discovery.md)
- [FAQ sur la découverte d’appareils](device-discovery-faq.md)
