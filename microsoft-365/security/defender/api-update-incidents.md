---
title: API de mise à jour de l’incident
description: Découvrez comment mettre à jour les incidents à l’aide Microsoft 365 API Defender
keywords: mise à jour, api, incident
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: e3f3919d067078ef1fd1e116dc52e8a73c0726d9
ms.sourcegitcommit: 0936f075a1205b8f8a71a7dd7761a2e2ce6167b3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52571780"
---
# <a name="update-incident-api"></a>API de mise à jour de l’incident

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**

- Microsoft 365 Defender

> [!IMPORTANT]
> Certaines informations ont trait à un produit préalablement publié, qui peut être modifié de manière significative avant sa publication commerciale. Microsoft n’offre aucune garantie, explicite ou implicite, concernant les informations fournies ici.

## <a name="api-description"></a>Description de l’API

Met à jour les propriétés d’un incident existant. Les propriétés updatables ```status``` sont : , , , , et ```determination``` ```classification``` ```assignedTo``` ```tags``` ```comments``` .

### <a name="quotas-resource-allocation-and-other-constraints"></a>Quotas, allocation de ressources et autres contraintes

1. Vous pouvez effectuer jusqu’à 50 appels par minute ou 1 500 appels par heure avant d’atteindre le seuil de limitation.
2. Vous ne pouvez définir `determination` la propriété que si elle est définie sur `classification` TruePositive.

Si votre demande est limitée, elle retourne un `429` code de réponse. Le corps de la réponse indique le moment où vous pouvez commencer à effectuer de nouveaux appels.

## <a name="permissions"></a>Autorisations

L’une des autorisations suivantes est nécessaire pour appeler cette API. Pour plus d’informations, notamment sur le choix des autorisations, voir [Access the Microsoft 365 Defender APIs](api-access.md).

Type d’autorisation | Autorisation | Nom d’affichage de l’autorisation
-|-|-
Application | Incident.ReadWrite.All | Lire et écrire tous les incidents
Déléguée (compte professionnel ou scolaire) | Incident.ReadWrite | Lire et écrire des incidents

> [!NOTE]
> Lors de l’obtention d’un jeton à l’aide des informations d’identification de l’utilisateur, l’utilisateur doit être autorisé à mettre à jour l’incident dans le portail.

## <a name="http-request"></a>Requête HTTP

```HTTP
PATCH /api/incidents/{id}
```

## <a name="request-headers"></a>En-têtes de demande

Nom | Type | Description
-|-|-
Autorisation | Chaîne | Porteur {token}. **Obligatoire**.
Content-Type | String | application/json. **Obligatoire**.

## <a name="request-body"></a>Corps de la demande

Dans le corps de la demande, fournissons les valeurs des champs qui doivent être mis à jour. Les propriétés existantes qui ne sont pas incluses dans le corps de la demande conserveront leurs valeurs, sauf si elles doivent être recalculées en raison de modifications apportées aux valeurs associées. Pour de meilleures performances, vous devez omettre les valeurs existantes qui n’ont pas changé.

Propriété | Type | Description
-|-|-
statut | Énum | Spécifie l’état actuel de l’incident. Les valeurs possibles ```Active``` sont : , et ```Resolved``` ```Redirected``` .
assignedTo | string | Propriétaire de l’incident.
classification | Énum | Spécification de l’incident. Les valeurs possibles sont les suivantes : ```Unknown```, ```FalsePositive``` et ```TruePositive```.
détermination | Énum | Spécifie la détermination de l’incident. Les valeurs possibles sont les suivantes : ```NotAvailable```, ```Apt```, ```Malware```, ```SecurityPersonnel```, ```SecurityTesting```, ```UnwantedSoftware``` et ```Other```.
étiquettes | liste de chaînes | Liste des balises d’incident.
comment | string | Commentaire à ajouter à l’incident.

## <a name="response"></a>Réponse

Si elle réussit, cette méthode renvoie `200 OK` . Le corps de la réponse contient l’entité d’incident avec les propriétés mises à jour. Si un incident avec l’ID spécifié n’a pas été trouvé, la méthode renvoie `404 Not Found` .

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
    "tags": ["Yossi's playground", "Don't mess with the Zohan"],
    "comments": [
          {
              "comment": "pen testing",
              "createdBy": "secop2@contoso.com",
              "createdTime": "2021-05-02T09:34:21.5519738Z"
          },
          {
              "comment": "valid incident",
              "createdBy": "secop2@contoso.comt",
              "createdTime": "2021-05-02T09:36:27.6652581Z"
          }
      ]
}
```

## <a name="related-articles"></a>Articles connexes

- [Accéder aux API Microsoft 365 Defender](api-access.md)
- [En savoir plus sur les limites d’API et les licences](api-terms.md)
- [Comprendre les codes d’erreur](api-error-codes.md)
- [API d’incident](api-incident.md)
- [Répertorier les incidents](api-list-incidents.md)
- [Vue d’ensemble des incidents](incidents-overview.md)
