---
title: Table DeviceTvmSecureConfigurationAssessment dans le schéma de repérage avancé
description: Découvrez les événements d’évaluation de la sécurité dans le tableau DeviceTvmSecureConfigurationAssessment du schéma de chasse avancé. Ces & des événements de gestion des vulnérabilités fournissent des informations sur les périphériques ainsi que des informations sur la configuration de la sécurité, l’impact et la conformité.
keywords: chasse de menace, recherche de menace, recherche de menace informatique, protection contre les menaces Microsoft, Microsoft 365, MTP, M365, recherche, requête, télémétrie, référence de schéma, Kusto, table, colonne, type de données, description, menace & gestion des vulnérabilités, TVM, gestion des appareils, configuration de la sécurité, DeviceTvmSecureConfigurationAssessment
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: microsoft-365-enterprise
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: lomayor
author: lomayor
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: article
ms.openlocfilehash: bfe63397d194567a7d71de703363083d2fd4fe75
ms.sourcegitcommit: 815229e39a0f905d9f06717f00dc82e2a028fa7c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2020
ms.locfileid: "48847607"
---
# <a name="devicetvmsecureconfigurationassessment"></a>DeviceTvmSecureConfigurationAssessment

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender



Chaque ligne du tableau `DeviceTvmSecureConfigurationAssessment` contient un événement d’évaluation pour une configuration de sécurité spécifique de [Gestion des menaces et des vulnérabilités](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt). Utilisez cette référence pour vérifier les derniers résultats de l’évaluation et déterminer si les appareils sont conformes.

Pour plus d’informations sur les autres tables du schéma de repérage avancé, consultez [la référence de repérage avancé](advanced-hunting-schema-tables.md).

| Nom de colonne | Type de données | Description |
|-------------|-----------|-------------|
| `DeviceId` | string | Identificateur unique de l’appareil dans le service |
| `DeviceName` | string | Nom de domaine complet (FQDN) du périphérique |
| `OSPlatform` | string | Plateforme du système d’exploitation s’exécutant sur l’appareil. Cela indique des systèmes d’exploitation spécifiques, y compris des variantes au sein d’une même famille, telles que Windows 10 et Windows 7.|
| `Timestamp` | DateHeure | Date et heure de génération de l’enregistrement |
| `ConfigurationId` | string | Identificateur unique pour une configuration spécifique |
| `ConfigurationCategory` | string | Catégorie ou regroupement auquel appartient la configuration : application, système d’exploitation, réseau, comptes, contrôles de sécurité |
| `ConfigurationSubcategory` | string | Sous-catégorie ou sous-groupement auquel appartient la configuration. Dans de nombreux cas, cela décrit des capacités ou des fonctionnalités spécifiques. |
| `ConfigurationImpact` | string | Impact nominal de la configuration sur la note de configuration globale (1-10) |
| `IsCompliant` | booléen | Indique si la configuration ou la stratégie est correctement configurée. |
| `IsApplicable` | valeur booléenne | Indique si la configuration ou la stratégie s’applique à l’appareil. |
| `Context` | string | Informations contextuelles supplémentaires sur la configuration ou la stratégie |
| `IsExpectedUserImpactCompliant` | valeur booléenne | Indique s’il y aura un impact sur l’utilisateur si la configuration ou la stratégie est appliquée. |

## <a name="related-topics"></a>Sujets associés

- [Repérage proactif des menaces](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Utiliser des requêtes partagées](advanced-hunting-shared-queries.md)
- [Rechercher sur les appareils, les emails, les applications et les identités](advanced-hunting-query-emails-devices.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)
- [Présentation de la fonction Gestion des menaces et des vulnérabilités](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt)
