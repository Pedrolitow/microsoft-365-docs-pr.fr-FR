---
title: Type de ressource Indicateur
description: Spécifiez les détails de l’entité et définissez l’expiration de l’indicateur à l’aide de Microsoft Defender pour endpoint.
keywords: api, api pris en charge, get, TiIndicator, Indicateur, récent
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
ms.openlocfilehash: 75b62f1bada67c30dc05237a284f8b64c3c7072d
ms.sourcegitcommit: 5d8de3e9ee5f52a3eb4206f690365bb108a3247b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2021
ms.locfileid: "52771380"
---
# <a name="indicator-resource-type"></a>Type de ressource Indicateur

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez découvrir Microsoft Defender pour le point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink) 


[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]


- Consultez la [page Indicateurs correspondante](https://securitycenter.windows.com/preferences2/custom_ti_indicators/files) dans le portail. 

Méthode|Type renvoyé |Description
:---|:---|:---
[Répertorier des indicateurs](get-ti-indicators-collection.md) | [Indicateur](ti-indicator.md) Collection | Entités [d’indicateur](ti-indicator.md) de liste.
[Envoyer des indicateurs](post-ti-indicator.md) | [Indicateur](ti-indicator.md) | Entité d’indicateur [d’soumission ou](ti-indicator.md) de mise à jour.
[Importer des indicateurs](import-ti-indicators.md) | [Indicateur](ti-indicator.md) Collection | Envoyer ou mettre à jour [des entités](ti-indicator.md) d’indicateurs.
[Supprimer des indicateurs](delete-ti-indicator-by-id.md) | Aucun contenu | Supprime [l’entité Indicateur.](ti-indicator.md)


## <a name="properties"></a>Propriétés
Propriété |  Type    |   Description
:---|:---|:---
id | String | Identité de [l’entité Indicateur.](ti-indicator.md)
indicatorValue | String | Valeur de [l’indicateur](ti-indicator.md).
indicatorType | Énum | Type de l’indicateur. Les valeurs possibles sont les suivantes : « FileSha1 », « FileSha256 », « IpAddress », « DomainName » et « Url ».
application | String | Application associée à l’indicateur. 
action | Énum | Action qui sera entreprise si l’indicateur est détecté dans l’organisation. Les valeurs possibles sont : « Alert », « AlertAndBlock » et « Allowed ».
sourceType | Énum | « Utilisateur » au cas où l’indicateur créé par un utilisateur (par exemple, à partir du portail), « AadApp » au cas où il a été envoyé à l’aide d’une application automatisée via l’API.
source | string | Nom de l’utilisateur/de l’application qui a soumis l’indicateur.
createdBy | String | Identité unique de l’utilisateur/de l’application qui a soumis l’indicateur.
lastUpdatedBy | String | Identité de l’utilisateur/de l’application qui a mis à jour l’indicateur pour la dernière fois.
creationTimeDateTimeUtc | DateTimeOffset | Date et heure de création de l’indicateur.
expirationTime | DateTimeOffset | Heure d’expiration de l’indicateur.
lastUpdateTime | DateTimeOffset | Dernière mise à jour de l’indicateur.
Sévérité  | Énum | Gravité de l’indicateur. les valeurs possibles sont : « Informational », « Low », « Medium » et « High ».
title | String | Titre de l’indicateur.
description | String | Description de l’indicateur.
recommendedActions | String | Actions recommandées pour l’indicateur.
rbacGroupNames | Liste des chaînes | Noms de groupes d’appareils RBAC où l’indicateur est exposé et actif. Liste vide au cas où elle serait exposée à tous les appareils.


## <a name="json-representation"></a>Représentation Json

```json
{
    "id": "994",
    "indicatorValue": "881c0f10c75e64ec39d257a131fcd531f47dd2cff2070ae94baa347d375126fd",
    "indicatorType": "FileSha256",
    "action": "AlertAndBlock",
    "application": null,
    "source": "user@contoso.onmicrosoft.com",
    "sourceType": "User",
    "createdBy": "user@contoso.onmicrosoft.com",
    "severity": "Informational",
    "title": "Michael test",
    "description": "test",
    "recommendedActions": "nothing",
    "creationTimeDateTimeUtc": "2019-12-19T09:09:46.9139216Z",
    "expirationTime": null,
    "lastUpdateTime": "2019-12-19T09:09:47.3358111Z",
    "lastUpdatedBy": null,
    "rbacGroupNames": ["team1"]
}
```
