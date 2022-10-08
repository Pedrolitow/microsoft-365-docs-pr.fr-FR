---
title: Table DeviceInfo dans le schéma de chasse avancé
description: En savoir plus sur le système d’exploitation, le nom de l’ordinateur et d’autres informations sur l’ordinateur dans la table DeviceInfo du schéma de repérage avancé
keywords: repérage avancé, repérage de menaces, repérage de cybermenaces, Microsoft 365 Defender, microsoft 365, m365, recherche, requête, télémétrie, référence de schéma, kusto, table, colonne, type de données, description, machineinfo, DeviceInfo, appareil, machine, système d’exploitation, plateforme, utilisateurs
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.service: microsoft-365-security
ms.subservice: m365d
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- tier3
- m365-security
ms.topic: article
ms.openlocfilehash: d17eb655467acff37e7bcc22c01c10d12daa975e
ms.sourcegitcommit: 12af9e8e3a6eaa090fda9e98ccb831dff65863a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2022
ms.locfileid: "68067221"
---
# <a name="deviceinfo"></a>DeviceInfo

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender
- Microsoft Defender pour point de terminaison

Le `DeviceInfo` tableau du schéma [de repérage avancé](advanced-hunting-overview.md) contient des informations sur les appareils de l’organisation, notamment la version du système d’exploitation, les utilisateurs actifs et le nom de l’ordinateur. Utilisez cette référence pour créer des requêtes qui renvoient des informations de cette table.

Pour plus d’informations sur les autres tables du schéma de repérage avancé, [consultez la référence de repérage avancé](advanced-hunting-schema-tables.md).

| Nom de colonne | Type de données | Description |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | Date et heure d’enregistrement de l’événement |
| `DeviceId` | `string` | Identificateur unique de la machine dans le service |
| `DeviceName` | `string` | Nom de domaine complet (FQDN) de la machine |
| `ClientVersion` | `string` | Version de l’agent de point de terminaison ou du capteur en cours d’exécution sur l’ordinateur |
| `PublicIP` | `string` | Adresse IP publique utilisée par l’ordinateur intégré pour se connecter au service Microsoft Defender pour point de terminaison. Il peut s’agir de l’adresse IP de l’ordinateur lui-même, d’un appareil NAT ou d’un proxy |
| `OSArchitecture` | `string` | Architecture du système d’exploitation s’exécutant sur la machine |
| `OSPlatform` | `string` | Plateforme du système d’exploitation client s’exécutant sur la machine. Cela indique des systèmes d’exploitation spécifiques, y compris des variations au sein de la même famille, telles que Windows 11, Windows 10 et Windows 7. |
| `OSBuild` | `string` | Version de build du système d’exploitation en cours d’exécution sur l’ordinateur |
| `IsAzureADJoined` | `boolean` | Indicateur booléen indiquant si la machine est jointe à Azure Active Directory |
| `AadDeviceId` | `string` | Identificateur unique de l’appareil dans Azure AD |
| `LoggedOnUsers` | `string` | Liste de tous les utilisateurs connectés à l’ordinateur au moment de l’événement au format tableau JSON |
| `RegistryDeviceTag` | `string` | Balise d’ordinateur ajoutée via le Registre |
| `OSVersion` | `string` | Version du système d’exploitation s’exécutant sur la machine |
| `MachineGroup` | `string` | Groupe d’ordinateurs de l’ordinateur. Ce groupe est utilisé par le contrôle d’accès en fonction du rôle pour déterminer l’accès à la machine |
| `ReportId` | `long` | Identificateur d’événement basé sur un compteur extensible. Pour identifier les événements uniques, cette colonne doit être utilisée conjointement avec les colonnes DeviceName et Timestamp |
| `OnboardingStatus` | `string` | Indique si l’appareil est actuellement intégré ou non à Microsoft Defender pour point de terminaison ou si l’appareil n’est pas pris en charge |
|`AdditionalFields` | `string` | Informations supplémentaires sur l’événement au format tableau JSON |
|`DeviceCategory` | `string` | Classification plus large qui regroupe certains types d’appareils dans les catégories suivantes : Point de terminaison, Appareil réseau, IoT, Inconnu |
|`DeviceType` | `string` | Type d’appareil basé sur l’objectif et les fonctionnalités, tels que l’appareil réseau, la station de travail, le serveur, le mobile, la console de jeu ou l’imprimante |
|`DeviceSubType` | `string` | Modificateur supplémentaire pour certains types d’appareils, par exemple, un appareil mobile peut être une tablette ou un smartphone; disponible uniquement si la découverte d’appareils trouve suffisamment d’informations sur cet attribut |
|`Model` | `string` | Nom de modèle ou numéro du produit du fournisseur ou du fabricant, disponible uniquement si la découverte d’appareils trouve suffisamment d’informations sur cet attribut |
|`Vendor` | `string` | Nom du fournisseur ou du fabricant du produit, disponible uniquement si la découverte d’appareils trouve suffisamment d’informations sur cet attribut |
|`OSDistribution` | `string` | Distribution de la plateforme du système d’exploitation, telle que les plateformes Ubuntu ou RedHat pour Linux |
|`OSVersionInfo` | `string` | Informations supplémentaires sur la version du système d’exploitation, telles que le nom populaire, le nom de code ou le numéro de version |
|`MergedDeviceIds` | `string` | ID d’appareil précédents qui ont été affectés au même appareil |
|`MergedToDeviceId` | `string` | ID d’appareil le plus récent affecté à un appareil |

Le `DeviceInfo` tableau fournit des informations sur l’appareil en fonction des pulsations, qui sont des rapports périodiques ou des signaux provenant d’un appareil. Toutes les quinze minutes, l’appareil envoie une pulsation partielle qui contient des attributs qui changent fréquemment, comme `LoggedOnUsers`. Une fois par jour, une pulsation complète contenant les attributs de l’appareil est envoyée.

Vous pouvez utiliser l’exemple de requête suivant pour obtenir l’état le plus récent d’un appareil :

```kusto
// Get latest information on user/device
DeviceInfo
| where DeviceName == "example" and isnotempty(OSPlatform)
| summarize arg_max(Timestamp, *) by DeviceId 
```

## <a name="related-topics"></a>Voir aussi
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Utiliser des requêtes partagées](advanced-hunting-shared-queries.md)
- [Repérer des menaces sur les appareils, les e-mails, les applications et les identités](advanced-hunting-query-emails-devices.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)
