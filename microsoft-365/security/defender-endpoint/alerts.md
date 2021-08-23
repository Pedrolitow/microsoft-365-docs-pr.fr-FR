---
title: API Obtenir des alertes
description: Découvrez les méthodes et les propriétés du type de ressource Alerte dans Microsoft Defender pour point de terminaison.
keywords: api, api de graphique, api pris en charge, obtenir, alertes, récent
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 77e7b86de5369b6a65224579de214d32c1f628e3
ms.sourcegitcommit: a0452cef05f2322b74967add41fd84ac4d07fe5c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2021
ms.locfileid: "58377976"
---
# <a name="alert-resource-type"></a>Type de ressource Alerte

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/?linkid=2154037)

- Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]


## <a name="methods"></a>Méthodes

Méthode |Type renvoyé |Description
:---|:---|:---
[Obtenir une alerte](get-alert-info-by-id.md) | [Alerte](alerts.md) | Obtenir un objet [d’alerte](alerts.md) unique.
[Répertorier les alertes](get-alerts.md) | [Collection d’alertes](alerts.md) | Liste de la collection [d’alertes.](alerts.md)
[Mettre à jour une alerte](update-alert.md) | [Alerte](alerts.md) | Mettre à jour une [alerte spécifique.](alerts.md)
[Alertes de mise à jour par lot](batch-update-alerts.md) | | Mettre à jour un lot [d’alertes.](alerts.md)
[Créer une alerte](create-alert-by-reference.md)|[Alerte](alerts.md)|Créez une alerte basée sur les données d’événement obtenues à partir [de la recherche avancée](run-advanced-query-api.md).
[Liste des domaines associés](get-alert-related-domain-info.md)|Collection de domaines| Ré lister les URL associées à l’alerte.
[Liste des fichiers associés](get-alert-related-files-info.md) | [Collection de](files.md) fichiers |  Liste des [entités](files.md) de fichier associées à [l’alerte.](alerts.md)
[Liste des IP associées](get-alert-related-ip-info.md) | Collection d’adresses IP | List IPs that are associated with the alert.
[Obtenir des ordinateurs associés](get-alert-related-machine-info.md) | [Ordinateur](machine.md) | [L’ordinateur](machine.md) associé à [l’alerte](alerts.md).
[Obtenir des utilisateurs associés](get-alert-related-user-info.md) | [Utilisateur](user.md) | Utilisateur [associé](user.md) à [l’alerte.](alerts.md)

## <a name="properties"></a>Propriétés

Propriété |    Type    |    Description
:---|:---|:---
id | String | ID d’alerte.
title | String | Titre de l’alerte.
description | String | Description de l’alerte.
alertCreationTime | Nullable DateTimeOffset | Date et heure (au UTC) de création de l’alerte.
lastEventTime | Nullable DateTimeOffset | Dernière occurrence de l’événement qui a déclenché l’alerte sur le même appareil.
firstEventTime | Nullable DateTimeOffset | Première occurrence de l’événement qui a déclenché l’alerte sur cet appareil.
lastUpdateTime | Nullable DateTimeOffset | Date et heure (au UTC) de la dernière mise à jour de l’alerte.
resolvedTime | Nullable DateTimeOffset | Date et heure à laquelle l’état de l’alerte a été modifié en « Résolu ».
incidentId | Nullable Long | ID [d’incident](view-incidents-queue.md) de l’alerte.
investigationId | Nullable Long | ID [d’examen](automated-investigations.md) lié à l’alerte.
investigationState | Nullable, enum | L’état actuel de [l’examen](automated-investigations.md). Les valeurs possibles sont : « Unknown » (inconnu), « Terminated » (terminé), « SuccessfullyRemediated », 'Suppress', 'Failed', 'PartiallyRemediated', 'Running', 'PendingApproval', 'PendingResource', 'PartiallySystemigated', 'TerminatedByUser', 'TerminatedBySystem', 'Queued', 'InnerFailure', 'PreexistingAlert', 'UnsupportedOs', 'UnsupportedAlertType', 'SuppressedAlert'.
assignedTo | String | Propriétaire de l’alerte.
rbacGroupName | String | Nom du groupe d’appareils RBAC.
mitreTechniques | String | ID Enterprise technique mitre.
relatedUser | String |  Détails de l’utilisateur associé à une alerte spécifique.
Sévérité  | Énum | Gravité de l’alerte. Les valeurs possibles sont : « UnSpecified » (non spécifié), « Informational » (informations), « Low » (faible), « Medium » (moyen) et « High » (élevé).
status | Énum | Spécifie l’état actuel de l’alerte. Les valeurs possibles sont : « Unknown » (inconnu), « New » (nouveau), « InProgress » (inprogress) et « Resolved » (résolu).
classification | Nullable, enum | Spécification de l’alerte. Les valeurs possibles sont : « Unknown » (inconnu), « FalsePositive » (fauxpositif), « TruePositive » (vraipositif).
détermination | Nullable, enum | Spécifie la détermination de l’alerte. Les valeurs possibles sont : 'NotAvailable', 'Apt', 'Malware', 'SecurityPersonnel', 'SecurityTesting', 'UnwantedSoftware', 'Other'.
category| String | Catégorie de l’alerte.
detectionSource | String | Source de détection.
threatFamilyName | String | Famille de menaces.
threatName | String | Nom de la menace.
machineId | String | ID d’une [entité](machine.md) d’ordinateur associée à l’alerte.
computerDnsName | String | [nom complet](machine.md) de l’ordinateur.
aadTenantId | String | ID Azure Active Directory de l’autre.
détecteurId | String | ID du détecteur qui a déclenché l’alerte.
commentaires | Liste des commentaires d’alerte | L’objet Comment de l’alerte contient : chaîne de commentaire, chaîne createdBy et heure de date createTime.
Évidence | Liste des preuves d’alerte | Preuve liée à l’alerte. Voir l’exemple ci-dessous.

### <a name="response-example-for-getting-single-alert"></a>Exemple de réponse pour l’obtention d’une alerte unique :

```http
GET https://api.securitycenter.microsoft.com/api/alerts/da637472900382838869_1364969609
```

```json
{
    "id": "da637472900382838869_1364969609",
    "incidentId": 1126093,
    "investigationId": null,
    "assignedTo": null,
    "severity": "Low",
    "status": "New",
    "classification": null,
    "determination": null,
    "investigationState": "Queued",
    "detectionSource": "WindowsDefenderAtp",
    "detectorId": "17e10bbc-3a68-474a-8aad-faef14d43952",
    "category": "Execution",
    "threatFamilyName": null,
    "title": "Low-reputation arbitrary code executed by signed executable",
    "description": "Binaries signed by Microsoft can be used to run low-reputation arbitrary code. This technique hides the execution of malicious code within a trusted process. As a result, the trusted process might exhibit suspicious behaviors, such as opening a listening port or connecting to a command-and-control (C&C) server.",
    "alertCreationTime": "2021-01-26T20:33:57.7220239Z",
    "firstEventTime": "2021-01-26T20:31:32.9562661Z",
    "lastEventTime": "2021-01-26T20:31:33.0577322Z",
    "lastUpdateTime": "2021-01-26T20:33:59.2Z",
    "resolvedTime": null,
    "machineId": "111e6dd8c833c8a052ea231ec1b19adaf497b625",
    "computerDnsName": "temp123.middleeast.corp.microsoft.com",
    "rbacGroupName": "A",
    "aadTenantId": "a839b112-1253-6432-9bf6-94542403f21c",
    "threatName": null,
    "mitreTechniques": [
        "T1064",
        "T1085",
        "T1220"
    ],
    "relatedUser": {
        "userName": "temp123",
        "domainName": "DOMAIN"
    },
    "comments": [
        {
            "comment": "test comment for docs",
            "createdBy": "secop123@contoso.com",
            "createdTime": "2021-01-26T01:00:37.8404534Z"
        }
    ],
    "evidence": [
        {
            "entityType": "User",
            "evidenceCreationTime": "2021-01-26T20:33:58.42Z",
            "sha1": null,
            "sha256": null,
            "fileName": null,
            "filePath": null,
            "processId": null,
            "processCommandLine": null,
            "processCreationTime": null,
            "parentProcessId": null,
            "parentProcessCreationTime": null,
            "parentProcessFileName": null,
            "parentProcessFilePath": null,
            "ipAddress": null,
            "url": null,
            "registryKey": null,
            "registryHive": null,
            "registryValueType": null,
            "registryValue": null,
            "accountName": "name",
            "domainName": "DOMAIN",
            "userSid": "S-1-5-21-11111607-1111760036-109187956-75141",
            "aadUserId": "11118379-2a59-1111-ac3c-a51eb4a3c627",
            "userPrincipalName": "temp123@microsoft.com",
            "detectionStatus": null
        },
        {
            "entityType": "Process",
            "evidenceCreationTime": "2021-01-26T20:33:58.6133333Z",
            "sha1": "ff836cfb1af40252bd2a2ea843032e99a5b262ed",
            "sha256": "a4752c71d81afd3d5865d24ddb11a6b0c615062fcc448d24050c2172d2cbccd6",
            "fileName": "rundll32.exe",
            "filePath": "C:\\Windows\\SysWOW64",
            "processId": 3276,
            "processCommandLine": "rundll32.exe  c:\\temp\\suspicious.dll,RepeatAfterMe",
            "processCreationTime": "2021-01-26T20:31:32.9581596Z",
            "parentProcessId": 8420,
            "parentProcessCreationTime": "2021-01-26T20:31:32.9004163Z",
            "parentProcessFileName": "rundll32.exe",
            "parentProcessFilePath": "C:\\Windows\\System32",
            "ipAddress": null,
            "url": null,
            "registryKey": null,
            "registryHive": null,
            "registryValueType": null,
            "registryValue": null,
            "accountName": null,
            "domainName": null,
            "userSid": null,
            "aadUserId": null,
            "userPrincipalName": null,
            "detectionStatus": "Detected"
        },
        {
            "entityType": "File",
            "evidenceCreationTime": "2021-01-26T20:33:58.42Z",
            "sha1": "8563f95b2f8a284fc99da44500cd51a77c1ff36c",
            "sha256": "dc0ade0c95d6db98882bc8fa6707e64353cd6f7767ff48d6a81a6c2aef21c608",
            "fileName": "suspicious.dll",
            "filePath": "c:\\temp",
            "processId": null,
            "processCommandLine": null,
            "processCreationTime": null,
            "parentProcessId": null,
            "parentProcessCreationTime": null,
            "parentProcessFileName": null,
            "parentProcessFilePath": null,
            "ipAddress": null,
            "url": null,
            "registryKey": null,
            "registryHive": null,
            "registryValueType": null,
            "registryValue": null,
            "accountName": null,
            "domainName": null,
            "userSid": null,
            "aadUserId": null,
            "userPrincipalName": null,
            "detectionStatus": "Detected"
        }
    ]
}
```
