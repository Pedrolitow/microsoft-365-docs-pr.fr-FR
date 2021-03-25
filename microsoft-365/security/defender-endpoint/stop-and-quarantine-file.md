---
title: API de fichier d’arrêt et de mise en quarantaine
description: Découvrez comment arrêter l’exécution d’un fichier sur un appareil et supprimer le fichier dans Microsoft Defender pour le point de terminaison. Consultez un exemple.
keywords: api, api de graphique, api pris en charge, arrêter et mettre en quarantaine le fichier
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
ms.openlocfilehash: 670282f0f87092437bb1f3c6bf7be908e4649042
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2021
ms.locfileid: "51199728"
---
# <a name="stop-and-quarantine-file-api"></a>API de fichier d’arrêt et de mise en quarantaine

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :** [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/?linkid=2154037)

- Vous souhaitez découvrir Microsoft Defender pour le point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink) 

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]


## <a name="api-description"></a>Description de l’API
Arrêtez l’exécution d’un fichier sur un appareil et supprimez-le.


## <a name="limitations"></a>Limites
1. Les limites de taux pour cette API sont de 100 appels par minute et de 1 500 appels par heure.


[!include[Device actions note](../../includes/machineactionsnote.md)]

## <a name="permissions"></a>Autorisations
L’une des autorisations suivantes est nécessaire pour appeler cette API. Pour en savoir plus, notamment sur le choix des autorisations, voir [Utiliser Microsoft Defender pour les API de point de terminaison](apis-intro.md)

Type d’autorisation |   Autorisation  |   Nom d’affichage de l’autorisation
:---|:---|:---
Application |   Machine.StopAndQuarantine | « Arrêter et mettre en quarantaine »
Déléguée (compte professionnel ou scolaire) | Machine.StopAndQuarantine | « Arrêter et mettre en quarantaine »

>[!Note]
> Lors de l’obtention d’un jeton à l’aide des informations d’identification de l’utilisateur :
>- L’utilisateur doit avoir au moins l’autorisation de rôle suivante : « Actions de correction actives » (pour plus d’informations, voir Créer et gérer [des](user-roles.md) rôles)
>- L’utilisateur doit avoir accès à l’appareil, en fonction des paramètres de groupe d’appareils (voir Créer et gérer des groupes d’appareils [pour](machine-groups.md) plus d’informations)

## <a name="http-request"></a>Requête HTTP
```
POST https://api.securitycenter.microsoft.com/api/machines/{id}/StopAndQuarantineFile
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
Commentaire |   Chaîne |    Commentaire à associer à l’action. **Obligatoire**.
Sha1 |  Chaîne   | Sha1 du fichier à arrêter et mettre en quarantaine sur l’appareil. **Obligatoire**.

## <a name="response"></a>Réponse
Si elle réussit, cette méthode renvoie 201 - Code de réponse créé et Action de [l’ordinateur](machineaction.md) dans le corps de la réponse.


## <a name="example"></a>Exemple

**Demande**

Voici un exemple de demande.

```http
POST https://api.securitycenter.microsoft.com/api/machines/1e5bc9d7e413ddd7902c2932e418702b84d0cc07/StopAndQuarantineFile 
```

```json
{
  "Comment": "Stop and quarantine file on machine due to alert 441688558380765161_2136280442",
  "Sha1": "87662bc3d60e4200ceaf7aae249d1c343f4b83c9"
}

```
