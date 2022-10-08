---
title: Supprimer un fichier de la bibliothèque de réponses en direct
description: Découvrez comment supprimer un fichier de la bibliothèque de réponses actives.
keywords: api, API de graphe, api prises en charge, suppression de la bibliothèque
search.product: eADQiWindows 10XVcnh
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
- tier2
ms.topic: reference
ms.subservice: mde
ms.custom: api
ms.openlocfilehash: 39cacff58686f668ec3a4c1eed1f55d669db211b
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68207619"
---
#  <a name="delete-a-file-from-the-live-response-library"></a>Supprimer un fichier de la bibliothèque de réponses en direct  

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/microsoft-defender-endpoint)

[!include[Prerelease information](../../includes/prerelease.md)]

>Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink) 

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>Description de l’API

Supprimez un fichier de la bibliothèque de réponses actives.

## <a name="limitations"></a>Limites

1.  Les limites de débit pour cette API sont de 100 appels par minute et de 1 500 appels par heure.

## <a name="permissions"></a>Autorisations

L’une des autorisations suivantes est requise pour appeler cette API. Pour en savoir plus, notamment sur le choix des autorisations, consultez [Prise en main](apis-intro.md).

| Type d’autorisation                    | Autorisation     | Nom d’affichage de l’autorisation        |
|------------------------------------|----------------|--------------------------------|
| Application                        | Library.Manage | Gérer la bibliothèque de réponses en direct |
| Déléguée (compte professionnel ou scolaire) | Library.Manage | Gérer la bibliothèque de réponses en direct |

## <a name="http-request"></a>Requête HTTP

SUPPRIMER https://api.securitycenter.microsoft.com/api/libraryfiles/{fileName}

## <a name="request-headers"></a>En-têtes de demande

| Nom            | Type   | Description               |
|-----------------|--------|---------------------------|
| Autorisation   | Chaîne | Porteur\<token>\. Obligatoire. |

## <a name="request-body"></a>Corps de la demande

Vide

## <a name="response"></a>Réponse

-   Si le fichier existe dans la bibliothèque et a été supprimé avec succès 204 Aucun contenu.

-   Si le nom de fichier spécifié est introuvable 404 Introuvable.

## <a name="example"></a>Exemple

Demande

Voici un exemple de demande.

```HTTP
DELETE https://api.securitycenter.microsoft.com/api/libraryfiles/script1.ps1
```

## <a name="related-topic"></a>Rubrique connexe
- [Exécuter la réponse en direct](run-live-response.md) 