---
title: Obtenir un score d'exposition
description: Récupère le score d’exposition de l’organisation.
keywords: api, api de graphique, api pris en charge, obtenir, score d’exposition, score d’exposition de l’organisation
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
author: dansimp
ms.author: dansimp
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 99aa5a74daf183788f42cd39765f39eda50472a3
ms.sourcegitcommit: 3576c2fee77962b516236cb67dd3df847d61c527
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2021
ms.locfileid: "53621918"
---
# <a name="get-exposure-score"></a>Obtenir un score d'exposition

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]


[!include[Prerelease information](../../includes/prerelease.md)]

Récupère le score d’exposition de l’organisation.

## <a name="permissions"></a>Autorisations

L’une des autorisations suivantes est nécessaire pour appeler cette API. Pour en savoir plus, notamment sur le choix des autorisations, voir [Utiliser Microsoft Defender pour les API de point de terminaison](apis-intro.md)

Type d’autorisation | Autorisation | Nom d’affichage de l’autorisation
:---|:---|:---
Application | Score.Read.All | « Lire le score de gestion des menaces et des vulnérabilités »
Déléguée (compte professionnel ou scolaire) | Score.Read | « Lire le score de gestion des menaces et des vulnérabilités »

## <a name="http-request"></a>Requête HTTP

```http
GET /api/exposureScore
```

## <a name="request-headers"></a>En-têtes de demande

Nom|Type|Description
:---|:---|:---
Autorisation | Chaîne | Porteur {token}. **Obligatoire**.

## <a name="request-body"></a>Corps de la demande

Vide

## <a name="response"></a>Réponse

Si elle réussit, cette méthode renvoie 200 OK, avec les données d’exposition dans le corps de la réponse.

## <a name="example"></a>Exemple

### <a name="request"></a>Demande

Voici un exemple de demande.

```http
GET https://api.securitycenter.microsoft.com/api/exposureScore
```

### <a name="response"></a>Réponse

Voici un exemple de réponse.

>[!NOTE]
>La liste de réponses présentée ici peut être tronquée à des raisons de concision. 

```json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#ExposureScore/$entity",
    "time": "2019-12-03T07:23:53.280499Z",
    "score": 33.491554051195706
}

```

## <a name="see-also"></a>Voir aussi

- [Gestion des menaces & vulnérabilité basée sur les risques](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt)
- [Score d& exposition des menaces et des vulnérabilités](/microsoft-365/security/defender-endpoint/tvm-exposure-score)
