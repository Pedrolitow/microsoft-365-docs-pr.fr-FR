---
title: Type de ressource Fichier
description: Récupérez les alertes de Microsoft Defender pour point de terminaison récentes liées aux fichiers.
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
- tier3
ms.topic: conceptual
ms.subservice: mde
ms.custom: api
search.appverid: met150
ms.openlocfilehash: 0618c1bfdae63c5a8d7ac36f2d8531f1a7fe7b90
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68635529"
---
# <a name="file-resource-type"></a>Type de ressource Fichier

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :** 
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

Représente une entité de fichier dans Defender pour point de terminaison.

## <a name="methods"></a>Méthodes

Méthode|Type renvoyé |Description
:---|:---|:---
[Obtenir un fichier](get-file-information.md) | [file](files.md) | Obtenir un seul fichier 
[Répertorier les alertes liées aux fichiers](get-file-related-alerts.md) | collection[alert](alerts.md) | Obtenez les entités [d’alerte](alerts.md) associées au fichier.
[Répertorier les machines associées aux fichiers](get-file-related-machines.md) | [collection d’ordinateurs](machine.md) | Obtenez les entités [de machine](machine.md) associées à l’alerte.
[statistiques de fichier](get-file-statistics.md) | Résumé des statistiques | Récupère la prévalence du fichier donné.


## <a name="properties"></a>Propriétés

|Propriété | Type | Description |
|:---|:---|:---|
|sha1 | Chaîne | Hachage Sha1 du contenu du fichier |
|sha256 | Chaîne | Hachage Sha256 du contenu du fichier |
|globalPrevalence | Valeur nullable longue | Prévalence des fichiers au sein de l’organisation |
|globalFirstObserved | DateTimeOffset | Première fois que le fichier a été observé |
|globalLastObserved | DateTimeOffset | Dernière fois que le fichier a été observé |
|size | Valeur nullable longue | Taille du fichier |
|Filetype | Chaîne | Type du fichier |
|isPeFile | Boolean | true si le fichier est exécutable portable (par exemple, « DLL », « EXE », etc.) |
|filePublisher | Chaîne | Éditeur de fichiers |
|fileProductName | Chaîne | Nom du produit |
|Signataire | Chaîne | Signataire de fichier |
|Émetteur | Chaîne | Émetteur de fichier |
|signerHash | Chaîne | Hachage du certificat de signature |
|isValidCertificate | Boolean | Le certificat de signature a été vérifié avec succès par Microsoft Defender pour point de terminaison agent |
|determinationType | Chaîne | Type de détermination du fichier |
|determinationValue | Chaîne | Valeur de détermination |

## <a name="json-representation"></a>Représentation Json

```json
{
    "sha1": "4388963aaa83afe2042a46a3c017ad50bdcdafb3",
    "sha256": "413c58c8267d2c8648d8f6384bacc2ae9c929b2b96578b6860b5087cd1bd6462",
    "globalPrevalence": 180022,
    "globalFirstObserved": "2017-09-19T03:51:27.6785431Z",
    "globalLastObserved": "2020-01-06T03:59:21.3229314Z",
    "size": 22139496,
    "fileType": "APP",
    "isPeFile": true,
    "filePublisher": "CHENGDU YIWO Tech Development Co., Ltd.",
    "fileProductName": "EaseUS MobiSaver for Android",
    "signer": "CHENGDU YIWO Tech Development Co., Ltd.",
    "issuer": "VeriSign Class 3 Code Signing 2010 CA",
    "signerHash": "6c3245d4a9bc0244d99dff27af259cbbae2e2d16",
    "isValidCertificate": false,
    "determinationType": "Pua",
    "determinationValue": "PUA:Win32/FusionCore"
}
```
