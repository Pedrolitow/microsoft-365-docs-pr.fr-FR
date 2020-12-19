---
title: Codes d’erreur de l’API REST Microsoft 365 Defender courants
description: En savoir plus sur les codes d’erreur de l’API REST Microsoft 365 Defender courants
keywords: API, erreur, codes, erreurs courantes, MTP, codes d’erreur de l’API
search.product: eADQiWindows 10XVcnh
ms.prod: microsoft-365-enterprise
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
ms.collection: M365-security-compliance
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.openlocfilehash: 0df741efb7555d587a6033acc23716e93f542d5e
ms.sourcegitcommit: d6b1da2e12d55f69e4353289e90f5ae2f60066d0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/19/2020
ms.locfileid: "49719213"
---
# <a name="common-microsoft-365-defender-rest-api-error-codes"></a>Codes d’erreur de l’API REST Microsoft 365 Defender courants

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**

- Protection Microsoft contre les menaces

> [!IMPORTANT]
> Certaines informations se rapportent à des produits précommercialisés susceptibles d’être modifiés de manière substantielle avant leur publication commerciale. Microsoft makes no warranties, express or implied, with respect to the information provided here.

Les codes d’erreur peuvent être renvoyés par une opération sur l’une des API Microsoft 365 Defender. Chaque réponse d’erreur contient un message d’erreur qui peut vous aider à résoudre le problème. La colonne message d’erreur de la section tableau fournit quelques exemples de messages. Le contenu des véritables messages dépend des facteurs qui ont déclenché la réponse. Le contenu des variables est indiqué dans le tableau par des chevrons.

## <a name="error-codes"></a>Codes d’erreur

Code d'erreur | Code d’état HTTP | Message
-|-|-
BadRequest | BadRequest (400) | Message d’erreur de requête incorrecte générale.
ODataError | BadRequest (400) | Requête URI OData non valide \<the specific error is specified\> .
InvalidInput | BadRequest (400) | Entrée non valide \<the invalid input\> .
InvalidRequestBody | BadRequest (400) | Corps de la requête non valide.
InvalidHashValue | BadRequest (400) | La valeur de hachage \<the invalid hash\> n’est pas valide.
InvalidDomainName | BadRequest (400) | Le nom de domaine \<the invalid domain\> n’est pas valide.
InvalidIpAddress | BadRequest (400) | L’adresse IP \<the invalid IP\> n’est pas valide.
InvalidUrl | BadRequest (400) | L’URL \<the invalid URL\> n’est pas valide.
MaximumBatchSizeExceeded | BadRequest (400) | Taille maximale de lot dépassée. Received : \<batch size received\> , allowed : {taille de lot autorisée}.
MissingRequiredParameter | BadRequest (400) | Le paramètre \<the missing parameter\> est manquant.
OsPlatformNotSupported | BadRequest (400) | La plateforme de système d’exploitation \<the client OS Platform\> n’est pas prise en charge pour cette action.
ClientVersionNotSupported | BadRequest (400) | \<The requested action\> est pris en charge sur la version du client \<supported client version\> et les versions ultérieures.
Non autorisé (Unauthorized) | Non autorisé (401) | Non autorisé (Unauthorized) <br /><br />*Remarque : cela est généralement dû à un en-tête d’autorisation non valide ou expiré.*
Interdit (Forbidden) | Interdit (403) | Interdit (Forbidden) <br /><br />*Remarque : jeton valide, mais autorisation insuffisante pour l’action*.
DisabledFeature | Interdit (403) | La fonctionnalité de client n’est pas activée.
DisallowedOperation | Interdit (403) | \<the disallowed operation and the reason\>.
NotFound | Introuvable (404) | Message d’erreur général introuvable.
ResourceNotFound | Introuvable (404) | Ressource \<the requested resource\> introuvable.
InternalServerError | Erreur de serveur interne (500) | *Remarque : aucun message d’erreur, retenter l’opération ou contacter Microsoft s’il n’est pas résolu*

## <a name="examples"></a>Exemples

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

## <a name="body-parameters"></a>Paramètres de corps

> [!IMPORTANT]
> Les paramètres Body respectent la casse.

Si vous êtes confronté à une erreur *InvalidRequestBody* ou *MissingRequiredParameter* , elle peut être causée par une faute de frappe. Examinez la documentation de l’API et assurez-vous que les paramètres soumis correspondent à l’exemple approprié.

## <a name="tracking-id"></a>ID de suivi

Chaque réponse d’erreur contient un paramètre ID unique pour le suivi. Le nom de la propriété de ce paramètre est *target*. Lors de la création d’une erreur, joindre cet ID nous permettra de trouver la cause première du problème.

## <a name="related-articles"></a>Articles connexes

- [Vue d’ensemble des API Microsoft 365 Defender](api-overview.md)
- [API Microsoft 365 Defender prises en charge](api-supported.md)
- [Accéder aux API Microsoft 365 Defender](api-access.md)
- [En savoir plus sur les limites d’API et la gestion des licences](api-terms.md)
