---
title: Supprimer un fichier de la bibliothèque de réponses en direct
description: Découvrez comment supprimer un fichier de la bibliothèque de réponses en direct.
keywords: api, api de graphique, api pris en charge, supprimer de la bibliothèque
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
localization_priority: normal
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
ms.topic: reference
MS.technology: mde
ms.custom: api
ms.openlocfilehash: bd5c77911c889bb52e04981c96be239ff17575f2
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63330841"
---
#  <a name="delete-a-file-from-the-live-response-library"></a>Supprimer un fichier de la bibliothèque de réponses en direct  

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2146631)

[!include[Prerelease information](../../includes/prerelease.md)]

>Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink) 

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>Description de l’API

Supprimez un fichier de la bibliothèque de réponses en direct.

## <a name="limitations"></a>Limites

1.  Les limites de taux pour cette API sont de 100 appels par minute et de 1 500 appels par heure.

## <a name="permissions"></a>Autorisations

L’une des autorisations suivantes est nécessaire pour appeler cette API. Pour en savoir plus, notamment sur le choix des autorisations, [consultez La mise en place](apis-intro.md).

| Type d’autorisation                    | Autorisation     | Nom d’affichage de l’autorisation        |
|------------------------------------|----------------|--------------------------------|
| Application                        | Library.Manage | Gérer la bibliothèque de réponses en direct |
| Déléguée (compte professionnel ou scolaire) | Library.Manage | Gérer la bibliothèque de réponses en direct |

## <a name="http-request"></a>Requête HTTP

SUPPRIMER https://api.securitycenter.microsoft.com/api/libraryfiles/{fileName}

## <a name="request-headers"></a>En-têtes de demande

| Nom            | Type   | Description               |
|-----------------|--------|---------------------------|
| Autorisation   | String | Porteur\<token>\. Obligatoire. |

## <a name="request-body"></a>Corps de la demande

Vide

## <a name="response"></a>Réponse

-   Si le fichier existe dans la bibliothèque et supprimé correctement 204 Aucun contenu.

-   Si le nom de fichier spécifié n’a pas été trouvé 404 In trouvé.

## <a name="example"></a>Exemple

Demande

Voici un exemple de demande.

```HTTP
DELETE https://api.securitycenter.microsoft.com/api/libraryfiles/script1.ps1
```

## <a name="related-topic"></a>Rubrique connexe
- [Exécuter la réponse en direct](run-live-response.md) 