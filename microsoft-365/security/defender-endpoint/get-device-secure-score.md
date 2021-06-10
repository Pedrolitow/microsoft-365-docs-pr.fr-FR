---
title: Obtenir un score sécurisé d’appareil
description: Récupère le score de sécurité de l’appareil de l’organisation.
keywords: api, api de graphique, api pris en charge, obtenir, alertes, récent
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
ms.openlocfilehash: dd9def688619b6079d947cb76069aa0f77d768de
ms.sourcegitcommit: 5d8de3e9ee5f52a3eb4206f690365bb108a3247b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2021
ms.locfileid: "52772304"
---
# <a name="get-device-secure-score"></a>Obtenir un score sécurisé d’appareil

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

**S’applique à :** [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/?linkid=2154037)

- Vous souhaitez découvrir Microsoft Defender pour le point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink) 

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]


Récupère votre score [de sécurité Microsoft pour les appareils.](tvm-microsoft-secure-score-devices.md) Un niveau de sécurité Microsoft plus élevé pour les appareils signifie que vos points de terminaison sont plus résistants aux attaques contre les menaces de cybersécurité. 

## <a name="permissions"></a>Autorisations

L’une des autorisations suivantes est nécessaire pour appeler cette API. Pour plus d’informations, notamment sur le choix des autorisations, voir [Utiliser Microsoft Defender pour les API de point](apis-intro.md) de terminaison pour plus d’informations.

Type d’autorisation |   Autorisation  |   Nom d’affichage de l’autorisation
:---|:---|:---
Application |   Score.Read.Alll |   « Lire le score de gestion des menaces et des vulnérabilités »
Déléguée (compte professionnel ou scolaire) | Score.Read | « Lire le score de gestion des menaces et des vulnérabilités »

## <a name="http-request"></a>Requête HTTP

```
GET /api/configurationScore
```

## <a name="request-headers"></a>En-têtes de demande

Nom | Type | Description
:---|:---|:---
Autorisation | String | Porteur {token}. **Obligatoire**.

## <a name="request-body"></a>Corps de la demande

Vide

## <a name="response"></a>Réponse

Si elle réussit, cette méthode renvoie 200 OK, avec les données de score de sécurité de l’appareil dans le corps de la réponse.

## <a name="example"></a>Exemple

### <a name="request"></a>Demande

Voici un exemple de demande.

```http
GET https://api.securitycenter.microsoft.com/api/configurationScore
```

### <a name="response"></a>Réponse

Voici un exemple de réponse.

>[!NOTE]
>La liste de réponses présentée ici peut être tronquée à des raisons de concision. 

```json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#ConfigurationScore/$entity",
    "time": "2019-12-03T09:15:58.1665846Z",
    "score": 340
}
```

## <a name="see-also"></a>Voir aussi

- [Requêtes OData avec Microsoft Defender pour le point de terminaison](exposed-apis-odata-samples.md)
