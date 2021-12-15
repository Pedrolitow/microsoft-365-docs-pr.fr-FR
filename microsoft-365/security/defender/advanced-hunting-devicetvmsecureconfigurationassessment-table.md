---
title: Table DeviceTvmSecureConfigurationAssessment dans le schéma de repérage avancé
description: Découvrez les événements d’évaluation de la sécurité dans la table DeviceTvmSecureConfigurationAssessment du schéma de recherche avancé. Ces événements fournissent des informations sur l’appareil, les détails de configuration de la sécurité, l’impact et les informations de conformité.
keywords: advanced hunting, threat hunting, cyber threat hunting, Microsoft 365 Defender, microsoft 365, m365, search, query, telemetry, schema reference, kusto, table, column, data type, description, threat & gestion des vulnérabilités, TVM, device management, security configuration, DeviceTvmSecureConfigurationAssessment
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
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-security-compliance
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: 43f44458cde7d466d1097034e7bcc9d0e3072745
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2021
ms.locfileid: "61530702"
---
# <a name="devicetvmsecureconfigurationassessment"></a>DeviceTvmSecureConfigurationAssessment

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender
- Microsoft Defender pour point de terminaison


Chaque ligne du tableau `DeviceTvmSecureConfigurationAssessment` contient un événement d’évaluation pour une configuration de sécurité spécifique de [Gestion des menaces et des vulnérabilités](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt). Utilisez cette référence pour vérifier les derniers résultats de l’évaluation et déterminer si les appareils sont conformes.

Vous pouvez joindre ce tableau à la table [DeviceTvmSecureConfigurationAssessmentKB](advanced-hunting-devicetvmsecureconfigurationassessmentkb-table.md) à l’aide de cette table pour pouvoir, par exemple, afficher la description de texte de la configuration dans la colonne du tableau, dans les résultats de l’évaluation de la `ConfigurationId` `ConfigurationDescription` `DeviceTvmSecureConfigurationAssessmentKB` configuration.

Pour plus d’informations sur les autres tables du schéma de repérage avancé, consultez [la référence de repérage avancé](advanced-hunting-schema-tables.md).

| Nom de colonne | Type de données | Description |
|-------------|-----------|-------------|
| `DeviceId` | `string` | Identificateur unique de l’appareil dans le service |
| `DeviceName` | `string` | Nom de domaine complet (FQDN) de l’appareil |
| `OSPlatform` | `string` | Plateforme du système d’exploitation en cours d’exécution sur l’appareil. Indique des systèmes d’exploitation spécifiques, y compris des variantes au sein de la même famille, telles que Windows 11, Windows 10 et Windows 7.|
| `Timestamp` | `datetime` | Date et heure de génération de l’enregistrement |
| `ConfigurationId` | `string` | Identificateur unique pour une configuration spécifique |
| `ConfigurationCategory` | `string` | Catégorie ou regroupement auquel appartient la configuration : application, système d’exploitation, réseau, comptes, contrôles de sécurité |
| `ConfigurationSubcategory` | `string` | Sous-catégorie ou sous-groupement auquel appartient la configuration. Dans de nombreux cas, la chaîne décrit des fonctionnalités spécifiques. |
| `ConfigurationImpact` | `string` | Impact nominal de la configuration sur la note de configuration globale (1-10) |
| `IsCompliant` | `boolean` | Indique si la configuration ou la stratégie est correctement configurée. |
| `IsApplicable` | `boolean` | Indique si la configuration ou la stratégie s’applique à l’appareil |
| `Context` | `string` | Informations contextuelles supplémentaires sur la configuration ou la stratégie |
| `IsExpectedUserImpact` | `boolean` | Indique s’il y aura un impact sur l’utilisateur si la configuration ou la stratégie est appliquée |

Vous pouvez essayer cette requête d’exemple pour retourner des informations sur les appareils avec des configurations antivirus non conformes, ainsi que les métadonnées de configuration pertinentes du `DeviceTvmSecureConfigurationAssessmentKB` tableau :

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
- [Présentation de la fonction Gestion des menaces et des vulnérabilités](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt)