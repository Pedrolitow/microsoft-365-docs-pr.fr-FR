---
title: Exécuter des commandes de réponse en direct sur un appareil
description: Découvrez comment exécuter une séquence de commandes de réponse en direct sur un appareil.
keywords: api, api de graphique, api pris en charge, téléchargement vers la bibliothèque
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
localization_priority: normal
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: article
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 9c974da84dfffeeb655e29e934e2fe37c9af94bc
ms.sourcegitcommit: d817a3aecb700f7227a05cd165ffa7dbad67b09d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/29/2021
ms.locfileid: "53650930"
---
#  <a name="run-live-response-commands-on-a-device"></a>Exécuter des commandes de réponse en direct sur un appareil

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2146631)


[!include[Prerelease information](../../includes/prerelease.md)]

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>Description de l’API

Exécute une séquence de commandes de réponse en direct sur un appareil

## <a name="limitations"></a>Limites

1.  Les limites de taux pour cette API sont de 10 appels par minute (les demandes supplémentaires sont répondues par HTTP 429).

2.  25 sessions en cours d’exécution simultanée (les demandes dépassant la limite de limitation recevront une réponse « 429 - Trop de demandes »).

3.  Si l’ordinateur n’est pas disponible, la session est en file d’attente pendant 3 jours.

4.  Le délai d’un délai de commande RunScript est passé au bout de 10 minutes.

5.  En cas d’échec d’une commande de réponse en direct, toutes les actions suivies ne sont pas exécutées.

## <a name="permissions"></a>Autorisations

L’une des autorisations suivantes est nécessaire pour appeler cette API. Pour en savoir plus, notamment sur le choix des autorisations, [consultez La mise en place.](apis-intro.md)

|Type d’autorisation|Autorisation|Nom d’affichage de l’autorisation|
|---|---|---|
|Application|Machine.LiveResponse|Exécuter une réponse en direct sur un ordinateur spécifique|
|Déléguée (compte professionnel ou scolaire)|Machine.LiveResponse|Exécuter une réponse en direct sur un ordinateur spécifique|

## <a name="http-request"></a>Requête HTTP

```HTTP
POST https://api.securitycenter.microsoft.com/API/machines/{machine_id}/runliveresponse
```

## <a name="request-headers"></a>En-têtes de demande

|Nom|Type|Description|
|---|---|---|
|Autorisation|Chaîne|Porteur\<token>\. Obligatoire.|
|Content-Type|string|application/json. Obligatoire.|

## <a name="request-body"></a>Corps de la demande

|Parameter|Type|Description|
|---|---|---|
|Commentaire|Chaîne|Commentaire à associer à l’action.|
|Commandes|Tableau|Commandes à exécuter. Les valeurs autorisées sont PutFile, RunScript, GetFile.|

**Commandes**:

|Type de commande|Paramètres|Description|
|---|---|---|
|PutFile|Clé : FileName <p> Valeur : \<file name\>|Place un fichier de la bibliothèque sur l’appareil. Les fichiers sont enregistrés dans un dossier de travail et supprimés lorsque l’appareil redémarre par défaut.
|RunScript|Clé : ScriptName <br> Valeur : \<Script from library\> <p> Clé : Args <br> Valeur : \<Script arguments\>|Exécute un script à partir de la bibliothèque sur un appareil. <p>  Le paramètre Args est transmis à votre script. <p> Délai d’délai au bout de 10 minutes.|
|GetFile|Clé : Chemin d’accès <br> Valeur : \<File path\>|Collecter un fichier à partir d’un appareil. REMARQUE : les barre obliques inverses dans le chemin d’accès doivent être échappés.|

## <a name="response"></a>Réponse

- Si elle réussit, cette méthode renvoie 200, OK.

  Entité Action. Si l’ordinateur avec l’ID spécifié est in trouvé - 404 - In trouvé.

## <a name="example"></a>Exemple

### <a name="request-example"></a>Exemple de requête

Voici un exemple de demande.

```HTTP
POST https://api.securitycenter.microsoft.com/api/machines/1e5bc9d7e413ddd7902c2932e418702b84d0cc07/runliveresponse

```JSON
{
   "Commands":[
      {
         "type":"RunScript",
         "params":[
            {
               "key":"ScriptName",
               "value":"minidump.ps1"
            },
            {
               "key":"Args",
               "value":"OfficeClickToRun"
            }

         ]
      },
      {
         "type":"GetFile",
         "params":[
            {
               "key":"Path",
               "value":"C:\\windows\\TEMP\\OfficeClickToRun.dmp.zip"
            }
         ]
      }
   ],
   "Comment":"Testing Live Response API"
}
```

### <a name="response-example"></a>Exemple de réponse

Voici un exemple de réponse.

```HTTP
HTTP/1.1 200 Ok
```

Content-type: application/json

```JSON
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#MachineActions/$entity",
    "id": "{machine_action_id}",
    "type": "LiveResponse",
    "requestor": "analyst@microsoft.com",
    "requestorComment": "Testing Live Response API",
    "status": "Pending",
    "machineId": "{machine_id}",
    "computerDnsName": "hostname",
    "creationDateTimeUtc": "2021-02-04T15:36:52.7788848Z",
    "lastUpdateDateTimeUtc": "2021-02-04T15:36:52.7788848Z",
    "errorHResult": 0,
    "commands": [
        {
            "index": 0,
            "startTime": null,
            "endTime": null,
            "commandStatus": "Created",
            "errors": [],
            "command": {
                "type": "RunScript",
                "params": [
                    {
                        "key": "ScriptName",
                        "value": "minidump.ps1"
                    },{
                        "key": "Args",
                        "value": "OfficeClickToRun"
                    }
                ]
            }
        }, {
            "index": 1,
            "startTime": null,
            "endTime": null,
            "commandStatus": "Created",
            "errors": [],
            "command": {
                "type": "GetFile",
                "params": [{
                        "key": "Path", "value": "C:\\windows\\TEMP\\OfficeClickToRun.dmp.zip"
                    }
                ]
            }
        }
    ]
}
```

## <a name="related-topics"></a>Voir aussi

- [API Obtenir l’action de l’ordinateur](get-machineaction-object.md)
- [Obtenir le résultat de la réponse en direct](get-live-response-result.md)
- [Annuler l’action de l’ordinateur](cancel-machine-action.md)
