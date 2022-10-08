---
title: Obtenir l’API des machines associées à l’utilisateur
description: Découvrez comment utiliser l’API Obtenir des machines liées à l’utilisateur pour récupérer une collection d’appareils liés à un ID utilisateur dans Microsoft Defender pour point de terminaison.
keywords: api, api graphe, api prises en charge, get, utilisateur, alertes liées à l’utilisateur
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- tier3
ms.topic: article
ms.subservice: mde
ms.custom: api
search.appverid: met150
ms.openlocfilehash: 5901e3fbcf5f1506009793cd96f5e7491665d14c
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68190592"
---
# <a name="get-user-related-machines-api"></a>Obtenir l’API des machines associées à l’utilisateur

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)


[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>Description de l’API
Récupère une collection d’appareils liés à un ID d’utilisateur donné.

## <a name="limitations"></a>Limites

Les limites de débit pour cette API sont de 100 appels par minute et de 1 500 appels par heure.

## <a name="permissions"></a>Autorisations

L’une des autorisations suivantes est requise pour appeler cette API. Pour en savoir plus, notamment sur le choix des autorisations, consultez [Utiliser Microsoft Defender pour point de terminaison API](apis-intro.md)

Type d’autorisation|Autorisation|Nom d’affichage de l’autorisation
:---|:---|:---
Application |Machine.Read.All|'Lire tous les profils d’ordinateur'
Application |Machine.ReadWrite.All |« Lire et écrire toutes les informations sur l’ordinateur »
Déléguée (compte professionnel ou scolaire) | Machine.Read | « Lire les informations de l’ordinateur »
Déléguée (compte professionnel ou scolaire) | Machine.ReadWrite | « Lire et écrire des informations sur la machine »

> [!NOTE]
> Lors de l’obtention d’un jeton à l’aide des informations d’identification de l’utilisateur :
>
> - L’utilisateur doit disposer au moins de l’autorisation de rôle suivante : « Afficher les données ». Pour plus d’informations, consultez [Créer et gérer des rôles](user-roles.md)
> - La réponse inclut uniquement les appareils auxquels l’utilisateur peut accéder, en fonction des paramètres du groupe d’appareils. Pour plus d’informations, consultez [Créer et gérer des groupes d’appareils](machine-groups.md).
>
> La création de groupes d’appareils est prise en charge dans Defender pour point de terminaison Plan 1 et Plan 2. 

## <a name="http-request"></a>Requête HTTP

```http
GET /api/users/{id}/machines
```

**L’ID n’est pas l’UPN complet, mais uniquement le nom d’utilisateur. (par exemple, pour récupérer des machines pour user1@contoso.com utiliser /api/users/user1/machines)**

## <a name="request-headers"></a>En-têtes de demande

Nom|Type|Description
:---|:---|:---
Autorisation | Chaîne | Porteur {token}. **Obligatoire**.

## <a name="request-body"></a>Corps de la demande

Vide

## <a name="response"></a>Réponse

En cas de réussite et d’existence de l’utilisateur : 200 OK avec la liste des entités de [machine](machine.md) dans le corps. Si l’utilisateur n’existe pas , 200 OK avec un jeu vide.

## <a name="example"></a>Exemple

### <a name="request"></a>Demande

Voici un exemple de demande.

```http
GET https://api.securitycenter.microsoft.com/api/users/user1/machines
```
