---
title: Codes d’Microsoft 365 Defender l’API REST courants
description: En savoir plus sur les codes d’Microsoft 365 Defender l’API REST courants
keywords: api, erreur, codes, erreurs courantes, Microsoft 365 Defender, codes d’erreur d’api
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
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
ms.technology: m365d
ms.custom: api
ms.openlocfilehash: 499ab1722b2754e893361784f7ff1ce257ceb58b
ms.sourcegitcommit: 6f3bc00a5cf25c48c61eb3835ac069e9f41dc4db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2022
ms.locfileid: "62171946"
---
# <a name="common-microsoft-365-defender-rest-api-error-codes"></a>Codes d’Microsoft 365 Defender l’API REST courants

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**

- Microsoft 365 Defender

> [!IMPORTANT]
> Certaines informations ont trait à un produit préalablement publié, qui peut être modifié de manière significative avant sa publication commerciale. Microsoft n’offre aucune garantie, explicite ou implicite, concernant les informations fournies ici.

Les codes d’erreur peuvent être renvoyés par une opération sur l’une Microsoft 365 Defender API. Chaque réponse d’erreur contient un message d’erreur, qui peut aider à résoudre le problème. La colonne message d’erreur de la section tableau fournit des exemples de messages. Le contenu des messages réels varie en fonction des facteurs qui ont déclenché la réponse. Le contenu de la variable est indiqué dans le tableau par des crochets.

## <a name="error-codes"></a>Codes d’erreur

Code d’erreur | Code d’état HTTP | Message
-|-|-
BadRequest | BadRequest (400) | Message d’erreur Général Bad Request.
ODataError | BadRequest (400) | Requête URI OData non \<the specific error is specified\> valide.
InvalidInput | BadRequest (400) | Entrée non valide \<the invalid input\> .
InvalidRequestBody | BadRequest (400) | Corps de la demande non valide.
InvalidHashValue | BadRequest (400) | La valeur de \<the invalid hash\> hachage n’est pas valide.
InvalidDomainName | BadRequest (400) | Le nom de \<the invalid domain\> domaine n’est pas valide.
InvalidIpAddress | BadRequest (400) | L’adresse IP \<the invalid IP\> n’est pas valide.
InvalidUrl | BadRequest (400) | \<the invalid URL\>L’URL n’est pas valide.
MaximumBatchSizeExceeded | BadRequest (400) | La taille maximale du lot est dépassée. Reçu : \<batch size received\> , autorisé : {taille de lot autorisée}.
MissingRequiredParameter | BadRequest (400) | Le \<the missing parameter\> paramètre est manquant.
OsPlatformNotSupported | BadRequest (400) | La plateforme du \<the client OS Platform\> système d’exploitation n’est pas prise en charge pour cette action.
ClientVersionNotSupported | BadRequest (400) | \<The requested action\> est pris en charge sur la version du client \<supported client version\> et versions supérieures.
Non autorisé (Unauthorized) | Non autorisé (401) | Non autorisé (Unauthorized) <br /><br />*Remarque : généralement causée par un en-tête d’autorisation non valide ou expiré.*
Interdit (Forbidden) | Interdit (403) | Interdit (Forbidden) <br /><br />*Remarque : Jeton valide mais autorisation insuffisante pour l’action.*
DisabledFeature | Interdit (403) | La fonctionnalité client n’est pas activée.
DisallowedOperation | Interdit (403) | \<the disallowed operation and the reason\>.
NotFound | In found (404) | Message d’erreur Général in trouvé.
ResourceNotFound | In found (404) | Ressource \<the requested resource\> in trouvée.
InternalServerError | Erreur interne du serveur (500) | *Remarque : aucun message d’erreur, retenter l’opération ou [contacter Microsoft](../../admin/get-help-support.md) si elle n’est pas résolue*

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
> Les paramètres de corps sont sensibles à la cas.

Si vous faites l’expérience d’une erreur *InvalidRequestBody* ou *MissingRequiredParameter,* elle peut être causée par une faute de frappe. Consultez la documentation de l’API et vérifiez que les paramètres envoyés correspondent à l’exemple approprié.

## <a name="tracking-id"></a>ID de suivi

Chaque réponse d’erreur contient un paramètre d’ID unique pour le suivi. Le nom de propriété de ce paramètre est *cible.* Lorsque vous nous contactez à propos d’une erreur, l’attachement de cet ID nous aidera à trouver la cause première du problème.

## <a name="related-articles"></a>Articles connexes

- [présentation Microsoft 365 Defender API de Microsoft 365 Defender’api](api-overview.md)
- [API Microsoft 365 Defender prises en charge](api-supported.md)
- [Accéder aux API Microsoft 365 Defender de données](api-access.md)
- [En savoir plus sur les limites d’API et les licences](api-terms.md)
