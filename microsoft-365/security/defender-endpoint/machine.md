---
title: Type de ressource de machine
description: Découvrez les méthodes et les propriétés du type de ressource Machine dans Microsoft Defender pour point de terminaison.
keywords: api, api prises en charge, get, machines
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.subservice: mde
ms.custom: api
search.appverid: met150
ms.openlocfilehash: ffa155a0b1d9598d19af5842553f68372f30b076
ms.sourcegitcommit: 95ac076310ab9006ed92c69938f7ae771cd10826
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2022
ms.locfileid: "67851719"
---
# <a name="machine-resource-type"></a>Type de ressource de machine

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

[!include[Prerelease information](../../includes/prerelease.md)]

## <a name="methods"></a>Méthodes

|Méthode|Type renvoyé|Description|
|---|---|---|
|[Répertorier les ordinateurs](get-machines.md)|[collection d’ordinateurs](machine.md)|Répertorie l’ensemble d’entités de [machine](machine.md) dans l’organisation.|
|[Obtenir une machine](get-machine-by-id.md)|[Machine](machine.md)|Obtenez une [machine](machine.md) par son identité.|
|[Se connecter aux utilisateurs](get-machine-log-on-users.md)|Collection d’[utilisateurs](user.md)|Obtenez l’ensemble de [l’utilisateur](user.md) connecté à [l’ordinateur](machine.md).|
|[Obtenir des alertes associées](get-machine-related-alerts.md)|collection[alert](alerts.md)|Obtenez l’ensemble des entités [d’alerte](alerts.md) qui ont été déclenchées sur [l’ordinateur](machine.md).|
|[Obtenir les logiciels installés](get-installed-software.md)|[collection de logiciels](software.md)|Récupère une collection de logiciels installés liés à un ID d’ordinateur donné.|
|[Obtenir les vulnérabilités découvertes](get-discovered-vulnerabilities.md)|[collection de vulnérabilités](vulnerability.md)|Récupère une collection de vulnérabilités découvertes liées à un ID d’ordinateur donné.|
|[Obtenir les recommandations de sécurité](get-security-recommendations.md)|[collection de recommandations](recommendation.md)|Récupère une collection de recommandations de sécurité liées à un ID de machine donné.|
|[Ajouter ou supprimer les balises de l’ordinateur](add-or-remove-machine-tags.md)|[Machine](machine.md)|Ajouter ou supprimer une balise à un ordinateur spécifique.|
|[Rechercher des ordinateurs par IP](find-machines-by-ip.md)|[collection d’ordinateurs](machine.md)|Recherchez les ordinateurs affichés avec l’adresse IP.|
|[Rechercher des ordinateurs par balise](find-machines-by-tag.md)|[collection d’ordinateurs](machine.md)|Rechercher des machines par [balise](machine-tags.md).|
|[Obtenir des Ko manquants](get-missing-kbs-machine.md)|Collection de bases de connaissances|Obtenir la liste des ko manquants associés à l’ID d’ordinateur|
|[Définir la valeur de l’appareil](set-device-value.md)|[collection d’ordinateurs](machine.md)|Définissez la [valeur d’un appareil](tvm-assign-device-value.md).|
|[Mettre à jour l’ordinateur](update-machine-method.md)|[collection d’ordinateurs](machine.md)|Obtenez l’état de mise à jour d’un ordinateur.|

## <a name="properties"></a>Propriétés

|Propriété|Type|Description|
|---|---|---|
|id|Chaîne|[identité de la machine](machine.md) .|
|computerDnsName|Chaîne|nom complet de [l’ordinateur](machine.md).|
|firstSeen|DateTimeOffset|Première date et heure auxquelles [l’ordinateur](machine.md) a été observé par Microsoft Defender pour point de terminaison.|
|lastSeen|DateTimeOffset|Heure et date du dernier rapport d’appareil complet reçu. Un appareil envoie généralement un rapport complet toutes les 24 heures.|
|osPlatform|Chaîne|Plateforme du système d’exploitation.|
|onboardingstatus|Chaîne|État de l’intégration de l’ordinateur. Les valeurs possibles sont : « onboarded », « CanBeOnboarded », « Unsupported » et « InsufficientInfo ».|
|osProcessor|Chaîne|Processeur de système d’exploitation. Utilisez plutôt la propriété osArchitecture.|
|version|String|Version du système d’exploitation.|
|osBuild|Valeur nullable longue|Numéro de build du système d’exploitation.|
|lastIpAddress|Chaîne|Dernière adresse IP sur la carte réseau locale sur [l’ordinateur](machine.md).|
|lastExternalIpAddress|Chaîne|Dernière adresse IP via laquelle [l’ordinateur](machine.md) a accédé à Internet.|
|healthStatus|Énum|[état](machine.md) d’intégrité de la machine. Les valeurs possibles sont : « Active », « Inactive », « ImpairedCommunication », « NoSensorData », « NoSensorDataImpairedCommunication » et « Unknown ».|
|rbacGroupName|Chaîne|Nom du groupe d’ordinateurs.|
|rbacGroupId|Chaîne|ID de groupe d’ordinateurs.|
|riskScore|Énumération nullable|Score de risque tel qu’évalué par Microsoft Defender pour point de terminaison. Les valeurs possibles sont : « None », « Informational », « Low », « Medium » et « High ».|
|aadDeviceId|Guid de représentation nullable|ID d’appareil AAD (quand [l’ordinateur](machine.md) est joint à AAD).|
|machineTags|String collection|Ensemble de balises [d’ordinateur](machine.md) .|
|exposureLevel|Énumération nullable|Niveau d’exposition tel qu’évalué par Microsoft Defender pour point de terminaison. Les valeurs possibles sont : « None », « Low », « Medium » et « High ».|
|deviceValue|Énumération nullable|[Valeur de l’appareil](tvm-assign-device-value.md). Les valeurs possibles sont : ' Normal', 'Low' et 'High'.|
|ipAddresses|Collection IpAddress|Ensemble d’objets ***IpAddress*** . Consultez [l’API Obtenir des machines](get-machines.md).|
|osArchitecture|Chaîne|Architecture du système d’exploitation. Les valeurs possibles sont : « 32 bits », « 64 bits ». Utilisez cette propriété au lieu d’osProcessor.|
