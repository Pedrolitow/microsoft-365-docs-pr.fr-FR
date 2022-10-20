---
title: Isoler l’API de l’ordinateur
description: Découvrez comment utiliser l’API Isolate Machine pour isoler un appareil de l’accès au réseau externe dans Microsoft Defender pour point de terminaison.
keywords: api, API de graphe, api prises en charge, isoler l’appareil
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
ms.openlocfilehash: 96a03ae7664a1332ce29a1ead574c5caba18b524
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68631587"
---
# <a name="isolate-machine-api"></a>Isoler l’API de l’ordinateur

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>Description de l’API

Isole un appareil de l’accès au réseau externe.

## <a name="limitations"></a>Limites

1. Les limites de débit pour cette API sont de 100 appels par minute et de 1 500 appels par heure.

[!include[Device actions note](../../includes/machineactionsnote.md)]

> [!IMPORTANT]
>
> - L’isolation complète est disponible pour les appareils sur Windows 10, version 1703 et sur Windows 11.
> - L’isolation sélective est disponible pour les appareils sur Windows 10, version 1709 ou ultérieure, et sur Windows 11.
> - Lors de l’isolation d’un appareil, seuls certains processus et destinations sont autorisés. Par conséquent, les appareils qui se trouvent derrière un tunnel VPN complet ne pourront pas atteindre le service cloud Microsoft Defender pour point de terminaison une fois l’appareil isolé. Nous vous recommandons d’utiliser un VPN de tunneling fractionné pour Microsoft Defender pour point de terminaison et Microsoft Defender trafic lié à la protection basée sur le cloud antivirus.

## <a name="permissions"></a>Autorisations

L’une des autorisations suivantes est requise pour appeler cette API. Pour en savoir plus, notamment sur le choix des autorisations, consultez [Utiliser Microsoft Defender pour point de terminaison API](apis-intro.md)

Type d’autorisation|Autorisation|Nom d’affichage de l’autorisation
:---|:---|:---
Application|Machine.Isolate|'Isoler la machine'
Déléguée (compte professionnel ou scolaire)|Machine.Isolate|'Isoler la machine'

> [!NOTE]
> Lors de l’obtention d’un jeton à l’aide des informations d’identification de l’utilisateur :
>
> - L’utilisateur doit disposer au moins de l’autorisation de rôle suivante : « Actions de correction actives » (voir [Créer et gérer des rôles](user-roles.md) pour plus d’informations)
> - L’utilisateur doit avoir accès à l’appareil, en fonction des paramètres du groupe d’appareils (voir [Créer et gérer des groupes d’appareils](machine-groups.md) pour plus d’informations)
>
> La création de groupes d’appareils est prise en charge dans Defender pour point de terminaison Plan 1 et Plan 2. 

## <a name="http-request"></a>Requête HTTP

```http
POST https://api.securitycenter.microsoft.com/api/machines/{id}/isolate
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
IsolationType|Chaîne|Type de l’isolation. Les valeurs autorisées sont : « Full » ou « Selective ».

**IsolationType** contrôle le type d’isolation à effectuer et peut être l’un des éléments suivants :

- Complet : isolation complète
- Sélectif : empêcher uniquement un ensemble limité d’applications d’accéder au réseau (voir [Isoler les appareils du réseau](respond-machine-alerts.md#isolate-devices-from-the-network) pour plus d’informations)

## <a name="response"></a>Réponse

Si elle réussit, cette méthode renvoie le code de réponse 201 - Créé et [l’action de l’ordinateur](machineaction.md) dans le corps de la réponse.

## <a name="example"></a>Exemple

### <a name="request"></a>Demande

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

- Pour libérer un appareil de l’isolation, consultez [Libérer l’appareil de l’isolation](unisolate-machine.md).
