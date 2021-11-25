---
title: Type de ressource machineAction
description: Découvrez les méthodes et les propriétés du type de ressource MachineAction dans Microsoft Defender for Endpoint.
keywords: api, api pris en charge, obtenir, machineaction, récent
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 79503f4089f1ff19bc9f47c6032b6ebc33b244d8
ms.sourcegitcommit: 2b9d40e888ff2f2b3385e2a90b50d719bba1e653
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/25/2021
ms.locfileid: "61171160"
---
# <a name="machineaction-resource-type"></a>Type de ressource MachineAction

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)


[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]


- Pour plus d’informations, voir [Actions de réponse.](respond-machine-alerts.md)

|Méthode|Type renvoyé|Description|
|---|---|---|
|[List MachineActions](get-machineactions-collection.md)|[Action de l’ordinateur](machineaction.md)|Liste des [entités d’action](machineaction.md) de l’ordinateur.|
|[Obtenir MachineAction](get-machineaction-object.md)|[Action de l’ordinateur](machineaction.md)|Obtenir une seule [entité d’action](machineaction.md) de l’ordinateur.|
|[Collecter un package d’examen](collect-investigation-package.md)|[Action de l’ordinateur](machineaction.md)|Collecter un package d’examen à partir [d’un ordinateur.](machine.md)|
|[Obtenir SAS de l’URI du package d’examen](get-package-sas-uri.md)|[Action de l’ordinateur](machineaction.md)|Obtenez l’URI pour télécharger le package d’enquête.|
|[Isoler l’ordinateur](isolate-machine.md)|[Action de l’ordinateur](machineaction.md)|Isoler [l’ordinateur](machine.md) du réseau.|
|[Libérer la machine de l’isolation](unisolate-machine.md)|[Action de l’ordinateur](machineaction.md)|Libérer [l’ordinateur](machine.md) de l’isolation.|
|[Restreindre l’exécution des applications](restrict-code-execution.md)|[Action de l’ordinateur](machineaction.md)|Restreindre l’exécution de l’application.|
|[Supprimer la restriction des applications](unrestrict-code-execution.md)|[Action de l’ordinateur](machineaction.md)|Supprimer la restriction d’exécution de l’application.|
|[Exécuter une analyse antivirus](run-av-scan.md)|[Action de l’ordinateur](machineaction.md)|Exécutez une analyse antivirus à l’Windows Defender (le cas échéant).|
|[Retirer un ordinateur](offboard-machine-api.md)|[Action de l’ordinateur](machineaction.md)|[Hors-carte de](machine.md) Microsoft Defender pour point de terminaison.|
|[Arrêt et fichier mis en quarantaine](stop-and-quarantine-file.md)|[Action de l’ordinateur](machineaction.md)|Arrêtez l’exécution d’un fichier sur un ordinateur et supprimez-le.|
|[Exécuter la réponse en direct](run-live-response.md)|[Action de l’ordinateur](machineaction.md)|Exécute une séquence de commandes de réponse en direct sur un appareil|
|[Obtenir le résultat de la réponse en direct](get-live-response-result.md)|Entité d’URL|Extrait le lien de téléchargement des résultats de la commande de réponse en direct spécifique par son index.|
|[Annuler l’action de l’ordinateur](cancel-machine-action.md)|[Action de l’ordinateur](machineaction.md)|Annuler une action de l’ordinateur actif.|

<br>

## <a name="properties"></a>Propriétés

|Propriété|Type|Description|
|---|---|---|
|ID|Guid|Identité de [l’entité Action](machineaction.md) de l’ordinateur.|
|type|Énum|Type de l’action. Les valeurs possibles sont : « RunAntiVirusScan », « Offboard », « Live Response », « CollectConditionigationPackage », « Isolate », « Unisolate », « StopAndQuarantineFile », « RestrictCodeExecution » et « IsolaterictCodeExecution ».|
|étendue|string|Étendue de l’action. « Complète » ou « Sélective » pour l’isolation, « Rapide » ou « Complète » pour l’analyse antivirus.|
|demandeur|String|Identité de la personne qui a exécuté l’action.|
|externalID|String|ID que le client peut envoyer dans la demande de corrélation personnalisée.|
|requestSource|string|Nom de l’utilisateur/de l’application qui a soumis l’action.|
|Commandes |tableau|Commandes à exécuter. Les valeurs autorisées sont PutFile, RunScript, GetFile.|
|cancellationRequestor|String|Identité de la personne qui a annulé l’action.|
|requestorComment|String|Commentaire écrit lors de l’émission de l’action.|
|cancellationComment|String|Commentaire écrit lors de l’annulation de l’action.|
|statut|Énum|État actuel de la commande. Les valeurs possibles sont : « En attente », « InProgress », « Succeeded », « Failed », « TimeOut » et « Cancelled ».|
|machineId|String|ID de [l’ordinateur](machine.md) sur lequel l’action a été exécutée.|
|computerDnsName|String|Nom de [l’ordinateur](machine.md) sur lequel l’action a été exécutée.|
|creationDateTimeUtc|DateTimeOffset|Date et heure de création de l’action.|
|cancellationDateTimeUtc|DateTimeOffset|Date et heure d’annulation de l’action.|
|lastUpdateDateTimeUtc|DateTimeOffset|Date et heure de la dernière mise à jour de l’état de l’action.|
|title|String|Titre de l’action de l’ordinateur.|
|relatedFileInfo|Classe|Contient deux propriétés. chaîne `fileIdentifier` , Enum `fileIdentifierType` avec les valeurs possibles : « Sha1 », « Sha256 » et « Md5 ».|

## <a name="json-representation"></a>Représentation Json

```json
{
        "id": "5382f7ea-7557-4ab7-9782-d50480024a4e",
        "type": "Isolate",
        "scope": "Selective",
        "requestor": "Analyst@TestPrd.onmicrosoft.com",
        "requestorComment": "test for docs",
        "status": "Succeeded",
        "machineId": "7b1f4967d9728e5aa3c06a9e617a22a4a5a17378",
        "computerDnsName": "desktop-test",
        "creationDateTimeUtc": "2019-01-02T14:39:38.2262283Z",
        "lastUpdateDateTimeUtc": "2019-01-02T14:40:44.6596267Z",
        "relatedFileInfo": null
}
```
