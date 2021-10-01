---
title: Table DeviceInfo dans le schéma de recherche avancée
description: En savoir plus sur le système d’exploitation, le nom de l’ordinateur et d’autres informations sur l’ordinateur dans la table DeviceInfo du schéma de recherche avancée
keywords: advanced hunting, threat hunting, cyber threat hunting, Microsoft 365 Defender, microsoft 365, m365, search, query, telemetry, schema reference, kusto, table, column, data type, description, machineinfo, DeviceInfo, device, machine, OS, platform, users
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: maccruz
author: schmurky
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: 88d91e2434871014cf286bbb27812e60036cb5cb
ms.sourcegitcommit: e5de03d4bd669945fec0d25a3f5eae56f86c9dcc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2021
ms.locfileid: "60042721"
---
# <a name="deviceinfo"></a>DeviceInfo

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender
- Microsoft Defender pour point de terminaison



Le tableau du schéma de recherche avancée contient des informations sur les appareils de l’organisation, notamment la version du système d’exploitation, les utilisateurs `DeviceInfo` actifs et le nom de l’ordinateur. [](advanced-hunting-overview.md) Utilisez cette référence pour créer des requêtes qui renvoient des informations de cette table.

Pour plus d’informations sur les autres tables du schéma de repérage avancé, [consultez la référence de repérage avancé](advanced-hunting-schema-tables.md).

| Nom de colonne | Type de données | Description |
|-------------|-----------|-------------|
| `Timestamp` | DateHeure | Date et heure d’enregistrement de l’événement |
| `DeviceId` | string | Identificateur unique de la machine dans le service |
| `DeviceName` | string | Nom de domaine complet (FQDN) de la machine |
| `ClientVersion` | string | Version de l’agent de point de terminaison ou du capteur en cours d’exécution sur l’ordinateur |
| `PublicIP` | string | Adresse IP publique utilisée par l’ordinateur intégré pour se connecter au service Microsoft Defender for Endpoint. Il peut s’agit de l’adresse IP de l’ordinateur lui-même, d’un périphérique NAT ou d’un proxy. |
| `OSArchitecture` | string | Architecture du système d’exploitation s’exécutant sur la machine |
| `OSPlatform` | string | Plateforme du système d’exploitation client s’exécutant sur la machine. Cela indique des systèmes d’exploitation spécifiques, y compris des variantes au sein de la même famille, telles que Windows 11, Windows 10 et Windows 7. |
| `OSBuild` | string | Version de build du système d’exploitation en cours d’exécution sur l’ordinateur |
| `IsAzureADJoined` | booléen | Indicateur booléen pour savoir si l’ordinateur est joint au Azure Active Directory |
| `AadObjectId` | string | Identificateur unique de l’appareil dans Azure AD |
| `LoggedOnUsers` | string | Liste de tous les utilisateurs connectés à l’ordinateur au moment de l’événement au format de tableau JSON |
| `RegistryDeviceTag` | string | Balise d’ordinateur ajoutée via le Registre |
| `OSVersion` | string | Version du système d’exploitation s’exécutant sur la machine |
| `MachineGroup` | string | Groupe d’ordinateurs de l’ordinateur. Ce groupe est utilisé par le contrôle d’accès basé sur un rôle pour déterminer l’accès à l’ordinateur |
| `ReportId` | long | Identificateur d’événement basé sur un compteur extensible. Pour identifier des événements uniques, cette colonne doit être utilisée conjointement avec les colonnes DeviceName et Timestamp |
| `OnboardingStatus` | string | Indique si l’appareil est actuellement intégré à Microsoft Defender pour le point de terminaison ou si l’appareil n’est pas pris en charge |
|`AdditionalFields` | string | Informations supplémentaires sur l’événement au format de tableau JSON |
|`DeviceCategory` | string | Classification plus large qui groupe certains types d’appareils sous les catégories suivantes : Point de terminaison, Périphérique réseau, IoT, Inconnu |
|`DeviceType` | string | Type d’appareil en fonction de l’objectif et des fonctionnalités, tels que l’appareil réseau, la station de travail, le serveur, l’appareil mobile, la console de jeu ou l’imprimante |
|`DeviceSubType` | string | Modificateur supplémentaire pour certains types d’appareils, par exemple, un appareil mobile peut être une tablette ou un smartphone |
|`Model` | string | Nom du modèle ou numéro du produit du fournisseur ou du fabricant |
|`Vendor` | string | Nom du fournisseur ou du fabricant du produit |
|`OSDistribution` | string | Distribution de la plateforme du système d’exploitation, telle que Ubuntu ou RedHat pour les plateformes Linux |
|`OSVersionInfo` | string | Informations supplémentaires sur la version du système d’exploitation, telles que le nom populaire, le nom de code ou le numéro de version |
|`MergedDeviceIds` | string | ID d’appareil précédents qui ont été affectés au même appareil |
|`MergedToDeviceId` | string | ID d’appareil le plus récent affecté à un appareil |

Le tableau fournit des informations sur l’appareil en fonction des pulsations, qui sont des rapports ou signaux périodiques `DeviceInfo` d’un appareil. Toutes les quinze minutes, l’appareil envoie une pulsation partielle qui contient des attributs qui changent fréquemment comme `LoggedOnUsers` . Une fois par jour, une pulsation complète contenant les attributs de l’appareil est envoyée.

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
