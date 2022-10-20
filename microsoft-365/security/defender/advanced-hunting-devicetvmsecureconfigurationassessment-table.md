---
title: Table DeviceTvmSecureConfigurationAssessment dans le schéma de repérage avancé
description: Découvrez les événements d’évaluation de la sécurité dans la table DeviceTvmSecureConfigurationAssessment du schéma de chasse avancé. Ces événements fournissent des informations sur l’appareil, les détails de configuration de la sécurité, l’impact et les informations de conformité.
keywords: repérage avancé, repérage de menaces, repérage de cybermenaces, Microsoft 365 Defender, microsoft 365, m365, recherche, requête, télémétrie, référence de schéma, kusto, table, colonne, type de données, description, gestion des vulnérabilités & menaces, GESTION DES MENACES, gestion des appareils, configuration de la sécurité, DeviceTvmSecureConfigurationAssessment
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
- m365-security
- tier3
ms.topic: conceptual
ms.openlocfilehash: 6f2ca4e131d46ed481590d43ed35824e97acd8d2
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68622901"
---
# <a name="devicetvmsecureconfigurationassessment"></a>DeviceTvmSecureConfigurationAssessment

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender
- Microsoft Defender pour point de terminaison

Chaque ligne du `DeviceTvmSecureConfigurationAssessment` tableau contient un événement d’évaluation pour une configuration de sécurité spécifique à partir de [Gestion des vulnérabilités Microsoft Defender](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt). Utilisez cette référence pour vérifier les derniers résultats de l’évaluation et déterminer si les appareils sont conformes.

Vous pouvez joindre cette table à la table [DeviceTvmSecureConfigurationAssessmentKB à l’aide](advanced-hunting-devicetvmsecureconfigurationassessmentkb-table.md) `ConfigurationId` de laquelle vous pouvez, par exemple, afficher la description textuelle de la configuration à partir de la `ConfigurationDescription` colonne de la `DeviceTvmSecureConfigurationAssessmentKB` table, dans les résultats de l’évaluation de la configuration.

Pour plus d’informations sur les autres tables du schéma de repérage avancé, consultez [la référence de repérage avancé](advanced-hunting-schema-tables.md).

| Nom de colonne | Type de données | Description |
|-------------|-----------|-------------|
| `DeviceId` | `string` | Identificateur unique de l’appareil dans le service |
| `DeviceName` | `string` | Nom de domaine complet (FQDN) de l’appareil |
| `OSPlatform` | `string` | Plateforme du système d’exploitation en cours d’exécution sur l’appareil. Indique des systèmes d’exploitation spécifiques, y compris des variantes au sein de la même famille, telles que Windows 11, Windows 10 et Windows 7.|
| `Timestamp` | `datetime` | Date et heure de génération de l’enregistrement |
| `ConfigurationId` | `string` | Identificateur unique pour une configuration spécifique |
| `ConfigurationCategory` | `string` | Catégorie ou regroupement auquel appartient la configuration : application, système d’exploitation, réseau, comptes, contrôles de sécurité |
| `ConfigurationSubcategory` | `string` | Sous-catégorie ou sous-groupement auquel appartient la configuration. Dans de nombreux cas, la chaîne décrit des fonctionnalités ou fonctionnalités spécifiques. |
| `ConfigurationImpact` | `string` | Impact nominal de la configuration sur la note de configuration globale (1-10) |
| `IsCompliant` | `boolean` | Indique si la configuration ou la stratégie est correctement configurée. |
| `IsApplicable` | `boolean` | Indique si la configuration ou la stratégie s’applique à l’appareil |
| `Context` | `string` | Informations contextuelles supplémentaires sur la configuration ou la stratégie |
| `IsExpectedUserImpact` | `boolean` | Indique s’il y aura un impact sur l’utilisateur si la configuration ou la stratégie est appliquée |

Vous pouvez essayer cet exemple de requête pour retourner des informations sur les appareils avec des configurations antivirus non conformes, ainsi que les métadonnées de configuration pertinentes du `DeviceTvmSecureConfigurationAssessmentKB` tableau :

```kusto
// Get information on devices with antivirus configurations issues
DeviceTvmSecureConfigurationAssessment
| where ConfigurationSubcategory == 'Antivirus' and IsApplicable == 1 and IsCompliant == 0
| join kind=leftouter (
    DeviceTvmSecureConfigurationAssessmentKB
    | project ConfigurationId, ConfigurationName, ConfigurationDescription, RiskDescription, Tags, ConfigurationImpact
) on ConfigurationId
| project DeviceName, OSPlatform, ConfigurationId, ConfigurationName, ConfigurationCategory, ConfigurationSubcategory, ConfigurationDescription, RiskDescription, ConfigurationImpact, Tags
```

## <a name="related-topics"></a>Sujets associés

- [Repérage proactif des menaces](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Utiliser des requêtes partagées](advanced-hunting-shared-queries.md)
- [Repérer des menaces sur les appareils, les e-mails, les applications et les identités](advanced-hunting-query-emails-devices.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)
- [Vue d’ensemble de Gestion des vulnérabilités Microsoft Defender](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt)