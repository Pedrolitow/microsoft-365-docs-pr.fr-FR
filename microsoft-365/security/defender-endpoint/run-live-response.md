---
title: Exécuter des commandes de réponse en direct sur un appareil
description: Découvrez comment exécuter une séquence de commandes de réponse en direct sur un appareil.
keywords: api, API de graphe, api prises en charge, chargement dans la bibliothèque
search.appverid: met150
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-security-compliance
ms.topic: article
ms.subservice: mde
ms.custom: api
ms.openlocfilehash: e815af864aa66173a7ce110948c4cd8e9e19be35
ms.sourcegitcommit: d3ef9391f621e8f4ca70661184b3bb82c6cbda94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2022
ms.locfileid: "67577891"
---
# <a name="run-live-response-commands-on-a-device"></a>Exécuter des commandes de réponse en direct sur un appareil

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)


[!include[Prerelease information](../../includes/prerelease.md)]

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>Description de l’API

Exécute une séquence de commandes de réponse en direct sur un appareil

## <a name="limitations"></a>Limites

1. Les limitations de débit pour cette API sont de 10 appels par minute (des requêtes supplémentaires sont traitées avec HTTP 429).

2. 25 sessions exécutées simultanément (les demandes dépassant la limite de limitation recevront une réponse « 429 - Trop de demandes »).

3. Si l’ordinateur n’est pas disponible, la session est mise en file d’attente jusqu’à 3 jours.

4. Expirations des commandes RunScript après 10 minutes.

5. Les commandes de réponse dynamique ne peuvent pas être mises en file d’attente et ne peuvent être exécutées qu’une par une.

6. Si l’ordinateur que vous essayez d’exécuter cet appel d’API se trouve dans un groupe d’appareils RBAC auquel aucun niveau de correction automatisé n’est affecté, vous devez au moins activer le niveau de correction minimal pour un groupe d’appareils donné.

7. Plusieurs commandes de réponse dynamique peuvent être exécutées sur un seul appel d’API. Toutefois, lorsqu’une commande de réponse dynamique échoue, toutes les actions suivantes ne sont pas exécutées.

## <a name="minimum-requirements"></a>Exigences minimales

Avant de pouvoir lancer une session sur un appareil, vérifiez que vous remplissez les conditions suivantes :

- **Vérifiez que vous exécutez une version prise en charge de Windows**.

  Les appareils doivent exécuter l’une des versions suivantes de Windows

  - **Windows 11**
  
  - **Windows 10**
    - [Version 1909](/windows/whats-new/whats-new-windows-10-version-1909) ou ultérieure
    - [Version 1903](/windows/whats-new/whats-new-windows-10-version-1903) avec [KB4515384](https://support.microsoft.com/help/4515384/windows-10-update-kb4515384)
    - [Version 1809 (RS 5)](/windows/whats-new/whats-new-windows-10-version-1809) [avec KB4537818](https://support.microsoft.com/help/4537818/windows-10-update-kb4537818)
    - [Version 1803 (RS 4)](/windows/whats-new/whats-new-windows-10-version-1803) avec [KB4537795](https://support.microsoft.com/help/4537795/windows-10-update-kb4537795)
    - [Version 1709 (RS 3)](/windows/whats-new/whats-new-windows-10-version-1709) avec [KB4537816](https://support.microsoft.com/help/4537816/windows-10-update-kb4537816)

  - **Windows Server 2019 - Applicable uniquement pour la préversion publique**
    - Version 1903 ou (avec [KB4515384](https://support.microsoft.com/help/4515384/windows-10-update-kb4515384)) ultérieure
    - Version 1809 (avec [KB4537818](https://support.microsoft.com/help/4537818/windows-10-update-kb4537818))
    
  - **Windows Server 2022**

## <a name="permissions"></a>Autorisations

L’une des autorisations suivantes est requise pour appeler cette API. Pour en savoir plus, notamment sur le choix des autorisations, consultez [Prise en main](apis-intro.md).

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

|Paramètre|Type|Description|
|---|---|---|
|Commentaire|Chaîne|Commentaire à associer à l’action.|
|Commandes|Tableau|Commandes à exécuter. Les valeurs autorisées sont PutFile, RunScript, GetFile.|

## <a name="commands"></a>Commandes

|Type de commande|Paramètres|Description|
|---|---|---|
|Putfile|Clé : FileName <p> Valeur : \<file name\>|Place un fichier de la bibliothèque sur l’appareil. Les fichiers sont enregistrés dans un dossier de travail et sont supprimés lorsque l’appareil redémarre par défaut.
|RunScript|Clé : ScriptName <br> Valeur : \<Script from library\> <p> Clé : Args <br> Valeur : \<Script arguments\>|Exécute un script à partir de la bibliothèque sur un appareil. <p>  Le paramètre Args est passé à votre script. <p> Délai d’expiration après 10 minutes.|
|GetFile|Clé : chemin d’accès <br> Valeur : \<File path\>|Collectez le fichier à partir d’un appareil. REMARQUE : les barres obliques inverses dans le chemin d’accès doivent être placées dans une séquence d’échappement.|

## <a name="response"></a>Réponse

- Si elle réussit, cette méthode retourne 201 Created.

  Entité d’action. Si l’ordinateur avec l’ID spécifié est introuvable - 404 Introuvable.

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

Type de contenu : application/json

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

- [Obtenir l’API d’action de machine](get-machineaction-object.md)
- [Obtenir le résultat de la réponse en direct](get-live-response-result.md)
- [Annuler l’action de l’ordinateur](cancel-machine-action.md)
