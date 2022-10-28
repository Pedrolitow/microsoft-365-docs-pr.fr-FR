---
title: API de machine hors-bord
description: Découvrez comment utiliser une API pour retirer un appareil d’Microsoft Defender pour point de terminaison.
keywords: api, api graph, api prises en charge, package d’investigation de collecte
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
ms.openlocfilehash: 03b7c2b9af508740475ef6859788fec7ed91b866
ms.sourcegitcommit: a20d30f4e5027f90d8ea4cde95d1d5bacfdd2b5e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2022
ms.locfileid: "68770024"
---
# <a name="offboard-machine-api"></a>API de machine hors-bord

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>Description de l’API

Désintégez l’appareil de Defender pour point de terminaison.

## <a name="limitations"></a>Limites

- Les limitations de débit pour cette API sont de 100 appels par minute et de 1 500 appels par heure.

  [!include[Machine actions note](../../includes/machineactionsnote.md)]

> [!NOTE]
> Cette API est prise en charge sur Windows 11, Windows 10, version 1703 et ultérieure, sur Windows Server 2019 et versions ultérieures, et sur Windows Server 2012 R2 et Windows Server 2016 lors de l’utilisation du [nouvel agent unifié pour Defender pour point de terminaison](update-agent-mma-windows.md#upgrade-to-the-new-unified-agent-for-defender-for-endpoint).
> Cette API n’est pas prise en charge sur les appareils macOS ou Linux.

## <a name="permissions"></a>Autorisations

L’une des autorisations suivantes est requise pour appeler cette API. Pour en savoir plus, notamment sur le choix des autorisations, consultez [Utiliser les API Defender pour point de terminaison](apis-intro.md).

Type d’autorisation|Autorisation|Nom complet de l’autorisation
---|---|---
Application|Machine.Offboard|'Offboard machine'
Déléguée (compte professionnel ou scolaire)|Machine.Offboard|'Offboard machine'

> [!NOTE]
> Lors de l’obtention d’un jeton à l’aide des informations d’identification de l’utilisateur :
>
> - L’utilisateur doit disposer du rôle AD « Global Administration »
> - L’utilisateur doit avoir accès à l’appareil, en fonction des paramètres du groupe d’appareils (voir [Créer et gérer des groupes](machine-groups.md) d’appareils pour plus d’informations)
>
> La création de groupes d’appareils est prise en charge dans Defender pour point de terminaison Plan 1 et Plan 2.  

## <a name="http-request"></a>Requête HTTP

```http
POST https://api.securitycenter.microsoft.com/api/machines/{id}/offboard
```

L’ID de machine se trouve dans l’URL lorsque vous sélectionnez l’appareil. En règle générale, il s’agit d’un nombre alphanumérique à 40 chiffres qui se trouve dans l’URL.

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

Si elle réussit, cette méthode renvoie le code de réponse 200 - Créé et [l’action de l’ordinateur](machineaction.md) dans le corps de la réponse.

## <a name="example"></a>Exemple

### <a name="request"></a>Demande

Voici un exemple de demande. Si aucun commentaire JSON n’est ajouté, le code **400** génère une erreur.

```http
POST https://api.securitycenter.microsoft.com/api/machines/1e5bc9d7e413ddd7902c2932e418702b84d0cc07/offboard
```

```json
{
  "Comment": "Offboard machine by automation"
}
```
