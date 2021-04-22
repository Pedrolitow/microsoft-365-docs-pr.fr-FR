---
title: Obtenir les recommandations de sécurité
description: Récupère une collection de recommandations de sécurité relatives à un ID d'appareil donné.
keywords: api, api de graphique, api pris en charge, obtenir, liste, fichier, informations, recommandations de sécurité par appareil, api de gestion des menaces & vulnérabilité, api tvm Microsoft Defender pour endpoint
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
ms.openlocfilehash: bc209687d51b3e05bfcfd6028042ba5912b877f6
ms.sourcegitcommit: a8d8cee7df535a150985d6165afdfddfdf21f622
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2021
ms.locfileid: "51935304"
---
# <a name="get-security-recommendations"></a>Obtenir les recommandations de sécurité

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S'applique à :** [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/?linkid=2154037)

> Vous souhaitez faire l'expérience de Defender pour point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

[!include[Prerelease information](../../includes/prerelease.md)]

Récupère une collection de recommandations de sécurité relatives à un ID d'appareil donné.

## <a name="permissions"></a>Autorisations
L'une des autorisations suivantes est nécessaire pour appeler cette API. Pour en savoir plus, notamment sur le choix des autorisations, voir [Utiliser Microsoft Defender pour les API de point de terminaison](apis-intro.md)

Type d’autorisation |   Autorisation  |   Nom d'affichage de l'autorisation
:---|:---|:---
Application | SecurityRecommendation.Read.All | « Lire les informations de recommandation sur la sécurité de la gestion des menaces et des vulnérabilités »
Déléguée (compte professionnel ou scolaire) | SecurityRecommendation.Read |  « Lire les informations de recommandation sur la sécurité de la gestion des menaces et des vulnérabilités »

## <a name="http-request"></a>Requête HTTP
```
GET /api/machines/{machineId}/recommendations
```

## <a name="request-headers"></a>En-têtes de demande

Nom | Type | Description
:---|:---|:---
Autorisation | String | Porteur {token}. **Obligatoire**.


## <a name="request-body"></a>Corps de la demande
Vide

## <a name="response"></a>Réponse
Si elle réussit, cette méthode renvoie 200 OK avec les recommandations de sécurité dans le corps.


## <a name="example"></a>Exemple

**Demande**

Voici un exemple de demande.

```
GET https://api.securitycenter.microsoft.com/api/machines/ac233fa6208e1579620bf44207c4006ed7cc4501/recommendations
```

**Réponse**

Voici un exemple de réponse.


```
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#Recommendations",
    "value": [
        {
            "id": "va-_-git-scm-_-git",
            "productName": "git",
            "recommendationName": "Update Git to version 2.24.1.2",
            "weaknesses": 3,
            "vendor": "git-scm",
            "recommendedVersion": "2.24.1.2",
            "recommendationCategory": "Application",
            "subCategory": "",
            "severityScore": 0,
            "publicExploit": false,
            "activeAlert": false,
            "associatedThreats": [],
            "remediationType": "Update",
            "status": "Active",
            "configScoreImpact": 0,
            "exposureImpact": 0,
            "totalMachineCount": 0,
            "exposedMachinesCount": 1,
            "nonProductivityImpactedAssets": 0,
            "relatedComponent": "Git"
        },
…
}
```

## <a name="related-topics"></a>Voir aussi
- [Gestion des menaces & vulnérabilité basée sur les risques](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt)
- [Recommandations & sécurité des menaces et des vulnérabilités](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/tvm-security-recommendation)
