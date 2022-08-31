---
title: Migrer des requêtes de chasse avancées à partir de Microsoft Defender pour point de terminaison
description: Découvrez comment ajuster vos requêtes Microsoft Defender pour point de terminaison afin de pouvoir les utiliser dans Microsoft 365 Defender
keywords: repérage avancé, repérage de menaces, repérage de cybermenaces, Microsoft 365 Defender, microsoft 365, m365, Microsoft Defender pour point de terminaison, recherche, requête, télémétrie, détections personnalisées, schéma, kusto, mappage
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
- M365-security-compliance
ms.topic: article
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 05e498d7208e9cd72cde4b6899fedc70a70db766
ms.sourcegitcommit: 10e6abe740e27000e223378eb17d657a47555fa8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2022
ms.locfileid: "67483517"
---
# <a name="migrate-advanced-hunting-queries-from-microsoft-defender-for-endpoint"></a>Migrer des requêtes de chasse avancées à partir de Microsoft Defender pour point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**
- Microsoft 365 Defender

Déplacez vos flux de travail de chasse avancés de Microsoft Defender pour point de terminaison à la recherche proactive des menaces à l’aide d’un ensemble plus large de données. Dans Microsoft 365 Defender, vous avez accès aux données d’autres solutions de sécurité Microsoft 365, notamment :

- Microsoft Defender pour point de terminaison
- Microsoft Defender pour Office 365
- Microsoft Defender for Cloud Apps
- Microsoft Defender pour l’identité

>[!NOTE]
>La plupart des clients Microsoft Defender pour point de terminaison peuvent [utiliser Microsoft 365 Defender sans licences supplémentaires](prerequisites.md#licensing-requirements). Pour commencer la transition de vos flux de travail de chasse avancés à partir de Defender pour point de terminaison, [activez Microsoft 365 Defender](m365d-enable.md).

Vous pouvez effectuer une transition sans affecter vos workflows Defender pour point de terminaison existants. Les requêtes enregistrées restent intactes et les règles de détection personnalisées continuent à s’exécuter et à générer des alertes. Toutefois, ils seront visibles dans Microsoft 365 Defender.

## <a name="schema-tables-in-microsoft-365-defender-only"></a>Tables de schémas dans Microsoft 365 Defender uniquement

Le [Microsoft 365 Defender schéma de repérage avancé](advanced-hunting-schema-tables.md) fournit des tables supplémentaires contenant des données provenant de différentes solutions de sécurité Microsoft 365. Les tableaux suivants sont disponibles uniquement dans Microsoft 365 Defender :

| Nom du tableau | Description |
|------------|-------------|
| [AlertEvidence](advanced-hunting-alertevidence-table.md) | Fichiers, adresses IP, URL, utilisateurs ou appareils associés aux alertes |
| [AlertInfo](advanced-hunting-alertinfo-table.md) | Alertes provenant de Microsoft Defender pour point de terminaison, Microsoft Defender pour Office 365, Microsoft Defender for Cloud Apps et Microsoft Defender pour Identity, y compris les informations de gravité et les catégories de menaces  |
| [EmailAttachmentInfo](advanced-hunting-emailattachmentinfo-table.md) | Informations sur les fichiers joints aux e-mails |
| [EmailEvents](advanced-hunting-emailevents-table.md) | Événements d’e-mails Microsoft 365, y compris les événements de remise et de blocage d’e-mail |
| [EmailPostDeliveryEvents](advanced-hunting-emailpostdeliveryevents-table.md) | Événements de sécurité qui se produisent après la remise, une fois que Microsoft 365 a remis les e-mails à la boîte aux lettres du destinataire |
| [EmailUrlInfo](advanced-hunting-emailurlinfo-table.md) | Informations sur les URL des e-mails |
| [IdentityDirectoryEvents](advanced-hunting-identitydirectoryevents-table.md) | Événements impliquant un contrôleur de domaine local exécutant Active Directory (AD). Ce tableau couvre un ensemble d’événements liés à l’identité, ainsi que des événements système sur le contrôleur de domaine. |
| [IdentityInfo](advanced-hunting-identityinfo-table.md) | Informations de compte provenant de différentes sources, notamment Azure Active Directory |
| [IdentityLogonEvents](advanced-hunting-identitylogonevents-table.md) | Événements d’authentification sur Active Directory et les services en ligne Microsoft |
| [IdentityQueryEvents](advanced-hunting-identityqueryevents-table.md) | Requêtes pour les objets Active Directory, tels que les utilisateurs, les groupes, les appareils et les domaines |

>[!IMPORTANT]
> Les requêtes et les détections personnalisées qui utilisent des tables de schémas disponibles uniquement dans Microsoft 365 Defender ne peuvent être affichées que dans Microsoft 365 Defender.

## <a name="map-devicealertevents-table"></a>Mapper la table DeviceAlertEvents

Les `AlertInfo` tables et `AlertEvidence` les tables remplacent la `DeviceAlertEvents` table dans le schéma Microsoft Defender pour point de terminaison. Outre les données relatives aux alertes d’appareil, ces deux tables incluent des données sur les alertes pour les identités, les applications et les e-mails.

Utilisez le tableau suivant pour vérifier comment `DeviceAlertEvents` les colonnes sont mappées aux colonnes des tables et `AlertEvidence` des `AlertInfo` colonnes.

> [!TIP]
> En plus des colonnes du tableau suivant, le `AlertEvidence` tableau inclut de nombreuses autres colonnes qui fournissent une image plus holistique des alertes provenant de différentes sources. [Afficher toutes les colonnes AlertEvidence](advanced-hunting-alertevidence-table.md)

| Colonne DeviceAlertEvents | Où trouver les mêmes données dans Microsoft 365 Defender |
|-------------|-----------|-------------|-------------|
| `AlertId` | `AlertInfo` et  `AlertEvidence` tables |
| `Timestamp` | `AlertInfo` et  `AlertEvidence` tables |
| `DeviceId` | `AlertEvidence` Table |
| `DeviceName` | `AlertEvidence` Table |
| `Severity` | `AlertInfo` Table |
| `Category` | `AlertInfo` Table |
| `Title` | `AlertInfo` Table |
| `FileName` | `AlertEvidence` Table |
| `SHA1` | `AlertEvidence` Table |
| `RemoteUrl` | `AlertEvidence` Table |
| `RemoteIP` | `AlertEvidence` Table |
| `AttackTechniques` | `AlertInfo` Table |
| `ReportId` | Cette colonne est généralement utilisée dans Microsoft Defender pour point de terminaison pour localiser les enregistrements associés dans d’autres tables. Dans Microsoft 365 Defender, vous pouvez obtenir des données associées directement à partir de la `AlertEvidence` table. |
| `Table` | Cette colonne est généralement utilisée dans Microsoft Defender pour point de terminaison pour obtenir des informations supplémentaires sur les événements dans d’autres tables. Dans Microsoft 365 Defender, vous pouvez obtenir des données associées directement à partir de la `AlertEvidence` table. |

## <a name="adjust-existing-microsoft-defender-for-endpoint-queries"></a>Ajuster les requêtes Microsoft Defender pour point de terminaison existantes

Microsoft Defender pour point de terminaison requêtes fonctionnent telles quelle, sauf si elles font référence à la `DeviceAlertEvents` table. Pour utiliser ces requêtes dans Microsoft 365 Defender, appliquez les modifications suivantes :

- Remplacez `DeviceAlertEvents` par `AlertInfo`.
- Joignez les tables et les `AlertInfo` `AlertEvidence` tables `AlertId` pour obtenir des données équivalentes.

### <a name="original-query"></a>Requête d’origine

La requête suivante utilise `DeviceAlertEvents` dans Microsoft Defender pour point de terminaison pour obtenir les alertes qui impliquent _powershell.exe_:

```kusto
DeviceAlertEvents
| where Timestamp > ago(7d)
| where AttackTechniques has "PowerShell (T1086)" and FileName == "powershell.exe"
```

### <a name="modified-query"></a>Requête modifiée

La requête suivante a été ajustée pour une utilisation dans Microsoft 365 Defender. Au lieu de vérifier directement le nom du `DeviceAlertEvents`fichier, il joint `AlertEvidence` et recherche le nom de fichier dans cette table.

```kusto
AlertInfo
| where Timestamp > ago(7d)
| where AttackTechniques has "PowerShell (T1086)"
| join AlertEvidence on AlertId
| where FileName == "powershell.exe"
```

## <a name="migrate-custom-detection-rules"></a>Migrer des règles de détection personnalisées

Lorsque Microsoft Defender pour point de terminaison règles sont modifiées sur Microsoft 365 Defender, elles continuent de fonctionner comme avant si la requête résultante examine uniquement les tables d’appareils.

Par exemple, les alertes générées par des règles de détection personnalisées qui interrogent uniquement les tables d’appareils continuent d’être remises à votre SIEM et génèrent des notifications par e-mail, selon la façon dont vous les avez configurées dans Microsoft Defender pour point de terminaison. Toutes les règles de suppression existantes dans Defender pour point de terminaison continueront également à s’appliquer.

Une fois que vous avez modifié une règle Defender pour point de terminaison afin qu’elle interroge les tables d’identité et de messagerie, qui ne sont disponibles que dans Microsoft 365 Defender, la règle est automatiquement déplacée vers Microsoft 365 Defender.

Alertes générées par la règle migrée :

- Ne sont plus visibles dans le portail Defender pour point de terminaison (Centre de sécurité Microsoft Defender)
- Arrêtez d’être remis à votre SIEM ou générez des notifications par e-mail. Pour contourner cette modification, configurez les notifications via Microsoft 365 Defender pour obtenir les alertes. Vous pouvez utiliser [l’API Microsoft 365 Defender](api-incident.md) pour recevoir des notifications pour les alertes de détection des clients ou les incidents connexes.
- Ne sera pas supprimé par Microsoft Defender pour point de terminaison règles de suppression. Pour empêcher la génération d’alertes pour certains utilisateurs, appareils ou boîtes aux lettres, modifiez les requêtes correspondantes pour exclure explicitement ces entités.

Si vous modifiez une règle de cette façon, vous êtes invité à confirmer l’application de ces modifications.

Les nouvelles alertes générées par les règles de détection personnalisées dans Microsoft 365 Defender sont affichées dans une page d’alerte qui fournit les informations suivantes :

- Titre et description de l’alerte
- Ressources impactées
- Actions effectuées en réponse à l’alerte
- Résultats de la requête qui ont déclenché l’alerte
- Informations sur la règle de détection personnalisée

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/new-alert-page.png" alt-text="Exemple de page d’alerte qui affiche de nouvelles alertes générées par des règles de détection personnalisées dans Microsoft 365 Defender portail" lightbox="../../media/new-alert-page.png":::

## <a name="write-queries-without-devicealertevents"></a>Écrire des requêtes sans DeviceAlertEvents

Dans le schéma Microsoft 365 Defender, les tables et `AlertEvidence` les `AlertInfo` tables sont fournies pour prendre en charge l’ensemble diversifié d’informations qui accompagnent les alertes provenant de différentes sources.

Pour obtenir les mêmes informations d’alerte que celles que vous avez utilisées pour obtenir de la `DeviceAlertEvents` table dans le schéma Microsoft Defender pour point de terminaison, filtrez la `AlertInfo` table`ServiceSource`, puis joignez chaque ID unique à la `AlertEvidence` table, qui fournit des informations détaillées sur l’événement et l’entité.

Consultez l’exemple de requête ci-dessous :

```kusto
AlertInfo
| where Timestamp > ago(7d)
| where ServiceSource == "Microsoft Defender for Endpoint"
| join AlertEvidence on AlertId
```

Cette requête génère beaucoup plus de colonnes que `DeviceAlertEvents` dans le schéma Microsoft Defender pour point de terminaison. Pour que les résultats restent gérables, utilisez cette option `project` pour obtenir uniquement les colonnes qui vous intéressent. L’exemple ci-dessous projette des colonnes qui peuvent vous intéresser lorsque l’enquête a détecté une activité PowerShell :

```kusto
AlertInfo
| where Timestamp > ago(7d)
| where ServiceSource == "Microsoft Defender for Endpoint"
    and AttackTechniques has "powershell"
| join AlertEvidence on AlertId
| project Timestamp, Title, AlertId, DeviceName, FileName, ProcessCommandLine
```

Si vous souhaitez filtrer des entités spécifiques impliquées dans les alertes, vous pouvez le faire en spécifiant le type d’entité et `EntityType` la valeur que vous souhaitez filtrer. L’exemple suivant recherche une adresse IP spécifique :

```kusto
AlertInfo
| where Title == "Insert_your_alert_title"
| join AlertEvidence on AlertId
| where EntityType == "Ip" and RemoteIP == "192.88.99.01"
```

## <a name="see-also"></a>Voir aussi

- [Activer Microsoft 365 Defender](advanced-hunting-query-language.md)
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Repérage avancé dans Microsoft Defender pour point de terminaison](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-overview)
