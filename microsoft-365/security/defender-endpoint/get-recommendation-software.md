---
title: Obtenir les actions d’amélioration par logiciel
description: Récupère une recommandation de sécurité liée à un logiciel spécifique.
keywords: api, api de graphique, api pris en charge, obtenir, recommandation de sécurité, recommandation de sécurité pour les logiciels, Gestion des menaces et des vulnérabilités, Gestion des menaces et des vulnérabilités api
search.product: eADQiWindows 10XVcnh
ms.prod: w10
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dolmont
author: DulceMontemayor
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 9227987544e1cee1eeb4b65b5ae6bbf719558dd4
ms.sourcegitcommit: 4fb1226d5875bf5b9b29252596855a6562cea9ae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2021
ms.locfileid: "52845207"
---
# <a name="get-recommendation-by-software"></a>Obtenir les actions d’amélioration par logiciel

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :** [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/?linkid=2154037)

> Vous souhaitez faire l’expérience de Defender for Endpoint ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]


[!include[Prerelease information](../../includes/prerelease.md)]

Récupère une recommandation de sécurité liée à un logiciel spécifique.

## <a name="permissions"></a>Autorisations
L’une des autorisations suivantes est nécessaire pour appeler cette API. Pour plus d’informations, notamment sur le choix des autorisations, voir [Utiliser Microsoft Defender pour les API de point](apis-intro.md) de terminaison pour plus d’informations.

Type d’autorisation |   Autorisation  |   Nom d’affichage de l’autorisation
:---|:---|:---
Application |   SecurityRecommendation.Read.All |   « Lire les informations de recommandation sur la sécurité de la gestion des menaces et des vulnérabilités »
Déléguée (compte professionnel ou scolaire) | SecurityRecommendation.Read |  « Lire les informations de recommandation sur la sécurité de la gestion des menaces et des vulnérabilités »

## <a name="http-request"></a>Requête HTTP
```
GET /api/recommendations/{id}/software
```

## <a name="request-headers"></a>En-têtes de demande

Nom | Type | Description
:---|:---|:---
Autorisation | String | Porteur {token}. **Obligatoire**.


## <a name="request-body"></a>Corps de la demande
Vide

## <a name="response"></a>Réponse
Si elle réussit, cette méthode renvoie 200 OK avec le logiciel associé aux recommandations de sécurité dans le corps.


## <a name="example"></a>Exemple

**Demande**

Voici un exemple de demande.

```
GET https://api.securitycenter.microsoft.com/api/recommendations/va-_-google-_-chrome/software 
```

**Réponse**

Voici un exemple de réponse.

```json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#Analytics.Contracts.PublicAPI.PublicProductDto",
    "id": "google-_-chrome",
    "name": "chrome",
    "vendor": "google",
    "weaknesses": 38,
    "publicExploit": false,
    "activeAlert": false,
    "exposedMachines": 5,
    "impactScore": 3.94418621
}
```

## <a name="related-topics"></a>Voir aussi
- [Gestion des menaces & vulnérabilité basée sur les risques](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt)
- [Recommandations & sécurité des menaces et des vulnérabilités](/microsoft-365/security/defender-endpoint/tvm-security-recommendation)
