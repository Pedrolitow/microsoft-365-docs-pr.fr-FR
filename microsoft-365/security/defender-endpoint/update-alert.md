---
title: API d’entité d’alerte de mise à jour
description: Découvrez comment mettre à jour une alerte Microsoft Defender pour point de terminaison à l’aide de cette API. Vous pouvez mettre à jour l’état, la détermination, la classification et les propriétés assignedTo.
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
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 4bf668379edccff3e85fdeece6cfdcf7482ac8a5a9910cc5a8cf8629463db26c
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53884534"
---
# <a name="update-alert"></a>Mettre à jour une alerte

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>Description de l’API
Met à jour les propriétés de l’alerte [existante.](alerts.md)

L’envoi **de commentaire** est disponible avec ou sans mise à jour des propriétés.

Les propriétés qui peuvent être mis à jour `status` sont : , et `determination` `classification` `assignedTo` .

## <a name="limitations"></a>Limites

1. Vous pouvez mettre à jour les alertes disponibles dans l’API. Pour plus [d’informations, voir Alertes](get-alerts.md) de liste.
2. Les limites de taux pour cette API sont de 100 appels par minute et de 1 500 appels par heure.

## <a name="permissions"></a>Autorisations

L’une des autorisations suivantes est nécessaire pour appeler cette API. Pour en savoir plus, notamment sur le choix des autorisations, voir [Utiliser Microsoft Defender pour les API de point de terminaison](apis-intro.md)

Type d’autorisation|Autorisation|Nom d’affichage de l’autorisation
:---|:---|:---
Application|Alerts.ReadWrite.All|« Lire et écrire toutes les alertes »
Déléguée (compte professionnel ou scolaire)|Alert.ReadWrite|« Lire et écrire des alertes »

> [!NOTE]
> Lors de l’obtention d’un jeton à l’aide des informations d’identification de l’utilisateur :
>
> - L’utilisateur doit avoir au moins l’autorisation de rôle suivante : « Enquête sur les alertes » (voir Créer et gérer des rôles [pour](user-roles.md) plus d’informations)
> - L’utilisateur doit avoir accès à l’appareil associé à l’alerte, en fonction des paramètres de groupe d’appareils (pour plus d’informations, voir Créer et gérer des groupes d’appareils) [](machine-groups.md)

## <a name="http-request"></a>Requête HTTP

```http
PATCH /api/alerts/{id}
```

## <a name="request-headers"></a>En-têtes de demande

Nom|Type|Description
:---|:---|:---
Autorisation|Chaîne|Porteur {token}. **Obligatoire**.
Content-Type|String|application/json. **Obligatoire**.

## <a name="request-body"></a>Corps de la demande

Dans le corps de la demande, fournissons les valeurs des champs appropriés qui doivent être mis à jour.

Les propriétés existantes qui ne sont pas incluses dans le corps de la demande conserveront leurs valeurs précédentes ou seront recalculées en fonction des modifications apportées à d’autres valeurs des propriétés.

Pour de meilleures performances, n’incluez pas de valeurs existantes qui n’ont pas changé.

Propriété|Type|Description
:---|:---|:---
status|Chaîne|Spécifie l’état actuel de l’alerte. Les valeurs des propriétés sont : « New » (nouveau), « InProgress » (InProgress) et « Resolved » (résolu).
assignedTo|Chaîne|Propriétaire de l’alerte
classification|String|Spécifie la spécification de l’alerte. Les valeurs de propriété sont : « Unknown » (inconnu), « FalsePositive » (fauxpositif), « TruePositive » (vraipositif).
détermination|Chaîne|Spécifie la détermination de l’alerte. Les valeurs de propriété sont : 'NotAvailable', 'Apt', 'Malware', 'SecurityPersonnel', 'SecurityTesting', 'UnwantedSoftware', 'Other'
comment|String|Commentaire à ajouter à l’alerte.

## <a name="response"></a>Réponse

Si elle réussit, cette méthode renvoie 200 OK et l’entité d’alerte dans le corps de la réponse avec les propriétés mises à jour. [](alerts.md) Si l’alerte avec l’ID spécifié est in trouvée - 404 - In trouvé.

## <a name="example"></a>Exemple

### <a name="request"></a>Demande

Voici un exemple de demande.

```http
PATCH https://api.securitycenter.microsoft.com/api/alerts/121688558380765161_2136280442
```

```json
{
    "status": "Resolved",
    "assignedTo": "secop2@contoso.com",
    "classification": "FalsePositive",
    "determination": "Malware",
    "comment": "Resolve my alert and assign to secop2"
}
```
