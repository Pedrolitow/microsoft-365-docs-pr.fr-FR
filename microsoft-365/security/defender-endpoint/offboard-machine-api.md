---
title: API de l’ordinateur hors carte
description: Découvrez comment utiliser une API pour déconnecter un appareil de Microsoft Defender pour point de terminaison.
keywords: api, api graphe, api prises en charge, collecter le package d’investigation
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
ms.openlocfilehash: d29e0d30c3672ce3a6987059b2d1ddf9a4e07919
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68631895"
---
# <a name="offboard-machine-api"></a>API de l’ordinateur hors carte

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>Description de l’API

Appareil hors-bord de Defender pour point de terminaison.

## <a name="limitations"></a>Limites

- Les limites de débit pour cette API sont de 100 appels par minute et de 1 500 appels par heure.

  [!include[Machine actions note](../../includes/machineactionsnote.md)]

> [!NOTE]
> Cette API est prise en charge sur Windows 11, Windows 10, version 1703 et ultérieure, ou Windows Server 2019 et versions ultérieures.
>
> Cette API n’est pas prise en charge sur les appareils MacOS ou Linux.

## <a name="permissions"></a>Autorisations

L’une des autorisations suivantes est requise pour appeler cette API. Pour en savoir plus, notamment sur le choix des autorisations, consultez [Utiliser Defender pour les API de point de terminaison](apis-intro.md)

Type d’autorisation|Autorisation|Nom d’affichage de l’autorisation
---|---|---
Application|Machine.Offboard|'Machine hors-bord'
Déléguée (compte professionnel ou scolaire)|Machine.Offboard|'Machine hors-bord'

> [!NOTE]
> Lors de l’obtention d’un jeton à l’aide des informations d’identification de l’utilisateur :
>
> - L’utilisateur a besoin du rôle AD « Global Administration »
> - L’utilisateur doit avoir accès à l’appareil, en fonction des paramètres du groupe d’appareils (voir [Créer et gérer des groupes d’appareils](machine-groups.md) pour plus d’informations)
>
> La création de groupes d’appareils est prise en charge dans Defender pour point de terminaison Plan 1 et Plan 2.  

## <a name="http-request"></a>Requête HTTP

```http
POST https://api.securitycenter.microsoft.com/api/machines/{id}/offboard
```

L’ID de l’ordinateur se trouve dans l’URL lorsque vous sélectionnez l’appareil. En règle générale, il s’agit d’un nombre alphanumérique à 40 chiffres qui se trouve dans l’URL.

## <a name="request-headers"></a>En-têtes de demande

Nom|Type|Description
---|---|---
Autorisation|Chaîne|Porteur {token}. **Obligatoire**.
Content-Type|string|application/json. **Obligatoire**.

## <a name="request-body"></a>Corps de la demande

Dans le corps de la demande, fournissez un objet JSON avec les paramètres suivants :

Paramètre|Type|Description
---|---|---
Commentaire|Chaîne|Commentaire à associer à l’action. **Obligatoire**.

## <a name="response"></a>Réponse

Si elle réussit, cette méthode renvoie le code de réponse 200 - Créé et [l’action de la machine](machineaction.md) dans le corps de la réponse.

## <a name="example"></a>Exemple

### <a name="request"></a>Demande

Voici un exemple de demande. Si aucun commentaire JSON n’est ajouté, il s’affiche avec le code **400**.

```http
POST https://api.securitycenter.microsoft.com/api/machines/1e5bc9d7e413ddd7902c2932e418702b84d0cc07/offboard
```

```json
{
  "Comment": "Offboard machine by automation"
}
```
