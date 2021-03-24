---
title: Erreurs courantes de l’API Microsoft Defender ATP
description: Liste des erreurs d’API Microsoft Defender ATP courantes avec descriptions.
keywords: api, api mdatp, erreurs, résolution des problèmes
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
ms.technology: mde
ms.openlocfilehash: ddbbe07bc477ae3a5016feb795b5bad5ed82a30a
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2021
ms.locfileid: "51064377"
---
# <a name="common-rest-api-error-codes"></a>Codes d’erreur courants de l’API REST

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


* Les codes d’erreur répertoriés dans le tableau suivant peuvent être renvoyés par une opération sur n’importe quelle API Microsoft Defender pour point de terminaison.
* En plus du code d’erreur, chaque réponse d’erreur contient un message d’erreur, qui peut aider à résoudre le problème.
* Le message est un texte libre qui peut être modifié.
* En bas de la page, vous trouverez des exemples de réponse.

>Vous souhaitez faire l’expérience de Defender pour point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-assignaccess-abovefoldlink)

Code d’erreur |Code d’état HTTP |Message 
:---|:---|:---
BadRequest | BadRequest (400) | Message d’erreur Général Bad Request.
ODataError | BadRequest (400) | Requête URI OData non valide (l’erreur spécifique est spécifiée).
InvalidInput | BadRequest (400) | Entrée non valide {l’entrée non valide}.
InvalidRequestBody | BadRequest (400) | Corps de la demande non valide.
InvalidHashValue | BadRequest (400) | La valeur de hachage {le hachage non valide} n’est pas valide.
InvalidDomainName | BadRequest (400) | Nom de domaine {le domaine non valide} non valide.
InvalidIpAddress | BadRequest (400) | Adresse IP {l’adresse IP non valide} n’est pas valide.
InvalidUrl | BadRequest (400) | URL {l’URL non valide} n’est pas valide.
MaximumBatchSizeExceeded | BadRequest (400) | La taille maximale du lot est dépassée. Received: {batch size received}, allowed: {batch size allowed}.
MissingRequiredParameter | BadRequest (400) | Le paramètre {le paramètre manquant} est manquant.
OsPlatformNotSupported | BadRequest (400) | La plateforme du système d’exploitation {la plateforme de système d’exploitation cliente} n’est pas prise en charge pour cette action.
ClientVersionNotSupported | BadRequest (400) | {The requested action} is supported on client version {supported client version} and above.
Non autorisé (Unauthorized) | Non autorisé (401) | Non autorisé (en-tête d’autorisation non valide ou expiré).
Interdit (Forbidden) | Interdit (403) | Interdit (jeton valide mais autorisation insuffisante pour l’action).
DisabledFeature | Interdit (403) | La fonctionnalité client n’est pas activée.
DisallowedOperation | Interdit (403) | {l’opération nonallée et la raison}.
NotFound | In found (404) | Message d’erreur Général in trouvé.
ResourceNotFound | In found (404) | Ressource {la ressource demandée} in trouvée.
InternalServerError | Erreur interne du serveur (500) | (Aucun message d’erreur, nouvelle tentative de l’opération)
TooManyRequests | Trop de demandes (429) | La réponse représente l’atteinte de la limite de quota soit par nombre de demandes, soit par processeur.

## <a name="body-parameters-are-case-sensitive"></a>Les paramètres body sont sensibles à la cas

Les paramètres du corps soumis sont actuellement sensibles à la cas.
<br>Si vous faites l’expérience d’erreurs **InvalidRequestBody** ou **MissingRequiredParameter,** cela peut être dû à une majuscule de paramètre incorrecte ou à une lettre majuscule incorrecte.
<br>Consultez la page de documentation de l’API et vérifiez que les paramètres envoyés correspondent à l’exemple approprié.

## <a name="correlation-request-id"></a>ID de demande de corrélation

Chaque réponse d’erreur contient un paramètre d’ID unique pour le suivi.
<br>Le nom de propriété de ce paramètre est « target ».
<br>Lorsque vous nous contactez à propos d’une erreur, l’attachement de cet ID permet de trouver la cause première du problème.

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
