---
title: Type de ressource Fichier
description: Récupérer les alertes récentes de Microsoft Defender for Endpoint relatives aux fichiers.
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
ms.openlocfilehash: c4d392c9c7777a5ab5435d70e36822e11aa39dae
ms.sourcegitcommit: 5d8de3e9ee5f52a3eb4206f690365bb108a3247b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2021
ms.locfileid: "52771188"
---
# <a name="file-resource-type"></a>Type de ressource Fichier

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :** [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/?linkid=2154037)

- Vous souhaitez découvrir Microsoft Defender pour le point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink) 

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]


Représente une entité de fichier dans Defender pour le point de terminaison.

## <a name="methods"></a>Méthodes
Méthode|Type renvoyé |Description
:---|:---|:---
[Obtenir un fichier](get-file-information.md) | [fichier](files.md) | Obtenir un fichier unique 
[Liste des alertes associées au fichier](get-file-related-alerts.md) | collection[alert](alerts.md) | Obtenez les [entités](alerts.md) d’alerte associées au fichier.
[List file related machines](get-file-related-machines.md) | [collection d’ordinateurs](machine.md) | Obtenez les [entités de](machine.md) l’ordinateur associées à l’alerte.
[statistiques de fichier](get-file-statistics.md) | Résumé des statistiques | Récupère la prévalence du fichier donné.


## <a name="properties"></a>Propriétés
|Propriété | Type    |   Description |
|:---|:---|:---|
|sha1 | String | Hachage Sha1 du contenu du fichier |
|sha256 | String | Hachage Sha256 du contenu du fichier |
|globalPrevalence | Nullable long | Prévalence des fichiers au sein de l’organisation |
|globalFirstObserved | DateTimeOffset | Première observation du fichier |
|globalLastObserved | DateTimeOffset | Dernière observation du fichier |
|taille | Nullable long | Taille du fichier |
|fileType | String | Type du fichier |
|isPeFile | Boolean | true si le fichier est portable exécutable (par exemple, « DLL », « EXE », etc.) |
|filePublisher | String | Éditeur de fichiers |
|fileProductName | String | Nom du produit |
|signataire | String | Signataire de fichiers |
|émetteur | String | Émetteur de fichier |
|signerHash | String | Hachage du certificat de signature |
|isValidCertificate | Boolean | Le certificat de signature a été vérifié avec succès par l’agent Microsoft Defender for Endpoint |
|determinationType | String | Type de détermination du fichier |
|determinationValue | String | Valeur de détermination |


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
