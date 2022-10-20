---
title: Type de ressource d’indicateur
description: Spécifiez les détails de l’entité et définissez l’expiration de l’indicateur à l’aide de Microsoft Defender pour point de terminaison.
keywords: api, api prises en charge, get, TiIndicator, Indicator, recent
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
- tier2
ms.topic: conceptual
ms.subservice: mde
ms.custom: api
search.appverid: met150
ms.openlocfilehash: 0cc1df14f60088efe72a48bea5a755ea375cd7e7
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68635118"
---
# <a name="indicator-resource-type"></a>Type de ressource d’indicateur

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

- Consultez la [page Indicateurs](https://securitycenter.windows.com/preferences2/custom_ti_indicators/files) correspondante dans le portail.

Méthode|Type renvoyé|Description
:---|:---|:---
[Répertorier des indicateurs](get-ti-indicators-collection.md)|[Indicateur](ti-indicator.md) Collection|[Répertorier les entités d’indicateur](ti-indicator.md).
[Envoyer des indicateurs](post-ti-indicator.md)|[Indicateur](ti-indicator.md)|Soumettre ou mettre à jour l’entité [Indicateur](ti-indicator.md) .
[Importer des indicateurs](import-ti-indicators.md)|[Indicateur](ti-indicator.md) Collection|Soumettre ou mettre à jour [des entités Indicators](ti-indicator.md) .
[Supprimer des indicateurs](delete-ti-indicator-by-id.md)|Aucun contenu|Supprime l’entité [Indicateur](ti-indicator.md) .

## <a name="properties"></a>Propriétés

Propriété|Type|Description
:---|:---|:---
id|Chaîne|Identité de l’entité [Indicateur](ti-indicator.md) .
indicatorValue|Chaîne|Valeur de [l’indicateur](ti-indicator.md).
indicatorType|Énum|Type de l’indicateur. Les valeurs possibles sont : « FileSha1 », « FileSha256 », « FileMd5 », « CertificateThumbprint », « IpAddress », « DomainName » et « Url ».
application|Chaîne|Application associée à l’indicateur.
action|Énum|Action qui sera effectuée si l’indicateur est détecté dans l’organisation. Les valeurs possibles sont : « Warn », « Block », « Audit », « Alert », « AlertAndBlock », « BlockAndRemediate » et « Allowed ».
|externalID|Chaîne|ID que le client peut envoyer dans la demande de corrélation personnalisée.|
Sourcetype|Énum|« Utilisateur » dans le cas où l’indicateur créé par un utilisateur (par exemple, à partir du portail), « AadApp » au cas où il serait soumis à l’aide d’une application automatisée via l’API.
createdBySource|chaîne|Nom de l’utilisateur/de l’application qui a envoyé l’indicateur.
createdBy|String|Identité unique de l’utilisateur/de l’application qui a envoyé l’indicateur.
lastUpdatedBy|Chaîne|Identité de l’utilisateur/de l’application qui a mis à jour l’indicateur pour la dernière fois.
creationTimeDateTimeUtc|DateTimeOffset|Date et heure de création de l’indicateur.
expirationTime|DateTimeOffset|Heure d’expiration de l’indicateur.
lastUpdateTime|DateTimeOffset|Dernière mise à jour de l’indicateur.
Sévérité |Énum|Gravité de l’indicateur. les valeurs possibles sont : « Informational », « Low », « Medium » et « High ».
title|Chaîne|Titre de l’indicateur.
description|Chaîne|Description de l’indicateur.
recommendedActions|Chaîne|Actions recommandées pour l’indicateur.
rbacGroupNames|Liste des chaînes|Noms de groupes d’appareils RBAC où l’indicateur est exposé et actif. Liste vide au cas où elle serait exposée à tous les appareils.
rbacGroupIds|Liste des chaînes|ID de groupe d’appareils RBAC où l’indicateur est exposé et actif. Liste vide au cas où elle serait exposée à tous les appareils.
generateAlert|Énum|**True** si la génération d’alerte est requise, **False** si cet indicateur ne doit pas générer d’alerte.

## <a name="indicator-types"></a>Types d’indicateurs

Les types d’actions d’indicateur pris en charge par l’API sont les suivants :

- Autorisé
- Audit
- Bloquer
- BlockAndRemediate
- Avertir (Defender pour Cloud Apps uniquement)

Pour plus d’informations sur la description des types d’actions de réponse, consultez [Créer des indicateurs](manage-indicators.md).

> [!Note]
>
> Les actions de réponse précédentes (AlertAndBlock et Alert) seront prises en charge jusqu’en janvier 2022. Après cette date, tous les clients doivent utiliser l’un des types d’actions répertoriés ci-dessus.

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
