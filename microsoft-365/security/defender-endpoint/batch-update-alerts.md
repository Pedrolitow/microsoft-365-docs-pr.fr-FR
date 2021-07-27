---
title: API des entités d’alerte de mise à jour par lot
description: Découvrez comment mettre à jour les alertes Microsoft Defender pour les points de terminaison dans un lot à l’aide de cette API. Vous pouvez mettre à jour l’état, la détermination, la classification et les propriétés assignedTo.
keywords: api, api de graphique, api pris en charge, obtenir, alerte, informations, ID
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
ms.openlocfilehash: 281149429329f23efd828227e3773060106f2d34
ms.sourcegitcommit: af575ade7b187af70f94db904b03f0471f56452a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/26/2021
ms.locfileid: "53590790"
---
# <a name="batch-update-alerts"></a>Alertes de mise à jour par lot

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :** [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2154037)

- Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]


## <a name="api-description"></a>Description de l’API

Met à jour les propriétés d’un lot d’alertes [existantes.](alerts.md)

L’envoi **de commentaire** est disponible avec ou sans mise à jour des propriétés.

Les propriétés qui peuvent être mis à jour `status` sont : , et `determination` `classification` `assignedTo` .

## <a name="limitations"></a>Limites

1. Vous pouvez mettre à jour les alertes disponibles dans l’API. Pour plus [d’informations, voir Alertes](get-alerts.md) de liste.
2. Les limites de taux pour cette API sont de 10 appels par minute et de 500 appels par heure.

## <a name="permissions"></a>Autorisations

L’une des autorisations suivantes est nécessaire pour appeler cette API. Pour en savoir plus, notamment sur le choix des autorisations, voir [Utiliser Microsoft Defender pour les API de point de terminaison](apis-intro.md)

Type d’autorisation | Autorisation | Nom d’affichage de l’autorisation
:---|:---|:---
Application | Alerts.ReadWrite.All | « Lire et écrire toutes les alertes »
Déléguée (compte professionnel ou scolaire) | Alert.ReadWrite | « Lire et écrire des alertes »

> [!NOTE]
> Lors de l’obtention d’un jeton à l’aide des informations d’identification de l’utilisateur :
>
> - L’utilisateur doit avoir au moins l’autorisation de rôle suivante : « Enquête sur les alertes » (voir Créer et gérer des rôles [pour](user-roles.md) plus d’informations)
> - L’utilisateur doit avoir accès à l’appareil associé à l’alerte, en fonction des paramètres de groupe d’appareils (pour plus d’informations, voir Créer et gérer des groupes d’appareils) [](machine-groups.md)

## <a name="http-request"></a>Requête HTTP

```http
POST /api/alerts/batchUpdate
```

## <a name="request-headers"></a>En-têtes de demande

Nom|Type|Description
:---|:---|:---
Autorisation | String | Porteur {token}. **Obligatoire**.
Content-Type | String | application/json. **Obligatoire**.

## <a name="request-body"></a>Corps de la demande

Dans le corps de la demande, fournissez les ID des alertes à mettre à jour et les valeurs des champs pertinents que vous souhaitez mettre à jour pour ces alertes.

Les propriétés existantes qui ne sont pas incluses dans le corps de la demande conserveront leurs valeurs précédentes ou seront recalculées en fonction des modifications apportées à d’autres valeurs des propriétés.

Pour de meilleures performances, n’incluez pas de valeurs existantes qui n’ont pas changé.

Propriété | Type | Description
:---|:---|:---
alertIds | Chaîne de &lt; liste&gt;| Liste des ID des alertes à mettre à jour. **Obligatoire**
status | String | Spécifie l’état mis à jour des alertes spécifiées. Les valeurs des propriétés sont : « New » (nouveau), « InProgress » (InProgress) et « Resolved » (résolu).
assignedTo | String | Propriétaire des alertes spécifiées
classification | String | Spécifie la spécification des alertes spécifiées. Les valeurs de propriété sont : « Unknown » (inconnu), « FalsePositive » (fauxpositif), « TruePositive » (vraipositif). 
détermination | String | Spécifie la détermination des alertes spécifiées. Les valeurs de propriété sont : 'NotAvailable', 'Apt', 'Malware', 'SecurityPersonnel', 'SecurityTesting', 'UnwantedSoftware', 'Other'
comment | String | Commentaire à ajouter aux alertes spécifiées.

## <a name="response"></a>Réponse

Si elle réussit, cette méthode renvoie 200 OK, avec un corps de réponse vide.

## <a name="example"></a>Exemple

### <a name="request"></a>Demande

Voici un exemple de demande.

```http
POST https://api.securitycenter.microsoft.com/api/alerts/batchUpdate
```

```json
{
    "alertIds": ["da637399794050273582_760707377", "da637399989469816469_51697947354"],
    "status": "Resolved",
    "assignedTo": "secop2@contoso.com",
    "classification": "FalsePositive",
    "determination": "Malware",
    "comment": "Resolve my alert and assign to secop2"
}
```
