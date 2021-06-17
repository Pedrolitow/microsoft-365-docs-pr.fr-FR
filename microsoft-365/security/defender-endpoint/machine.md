---
title: Type de ressource Machine
description: Découvrez les méthodes et les propriétés du type de ressource Machine dans Microsoft Defender for Endpoint.
keywords: api, api pris en charge, obtenir, ordinateurs
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 5ca147c9e69168b2f15aa69bba8728567b782fa9
ms.sourcegitcommit: 34c06715e036255faa75c66ebf95c12a85f8ef42
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2021
ms.locfileid: "52984459"
---
# <a name="machine-resource-type"></a>Type de ressource Machine

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez découvrir Microsoft Defender pour le point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink) 

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

[!include[Prerelease information](../../includes/prerelease.md)]

## <a name="methods"></a>Méthodes

Méthode|Type renvoyé |Description
:---|:---|:---
[Répertorier les ordinateurs](get-machines.md) | [collection d’ordinateurs](machine.md) | Liste des [ensembles d’entités](machine.md) d’ordinateurs dans l’organisation.
[Obtenir un ordinateur](get-machine-by-id.md) | [ordinateur](machine.md) | Obtenez un [ordinateur par](machine.md) son identité.
[Obtenir des utilisateurs connectés](get-machine-log-on-users.md) | Collection d’[utilisateurs](user.md) | Obtenez l’ensemble [de l’utilisateur](user.md) qui s’est connecté à l’ordinateur. [](machine.md)
[Obtenir les alertes associées](get-machine-related-alerts.md) | collection[alert](alerts.md) | Obtenir [l’ensemble](alerts.md) des entités d’alerte qui ont été élevés sur l’ordinateur . [](machine.md)
[Obtenir les logiciels installés](get-installed-software.md) | [collection de](software.md) logiciels | Extrait une collection de logiciels installés liés à un ID d’ordinateur donné.
[Obtenir les vulnérabilités découvertes](get-discovered-vulnerabilities.md) | [collection de vulnérabilités](vulnerability.md) | Récupère une collection de vulnérabilités découvertes liées à un ID d’ordinateur donné.
[Obtenir les recommandations de sécurité](get-security-recommendations.md) | [collection de recommandations](recommendation.md) | Récupère une collection de recommandations de sécurité relatives à un ID d’ordinateur donné.
[Ajouter ou supprimer les balises de l’ordinateur](add-or-remove-machine-tags.md) | [ordinateur](machine.md) | Ajouter ou supprimer une balise à un ordinateur spécifique.
[Rechercher des ordinateurs par IP](find-machines-by-ip.md) | [collection d’ordinateurs](machine.md) | Recherchez les ordinateurs visibles avec l’adresse IP.
[Rechercher des ordinateurs par balise](find-machines-by-tag.md) | [collection d’ordinateurs](machine.md) | Rechercher des ordinateurs par [balise](machine-tags.md).
[Obtenir des Ko manquants](get-missing-kbs-machine.md) | Collection KB | Obtenir la liste des ko manquants associés à l’ID de l’ordinateur
[Définir la valeur de l’appareil](set-device-value.md)| [collection d’ordinateurs](machine.md) | Définissez [la valeur d’un appareil.](tvm-assign-device-value.md)
[Mettre à jour l’ordinateur](update-machine-method.md) |[collection d’ordinateurs](machine.md) | Obtenir l’état de mise à jour d’un ordinateur.

## <a name="properties"></a>Propriétés

Propriété |   Type   |   Description
:---|:---|:---
id | String | [identité de](machine.md) l’ordinateur.
computerDnsName | String | [nom complet](machine.md) de l’ordinateur.
firstSeen | DateTimeOffset | Date et heure de la première observation [de l’ordinateur](machine.md) par Microsoft Defender pour le point de terminaison.
lastSeen | DateTimeOffset |Heure et date du dernier rapport d’appareil complet reçu. Un appareil envoie généralement un rapport complet toutes les 24 heures.
osPlatform | String | Plateforme du système d’exploitation.
osProcessor | String | Processeur du système d’exploitation. Utilisez la propriété osArchitecture à la place.
version | String | Version du système d’exploitation.
osBuild | Nullable long | Numéro de build du système d’exploitation.
lastIpAddress | String | Dernière adresse IP sur la NIC locale sur [l’ordinateur.](machine.md)
lastExternalIpAddress | String | Dernière adresse IP via laquelle [l’ordinateur](machine.md) a accédé à Internet.
healthStatus | Énum | [état d’état](machine.md) de l’ordinateur. Les valeurs possibles sont : « Active », « Inactive », « ImpairedCommunication », « NoSensorData », « NoSensorDataImpairedCommunication » et « Unknown ». 
rbacGroupName | String | Nom du groupe d’ordinateurs.
riskScore | Nullable, enum | Score de risque tel qu’évalué par Microsoft Defender pour le point de terminaison. Les valeurs possibles sont : « None » (aucun), « Informational » (informations), « Low » (faible), « Medium » (moyen) et « High » (élevé).
exposureScore | Nullable, enum | [Score d’exposition](tvm-exposure-score.md) tel qu’évalué par Microsoft Defender pour le point de terminaison. Les valeurs possibles sont : « None » (aucun), « Low » (faible), « Medium » (moyen) et « High » (élevé).
aadDeviceId | Guid de représentation nullable | ID d’appareil AAD [(lorsque l’ordinateur](machine.md) est joint à AAD).
machineTags | String collection | Ensemble de [balises d’ordinateur.](machine.md)
exposureLevel | Nullable, enum | Niveau d’exposition tel qu’évalué par Microsoft Defender pour le point de terminaison. Les valeurs possibles sont : « None » (aucun), « Low » (faible), « Medium » (moyen) et « High » (élevé).
deviceValue | Nullable, enum | Valeur [de l’appareil.](tvm-assign-device-value.md) Les valeurs possibles sont : « Normal » (normal), « Low » (faible) et « High » (élevé).
ipAddresses | Collection IpAddress | Ensemble ***d’objets IpAddress.*** Voir [API Obtenir des ordinateurs.](get-machines.md)
osArchitecture | String | Architecture du système d’exploitation. Les valeurs possibles sont : « 32 bits », « 64 bits ». Utilisez cette propriété au lieu d’osProcessor.


