---
title: Erreurs courantes de l’API Microsoft Defender pour point de terminaison
description: Liste des erreurs courantes de l’API Microsoft Defender pour point de terminaison avec des descriptions.
keywords: API, API Microsoft Defender pour point de terminaison, erreurs, résolution des problèmes
ms.service: microsoft-365-security
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
ms.subservice: mde
ms.custom: api
ms.openlocfilehash: 75ecf39967f6308806ceb4f19f3f94fe3d603f80
ms.sourcegitcommit: 10e6abe740e27000e223378eb17d657a47555fa8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2022
ms.locfileid: "67679534"
---
# <a name="common-rest-api-error-codes"></a>Codes d’erreur courants de l’API REST



[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


* Les codes d’erreur répertoriés dans le tableau suivant peuvent être retournés par une opération sur l’une des API Microsoft Defender pour point de terminaison.
* En plus du code d’erreur, chaque réponse d’erreur contient un message d’erreur, qui peut aider à résoudre le problème.
* Le message est un texte libre qui peut être modifié.
* En bas de la page, vous trouverez des exemples de réponse.

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)


> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

Code d'erreur|Code d’état HTTP|Message
---|---|---
BadRequest|BadRequest (400)|Message d’erreur général de demande incorrecte.
ODataError|BadRequest (400)|Requête d’URI OData non valide (l’erreur spécifique est spécifiée).
InvalidInput|BadRequest (400)|Entrée non valide {entrée non valide}.
InvalidRequestBody|BadRequest (400)|Corps de la demande non valide.
InvalidHashValue|BadRequest (400)|La valeur de hachage {le hachage non valide} n’est pas valide.
InvalidDomainName|BadRequest (400)|Le nom de domaine {le domaine non valide} n’est pas valide.
InvalidIpAddress|BadRequest (400)|L’adresse IP {l’adresse IP non valide} n’est pas valide.
InvalidUrl|BadRequest (400)|L’URL {l’URL non valide} n’est pas valide.
MaximumBatchSizeExceeded|BadRequest (400)|Taille maximale du lot dépassée. Reçu : {taille de lot reçue}, autorisé : {taille de lot autorisée}.
MissingRequiredParameter|BadRequest (400)|Le paramètre {paramètre manquant} est manquant.
OsPlatformNotSupported|BadRequest (400)|La plateforme de système d’exploitation {la plateforme de système d’exploitation cliente} n’est pas prise en charge pour cette action.
ClientVersionNotSupported|BadRequest (400)|{L’action demandée} est prise en charge sur la version du client {version du client prise en charge} et versions ultérieures.
Non autorisé (Unauthorized)|Non autorisé (401)|Non autorisé (en-tête d’autorisation non valide ou expiré).
Interdit (Forbidden)|Interdit (403)|Interdit (jeton valide mais autorisation insuffisante pour l’action).
DisabledFeature|Interdit (403)|La fonctionnalité de locataire n’est pas activée.
DisallowedOperation|Interdit (403)|{l’opération non autorisée et la raison}.
NotFound|Introuvable (404)|Message d’erreur général introuvable.
ResourceNotFound|Introuvable (404)|La ressource {la ressource demandée} est introuvable.
InternalServerError|Erreur interne du serveur (500)|(Aucun message d’erreur, réessayez l’opération)
TooManyRequests|Trop de demandes (429)|La réponse représente l’atteinte de la limite de quota par nombre de demandes ou par processeur.

## <a name="body-parameters-are-case-sensitive"></a>Les paramètres de corps respectent la casse

Les paramètres de corps soumis respectent actuellement la casse.

Si vous rencontrez des erreurs **InvalidRequestBody** ou **MissingRequiredParameter** , cela peut être dû à une lettre majuscule ou minuscule de paramètre incorrecte.

Examinez la page de documentation de l’API et vérifiez que les paramètres envoyés correspondent à l’exemple approprié.

## <a name="correlation-request-id"></a>ID de demande de corrélation

Chaque réponse d’erreur contient un paramètre d’ID unique pour le suivi.

Le nom de propriété de ce paramètre est « target ».

Lorsque vous nous contactez au sujet d’une erreur, l’attachement de cet ID vous aidera à trouver la cause racine du problème.

## <a name="examples"></a>範例

```json
{
    "error": {
        "code": "ResourceNotFound",
        "message": "Machine 123123123 was not found",
        "target": "43f4cb08-8fac-4b65-9db1-745c2ae65f3a"
    }
}
```

```json
{
    "error": {
        "code": "InvalidRequestBody",
        "message": "Request body is incorrect",
        "target": "1fa66c0f-18bd-4133-b378-36d76f3a2ba0"
    }
}
```
