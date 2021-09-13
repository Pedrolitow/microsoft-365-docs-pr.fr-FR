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
ms.openlocfilehash: 3dc075caccc5724ed3ea76e5d3c06f3a5b6f7f2e
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59164897"
---
# <a name="indicator-resource-type"></a>Type de ressource Indicateur

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

- Consultez la [page Indicateurs correspondante](https://securitycenter.windows.com/preferences2/custom_ti_indicators/files) dans le portail.

Méthode|Type renvoyé|Description
:---|:---|:---
[Répertorier des indicateurs](get-ti-indicators-collection.md)|[Indicateur](ti-indicator.md) Collection|Entités [d’indicateur](ti-indicator.md) de liste.
[Envoyer des indicateurs](post-ti-indicator.md)|[Indicateur](ti-indicator.md)|Entité d’indicateur [d’soumission ou](ti-indicator.md) de mise à jour.
[Importer des indicateurs](import-ti-indicators.md)|[Indicateur](ti-indicator.md) Collection|Envoyer ou mettre à jour [des entités](ti-indicator.md) d’indicateurs.
[Supprimer des indicateurs](delete-ti-indicator-by-id.md)|Aucun contenu|Supprime [l’entité Indicateur.](ti-indicator.md)

## <a name="properties"></a>Propriétés

Propriété|Type|Description
:---|:---|:---
id|Chaîne|Identité de [l’entité Indicateur.](ti-indicator.md)
indicatorValue|Chaîne|Valeur de [l’indicateur](ti-indicator.md).
indicatorType|Énum|Type de l’indicateur. Les valeurs possibles sont les suivantes : « FileSha1 », « FileSha256 », « FileMd5 », « CertificateThumbprint », « IpAddress », « DomainName » et « Url ».
application|Chaîne|Application associée à l’indicateur.
action|Énum|Action qui sera entreprise si l’indicateur est détecté dans l’organisation. Les valeurs possibles sont : « Warn », « Block », « Audit », « Alert », « AlertAndBlock », « BlockAndRemediate » et « Allowed ».
|externalID|Chaîne|ID que le client peut envoyer dans la demande de corrélation personnalisée.|
sourceType|Énum|« Utilisateur » au cas où l’indicateur créé par un utilisateur (par exemple, à partir du portail), « AadApp » au cas où il a été envoyé à l’aide d’une application automatisée via l’API.
createdBySource|chaîne|Nom de l’utilisateur/de l’application qui a soumis l’indicateur.
createdBy|String|Identité unique de l’utilisateur/de l’application qui a soumis l’indicateur.
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
## <a name="public-preview-indicator-types"></a>Prévisualisation publique : types d’indicateurs

> [!IMPORTANT]
> Les informations de cette section **(prévisualisation publique** pour le moteur automatisé d’investigation et de correction) concernent les produits pré-publiés qui peuvent être considérablement modifiés avant leur commercialisation. Microsoft n’offre aucune garantie, explicite ou implicite, concernant les informations fournies ici.

Les types d’action d’indicateur pris en charge par l’API sont :

- Autorisé
- Alerte
- AlertAndBlock
- Audit
- Bloquer
- BlockAndRemediate
- Avertir

La liste API des types d’actions contient les nouvelles actions de réponse, ainsi que les actions de réponse précédentes (AlertAndBlock et Alert). Pour plus d’informations sur la description des types d’action de réponse, voir [Créer des indicateurs.](manage-indicators.md)

Les actions de réponse IoC Autorisées, Avertir, Bloquer et BlockAndRemediate sont en prévisualisation publique. Pour plus d’informations sur la prévisualisation publique, voir Prévisualisation publique : Améliorations apportées aux [fichiers personnalisés IoC](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/public-preview-custom-file-ioc-enhancements-and-api-schema/ba-p/2676997)et mise à jour du schéma d’API - Microsoft Tech Community .




> [!Note]
>
> Les actions de réponse précédentes (AlertAndBlock et Alert) sont supprimées lorsque la fonctionnalité a atteint GAed. La date de grâce estimée avec période de grâce est la fin d’octobre 2021.  Nous vous conseillons de mettre à jour les modèles ou les scripts existants dès que possible.

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
