---
title: L’antivirus Microsoft Defender exporte les propriétés et les méthodes de l’API des détails de l’antivirus de l’appareil
description: Découvrez comment exporter une liste des détails d’intégrité des appareils antivirus Microsoft Defender.
keywords: api, api graphe, api prises en charge, get, api d’intégrité de l’appareil, Microsoft Defender pour point de terminaison api de rapport api rapports microsoft defender, api de création de rapports microsoft defender pour point de terminaison, api de création de rapports Windows Defender, api de création de rapports Defender pour point de terminaison, API de rapport Windows Defender
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: v-jweston
author: jweston-1
ms.localizationpriority: medium
ms.date: 08/08/2022
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 91d8f711abf3a428b506d580227589253ee156a2
ms.sourcegitcommit: 402e0b2095b6cb141b8525a53194d47357bcd612
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2022
ms.locfileid: "67285080"
---
# <a name="export-device-antivirus-health-details-api-methods-and-properties"></a>Exporter les méthodes et propriétés de l’API des détails d’intégrité de l’antivirus de l’appareil

**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

[!include[Prerelease information](../../includes/prerelease.md)]

## <a name="export-device-antivirus-health-details-api-description"></a>Exporter la description de l’API des détails d’intégrité de l’antivirus de l’appareil

Récupère une liste des détails d’intégrité des appareils antivirus Microsoft Defender. Cette API a différents appels d’API (méthodes) pour obtenir différents types de données. Étant donné que la quantité de données peut être importante, il existe deux façons de les récupérer :

- **Réponse JSON**  L’API extrait toutes les données de votre organisation en tant que réponses JSON. Cette méthode est idéale pour _les petites organisations avec moins de 100 K d’appareils_. La réponse étant paginée, vous pouvez utiliser le \@champ odata.nextLink de la réponse pour extraire les résultats suivants.

- **via des fichiers** Cette solution d’API permet d’extraire de plus grandes quantités de données plus rapidement et de manière plus fiable. Par conséquent, il est recommandé pour les grandes organisations, avec plus de 100 000 appareils. Cette API extrait toutes les données de votre organisation en tant que fichiers de téléchargement. La réponse contient des URL pour télécharger toutes les données à partir du stockage Azure. Cette API vous permet de télécharger toutes vos données à partir du Stockage Azure comme suit :
  - Appelez l’API pour obtenir la liste des URL de téléchargement avec toutes les données de votre organisation.
  - Téléchargez tous les fichiers à l’aide des URL de téléchargement et traitez les données comme vous le souhaitez.

Les données collectées à l’aide de la _« réponse JSON_ ou _par le biais de fichiers_ » sont l’instantané actuel de l’état actuel. Il ne contient pas de données historiques. Pour collecter des données historiques, les clients doivent enregistrer les données dans leurs propres stockages de données.

> [!IMPORTANT]
>
> Pour que Windows&nbsp;Server&nbsp;2012&nbsp;R2 et Windows&nbsp;Server&nbsp;2016 apparaissent dans les rapports d’intégrité des appareils, ces appareils doivent être intégrés à l’aide du package de solution unifié moderne. Pour plus d’informations, consultez [Nouvelles fonctionnalités de la solution unifiée moderne pour Windows Server 2012 R2 et 2016](/microsoft-365/security/defender-endpoint/configure-server-endpoints#new-windows-server-2012-r2-and-2016-functionality-in-the-modern-unified-solution).

> [!NOTE]
>
> Pour plus d’informations sur l’utilisation de l’outil de création de rapports sur **l’intégrité de l’appareil et la conformité antivirus** dans le tableau de bord Sécurité de Microsoft 365, consultez : Rapport sur l’intégrité [des appareils et la conformité antivirus dans Microsoft Defender pour point de terminaison](machine-reports.md).
>

### <a name="11-export-device-antivirus-health-details-api-methods"></a>1.1 Exporter les méthodes d’API des détails d’intégrité de l’antivirus de l’appareil

Méthode|Type de données|Description
:---|:---|:---
**(Réponse JSON)**|Intégrité de l’antivirus Microsoft Defender par collection d’appareils. Voir : [1.2 Exporter les propriétés de l’API des détails d’intégrité de l’antivirus de l’appareil (réponse JSON)](#12-export-device-antivirus-health-details-api-properties-json-response)|Retourne une table avec une entrée pour chaque combinaison unique de DeviceId, ConfigurationId. | L’API extrait toutes les données de votre organisation en tant que réponses JSON. Cette méthode est idéale pour les petites organisations avec moins de 100 K d’appareils. La réponse étant paginée, vous pouvez utiliser le champ @odata.nextLink à partir de la réponse pour extraire les résultats suivants.
**(via des fichiers)**|Intégrité de l’antivirus Microsoft Defender par collection d’appareils. Voir : [1.3 Exporter les propriétés \(de l’API des détails d’intégrité de l’antivirus de l’appareil via des fichiers\)](#13-export-device-antivirus-health-details-api-properties-via-files)|Retourne une table avec une entrée pour chaque combinaison unique de DeviceId, ConfigurationId. |Cette solution d’API permet d’extraire de plus grandes quantités de données plus rapidement et de manière plus fiable. Par conséquent, il est recommandé pour les grandes organisations, avec plus de 100 000 appareils. Cette API extrait toutes les données de votre organisation en tant que fichiers de téléchargement. La réponse contient des URL pour télécharger toutes les données à partir du stockage Azure. Cette API vous permet de télécharger toutes vos données à partir du Stockage Azure comme suit : <ol><li>Appelez l’API pour obtenir la liste des URL de téléchargement avec toutes les données de votre organisation.</li><li>Téléchargez tous les fichiers à l’aide des URL de téléchargement et traitez les données comme vous le souhaitez.</li></ol>

### <a name="12-export-device-antivirus-health-details-api-properties-json-response"></a>1.2 Exporter les propriétés de l’API d’intégrité de l’antivirus de l’appareil (réponse JSON)

> [!NOTE]
>
> - Les propriétés définies dans le tableau suivant sont répertoriées par ordre alphabétique, par ID de propriété. Lors de l’exécution de cette API, la sortie résultante ne sera pas nécessairement retournée dans le même ordre que celui répertorié dans ce tableau.
> - Certaines colonnes supplémentaires peuvent être retournées dans la réponse. Ces colonnes sont temporaires et peuvent être supprimées. Utilisez uniquement les colonnes documentées.

| Propriété (ID) | Type de données | Description | Exemple de valeur retournée |
|:----|:----|:----|:----|
| avEngineUpdateTime | DateTimeOffset | Date et heure de la dernière mise à jour du moteur AV sur l’appareil | « 2022-08-04T12:44:02Z » |
| avEngineVersion | String | Version du moteur antivirus | "1.1.19400.3" |
| avIsEngineUpToDate | String | État à jour du moteur AV | « True », « False », « Unknown » |
| avIsPlatformUpToDate | String | Stauts à jour de la plateforme AV | « True », « False », « Unknown » |
| avIsSignatureUpToDate | String | État à jour de la signature AV | « True », « False », « Unknown » |
| avMode | String | Mode antivirus. | Chaque mode est une valeur entière typée par chaîne comprise entre 0 et 5. Reportez-vous au mappage ci-dessous pour voir la signification de sa valeur : <ul><li>'' = Autre</li><li> '0' = Actif</li><li> '1' = Passif</li><li> '2' = Désactivé</li><li> '3' = Autre</li><li> '4' = EDRBlocked</li><li>'5' = PassiveAudit</li></ul> |
| avPlatformUpdateTime | DateTimeOffset | Date et heure de la dernière mise à jour de la plateforme AV sur l’appareil | « 2022-08-04T12:44:02Z » |
| avPlatformVersion | String | Version de la plateforme antivirus | "4.18.2203.5" |
| avSignaturePublishTime | DateTimeOffset | Date et heure de publication de la build du renseignement de sécurité AV | « 2022-08-04T12:44:02Z » |
| avSignatureUpdateTime | DateTimeOffset | Date et heure de la dernière mise à jour du renseignement de sécurité AV sur l’appareil | « 2022-08-04T12:44:02Z » |
| avSignatureVersion | String | Version du renseignement de sécurité antivirus | "1.371.1323.0" |
| computerDnsName | String | Nom DNS | « SampleDns » |
| dataRefreshTimestamp | DateTimeOffset | Date et heure d’actualisation des données pour ce rapport | « 2022-08-04T12:44:02Z » |
| fullScanError | String | Codes d’erreur de l’analyse complète | « 0x80508023 » |
| fullScanResult | String | Résultat complet de l’analyse de cet appareil | « Terminé » <br> « Annulé » <br>« Échec » |
| fullScanTime | DateTimeOffset | Date et heure de fin de l’analyse complète | « 2022-08-04T12:44:02Z » |
| id | String | Machine GUID | « 30a8fa2826abf24d24379b23f8a44d471f00feab » |
| lastSeenTime | DateTimeOffset | Datetime de la dernière fois vue de cet ordinateur | « 2022-08-04T12:44:02Z » |
| machineId | String | Machine GUID | « 30a8fa2826abf24d24379b23f8a44d471f00feab » |
| osKind | String | Type de système d’exploitation | « windows », « mac », « linux » |
| osPlatform | String | Nom de la version principale du système d’exploitation | Windows 10, macOs |
| osVersion | String | Version du système d'exploitation | 10.0.18363.1440, 12.4.0.0 |
| quickScanError | String | Codes d’erreur de l’analyse rapide | « 0x80508023 » |
| quickScanResult | String | Résultat de l’analyse rapide de cet appareil | « Terminé » <br>« Annulé » <br>« Échec » |
| quickScanTime | DateTimeOffset | Date et heure de fin de l’analyse rapide   | « 2022-08-04T12:44:02Z » |
| rbacGroupId | Entier long | ID de groupe d’appareils auquel appartient cet ordinateur | 712 |
| rbacGroupName | String | Nom du groupe d’appareils auquel appartient cet ordinateur | « SampleGroup » |

### <a name="13-export-device-antivirus-health-details-api-properties-via-files"></a>1.3 Exporter les propriétés de l’API des détails d’intégrité de l’antivirus de l’appareil (via des fichiers)

> [!NOTE]
>
> - Les fichiers sont compressés par gzip & au format Json multiligne.
> - Les URL de téléchargement ne sont valides que pendant 3 heures ; sinon, vous pouvez utiliser le paramètre.
> - Pour une vitesse de téléchargement maximale de vos données, vous pouvez vous assurer que vous téléchargez à partir de la même région Azure que celle où résident vos données.
> - Chaque enregistrement est d’environ 1 Ko de données. Vous devez en tenir compte lors du choix du paramètre pageSize approprié pour vous.
> - Certaines colonnes supplémentaires peuvent être retournées dans la réponse. Ces colonnes sont temporaires et peuvent être supprimées. Utilisez uniquement les colonnes documentées.

| Propriété (ID) | Type de données | Description | Exemple de valeur retournée |
|:----|:----|:----|:----|
| Exporter des fichiers | array[string] | Liste des URL de téléchargement pour les fichiers contenant l’instantané actuel de l’organisation. | ["https://tvmexportstrstgeus.blob.core.windows.net/tvm-export...1", "https://tvmexportstrstgeus.blob.core.windows.net/tvm-export...2"] |
| GeneratedTime | String | Heure à laquelle l’exportation a été générée. | 2022-05-20T08:00:00Z |

> [!NOTE]
> Dans chacun des fichiers Export, une propriété « DeviceGatheredInfo » contenant les données sur les informations antivirus est disponible. Chacun de ses attributs peut vous fournir des informations sur l’intégrité de l’appareil et son état.

## <a name="see-also"></a>Voir aussi

[Exporter le rapport d’intégrité de l’antivirus de l’appareil](device-health-export-antivirus-health-report-api.md)

[Rapports sur l’intégrité et la conformité des appareils](machine-reports.md)
