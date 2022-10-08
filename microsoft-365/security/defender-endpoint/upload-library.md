---
title: Charger des fichiers dans la bibliothèque de réponses en direct
description: Découvrez comment charger un fichier dans la bibliothèque de réponses actives.
keywords: api, API de graphe, api prises en charge, chargement dans la bibliothèque
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.service: microsoft-365-security
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
- tier2
ms.topic: reference
ms.subservice: mde
ms.custom: api
ms.openlocfilehash: 2d38ab7c434e99a08b162045a7c69210401755ae
ms.sourcegitcommit: 4e42bafee965446f44f7f57d1defed2b9b24fce8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2022
ms.locfileid: "68225281"
---
#  <a name="upload-files-to-the-live-response-library"></a>Charger des fichiers dans la bibliothèque de réponses en direct  

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/microsoft-defender-endpoint)

[!include[Prerelease information](../../includes/prerelease.md)]

>Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink) 

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>Description de l’API

Chargez le fichier dans la bibliothèque de réponses dynamiques.

## <a name="limitations"></a>Limites

1.  La limite de taille maximale du fichier est de 20 Mo.

2.  Les limites de débit pour cette API sont de 100 appels par minute et de 1 500 appels par heure.

## <a name="permissions"></a>Autorisations

L’une des autorisations suivantes est requise pour appeler cette API. Pour en savoir plus, notamment sur le choix des autorisations, consultez [Prise en main](apis-intro.md).


| Type d’autorisation                    | Autorisation     | Nom d’affichage de l’autorisation        |
|------------------------------------|----------------|--------------------------------|
| Application                        | Library.Manage | Gérer la bibliothèque de réponses en direct |
| Déléguée (compte professionnel ou scolaire) | Library.Manage | Gérer la bibliothèque de réponses en direct |

## <a name="http-request"></a>Requête HTTP

Charger

```HTTP
POST https://api.securitycenter.microsoft.com/api/libraryfiles
```

## <a name="request-headers"></a>En-têtes de demande

|  Nom   |    Type    |       Description                         |
|-----------------|--------|--------------------------------|
| Autorisation   | Chaîne | \<token>Porteur. Obligatoire.      |
| Content-Type    | string | multipart/form-data. Obligatoire. |

## <a name="request-body"></a>Corps de la demande

Dans le corps de la demande, fournissez un objet form-data avec les paramètres suivants :

| Paramètre         |     Type         |       Description                                        |
|-----------------------|--------------|------------------------------------------------------------|
| File                  | Contenu du fichier | Fichier à charger dans la bibliothèque de réponses dynamiques. Obligatoire |
| Description           | Chaîne       | Description du fichier                                  |
| ParametersDescription | Chaîne       | (Facultatif) Paramètres requis pour l’exécution du script. La valeur par défaut est une chaîne vide.                |
| OverrideIfExists      | Boolean      | (Facultatif) Indique s’il faut remplacer le fichier s’il existe déjà. La valeur par défaut est une chaîne vide.          |



## <a name="response"></a>Réponse

-   Si elle réussit, cette méthode renvoie le code de réponse 200 - OK et l’entité de bibliothèque de réponses dynamiques chargée dans le corps de la réponse.

-   En cas d’échec : cette méthode retourne 400 - Demande incorrecte.  
    Une requête incorrecte indique généralement un corps incorrect.

## <a name="example"></a>Exemple

Demande

Voici un exemple de la requête utilisant curl.

```CURL
curl -X POST https://api.securitycenter.microsoft.com/api/libraryfiles -H
"Authorization: Bearer \$token" -F "file=\@mdatp1.png" -F
"ParametersDescription=test"  
-F "HasParameters=true" -F "OverrideIfExists=true" -F "Description=test
description"
```

## <a name="related-topic"></a>Rubrique connexe

-  [Exécuter la réponse en direct](run-live-response.md) 