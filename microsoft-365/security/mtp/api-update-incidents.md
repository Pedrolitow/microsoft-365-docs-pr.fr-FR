---
title: API de mise à jour des incidents
description: Découvrez comment mettre à jour les incidents à l’aide de l’API Microsoft 365 Defender
keywords: mise à jour, API, incident
search.product: eADQiWindows 10XVcnh
ms.prod: microsoft-365-enterprise
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.openlocfilehash: 6fc1ff730994f03aa500ad9a4559b66970e32d87
ms.sourcegitcommit: d6b1da2e12d55f69e4353289e90f5ae2f60066d0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/19/2020
ms.locfileid: "49719403"
---
# <a name="update-incidents-api"></a>API de mise à jour des incidents

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**

- Microsoft 365 Defender

> [!IMPORTANT]
> Certaines informations se rapportent à des produits précommercialisés susceptibles d’être modifiés de manière substantielle avant leur publication commerciale. Microsoft makes no warranties, express or implied, with respect to the information provided here.

## <a name="api-description"></a>Description de l’API

Met à jour les propriétés d’un incident existant. Les propriétés pouvant être mises à jour sont les suivantes : ```status``` , ```determination``` ,, ```classification``` ```assignedTo``` et ```tags``` .

### <a name="quotas-resource-allocation-and-other-constraints"></a>Quotas, allocation de ressources et autres contraintes

1. Vous pouvez effectuer jusqu’à 50 appels par minute ou 1500 appels par heure avant que vous atteigniez le seuil de limitation.
2. Vous pouvez définir la `determination` propriété uniquement si `classification` est défini sur TruePositive.

Si votre requête est limitée, elle renverra un code de `429` réponse. Le corps de la réponse indique le moment où vous pouvez commencer à passer des appels.

## <a name="permissions"></a>Autorisations

L’une des autorisations suivantes est nécessaire pour appeler cette API. Pour plus d’informations, notamment sur le choix des autorisations, consultez [la rubrique accéder aux API Microsoft 365 Defender](api-access.md).

Type d’autorisation | Autorisation | Nom d’affichage des autorisations
-|-|-
Application | Incident. ReadWrite. All | Lire et écrire tous les incidents
Déléguée (compte professionnel ou scolaire) | Incident. ReadWrite | Incidents de lecture et d’écriture

> [!NOTE]
> Lors de l’obtention d’un jeton à l’aide des informations d’identification de l’utilisateur, l’utilisateur doit avoir l’autorisation de mettre à jour l’incident dans le portail.

## <a name="http-request"></a>Requête HTTP

```HTTP
PATCH /api/incidents/{id}
```

## <a name="request-headers"></a>En-têtes de demande

Nom | Type | Description
-|-|-
Autorisation | String | Porteur {token}. **Obligatoire**.
Content-Type | String | application/json. **Obligatoire**.

## <a name="request-body"></a>Corps de la demande

Dans le corps de la demande, fournissez les valeurs des champs qui doivent être mis à jour. Les propriétés existantes qui ne sont pas incluses dans le corps de la demande conserveront leurs valeurs, sauf si elles doivent être recalculées en raison de modifications apportées aux valeurs associées. Pour de meilleures performances, vous devez omettre les valeurs existantes qui n’ont pas changé.

Propriété | Type | Description
-|-|-
statut | Énum | Spécifie l’état actuel de l’alerte. Les valeurs possibles sont les suivantes : ```Active``` , ```Resolved``` et ```Redirected``` .
assignedTo | string | Propriétaire de l’incident.
classification | Énum | Spécification de l’alerte. Les valeurs possibles sont ```Unknown```, ```FalsePositive``` et ```TruePositive```.
indications | Énum | Spécifie la détermination de l’alerte. Les valeurs possibles sont les suivantes : ```NotAvailable```, ```Apt```, ```Malware```, ```SecurityPersonnel```, ```SecurityTesting```, ```UnwantedSoftware``` et ```Other```.
étiquettes | Liste de chaînes | Liste des balises incident.

## <a name="response"></a>Réponse

Si elle réussit, cette méthode renvoie `200 OK` . Le corps de la réponse contiendra l’entité incidente dont les propriétés sont mises à jour. Si un incident avec l’ID spécifié est introuvable, la méthode renvoie `404 Not Found` .

## <a name="example"></a>Exemple

**Demande**

Voici un exemple de la demande.

```HTTP
 PATCH https://api.security.microsoft.com/api/incidents/{id}
```

**Réponse**

```json
{
    "status": "Resolved",
    "assignedTo": "secop2@contoso.com",
    "classification": "TruePositive",
    "determination": "Malware",
    "tags": ["Yossi's playground", "Don't mess with the Zohan"]
}
```

## <a name="related-articles"></a>Articles connexes

- [Accéder aux API Microsoft 365 Defender](api-access.md)
- [En savoir plus sur les limites d’API et la gestion des licences](api-terms.md)
- [Comprendre les codes d’erreur](api-error-codes.md)
- [API d’incident](api-incident.md)
- [Répertorier les incidents](api-list-incidents.md)
- [Vue d’ensemble des incidents](incidents-overview.md)
