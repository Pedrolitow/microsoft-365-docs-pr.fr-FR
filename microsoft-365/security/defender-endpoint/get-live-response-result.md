---
title: Obtenir des résultats de réponse en direct
description: Découvrez comment récupérer un résultat de commande de réponse dynamique spécifique par son index.
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
ms.collection:
- m365-security
- tier3
ms.topic: article
ms.subservice: mde
ms.custom: api
ms.openlocfilehash: ec5703664a1949ab763ef7d676655934b13041b9
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68209731"
---
# <a name="get-live-response-results"></a>Obtenir des résultats de réponse en direct

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

[!include[Prerelease information](../../includes/prerelease.md)]

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>Description de l’API

Récupère un résultat de commande de réponse dynamique spécifique par son index.

## <a name="limitations"></a>Limites

1. Les limites de débit pour cette API sont de 100 appels par minute et de 1 500 appels par heure.

## <a name="minimum-requirements"></a>Configuration minimale requise

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
Application|Machine.Read.All|''Lire tous les profils d’ordinateur''
Application|« Machine.ReadWrite.All|« Lire et écrire toutes les informations sur l’ordinateur »
|Déléguée (compte professionnel ou scolaire)|Machine.LiveResponse|Exécuter une réponse en direct sur un ordinateur spécifique|

## <a name="http-request"></a>Requête HTTP

```HTTP
GET https://api.securitycenter.microsoft.com/api/machineactions/{machine action
id}/GetLiveResponseResultDownloadLink(index={command-index})
```

## <a name="request-headers"></a>En-têtes de demande

|Nom|Type|Description|
|---|---|---|
|Autorisation|Chaîne|Bearer {token}. Required.|

## <a name="request-body"></a>Corps de la demande

Vide

## <a name="response"></a>Réponse

Si elle réussit, cette méthode renvoie le code de réponse 200 ok avec l’objet qui contient le lien vers le résultat de commande dans la propriété *value* . Ce lien est valide pendant 30 minutes et doit être utilisé immédiatement pour télécharger le package dans un stockage local. Un lien expiré peut être recréé par un autre appel, et il n’est pas nécessaire d’exécuter à nouveau la réponse en direct.

*Propriétés de transcription Runscript :*

|Propriété|Description|
|---|---|
|script_name|Nom du script exécuté|
|exit_code|Code de sortie du script exécuté|
|script_output|Sortie standard du script exécuté|
|script_errors|Sortie d’erreur standard du script exécuté|

## <a name="example"></a>Exemple

### <a name="request-example"></a>Exemple de requête

Voici un exemple de demande.

```HTTP
GET https://api.securitycenter.microsoft.com/api/machineactions/988cc94e-7a8f-4b28-ab65-54970c5d5018/GetLiveResponseResultDownloadLink(index=0)
```

### <a name="response-example"></a>Exemple de réponse

Voici un exemple de réponse.

HTTP/1.1 200 Ok

Type de contenu : application/json

```JSON
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#Edm.String",
    "value": "https://core.windows.net/investigation-actions-data/ID/CustomPlaybookCommandOutput/4ed5e7807ad1fe59b00b664fe06a0f07?se=2021-02-04T16%3A13%3A50Z&sp=r&sv=2019-07-07&sr=b&sig=1dYGe9rPvUlXBPvYSmr6/OLXPY98m8qWqfIQCBbyZTY%3D"
}
```

*Contenu du fichier :*

```JSON
{
    "script_name": "minidump.ps1",
    "exit_code": 0,
    "script_output": "Transcript started, output file is C:\\ProgramData\\Microsoft\\Windows Defender Advanced Threat Protection\\Temp\\PSScriptOutputs\\PSScript_Transcript_{TRANSCRIPT_ID}.txt
C:\\windows\\TEMP\\OfficeClickToRun.dmp.zip\n51 MB\n\u0000\u0000\u0000",
    "script_errors":""
}
```

## <a name="related-topics"></a>Voir aussi

- [Obtenir l’API d’action de machine](get-machineaction-object.md)
- [Annuler l’action de l’ordinateur](cancel-machine-action.md)
- [Exécuter la réponse en direct](run-live-response.md) 
