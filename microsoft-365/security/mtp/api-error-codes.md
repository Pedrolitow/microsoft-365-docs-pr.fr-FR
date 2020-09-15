---
title: Codes d’erreur de l’API REST Common protection Microsoft Threat
description: En savoir plus sur les codes d’erreur de l’API REST Microsoft Threat Protection courants
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
ms.openlocfilehash: 36a1cedacc5f16c422e2b0d458b0d1767cf08b64
ms.sourcegitcommit: 9a275a13af3e063e80ce1bd3cd8142a095db92d2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2020
ms.locfileid: "47650293"
---
# <a name="common-microsoft-threat-protection-rest-api-error-codes"></a>Codes d’erreur de l’API REST Common protection Microsoft Threat

**S’applique à :**
- Protection Microsoft contre les menaces

>[!IMPORTANT] 
>Certaines informations se rapportent à des produits précommercialisés susceptibles d’être modifiés de manière substantielle avant leur publication commerciale. Microsoft makes no warranties, express or implied, with respect to the information provided here.

Les codes d’erreur figurant dans le tableau suivant peuvent être renvoyés par une opération sur n’importe quelle API de protection contre les menaces Microsoft.

Chaque réponse d’erreur contient un message d’erreur qui peut vous aider à résoudre le problème.

Le message est un texte libre qui peut être modifié.

Au bas de la page, vous trouverez des exemples de réponses.

Code d'erreur |Code d’état HTTP |Message 
:---|:---|:---
BadRequest | BadRequest (400) | Message d’erreur de requête incorrecte générale.
ODataError | BadRequest (400) | Requête URI OData non valide (l’erreur spécifique est spécifiée).
InvalidInput | BadRequest (400) | Entrée non valide {entrée incorrecte}.
InvalidRequestBody | BadRequest (400) | Corps de la requête non valide.
InvalidHashValue | BadRequest (400) | Valeur de hachage {le hachage incorrect} n’est pas valide.
InvalidDomainName | BadRequest (400) | Nom de domaine {domaine non valide} non valide.
InvalidIpAddress | BadRequest (400) | Adresse IP {l’adresse IP incorrecte} n’est pas valide.
InvalidUrl | BadRequest (400) | URL {l’URL incorrecte} n’est pas valide.
MaximumBatchSizeExceeded | BadRequest (400) | Taille maximale de lot dépassée. Reçu : {taille de lot reçue}, autorisée : {taille du lot autorisée}.
MissingRequiredParameter | BadRequest (400) | Paramètre {le paramètre manquant} est manquant.
OsPlatformNotSupported | BadRequest (400) | Plateforme de système d’exploitation {la plateforme de système d’exploitation client} n’est pas prise en charge pour cette action.
ClientVersionNotSupported | BadRequest (400) | {L’action demandée} est prise en charge sur la version du client {version du client pris en charge} et versions ultérieures.
Non autorisé (Unauthorized) | Non autorisé (401) | Non autorisé (en général, en en-tête d’autorisation ou expiré).
Interdit (Forbidden) | Interdit (403) | Interdit (jeton valide, mais autorisation insuffisante pour l’action).
DisabledFeature | Interdit (403) | La fonctionnalité de client n’est pas activée.
DisallowedOperation | Interdit (403) | {l’opération non autorisée et la raison}.
NotFound | Introuvable (404) | Message d’erreur général introuvable.
ResourceNotFound | Introuvable (404) | Ressource {la ressource demandée} est introuvable.
InternalServerError | Erreur de serveur interne (500) | (Aucun message d’erreur, retentez l’opération ou contactez-nous s’il n’est pas résolu)

## <a name="body-parameters-are-case-sensitive"></a>Les paramètres Body respectent la casse

Les paramètres de corps soumis respectent actuellement la casse.
<br>Si vous constatez une erreur **InvalidRequestBody** ou **MissingRequiredParameter** , il peut s’agir d’un paramètre incorrect ou d’une lettre minuscule.
<br>Nous vous recommandons de consulter la page relative à la documentation de l’API et de vérifier que les paramètres soumis correspondent à l’exemple approprié.

## <a name="correlation-request-id"></a>ID de demande de corrélation

Chaque réponse d’erreur contient un paramètre ID unique pour le suivi.
<br>Le nom de la propriété de ce paramètre est « cible ».
<br>Lors de la création d’une erreur, la liaison de cet ID vous permettra de trouver la cause première du problème.

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

