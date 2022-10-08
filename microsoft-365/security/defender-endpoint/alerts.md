---
title: API Obtenir des alertes
description: Découvrez les méthodes et les propriétés du type de ressource Alerte dans Microsoft Defender pour point de terminaison.
keywords: api, api graphe, api prises en charge, get, alertes, recent
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- tier1
ms.topic: article
ms.subservice: mde
ms.custom: api
search.appverid: met150
ms.openlocfilehash: 551c29054747498a1728399b280381cfa7331f23
ms.sourcegitcommit: b9282493c371d59c2e583b9803825096499b5e2c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68157499"
---
# <a name="alert-resource-type"></a>Type de ressource d’alerte

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

>Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="methods"></a>Méthodes

|Méthode|Type renvoyé|Description|
|---|---|---|
|[Obtenir une alerte](get-alert-info-by-id.md)|[Alerte](alerts.md)|Obtenez un objet [d’alerte](alerts.md) unique.|
|[Répertorier les alertes](get-alerts.md)|[Collection d’alertes](alerts.md)|[Répertorier la collection d’alertes](alerts.md).|
|[Mettre à jour une alerte](update-alert.md)|[Alerte](alerts.md)|Mettre à jour une [alerte](alerts.md) spécifique.|
|[Alertes de mise à jour par lot](batch-update-alerts.md)||Mettez à jour un lot [d’alertes](alerts.md).|
|[Créer une alerte](create-alert-by-reference.md)|[Alerte](alerts.md)|Créez une alerte basée sur les données d’événement obtenues à partir [d’Advanced Hunting](run-advanced-query-api.md).|
|[Répertorier les domaines associés](get-alert-related-domain-info.md)|Collection de domaines|Répertorie les URL associées à l’alerte.|
|[Répertorier les fichiers associés](get-alert-related-files-info.md)|[Collection de fichiers](files.md)|Répertoriez les entités de [fichier](files.md) associées à [l’alerte](alerts.md).|
|[Répertorier les adresses IP associées](get-alert-related-ip-info.md)|Collection d’adresses IP|Répertorie les adresses IP associées à l’alerte.|
|[Obtenir les machines associées](get-alert-related-machine-info.md)|[Ordinateur](machine.md)|[Ordinateur](machine.md) associé à [l’alerte](alerts.md).|
|[Obtenir des utilisateurs associés](get-alert-related-user-info.md)|[Utilisateur](user.md)|[Utilisateur](user.md) associé à [l’alerte](alerts.md).|

## <a name="properties"></a>Propriétés

|Propriété|Type|Description|
|---|---|---|
|id|Chaîne|ID d’alerte.|
|title|String|Titre de l’alerte.|
|description|String|Description de l’alerte.|
|alertCreationTime|Nullable DateTimeOffset|Date et heure (en UTC) de la création de l’alerte.|
|lastEventTime|Nullable DateTimeOffset|Dernière occurrence de l’événement qui a déclenché l’alerte sur le même appareil.|
|firstEventTime|Nullable DateTimeOffset|Première occurrence de l’événement qui a déclenché l’alerte sur cet appareil.|
|lastUpdateTime|Nullable DateTimeOffset|Date et heure (en UTC) de la dernière mise à jour de l’alerte.|
|resolvedTime|Nullable DateTimeOffset|Date et heure auxquelles l’état de l’alerte a été remplacé par « Résolu ».|
|incidentId|Nullable Long|ID [d’incident](view-incidents-queue.md) de l’alerte.|
|investigationId|Nullable Long|ID [d’investigation](automated-investigations.md) associé à l’alerte.|
|investigationState|Énumération nullable|État actuel de [l’investigation](automated-investigations.md). Les valeurs possibles sont : ' Unknown', 'Terminateed', 'SuccessfullyRemediated', 'Benign', 'Failed', 'PartiallyRemediated', 'Running', 'PendingApproval', 'PendingResource', 'PartiallyInvestigated', 'TerminateedByUser', 'TerminateedBySystem', 'Queued', 'InnerFailure', 'PreexistingAlert', 'UnsupportedOs', 'UnsupportedAlertType', 'SuppressedAlert'.|
|assignedTo|Chaîne|Propriétaire de l’alerte.|
|rbacGroupName|Chaîne|Nom du groupe d’appareils RBAC.|
|mitreTechniques|Chaîne|ID de technique Mitre Enterprise.|
|relatedUser|Chaîne|Détails de l’utilisateur liés à une alerte spécifique.|
|Sévérité |Énum|Gravité de l’alerte. Les valeurs possibles sont : « UnSpecified », « Informational », « Low », « Medium » et « High ».|
|status|Énum|Spécifie l’état actuel de l’alerte. Les valeurs possibles sont : « Unknown », « New », « InProgress » et « Resolved ».|
|classification|Énumération nullable|Spécification de l’alerte. Les valeurs possibles sont : `TruePositive`, `Informational, expected activity`et `FalsePositive`.|
|Détermination|Énumération nullable|Spécifie la détermination de l’alerte. <p>Les valeurs de détermination possibles pour chaque classification sont les suivantes : <br><li> <b>Vrai positif</b> : `Multistage attack` (MultiStagedAttack), `Malicious user activity` (MaliciousUserActivity), `Compromised account` (CompromisedUser) : envisagez de modifier le nom de l’énumération dans l’API publique en conséquence, `Malware` (Malware), `Phishing` (Phishing), `Unwanted software` (UnwantedSoftware) et `Other` (Other). <li> <b>Activité informationnelle et attendue :</b> `Security test` (SecurityTesting), `Line-of-business application` (LineOfBusinessApplication), `Confirmed activity` (ConfirmedUserActivity) : envisagez de modifier le nom de l’énumération dans l’API publique en conséquence et `Other` (Autre). <li>  <b>Faux positif :</b> `Not malicious` (Clean) : envisagez de modifier le nom de l’énumération dans l’API publique en conséquence , `Not enough data to validate` (InsufficientData) et `Other` (Autre).|
|category|String|Catégorie de l’alerte.|
|detectionSource|Chaîne|Source de détection.|
|threatFamilyName|Chaîne|Famille de menaces.|
|threatName|Chaîne|Nom de la menace.|
|machineId|Chaîne|ID d’une entité [de machine](machine.md) associée à l’alerte.|
|computerDnsName|Chaîne|nom complet de [l’ordinateur](machine.md).|
|aadTenantId|Chaîne|ID Azure Active Directory.|
|detectorId|Chaîne|ID du détecteur qui a déclenché l’alerte.|
|commentaires|Liste des commentaires d’alerte|L’objet Commentaire d’alerte contient : chaîne de commentaire, chaîne createdBy et heure de date createTime.|
|Évidence|Liste des preuves d’alerte|Preuve liée à l’alerte. Voir l’exemple ci-dessous.|

>[!NOTE]
>Vers le 29 août 2022, les valeurs de détermination d’alerte précédemment prises en charge (« Apt » et « SecurityPersonnel ») seront déconseillées et ne seront plus disponibles via l’API.

### <a name="response-example-for-getting-single-alert"></a>Exemple de réponse pour l’obtention d’une seule alerte :

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
