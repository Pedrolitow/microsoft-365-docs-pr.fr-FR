---
title: Obtenir les informations d’autorisation des extensions de navigateur
description: Récupère la liste de toutes les autorisations requises pour une extension de navigateur
keywords: api, api graphe, api prises en charge, get, informations d’extension de navigateur, Microsoft Defender pour point de terminaison, Gestion des vulnérabilités Microsoft Defender
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: siosulli
author: siosulli
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 0dd9498e5ff126e8b91a8cb70cf352f6720db686
ms.sourcegitcommit: 10e6abe740e27000e223378eb17d657a47555fa8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2022
ms.locfileid: "67499055"
---
# <a name="get-browser-extensions-permission-information"></a>Obtenir les informations d’autorisation des extensions de navigateur

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Gestion des vulnérabilités de Microsoft Defender](../defender-vulnerability-management/index.yml)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

> Vous voulez découvrir Gestion des vulnérabilités Microsoft Defender ? En savoir plus sur la façon dont vous pouvez vous inscrire à la [Gestion des vulnérabilités Microsoft Defender préversion publique](../defender-vulnerability-management/get-defender-vulnerability-management.md).

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

[!include[Prerelease information](../../includes/prerelease.md)]

## <a name="api-description"></a>Description de l’API

Récupère une liste de toutes les autorisations demandées par une extension de navigateur spécifique. Il s’agit d’une description statique des données qui est principalement utilisée pour améliorer les données [retournées par l’API d’évaluation des extensions du navigateur Export](get-assessment-browser-extensions.md).

En combinant ces API, vous pouvez voir une description des autorisations demandées par les extensions de navigateur qui sont disponibles dans les résultats [d’évaluation des extensions de navigateur d’exportation](get-assessment-browser-extensions.md) .

<br>Prend [en charge les requêtes OData V4](https://www.odata.org/documentation/).
<br>Opérateurs OData pris en charge :
<br>```$filter``` on:  ```id```, ```name```, ```description```, ```cvssV3```, ```publishedOn```, ```severity```et ```updatedOn``` properties.
<br>```$top``` avec une valeur maximale de 10 000.
<br>```$skip```.
<br>Consultez des exemples dans les [requêtes OData avec Microsoft Defender pour point de terminaison](exposed-apis-odata-samples.md).

## <a name="permissions"></a>Autorisations

L’une des autorisations suivantes est requise pour appeler cette API. Pour plus d’informations, notamment sur le choix des autorisations, consultez [Utiliser Microsoft Defender pour point de terminaison API](apis-intro.md) pour plus d’informations.

Type d’autorisation|Autorisation|Nom d’affichage de l’autorisation
:---|:---|:---
Application|Software.Read.All|« Lire les informations sur les logiciels de gestion des menaces et des vulnérabilités »
Déléguée (compte professionnel ou scolaire)|Software.Read|« Lire les informations sur les logiciels de gestion des menaces et des vulnérabilités »

## <a name="http-request"></a>Requête HTTP

```http
GET api/browserextensions/permissionsinfo
```

## <a name="request-headers"></a>En-têtes de demande

Nom|Type|Description
:---|:---|:---
Autorisation|Chaîne|Porteur {token}. **Obligatoire**.

## <a name="request-body"></a>Corps de la demande

Vide

## <a name="response"></a>Réponse

Si elle réussit, cette méthode retourne 200 OK avec la liste de toutes les autorisations demandées par une extension de navigateur dans le corps.

## <a name="example"></a>Exemple

### <a name="request-example"></a>Exemple de requête

Voici un exemple de demande.

```http
GET https://api.securitycenter.microsoft.com/api/browserextensions/permissionsinfo
```

### <a name="response-example"></a>Exemple de réponse

Voici un exemple de réponse.

```json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#BrowserExtension",
    "value": [
{
  "value": [
    {
      "key": "audioCapture",
      "permissionName": "Capture audio from attached mic or webcam",
      "description": "Capture audio from attached mic or webcam. Could be used to listen in on use."
    },
    {
      "key": "app.window.fullscreen.overrideEsc",
      "permissionName": "Prevent escape button from exiting fullscreen",
      "description": "Can prevent escape button from exiting fullscreen."
    },
    {
      "key": "browsingData",
      "permissionName": "Clear browsing data",
      "description": "Clears browsing data which could result in a forensics/logging issues."
    },
    {
      "key": "content_security_policy",
      "permissionName": "Can manipulate default Content Security Policy (CSP)",
      "description": "CSP works as a block/allow listing mechanism for resources loaded or executed by your extensions. Can manipulate default CSP."
    }

            ]
}
    ]
```

## <a name="see-also"></a>Voir aussi

- [Obtenir les informations d’autorisation des extensions de navigateur](get-assessment-browser-extensions.md)
- [Évaluation des extensions de navigateur](../defender-vulnerability-management/tvm-browser-extensions.md)

## <a name="other-related"></a>Autres éléments connexes

- [Gestion des vulnérabilités](../defender-vulnerability-management/defender-vulnerability-management.md)
- [Vulnérabilités dans votre organisation](../defender-vulnerability-management/tvm-weaknesses.md)