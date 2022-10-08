---
title: Codes d’erreur courants de l’API REST Microsoft 365 Defender
description: En savoir plus sur les codes d’erreur courants de l’API REST Microsoft 365 Defender
keywords: api, erreur, codes, erreurs courantes, Microsoft 365 Defender, codes d’erreur d’api
search.product: eADQiWindows 10XVcnh
ms.service: microsoft-365-security
ms.subservice: m365d
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
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.custom: api
ms.openlocfilehash: 0fc6ca121b287887ec1e6ef82a13df1ca85acc35
ms.sourcegitcommit: 12af9e8e3a6eaa090fda9e98ccb831dff65863a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2022
ms.locfileid: "68066913"
---
# <a name="common-microsoft-365-defender-rest-api-error-codes"></a>Codes d’erreur courants de l’API REST Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**

- Microsoft 365 Defender

> [!IMPORTANT]
> Certaines informations ont trait à un produit préalablement publié, qui peut être modifié de manière significative avant sa publication commerciale. Microsoft n’offre aucune garantie, explicite ou implicite, concernant les informations fournies ici.

Les codes d’erreur peuvent être retournés par une opération sur l’une des API Microsoft 365 Defender. Chaque réponse d’erreur contient un message d’erreur, qui peut aider à résoudre le problème. La colonne message d’erreur dans la section de table fournit des exemples de messages. Le contenu des messages réels varie en fonction des facteurs qui ont déclenché la réponse. Le contenu de la variable est indiqué dans le tableau par des crochets d’angle.

## <a name="error-codes"></a>Codes d’erreur

Code d'erreur | Code d’état HTTP | Message
-|-|-
BadRequest | BadRequest (400) | Message d’erreur général de demande incorrecte.
ODataError | BadRequest (400) | Requête d’URI OData non valide \<the specific error is specified\>.
InvalidInput | BadRequest (400) | Entrée non valide \<the invalid input\>.
InvalidRequestBody | BadRequest (400) | Corps de la demande non valide.
InvalidHashValue | BadRequest (400) | La valeur \<the invalid hash\> de hachage n’est pas valide.
InvalidDomainName | BadRequest (400) | Le nom de \<the invalid domain\> domaine n’est pas valide.
InvalidIpAddress | BadRequest (400) | L’adresse \<the invalid IP\> IP n’est pas valide.
InvalidUrl | BadRequest (400) | L’URL \<the invalid URL\> n’est pas valide.
MaximumBatchSizeExceeded | BadRequest (400) | Taille maximale du lot dépassée. Reçu : \<batch size received\>, autorisé : {taille de lot autorisée}.
MissingRequiredParameter | BadRequest (400) | Le paramètre \<the missing parameter\> est manquant.
OsPlatformNotSupported | BadRequest (400) | La plateforme du système d’exploitation \<the client OS Platform\> n’est pas prise en charge pour cette action.
ClientVersionNotSupported | BadRequest (400) | \<The requested action\> est pris en charge sur la version \<supported client version\> du client et les versions ultérieures.
Non autorisé (Unauthorized) | Non autorisé (401) | Non autorisé (Unauthorized) <br /><br />*Remarque : généralement causée par un en-tête d’autorisation non valide ou expiré.*
Interdit (Forbidden) | Interdit (403) | Interdit (Forbidden) <br /><br />*Remarque : jeton valide, mais autorisation insuffisante pour l’action*.
DisabledFeature | Interdit (403) | La fonctionnalité de locataire n’est pas activée.
DisallowedOperation | Interdit (403) | \<the disallowed operation and the reason\>.
NotFound | Introuvable (404) | Message d’erreur général introuvable.
ResourceNotFound | Introuvable (404) | La ressource \<the requested resource\> est introuvable.
InternalServerError | Erreur interne du serveur (500) | *Remarque : Aucun message d’erreur, réessayez l’opération ou [contactez Microsoft](../../admin/get-help-support.md) s’il n’est pas résolu*

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
> Les paramètres de corps respectent la casse.

Si vous rencontrez une erreur *InvalidRequestBody* ou *MissingRequiredParameter* , elle peut être due à une faute de frappe. Passez en revue la documentation de l’API et vérifiez que les paramètres envoyés correspondent à l’exemple approprié.

## <a name="tracking-id"></a>ID de suivi

Chaque réponse d’erreur contient un paramètre d’ID unique pour le suivi. Le nom de propriété de ce paramètre est *target*. Lorsque vous nous contactez au sujet d’une erreur, l’attachement de cet ID nous aidera à trouver la cause racine du problème.

## <a name="related-articles"></a>Articles connexes

- [Vue d’ensemble des API Microsoft 365 Defender](api-overview.md)
- [API Microsoft 365 Defender prises en charge](api-supported.md)
- [Accéder aux API Microsoft 365 Defender](api-access.md)
- [En savoir plus sur les limites d’API et les licences](api-terms.md)
