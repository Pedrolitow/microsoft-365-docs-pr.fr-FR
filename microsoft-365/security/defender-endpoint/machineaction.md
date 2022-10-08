---
title: type de ressource machineAction
description: Découvrez les méthodes et les propriétés du type de ressource MachineAction dans Microsoft Defender pour point de terminaison.
keywords: api, api prises en charge, get, machineaction, recent
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
- tier3
ms.topic: article
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: e85038909d9cd68a96d2eb91ebea8fb9dbf6801e
ms.sourcegitcommit: 4e42bafee965446f44f7f57d1defed2b9b24fce8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2022
ms.locfileid: "68233197"
---
# <a name="machineaction-resource-type"></a>Type de ressource MachineAction

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)


[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]


- Pour plus d’informations, consultez [Actions de réponse](respond-machine-alerts.md).

|Méthode|Type renvoyé|Description|
|---|---|---|
|[Répertorier les actions automatiques](get-machineactions-collection.md)|[Action de l’ordinateur](machineaction.md)|[Répertorier les entités d’action de l’ordinateur](machineaction.md).|
|[Obtenir MachineAction](get-machineaction-object.md)|[Action de l’ordinateur](machineaction.md)|Obtenez une seule entité [d’action de](machineaction.md) machine.|
|[Collecter un package d’examen](collect-investigation-package.md)|[Action de l’ordinateur](machineaction.md)|Collectez le package d’investigation à partir d’un [ordinateur](machine.md).|
|[Obtenir SAS de l’URI du package d’examen](get-package-sas-uri.md)|[Action de l’ordinateur](machineaction.md)|Obtenez l’URI pour télécharger le package d’investigation.|
|[Isoler l’ordinateur](isolate-machine.md)|[Action de l’ordinateur](machineaction.md)|Isoler [l’ordinateur](machine.md) du réseau.|
|[Libérer la machine de l’isolation](unisolate-machine.md)|[Action de l’ordinateur](machineaction.md)|Libérer la [machine](machine.md) de l’isolation.|
|[Restreindre l’exécution des applications](restrict-code-execution.md)|[Action de l’ordinateur](machineaction.md)|Limitez l’exécution de l’application.|
|[Supprimer la restriction des applications](unrestrict-code-execution.md)|[Action de l’ordinateur](machineaction.md)|Supprimez la restriction d’exécution de l’application.|
|[Exécuter une analyse antivirus](run-av-scan.md)|[Action de l’ordinateur](machineaction.md)|Exécutez une analyse av à l’aide de Windows Defender (le cas échéant).|
|[Retirer un ordinateur](offboard-machine-api.md)|[Action de l’ordinateur](machineaction.md)|Désintégrateur de Microsoft Defender pour point de terminaison.[](machine.md)|
|[Arrêt et fichier mis en quarantaine](stop-and-quarantine-file.md)|[Action de l’ordinateur](machineaction.md)|Arrêtez l’exécution d’un fichier sur un ordinateur et supprimez-le.|
|[Exécuter la réponse en direct](run-live-response.md)|[Action de l’ordinateur](machineaction.md)|Exécute une séquence de commandes de réponse en direct sur un appareil|
|[Obtenir le résultat de la réponse en direct](get-live-response-result.md)|Entité d’URL|Récupère le lien de téléchargement du résultat de la commande de réponse active spécifique par son index.|
|[Annuler l’action de l’ordinateur](cancel-machine-action.md)|[Action de l’ordinateur](machineaction.md)|Annuler une action de machine active.|

<br>

## <a name="properties"></a>Propriétés

|Propriété|Type|Description|
|---|---|---|
|ID|Guid|Identité de l’entité [Action de la machine](machineaction.md) .|
|type|Énum|Type de l’action. Les valeurs possibles sont : « RunAntiVirusScan », « Offboard », « Live Response », « CollectInvestigationPackage », « Isolate », « Unisolate », « StopAndQuarantineFile », « RestrictCodeExecution » et « UnrestrictCodeExecution ».|
|étendue|chaîne|Étendue de l’action. « Full » ou « Selective » pour l’isolation, « Quick » ou « Full » pour l’analyse antivirus.|
|Demandeur|Chaîne|Identité de la personne qui a exécuté l’action.|
|externalID|Chaîne|ID que le client peut envoyer dans la demande de corrélation personnalisée.|
|requestSource|chaîne|Nom de l’utilisateur/de l’application qui a envoyé l’action.|
|Commandes |tableau|Commandes à exécuter. Les valeurs autorisées sont PutFile, RunScript, GetFile.|
|cancellationRequestor|Chaîne|Identité de la personne qui a annulé l’action.|
|requestorComment|Chaîne|Commentaire qui a été écrit lors de l’émission de l’action.|
|cancellationComment|Chaîne|Commentaire qui a été écrit lors de l’annulation de l’action.|
|status|Énum|État actuel de la commande. Les valeurs possibles sont : « En attente », « InProgress », « Succeeded », « Failed », « TimeOut » et « Cancelled ».|
|machineId|Chaîne|ID de [l’ordinateur](machine.md) sur lequel l’action a été exécutée.|
|computerDnsName|Chaîne|Nom de [l’ordinateur](machine.md) sur lequel l’action a été exécutée.|
|creationDateTimeUtc|DateTimeOffset|Date et heure de création de l’action.|
|cancellationDateTimeUtc|DateTimeOffset|Date et heure d’annulation de l’action.|
|lastUpdateDateTimeUtc|DateTimeOffset|Date et heure de la dernière mise à jour de l’état de l’action.|
|title|Chaîne|Titre de l’action de la machine.|
|relatedFileInfo|Classe|Contient deux propriétés. string `fileIdentifier`, Enum `fileIdentifierType` avec les valeurs possibles : « Sha1 », « Sha256 » et « Md5 ».|

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
