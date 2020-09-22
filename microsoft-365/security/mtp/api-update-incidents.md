---
title: API de mise à jour des incidents
description: Découvrez comment mettre à jour les incidents à l’aide de l’API Microsoft Threat Protection
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
ms.openlocfilehash: 8ad47453c7163bfac99c17f42986b818cdca603f
ms.sourcegitcommit: c083602dda3cdcb5b58cb8aa070d77019075f765
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "48203627"
---
# <a name="update-incidents-api"></a>API de mise à jour des incidents

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Protection Microsoft contre les menaces

>[!IMPORTANT] 
>Certaines informations se rapportent à des produits précommercialisés susceptibles d’être modifiés de manière substantielle avant leur publication commerciale. Microsoft makes no warranties, express or implied, with respect to the information provided here.


## <a name="api-description"></a>Description de l’API
Met à jour les propriétés d’un incident existant.
<br>Les propriétés pouvant être mises à jour sont les suivantes : ```status``` , ```determination``` , ```classification``` ```assignedTo``` et ```tags``` .


## <a name="limitations"></a>Limites
1. Les limites de taux pour cette API sont 50 appels par minute et 1500 appels par heure.
2. Vous ne pouvez définir la valeur ```determination``` que si la classification est définie sur TruePositive.


## <a name="permissions"></a>Autorisations
L’une des autorisations suivantes est nécessaire pour appeler cette API. Pour plus d’informations, notamment sur la façon de choisir des autorisations, voir [accéder aux API de protection contre les menaces Microsoft](api-access.md).

Type d’autorisation |   Autorisation  |   Nom d’affichage des autorisations
:---|:---|:---
Application |   Incident. ReadWrite. All |    « Lire et écrire tous les incidents »
Déléguée (compte professionnel ou scolaire) | Incident. ReadWrite | « Incidents en lecture et en écriture »

>[!NOTE]
> Lors de l’obtention d’un jeton à l’aide des informations d’identification de l’utilisateur :
>- L’utilisateur doit avoir l’autorisation de mettre à jour l’incident dans le portail.


## <a name="http-request"></a>Requête HTTP

```
PATCH /api/incidents/{id}
```

## <a name="request-headers"></a>En-têtes de demande

Nom | Type | Description
:---|:---|:---
Autorisation | String | Porteur {token}. **Obligatoire**.
Content-Type | String | application/json. **Obligatoire**.


## <a name="request-body"></a>Corps de la demande
Dans le corps de la demande, fournissez les valeurs des champs pertinents qui doivent être mis à jour.
<br>Les propriétés existantes qui ne sont pas incluses dans le corps de la demande conserveront leurs valeurs précédentes ou seront recalculées en fonction des modifications apportées à d’autres valeurs des propriétés. 
<br>Pour des performances optimales, vous ne devez pas inclure de valeurs existantes qui n’ont pas changé.

Propriété | Type | Description
:---|:---|:---
statut | Énum | Spécifie l’état actuel de l’alerte. Les valeurs possibles sont les suivantes : ```Active``` ```Resolved``` et ```Redirected``` .
assignedTo | string | Propriétaire de l’incident.
classification | Énum | Spécification de l’alerte. Les valeurs possibles sont ```Unknown```, ```FalsePositive``` et ```TruePositive```.
indications | Énum | Spécifie la détermination de l’alerte. Les valeurs possibles sont les suivantes : ```NotAvailable```, ```Apt```, ```Malware```, ```SecurityPersonnel```, ```SecurityTesting```, ```UnwantedSoftware``` et ```Other```.
étiquettes | Liste de chaînes | Liste des balises incident.



## <a name="response"></a>Réponse
Si elle réussit, cette méthode renvoie 200 OK et l’entité incident dans le corps de la réponse avec les propriétés mises à jour. Si l’incident portant l’ID spécifié est introuvable-404 introuvable.


## <a name="example"></a>Exemple

**Demande**

Voici un exemple de demande.

```
 PATCH https://api.security.microsoft.com/api/incidents/{id}
```

```json
{
    "status": "Resolved",
    "assignedTo": "secop2@contoso.com",
    "classification": "TruePositive",
    "determination": "Malware",
    "tags": ["Yossi's playground", "Don't mess with the Zohan"]
}
```


## <a name="related-topic"></a>Voir aussi
- [API d’incident](api-incident.md)
- [Répertorier les incidents](api-list-incidents.md)
