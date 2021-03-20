---
title: Migrer des requêtes de recherche avancée à partir de Microsoft Defender pour le point de terminaison
description: Découvrez comment ajuster vos requêtes Microsoft Defender for Endpoint afin de pouvoir les utiliser dans Microsoft 365 Defender
keywords: repérage avancé, repérage de menace, repérage de cybermenace, protection microsoft contre les menaces, microsoft 365, mtp, m365, microsoft defender atp, mdatp, recherche, requête, télémétrie, détections personnalisées, schéma, kusto, microsoft 365, mappage
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
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
ms.custom: seo-marvel-apr2020
ms.technology: m365d
ms.openlocfilehash: 5f356c5861586d4435a619a056a6fa1a0afc53f0
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50904137"
---
# <a name="migrate-advanced-hunting-queries-from-microsoft-defender-for-endpoint"></a>Migrer des requêtes de recherche avancée à partir de Microsoft Defender pour le point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**
- Microsoft 365 Defender

Déplacez vos flux de travail de recherche avancée de Microsoft Defender pour point de terminaison pour qu’ils recherchent de manière proactive les menaces à l’aide d’un ensemble plus large de données. Dans Microsoft 365 Defender, vous avez accès aux données à partir d’autres solutions de sécurité Microsoft 365, notamment :

- Microsoft Defender pour point de terminaison
- Microsoft Defender pour Office 365
- Microsoft Cloud App Security
- Microsoft Defender pour l’identité

>[!NOTE]
>La plupart des clients Microsoft Defender pour Endpoint peuvent [utiliser Microsoft 365 Defender sans licences supplémentaires.](prerequisites.md#licensing-requirements) Pour commencer la transition de vos flux de travail de recherche avancée à partir de Defender for Endpoint, [activer Microsoft 365 Defender](mtp-enable.md).

Vous pouvez faire la transition sans affecter vos flux de travail Defender for Endpoint existants. Les requêtes enregistrées restent intactes et les règles de détection personnalisées continuent à s’exécuter et à générer des alertes. Toutefois, elles seront visibles dans Microsoft 365 Defender. 

## <a name="schema-tables-in-microsoft-365-defender-only"></a>Tableaux de schéma dans Microsoft 365 Defender uniquement
Le schéma de [recherche avancée Microsoft 365 Defender](advanced-hunting-schema-tables.md) fournit des tableaux supplémentaires contenant des données de diverses solutions de sécurité Microsoft 365. Les tableaux suivants sont disponibles uniquement dans Microsoft 365 Defender :

| Nom du tableau | Description |
|------------|-------------|
| [AlertEvidence](advanced-hunting-alertevidence-table.md) | Fichiers, adresses IP, URL, utilisateurs ou appareils associés à des alertes |
| [AlertInfo](advanced-hunting-alertinfo-table.md) | Alertes de Microsoft Defender pour le point de terminaison, Microsoft Defender pour Office 365, Microsoft Cloud App Security et Microsoft Defender pour l’identité, y compris les informations de gravité et les catégories de menace  |
| [AppFileEvents](advanced-hunting-appfileevents-table.md) | Activités liées aux fichiers dans les applications et services cloud |
| [EmailAttachmentInfo](advanced-hunting-emailattachmentinfo-table.md) | Informations sur les fichiers joints aux e-mails |
| [EmailEvents](advanced-hunting-emailevents-table.md) | Événements de messagerie Microsoft 365, y compris les événements de remise et de blocage du courrier électronique |
| [EmailPostDeliveryEvents](advanced-hunting-emailpostdeliveryevents-table.md) | Événements de sécurité qui se produisent après la remise, une fois que Microsoft 365 a remis les messages électroniques à la boîte aux lettres du destinataire |
| [EmailUrlInfo](advanced-hunting-emailurlinfo-table.md) | Informations sur les URL des e-mails |
| [IdentityDirectoryEvents](advanced-hunting-identitydirectoryevents-table.md) | Événements impliquant un contrôleur de domaine local exécutant Active Directory (AD). Ce tableau couvre une plage d’événements liés à l’identité et d’événements système sur le contrôleur de domaine. |
| [IdentityInfo](advanced-hunting-identityinfo-table.md) | Informations de compte provenant de différentes sources, notamment Azure Active Directory |
| [IdentityLogonEvents](advanced-hunting-identitylogonevents-table.md) | Événements d’authentification sur Active Directory et les services en ligne Microsoft |
| [IdentityQueryEvents](advanced-hunting-identityqueryevents-table.md) | Requêtes pour les objets Active Directory, tels que les utilisateurs, les groupes, les appareils et les domaines |

>[!IMPORTANT]
> Les requêtes et les détections personnalisées qui utilisent des tables de schéma uniquement disponibles dans Microsoft 365 Defender peuvent uniquement être vues dans Microsoft 365 Defender.

## <a name="map-devicealertevents-table"></a>Table Map DeviceAlertEvents
Les `AlertInfo` `AlertEvidence` tableaux et les tables `DeviceAlertEvents` remplacent le tableau dans le schéma Microsoft Defender for Endpoint. En plus des données sur les alertes d’appareil, ces deux tableaux incluent des données sur les alertes pour les identités, les applications et les e-mails.

Utilisez le tableau suivant pour vérifier la façon dont les `DeviceAlertEvents` colonnes sont m mapées aux colonnes des `AlertInfo` tableaux et des `AlertEvidence` colonnes.

>[!TIP]
>Outre les colonnes du tableau suivant, le tableau inclut de nombreuses autres colonnes qui fournissent une image plus globale des alertes provenant de `AlertEvidence` différentes sources. [Voir toutes les colonnes AlertEvidence](advanced-hunting-alertevidence-table.md) 

| Colonne DeviceAlertEvents | Où trouver les mêmes données dans Microsoft 365 Defender |
|-------------|-----------|-------------|-------------|
| `AlertId` | `AlertInfo` et  `AlertEvidence` tableaux |
| `Timestamp` | `AlertInfo` et  `AlertEvidence` tableaux |
| `DeviceId` | `AlertEvidence` table |
| `DeviceName` | `AlertEvidence` table |
| `Severity` | `AlertInfo` table |
| `Category` | `AlertInfo` table |
| `Title` | `AlertInfo` table |
| `FileName` | `AlertEvidence` table |
| `SHA1` | `AlertEvidence` table |
| `RemoteUrl` | `AlertEvidence` table |
| `RemoteIP` | `AlertEvidence` table |
| `AttackTechniques` | `AlertInfo` table |
| `ReportId` | Cette colonne est généralement utilisée dans Microsoft Defender pour point de terminaison pour rechercher des enregistrements connexes dans d’autres tables. Dans Microsoft 365 Defender, vous pouvez obtenir des données associées directement à partir du `AlertEvidence` tableau. |
| `Table` | Cette colonne est généralement utilisée dans Microsoft Defender pour le point de terminaison pour des informations supplémentaires sur les événements dans d’autres tableaux. Dans Microsoft 365 Defender, vous pouvez obtenir des données associées directement à partir du `AlertEvidence` tableau. |

## <a name="adjust-existing-microsoft-defender-for-endpoint-queries"></a>Ajuster les requêtes Microsoft Defender pour les points de terminaison existantes
Les requêtes Microsoft Defender pour les points de terminaison fonctionneront telles qu’elles sont sauf si elles font référence au `DeviceAlertEvents` tableau. Pour utiliser ces requêtes dans Microsoft 365 Defender, appliquez les modifications ci-après :

- Remplacez `DeviceAlertEvents` par `AlertInfo` .
- Joignez les `AlertInfo` tables et les tables pour obtenir des données `AlertEvidence` `AlertId` équivalentes.

### <a name="original-query"></a>Requête d’origine
La requête suivante utilise Microsoft Defender pour le point de terminaison pour obtenir les alertes qui `DeviceAlertEvents` impliquent _powershell.exe_:

```kusto
DeviceAlertEvents
| where Timestamp > ago(7d) 
| where AttackTechniques has "PowerShell (T1086)" and FileName == "powershell.exe"
```
### <a name="modified-query"></a>Requête modifiée
La requête suivante a été ajustée pour être utilisé dans Microsoft 365 Defender. Au lieu de vérifier le nom de fichier directement à partir de , il joint et vérifie le nom de fichier `DeviceAlertEvents` `AlertEvidence` dans cette table.

```kusto
AlertInfo 
| where Timestamp > ago(7d) 
| where AttackTechniques has "PowerShell (T1086)" 
| join AlertEvidence on AlertId
| where FileName == "powershell.exe"
```

## <a name="migrate-custom-detection-rules"></a>Migrer des règles de détection personnalisées

Lorsque les règles microsoft Defender pour les points de terminaison sont modifiées sur Microsoft 365 Defender, elles continuent de fonctionner comme avant si la requête résultante examine uniquement les tables des appareils. 

Par exemple, les alertes générées par des règles de détection personnalisées qui interrogent uniquement les tables des appareils continueront d’être remis à votre SIEM et de générer des notifications par courrier électronique, selon la façon dont vous les avez configurées dans Microsoft Defender pour endpoint. Toutes les règles de suppression existantes dans Defender pour le point de terminaison continueront également de s’appliquer.

Une fois que vous avez modifié une règle Defender pour point de terminaison afin qu’elle interroge les tables d’identité et de messagerie, qui sont uniquement disponibles dans Microsoft 365 Defender, la règle est automatiquement déplacée vers Microsoft 365 Defender. 

Alertes générées par la règle migré :

- Ne sont plus visibles dans le portail Defender pour point de terminaison (Centre de sécurité Microsoft Defender)
- Ne plus être remis à votre SIEM ou générer des notifications par courrier électronique. Pour contourner ce changement, configurez les notifications via Microsoft 365 Defender pour obtenir les alertes. Vous pouvez utiliser [l’API Microsoft 365 Defender](api-incident.md) pour recevoir des notifications pour les alertes de détection des clients ou les incidents connexes.
- Ne sera pas supprimé par les règles de suppression des points de terminaison de Microsoft Defender. Pour empêcher la générer des alertes pour certains utilisateurs, périphériques ou boîtes aux lettres, modifiez les requêtes correspondantes pour exclure explicitement ces entités.

Si vous modifiez une règle de cette façon, vous serez invité à confirmer avant que de telles modifications ne soient appliquées.

Les nouvelles alertes générées par des règles de détection personnalisées dans le portail Microsoft 365 Defender s’affichent dans une page d’alerte qui fournit les informations suivantes :

- Titre et description de l’alerte 
- Ressources impactées
- Actions prises en réponse à l’alerte
- Résultats de la requête qui ont déclenché l’alerte 
- Informations sur la règle de détection personnalisée 
 
![Image de la nouvelle page d’alerte](../../media/new-alert-page.png)

## <a name="write-queries-without-devicealertevents"></a>Écrire des requêtes sans DeviceAlertEvents

Dans le schéma Microsoft 365 Defender, les tableaux et les tableaux sont fournis pour prendre en charge les diverses informations qui accompagnent les alertes provenant de `AlertInfo` `AlertEvidence` différentes sources. 

Pour obtenir les mêmes informations d’alerte que vous avez utilisées pour obtenir à partir de la table dans le schéma Microsoft Defender for Endpoint, filtrez la table, puis joignez chaque ID unique à la table, qui fournit des informations détaillées sur l’événement et `DeviceAlertEvents` `AlertInfo` l’entité. `ServiceSource` `AlertEvidence` 

Consultez l’exemple de requête ci-dessous :

```kusto
AlertInfo
| where Timestamp > ago(7d)
| where ServiceSource == "Microsoft Defender for Endpoint"
| join AlertEvidence on AlertId
```

Cette requête produit beaucoup plus de colonnes que dans le schéma `DeviceAlertEvents` Microsoft Defender for Endpoint. Pour que les résultats restent gérables, utilisez cette rubrique `project` pour obtenir uniquement les colonnes qui vous intéressent. L’exemple ci-dessous projete les colonnes qui peuvent vous intéresser lorsque l’enquête a détecté une activité PowerShell :

```kusto
AlertInfo
| where Timestamp > ago(7d)
| where ServiceSource == "Microsoft Defender for Endpoint"
    and AttackTechniques has "powershell"
| join AlertEvidence on AlertId
| project Timestamp, Title, AlertId, DeviceName, FileName, ProcessCommandLine 
```

Si vous souhaitez filtrer des entités spécifiques impliquées dans les alertes, vous pouvez le faire en spécifiant le type d’entité et la valeur que vous souhaitez `EntityType` filtrer. L’exemple suivant recherche une adresse IP spécifique :

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
- [Recherche avancée dans Microsoft Defender pour point de terminaison](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-overview)