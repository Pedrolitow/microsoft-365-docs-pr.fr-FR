---
title: API Obtenir les ordinateurs liés à l’utilisateur
description: Découvrez comment utiliser l’API Obtenir des ordinateurs liés à l’utilisateur pour récupérer une collection d’appareils liés à un ID d’utilisateur dans Microsoft Defender for Endpoint.
keywords: api, api de graphique, api pris en charge, obtenir, utilisateur, alertes associées à l’utilisateur
search.product: eADQiWindows 10XVcnh
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
ms.openlocfilehash: 8206592585544b2a4ef1d3a8acf2d9a27247b92f
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60212520"
---
# <a name="get-user-related-machines-api"></a>API Obtenir les ordinateurs liés à l’utilisateur

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez faire l’expérience de Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)


[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>Description de l’API
Récupère une collection d’appareils liés à un ID d’utilisateur donné.

## <a name="limitations"></a>Limites

Les limites de taux pour cette API sont de 100 appels par minute et de 1 500 appels par heure.

## <a name="permissions"></a>Autorisations

L’une des autorisations suivantes est nécessaire pour appeler cette API. Pour en savoir plus, notamment sur le choix des autorisations, voir [Utiliser Microsoft Defender pour les API de point de terminaison](apis-intro.md)

Type d’autorisation|Autorisation|Nom d’affichage de l’autorisation
:---|:---|:---
Application |Machine.Read.All|« Lire tous les profils d’ordinateur »
Application |Machine.ReadWrite.All |« Lire et écrire toutes les informations sur l’ordinateur »
Déléguée (compte professionnel ou scolaire) | Machine.Read | « Lire les informations sur l’ordinateur »
Déléguée (compte professionnel ou scolaire) | Machine.ReadWrite | « Lire et écrire des informations sur l’ordinateur »

> [!NOTE]
> Lors de l’obtention d’un jeton à l’aide des informations d’identification de l’utilisateur :
>
> - L’utilisateur doit avoir au moins l’autorisation de rôle suivante : « Afficher les données ». Pour plus d’informations, voir [Créer et gérer des rôles](user-roles.md))
> - La réponse inclut uniquement les appareils accessibles à l’utilisateur, en fonction des paramètres de groupe d’appareils. Pour plus d’informations, voir [Créer et gérer des groupes d’appareils.](machine-groups.md)

## <a name="http-request"></a>Requête HTTP

```http
GET /api/users/{id}/machines
```

**L’ID n’est pas l’UPN complet, mais uniquement le nom d’utilisateur. (par exemple, pour récupérer des ordinateurs user1@contoso.com utiliser /api/users/user1/machines)**

## <a name="request-headers"></a>En-têtes de demande

Nom|Type|Description
:---|:---|:---
Autorisation | Chaîne | Porteur {token}. **Obligatoire**.

## <a name="request-body"></a>Corps de la demande

Vide

## <a name="response"></a>Réponse

En cas de réussite et si l’utilisateur existe : 200 - OK avec la liste des entités de [l’ordinateur](machine.md) dans le corps. Si l’utilisateur n’existe pas : 200 - OK avec un ensemble vide.

## <a name="example"></a>Exemple

### <a name="request"></a>Demande

Voici un exemple de demande.

```http
GET https://api.securitycenter.microsoft.com/api/users/user1/machines
```
