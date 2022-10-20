---
title: Ajouter ou supprimer une API d’étiquettes de machine
description: Découvrez comment utiliser l’API Ajouter ou supprimer des balises de machine pour ajouter ou supprimer une balise pour un ordinateur dans Microsoft Defender pour point de terminaison.
keywords: api, api graphe, api prises en charge, balises, balises d’ordinateur
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
ms.topic: conceptual
ms.subservice: mde
ms.custom: api
search.appverid: met150
ms.openlocfilehash: 3117817f8172a7cfc2d0c819e5307d54143bed4a
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68627541"
---
# <a name="add-or-remove-machine-tags-api"></a>Ajouter ou supprimer une API d’étiquettes d’ordinateur

**S’applique à :**

- [Microsoft Defender pour point de terminaison plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [plan Microsoft Defender pour point de terminaison 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>Description de l’API

Ajoute ou supprime une balise à un [ordinateur](machine.md) spécifique.

## <a name="limitations"></a>Limites

1. Vous pouvez publier sur les ordinateurs vus pour la dernière fois en fonction de votre période de rétention configurée.

2. Les limites de débit pour cette API sont de 100 appels par minute et de 1 500 appels par heure.

## <a name="permissions"></a>Autorisations

L’une des autorisations suivantes est requise pour appeler cette API. Pour en savoir plus, notamment sur le choix des autorisations, consultez [Utiliser Defender pour les API de point de terminaison](apis-intro.md).

Type d’autorisation|Autorisation|Nom d’affichage de l’autorisation
:---|:---|:---
Application|Machine.ReadWrite.All|« Lire et écrire toutes les informations sur l’ordinateur »
Déléguée (compte professionnel ou scolaire)|Machine.ReadWrite|« Lire et écrire des informations sur la machine »

> [!NOTE]
> Lors de l’obtention d’un jeton à l’aide des informations d’identification de l’utilisateur :
>
> - L’utilisateur doit disposer au moins de l’autorisation de rôle suivante : « Gérer le paramètre de sécurité ». Pour plus d’informations (voir [Créer et gérer des rôles](user-roles.md) ).
> - L’utilisateur doit avoir accès à l’ordinateur, en fonction des paramètres du groupe d’ordinateurs (voir [Créer et gérer des groupes d’ordinateurs](machine-groups.md) pour plus d’informations).

## <a name="http-request"></a>Requête HTTP

```http
POST https://api.securitycenter.microsoft.com/api/machines/{id}/tags
```

## <a name="request-headers"></a>En-têtes de demande

Nom|Type|Description
:---|:---|:---
Autorisation|Chaîne|Porteur {token}. **Obligatoire**.
Content-Type|string|application/json. **Obligatoire**.

## <a name="request-body"></a>Corps de la demande

Dans le corps de la demande, fournissez un objet JSON avec les paramètres suivants :

Paramètre|Type|Description
:---|:---|:---
Valeur|Chaîne|Nom de la balise. **Obligatoire**.
Action|Énum|Ajouter ou supprimer. Les valeurs autorisées sont : « Ajouter » ou « Supprimer ». **Obligatoire**.

## <a name="response"></a>Réponse

Si elle réussit, cette méthode renvoie le code de réponse 200 - OK et la machine mise à jour dans le corps de la réponse.

## <a name="example-request"></a>Exemple de requête

Voici un exemple de requête qui ajoute une balise d’ordinateur.

```http
POST https://api.securitycenter.microsoft.com/api/machines/1e5bc9d7e413ddd7902c2932e418702b84d0cc07/tags
```

```json
{
  "Value" : "test Tag 2",
  "Action": "Add"
}
```

Pour supprimer la balise d’ordinateur, définissez l’action sur « Supprimer » au lieu de « Ajouter » dans le corps de la requête.
