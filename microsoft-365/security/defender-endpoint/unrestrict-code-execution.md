---
title: Supprimer l’API de restriction d’application
description: Utilisez cette API pour créer des appels liés à la suppression d’une restriction des applications de l’exécution.
keywords: api, API de graphe, api prises en charge, supprimer l’appareil de l’isolation
search.product: eADQiWindows 10XVcnh
ms.service: microsoft-365-security
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
ms.subservice: mde
ms.custom: api
search.appverid: met150
ms.openlocfilehash: d4f4b543af0d9953787f2346c0a4686208b779d7
ms.sourcegitcommit: 9b133379196da2b3a4bb311b07ff274f43780f68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2022
ms.locfileid: "67681470"
---
# <a name="remove-app-restriction-api"></a>Supprimer l’API de restriction d’application

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)


[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>Description de l’API

Activez l’exécution de n’importe quelle application sur l’appareil.

## <a name="limitations"></a>Limites

1. Les limites de débit pour cette API sont de 100 appels par minute et de 1 500 appels par heure.

[!include[Device actions note](../../includes/machineactionsnote.md)]

> [!IMPORTANT]
>
> - L’isolation complète est disponible pour les appareils sur Windows 10, version 1703.
> - L’isolation sélective est disponible pour les appareils sur Windows 10, version 1709 ou ultérieure.
> - Lors de l’isolation d’un appareil, seuls certains processus et destinations sont autorisés. Par conséquent, les appareils qui se trouvent derrière un tunnel VPN complet ne pourront pas atteindre le service cloud Microsoft Defender pour point de terminaison une fois l’appareil isolé. Nous vous recommandons d’utiliser un VPN de tunneling fractionné pour Microsoft Defender pour point de terminaison et le trafic lié à la protection cloud de l’Antivirus Microsoft Defender.

## <a name="permissions"></a>Autorisations

L’une des autorisations suivantes est requise pour appeler cette API. Pour en savoir plus, notamment sur le choix des autorisations, consultez [Utiliser Microsoft Defender pour point de terminaison API](apis-intro.md)

Type d’autorisation|Autorisation|Nom d’affichage de l’autorisation
:---|:---|:---
Application|Machine.RestrictExecution|'Restreindre l’exécution du code'
Déléguée (compte professionnel ou scolaire)|Machine.RestrictExecution|'Restreindre l’exécution du code'

> [!NOTE]
> Lors de l’obtention d’un jeton à l’aide des informations d’identification de l’utilisateur :
>
> - L’utilisateur doit disposer au moins de l’autorisation de rôle suivante : « Actions de correction actives » (voir [Créer et gérer des rôles](user-roles.md) pour plus d’informations)
> - L’utilisateur doit avoir accès à l’appareil, en fonction des paramètres du groupe d’appareils (voir [Créer et gérer des groupes d’appareils](machine-groups.md) pour plus d’informations)

## <a name="http-request"></a>Requête HTTP

```http
POST https://api.securitycenter.microsoft.com/api/machines/{id}/unrestrictCodeExecution
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
Commentaire|Chaîne|Commentaire à associer à l’action. **Obligatoire**.

## <a name="response"></a>Réponse

Si elle réussit, cette méthode renvoie le code de réponse 201 - Créé et [l’action de l’ordinateur](machineaction.md) dans le corps de la réponse.

Si vous envoyez plusieurs appels d’API pour supprimer les restrictions d’application pour le même appareil, elle retourne « Action de l’ordinateur en attente » ou HTTP 400 avec le message « L’action est déjà en cours ».

## <a name="example"></a>Exemple

### <a name="request"></a>Demande

Voici un exemple de demande.

```http
POST https://api.securitycenter.microsoft.com/api/machines/1e5bc9d7e413ddd7902c2932e418702b84d0cc07/unrestrictCodeExecution 
```

```json
{
  "Comment": "Unrestrict code execution since machine was cleaned and validated"
}

```

Pour restreindre l’exécution du code sur un appareil, consultez [Restreindre l’exécution de l’application](restrict-code-execution.md).
