---
title: Table DeviceTvmSecureConfigurationAssessmentKB dans le schéma de repérage avancé
description: Découvrez les différentes configurations sécurisées évaluées par la fonction Gestion des menaces et des vulnérabilités dans la table DeviceTvmSecureConfigurationAssessmentKB du schéma de repérage avancé.
keywords: repérage avancé, repérage de menace, repérage de cybermenace, recherche, requête, télémétrie, schéma, référence, kusto, table, colonne, type de données, description, gestion des menaces et vulnérabilités, TVM, gestion des appareils, configuration de la sécurité, infrastructure MITRE ATT&CK, base de connaissances, KB, DeviceTvmSecureConfigurationAssessmentKB
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: microsoft-365-enterprise
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: lomayor
author: lomayor
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.openlocfilehash: 62c21545be31c7332fba28348b7159a0d46aa4b3
ms.sourcegitcommit: 0c9c28a87201c7470716216d99175356fb3d1a47
ms.translationtype: MT + HT Review
ms.contentlocale: fr-FR
ms.lasthandoff: 12/09/2019
ms.locfileid: "39910994"
---
# <a name="devicetvmsecureconfigurationassessmentkb"></a>DeviceTvmSecureConfigurationAssessmentKB

**S’applique à :**
- Protection Microsoft contre les menaces

[!include[Prerelease information](prerelease.md)]

La table `DeviceTvmSecureConfigurationAssessmentKB` dans le schéma de repérage avancé contient des informations sur les différentes configurations sécurisées (par exemple, si un appareil dispose de mises à jour automatiques), vérifié par la fonction [Gestion des menaces et des vulnérabilités](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt). Elle inclut également des informations sur les risques, des références du secteur associées et des techniques et tactiques MITRE ATT & CK applicables. Utilisez cette référence pour créer des requêtes qui renvoient des informations de la table.

Pour plus d’informations sur les autres tables du schéma de repérage avancé, consultez [la référence de repérage avancé](advanced-hunting-schema-tables.md).

| Nom de colonne | Type de données | Description |
|-------------|-----------|-------------|
| `ConfigurationId` | string | Identificateur unique pour une configuration spécifique |
| `ConfigurationImpact` | string | Impact nominal de la configuration sur la note de configuration globale (1-10) |
| `ConfigurationName` | string | Nom d’affichage de la configuration |
| `ConfigurationDescription` | string | Description de la configuration |
| `RiskDescription` | string | Description du risque associé |
| `ConfigurationCategory` | string | Catégorie ou regroupement auquel appartient la configuration : application, système d’exploitation, réseau, comptes, contrôles de sécurité|
| `ConfigurationSubcategory` | string |Sous-catégorie ou sous-groupement auquel appartient la configuration. Dans de nombreux cas, cela décrit des capacités ou des fonctionnalités spécifiques. |
| `ConfigurationBenchmarks` | string | Liste des références du secteur recommandant une configuration identique ou similaire |
| `RelatedMitreTechniques` | string | Liste des techniques d’infrastructure Mitre ATT&CK relatives à la configuration |
| `RelatedMitreTactics ` | string | Liste des tactiques d’infrastructure Mitre ATT&CK relatives à la configuration |

## <a name="related-topics"></a>Sujets associés

- [Repérage proactif des menaces](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Utiliser des requêtes partagées](advanced-hunting-shared-queries.md)
- [Repérer les menaces sur divers appareils et e-mails](advanced-hunting-query-emails-devices.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)
- [Présentation de la fonction Gestion des menaces et des vulnérabilités](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt)
