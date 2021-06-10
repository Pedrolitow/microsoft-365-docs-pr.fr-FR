---
title: API Isoler l’ordinateur
description: Découvrez comment utiliser l’API Isoler l’ordinateur pour isoler un appareil de l’accès au réseau externe dans Microsoft Defender pour point de terminaison.
keywords: api, api de graphique, api pris en charge, isoler l’appareil
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 9f3313a08b072f4fb2f699148ab801207e56fc09
ms.sourcegitcommit: 5d8de3e9ee5f52a3eb4206f690365bb108a3247b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2021
ms.locfileid: "52772112"
---
# <a name="isolate-machine-api"></a>API Isoler l’ordinateur

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Vous souhaitez faire l’expérience de Defender pour point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink) 

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]


## <a name="api-description"></a>Description de l’API
Isole un appareil de l’accès au réseau externe.


## <a name="limitations"></a>Limites
1. Les limites de taux pour cette API sont de 100 appels par minute et de 1 500 appels par heure.


[!include[Device actions note](../../includes/machineactionsnote.md)]

## <a name="permissions"></a>Autorisations
L’une des autorisations suivantes est nécessaire pour appeler cette API. Pour en savoir plus, notamment sur le choix des autorisations, voir [Utiliser Microsoft Defender pour les API de point de terminaison](apis-intro.md)

Type d’autorisation |   Autorisation  |   Nom d’affichage de l’autorisation
:---|:---|:---
Application |   Machine.Isolate |   « Isoler l’ordinateur »
Déléguée (compte professionnel ou scolaire) | Machine.Isolate |  « Isoler l’ordinateur »

>[!Note]
> Lors de l’obtention d’un jeton à l’aide des informations d’identification de l’utilisateur :
>- L’utilisateur doit avoir au moins l’autorisation de rôle suivante : « Actions de correction actives » (pour plus d’informations, voir Créer et gérer [des](user-roles.md) rôles)
>- L’utilisateur doit avoir accès à l’appareil, en fonction des paramètres de groupe d’appareils (voir Créer et gérer des groupes d’appareils [pour](machine-groups.md) plus d’informations)


## <a name="http-request"></a>Requête HTTP
```
POST https://api.securitycenter.microsoft.com/api/machines/{id}/isolate
```

## <a name="request-headers"></a>En-têtes de demande

Nom | Type | Description
:---|:---|:---
Autorisation | String | Porteur {token}. **Obligatoire**.
Content-Type | string | application/json. **Obligatoire**.

## <a name="request-body"></a>Corps de la demande
Dans le corps de la demande, fournissons un objet JSON avec les paramètres suivants :

Paramètre | Type    | Description
:---|:---|:---
Commentaire |   Chaîne |    Commentaire à associer à l’action. **Obligatoire**.
IsolationType   | String |  Type de l’isolation. Les valeurs autorisées sont : « Full » ou « Selective ».

**IsolationType** contrôle le type d’isolation à effectuer et peut être l’une des suivantes :
- Complète – Isolation complète
- Sélectif : empêcher uniquement un ensemble limité d’applications d’accéder au réseau (voir [Isoler](respond-machine-alerts.md#isolate-devices-from-the-network) les appareils du réseau pour plus d’informations)


## <a name="response"></a>Réponse
Si elle réussit, cette méthode renvoie 201 - Code de réponse créé et Action de [l’ordinateur](machineaction.md) dans le corps de la réponse.


## <a name="example"></a>Exemple

**Demande**

Voici un exemple de demande.

```http
POST https://api.securitycenter.microsoft.com/api/machines/1e5bc9d7e413ddd7902c2932e418702b84d0cc07/isolate
```

```json
{
  "Comment": "Isolate machine due to alert 1234",
  "IsolationType": "Full" 
}
```

- Pour libérer un appareil de l’isolation, voir [Libérer l’appareil de l’isolation.](unisolate-machine.md)
