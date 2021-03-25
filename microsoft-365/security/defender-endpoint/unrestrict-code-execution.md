---
title: SUPPRIMER l’API de restriction d’application
description: Utilisez cette API pour créer des appels liés à la suppression d’une restriction d’exécution d’applications.
keywords: api, api de graphique, api pris en charge, supprimer l’appareil de l’isolation
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
ms.technology: mde
ms.openlocfilehash: abff4e02bfdfe6f5598ca96121815930dce3c85e
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2021
ms.locfileid: "51199320"
---
# <a name="remove-app-restriction-api"></a>SUPPRIMER l’API de restriction d’application

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez découvrir Microsoft Defender pour le point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink) 


[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]


## <a name="api-description"></a>Description de l’API
Activez l’exécution de n’importe quelle application sur l’appareil.


## <a name="limitations"></a>Limites
1. Les limites de taux pour cette API sont de 100 appels par minute et de 1 500 appels par heure.


[!include[Device actions note](../../includes/machineactionsnote.md)]

## <a name="permissions"></a>Autorisations
L’une des autorisations suivantes est nécessaire pour appeler cette API. Pour en savoir plus, notamment sur le choix des autorisations, voir [Utiliser Microsoft Defender pour les API de point de terminaison](apis-intro.md)

Type d’autorisation |   Autorisation  |   Nom d’affichage de l’autorisation
:---|:---|:---
Application |   Machine.RestrictExecution | « Restreindre l’exécution du code »
Déléguée (compte professionnel ou scolaire) | Machine.RestrictExecution | « Restreindre l’exécution du code »

>[!Note]
> Lors de l’obtention d’un jeton à l’aide des informations d’identification de l’utilisateur :
>- L’utilisateur doit avoir au moins l’autorisation de rôle suivante : « Actions de correction actives » (voir Créer et gérer des rôles [pour](user-roles.md) plus d’informations)
>- L’utilisateur doit avoir accès à l’appareil, en fonction des paramètres de groupe d’appareils (voir Créer et gérer des groupes d’appareils [pour](machine-groups.md) plus d’informations)

## <a name="http-request"></a>Requête HTTP
```
POST https://api.securitycenter.microsoft.com/api/machines/{id}/unrestrictCodeExecution
```

## <a name="request-headers"></a>En-têtes de demande
Nom | Type | Description
:---|:---|:---
Autorisation | Chaîne | Porteur {token}. **Obligatoire**.
Content-Type | string | application/json. **Obligatoire**.

## <a name="request-body"></a>Corps de la demande
Dans le corps de la demande, fournissons un objet JSON avec les paramètres suivants :

Paramètre | Type    | Description
:---|:---|:---
Commentaire |   Chaîne | Commentaire à associer à l’action. **Obligatoire**.

## <a name="response"></a>Réponse
Si elle réussit, cette méthode renvoie 201 : code de réponse créé et action de [l’ordinateur](machineaction.md) dans le corps de la réponse.


## <a name="example"></a>Exemple

**Demande**

Voici un exemple de demande.

```http
POST https://api.securitycenter.microsoft.com/api/machines/1e5bc9d7e413ddd7902c2932e418702b84d0cc07/unrestrictCodeExecution 
```

```json
{
  "Comment": "Unrestrict code execution since machine was cleaned and validated"
}

```


Pour restreindre l’exécution du code sur un appareil, voir [Restreindre l’exécution de l’application.](restrict-code-execution.md)
