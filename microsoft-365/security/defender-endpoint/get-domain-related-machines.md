---
title: API Obtenir les ordinateurs liés au domaine
description: Découvrez comment utiliser l’API Obtenir des ordinateurs liés au domaine pour obtenir des ordinateurs qui ont communiqué avec ou depuis un domaine dans Microsoft Defender pour le point de terminaison.
keywords: api, api de graphique, api pris en charge, obtenir, domaine, associé, appareils
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
MS.technology: mde
ms.custom: api
ms.openlocfilehash: a9f1a00173228cf973ed0149d88c81b3d3f2c6fa
ms.sourcegitcommit: c11d4a2b9cb891ba22e16a96cb9d6389f6482459
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2021
ms.locfileid: "61283064"
---
# <a name="get-domain-related-machines-api"></a>API Obtenir les ordinateurs liés au domaine

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!Include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!Include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>Description de l’API

Récupère une collection [d’ordinateurs](machine.md) qui ont communiqué avec ou à partir d’une adresse de domaine donnée.

## <a name="limitations"></a>Limites

1. Vous pouvez interroger sur les appareils la dernière mise à jour en fonction de votre période de rétention configurée.
2. Les limites de taux pour cette API sont de 100 appels par minute et de 1 500 appels par heure.

## <a name="permissions"></a>Autorisations

L’une des autorisations suivantes est nécessaire pour appeler cette API. Pour en savoir plus, notamment sur le choix des autorisations, voir [Utiliser Microsoft Defender pour les API de point de terminaison](apis-intro.md)

Type d’autorisation|Autorisation|Nom d’affichage de l’autorisation
:---|:---|:---
Application|Machine.Read.All|« Lire tous les profils d’ordinateur »
Application|Machine.ReadWrite.All|« Lire et écrire toutes les informations sur l’ordinateur »
Déléguée (compte professionnel ou scolaire)|Machine.Read|« Lire les informations sur l’ordinateur »
Déléguée (compte professionnel ou scolaire)|Machine.ReadWrite|« Lire et écrire des informations sur l’ordinateur »

> [!NOTE]
> Lors de l’obtention d’un jeton à l’aide des informations d’identification de l’utilisateur :
>
> - L’utilisateur doit avoir au moins l’autorisation de rôle suivante : « Afficher les données » (pour plus d’informations, voir [Créer et gérer des rôles)](user-roles.md)
> - La réponse inclut uniquement les appareils accessibles à l’utilisateur, en fonction des paramètres de groupe d’appareils (pour plus d’informations, voir Créer et gérer des groupes [d’appareils).](machine-groups.md)

## <a name="http-request"></a>Requête HTTP

```http
GET /api/domains/{domain}/machines
```

## <a name="request-headers"></a>En-têtes de demande

Nom|Type|Description
:---|:---|:---
Autorisation|String|Porteur {token}. **Obligatoire**.

## <a name="request-body"></a>Corps de la demande

Vide

## <a name="response"></a>Réponse

En cas de réussite et si le domaine existe : 200 - OK avec la liste des [entités de l’ordinateur.](machine.md) Si le domaine n’existe pas : 200 - OK avec un ensemble vide.

## <a name="example"></a>Exemple

### <a name="request"></a>Demande

Voici un exemple de la demande.

```http
GET https://api.securitycenter.microsoft.com/api/domains/api.securitycenter.microsoft.com/machines
```
