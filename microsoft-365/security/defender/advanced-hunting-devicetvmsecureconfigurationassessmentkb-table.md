---
title: Table DeviceTvmSecureConfigurationAssessmentKB dans le schéma de repérage avancé
description: Découvrez les différentes configurations sécurisées évaluées par Gestion des vulnérabilités Microsoft Defender dans la table DeviceTvmSecureConfigurationAssessmentKB du schéma de chasse avancé.
keywords: advanced hunting, threat hunting, cyber threat hunting, Microsoft 365 Defender, microsoft 365, m365, search, query, telemetry, schema reference, kusto, table, column, data type, description, threat & vulnerability management, TVM, device management, security configuration, MITRE ATT&CK framework, base de connaissances, KB, DeviceTvmSecureConfigurationAssessmentKB, MDVM, Gestion des vulnérabilités Microsoft Defender
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
ms.collection: m365-security-compliance
ms.topic: article
ms.openlocfilehash: 6bcd0c404e807c14bac8d33fe5a4014b5207bf19
ms.sourcegitcommit: 10e6abe740e27000e223378eb17d657a47555fa8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2022
ms.locfileid: "67481171"
---
# <a name="devicetvmsecureconfigurationassessmentkb"></a>DeviceTvmSecureConfigurationAssessmentKB

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender
- Microsoft Defender pour point de terminaison

La `DeviceTvmSecureConfigurationAssessmentKB` table du schéma de chasse avancé contient des informations sur les différentes configurations sécurisées vérifiées par [Gestion des vulnérabilités Microsoft Defender](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt). Elle inclut également des informations sur les risques, des références du secteur associées et des techniques et tactiques MITRE ATT & CK applicables.

Cette table ne retourne pas d’événements ou d’enregistrements. Nous vous recommandons de joindre cette table à la table [DeviceTvmSecureConfigurationAssessment](advanced-hunting-devicetvmsecureconfigurationassessment-table.md) à l’aide `ConfigurationId` de cette table pour afficher des informations textuelles sur les configurations de sécurité dans les évaluations retournées.

Par exemple, lorsque vous interrogez la `DeviceTvmSecureConfigurationAssessment` table, vous souhaiterez peut-être afficher les `ConfigurationDescription` configurations de sécurité qui sont affichées dans les résultats de l’évaluation. Vous pouvez voir ces informations en joignant cette table à l’utilisation `ConfigurationId` et au `DeviceTvmSecureConfigurationAssessment` projet`ConfigurationDescription`.

Pour plus d’informations sur les autres tables du schéma de repérage avancé, consultez [la référence de repérage avancé](advanced-hunting-schema-tables.md).

| Nom de colonne | Type de données | Description |
|-------------|-----------|-------------|
| `ConfigurationId` | `string` | Identificateur unique pour une configuration spécifique |
| `ConfigurationImpact` | `string` | Impact nominal de la configuration sur la note de configuration globale (1-10) |
| `ConfigurationName` | `string` | Nom d’affichage de la configuration |
| `ConfigurationDescription` | `string` | Description de la configuration |
| `RiskDescription` | `string` | Description du risque associé |
| `ConfigurationCategory` | `string` | Catégorie ou regroupement auquel appartient la configuration : application, système d’exploitation, réseau, comptes, contrôles de sécurité|
| `ConfigurationSubcategory` | `string` |Sous-catégorie ou sous-groupement auquel appartient la configuration. Dans de nombreux cas, cela décrit des capacités ou des fonctionnalités spécifiques. |
| `ConfigurationBenchmarks` | `string` | Liste des références du secteur recommandant une configuration identique ou similaire |
| `Tags` | `string` | Étiquettes représentant différents attributs utilisés pour identifier ou catégoriser une configuration de sécurité |
| `RemediationOptions` | `string` | Actions recommandées pour réduire ou résoudre les risques associés |

Vous pouvez essayer cet exemple de requête pour retourner les métadonnées de configuration pertinentes ainsi que des informations sur les appareils avec des configurations antivirus non conformes à partir du `DeviceTvmSecureConfigurationAssessment` tableau :

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