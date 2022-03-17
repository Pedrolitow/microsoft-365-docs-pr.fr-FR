---
title: Télécharger fichiers dans la bibliothèque de réponses en direct
description: Découvrez comment télécharger un fichier dans la bibliothèque de réponses en direct.
keywords: api, api de graphique, api pris en charge, téléchargement vers la bibliothèque
search.product: eADQiWindows 10XVcnh
search.appverid: met150
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
ms.collection:
- M365-security-compliance
ms.topic: reference
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 84ec7e361cccdc886650b0710f738a4315c4db8d
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2022
ms.locfileid: "63527057"
---
#  <a name="upload-files-to-the-live-response-library"></a>Télécharger fichiers dans la bibliothèque de réponses en direct  

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2146631)

[!include[Prerelease information](../../includes/prerelease.md)]

>Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink) 

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>Description de l’API

Télécharger fichier dans la bibliothèque de réponses en direct.

## <a name="limitations"></a>Limites

1.  La limite de taille maximale du fichier est de 20 Mo.

2.  Les limites de taux pour cette API sont de 100 appels par minute et de 1 500 appels par heure.

## <a name="permissions"></a>Autorisations

L’une des autorisations suivantes est nécessaire pour appeler cette API. Pour en savoir plus, notamment sur le choix des autorisations, [consultez La mise en place](apis-intro.md).


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

Dans le corps de la demande, fournissons un objet de données de formulaire avec les paramètres suivants :

| Paramètre         |     Type         |       Description                                        |
|-----------------------|--------------|------------------------------------------------------------|
| Fichier                  | Contenu du fichier | Fichier à télécharger dans la bibliothèque de réponses en direct. Obligatoire |
| Description           | Chaîne       | Description du fichier.                                  |
| ParametersDescription | Chaîne       | (Facultatif) Paramètres requis pour l’exécuter. La valeur par défaut est une chaîne vide.                |
| OverrideIfExists      | Booléen      | (Facultatif) S’il faut remplacer le fichier s’il existe déjà. La valeur par défaut est une chaîne vide.          |



## <a name="response"></a>Réponse

-   Si elle réussit, cette méthode renvoie le code de réponse 200 - OK et l’entité de bibliothèque de réponses en direct téléchargée dans le corps de la réponse.

-   Si elle ne réussit pas : cette méthode renvoie 400 - Demande non bonne.  
    Une demande incorrecte indique généralement un corps incorrect.

## <a name="example"></a>Exemple

Demande

Voici un exemple de demande à l’aide de l’exemple.

```CURL
curl -X POST https://api.securitycenter.microsoft.com/api/libraryfiles -H
"Authorization: Bearer \$token" -F "file=\@mdatp1.png" -F
"ParametersDescription=test"  
-F "HasParameters=true" -F "OverrideIfExists=true" -F "Description=test
description"
```

## <a name="related-topic"></a>Rubrique connexe

-  [Exécuter la réponse en direct](run-live-response.md) 