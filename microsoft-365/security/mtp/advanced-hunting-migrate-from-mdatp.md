---
title: Migrer les requêtes de chasse avancées à partir de Microsoft Defender ATP
description: Découvrez comment ajuster vos requêtes ATP Microsoft Defender afin de pouvoir les utiliser dans Microsoft Threat Protection
keywords: chasse aux menaces, recherche de menace, recherche de menace informatique, protection contre les menaces Microsoft, Microsoft 365, MTP, M365, Microsoft Defender ATP, mdatp, recherche, requête, télémétrie, détections personnalisées, schéma, Kusto, Microsoft 365, mappage
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
- m365-initiative-m365-defender
ms.topic: article
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: b1738180e192baafa60f76fada1e433319922b91
ms.sourcegitcommit: 5e1b8c959a081022826fb09358730096248507ed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/09/2020
ms.locfileid: "48412681"
---
# <a name="migrate-advanced-hunting-queries-from-microsoft-defender-atp"></a>Migrer les requêtes de chasse avancées à partir de Microsoft Defender ATP

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**
- Protection Microsoft contre les menaces

Déplacez vos flux de travail de chasse avancés de Microsoft Defender ATP vers la recherche proactive de menaces à l’aide d’un ensemble plus large de données. Dans Microsoft Threat Protection, vous pouvez accéder aux données à partir d’autres solutions de sécurité Microsoft 365, notamment :

- Microsoft Defender – Protection avancée contre les menaces
- Office 365 – Protection avancée contre les menaces
- Microsoft Cloud App Security
- Azure Advanced Threat Protection

>[!NOTE]
>La plupart des clients Microsoft Defender ATP peuvent [utiliser la protection contre les menaces Microsoft sans licence supplémentaire](prerequisites.md#licensing-requirements). Pour commencer la transition de vos flux de travail de chasse avancés à partir de Microsoft Defender ATP, [activez Microsoft Threat Protection](mtp-enable.md).

Vous pouvez procéder à une transition sans affecter vos flux de travail Microsoft Defender ATP existants. Les requêtes enregistrées restent intactes et les règles de détection personnalisées continuent à s’exécuter et génèrent des alertes. Elles seront toutefois visibles dans la protection contre les menaces Microsoft. 

## <a name="schema-tables-in-microsoft-threat-protection-only"></a>Tables de schéma dans la protection Microsoft contre les menaces uniquement
Le [schéma de la chasse avancée à la protection de Microsoft contre les menaces](advanced-hunting-schema-tables.md) fournit des tables supplémentaires contenant des données provenant de différentes solutions de sécurité Microsoft 365. Les tableaux suivants sont disponibles uniquement dans la protection contre les menaces Microsoft :

| Nom du tableau | Description |
|------------|-------------|
| [AlertEvidence](advanced-hunting-alertevidence-table.md) | Fichiers, adresses IP, URL, utilisateurs ou périphériques associés à des alertes |
| [AlertInfo](advanced-hunting-alertinfo-table.md) | Alertes de Microsoft Defender ATP, Office 365 ATP, sécurité de l’application Cloud Microsoft et Azure ATP, y compris les informations de gravité et les catégories de menaces  |
| [AppFileEvents](advanced-hunting-appfileevents-table.md) | Activités liées aux fichiers dans les applications et les services Cloud |
| [EmailAttachmentInfo](advanced-hunting-emailattachmentinfo-table.md) | Informations sur les fichiers joints aux courriers électroniques |
| [EmailEvents](advanced-hunting-emailevents-table.md) | Événements de messagerie Microsoft 365, y compris les événements de remise et de blocage du courrier électronique |
| [EmailPostDeliveryEvents](advanced-hunting-emailpostdeliveryevents-table.md) | Événements de sécurité qui se produisent après la livraison, après que Microsoft 365 a remis les courriers électroniques à la boîte aux lettres du destinataire |
| [EmailUrlInfo](advanced-hunting-emailurlinfo-table.md) | Informations sur les URL des courriers électroniques |
| [IdentityDirectoryEvents](advanced-hunting-identitydirectoryevents-table.md) | Événements impliquant un contrôleur de domaine sur site exécutant Active Directory (AD). Ce tableau couvre une série d’événements liés à l’identité et de système sur le contrôleur de domaine. |
| [IdentityInfo](advanced-hunting-identityinfo-table.md) | Informations de compte provenant de différentes sources, notamment Azure Active Directory |
| [IdentityLogonEvents](advanced-hunting-identitylogonevents-table.md) | Événements d’authentification sur Active Directory et Microsoft Online Services |
| [IdentityQueryEvents](advanced-hunting-identityqueryevents-table.md) | Requêtes pour les objets Active Directory, tels que les utilisateurs, les groupes, les appareils et les domaines |

## <a name="map-devicealertevents-table"></a>Mapper la table DeviceAlertEvents
Les `AlertInfo` `AlertEvidence` tables et remplacent la `DeviceAlertEvents` table dans le schéma ATP de Microsoft Defender. En plus des données relatives aux alertes de périphérique, ces deux tables incluent des données sur les alertes pour les identités, les applications et les courriers électroniques.

Utilisez le tableau suivant pour vérifier la `DeviceAlertEvents` correspondance des colonnes et des colonnes dans les `AlertInfo` `AlertEvidence` tableaux et.

>[!TIP]
>Outre les colonnes du tableau suivant, le `AlertEvidence` tableau inclut de nombreuses autres colonnes qui fournissent une image plus holistique des alertes provenant de différentes sources. [Afficher toutes les colonnes AlertEvidence](advanced-hunting-alertevidence-table.md) 

| Colonne DeviceAlertEvents | Où trouver les mêmes données dans Microsoft Threat Protection |
|-------------|-----------|-------------|-------------|
| `AlertId` | `AlertInfo` et des  `AlertEvidence` tableaux |
| `Timestamp` | `AlertInfo` et des  `AlertEvidence` tableaux |
| `DeviceId` | `AlertEvidence` tabulaire |
| `DeviceName` | `AlertEvidence` tabulaire |
| `Severity` | `AlertInfo` tabulaire |
| `Category` | `AlertInfo` tabulaire |
| `Title` | `AlertInfo` tabulaire |
| `FileName` | `AlertEvidence` tabulaire |
| `SHA1` | `AlertEvidence` tabulaire |
| `RemoteUrl` | `AlertEvidence` tabulaire |
| `RemoteIP` | `AlertEvidence` tabulaire |
| `AttackTechniques` | `AlertInfo` tabulaire |
| `ReportId` | Cette colonne est généralement utilisée dans Microsoft Defender ATP pour localiser des enregistrements connexes dans d’autres tables. Dans Microsoft Threat Protection, vous pouvez obtenir des données connexes directement à partir du `AlertEvidence` tableau. |
| `Table` | Cette colonne est généralement utilisée dans Microsoft Defender ATP pour obtenir des informations supplémentaires sur les événements dans d’autres tables. Dans Microsoft Threat Protection, vous pouvez obtenir des données connexes directement à partir du `AlertEvidence` tableau. |

## <a name="adjust-existing-microsoft-defender-atp-queries"></a>Ajuster les requêtes Microsoft Defender ATP existantes
Les requêtes Microsoft Defender ATP fonctionnent telles quelles, sauf si elles font référence à la `DeviceAlertEvents` table. Pour utiliser ces requêtes dans Microsoft Threat Protection, appliquez les modifications suivantes :

- Remplacez `DeviceAlertEvents` par `AlertInfo` .
- Rejoignez les `AlertInfo` `AlertEvidence` tables et `AlertId` pour obtenir des données équivalentes.

### <a name="original-query"></a>Requête d’origine
La requête suivante utilise `DeviceAlertEvents` Microsoft Defender ATP pour obtenir les alertes qui impliquent des _powershell.exe_:

```kusto
DeviceAlertEvents
| where Timestamp > ago(7d) 
| where AttackTechniques has "PowerShell (T1086)" and FileName == "powershell.exe"
```
### <a name="modified-query"></a>Requête modifiée
La requête suivante a été ajustée pour une utilisation dans Microsoft Threat Protection. Au lieu de vérifier le nom de fichier directement à partir de `DeviceAlertEvents` , il rejoint `AlertEvidence` et recherche le nom de fichier dans cette table.

```kusto
AlertInfo 
| where Timestamp > ago(7d) 
| where AttackTechniques has "PowerShell (T1086)" 
| join AlertEvidence on AlertId
| where FileName == "powershell.exe"
```

## <a name="related-topics"></a>Voir aussi
- [Activer la Protection Microsoft contre les menaces](advanced-hunting-query-language.md)
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Chasse avancée dans Microsoft Defender ATP](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-overview)