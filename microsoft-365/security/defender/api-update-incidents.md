---
title: Mettre à jour l’API d’incident
description: Découvrez comment mettre à jour des incidents à l’aide de l’API Microsoft 365 Defender
keywords: mise à jour, API, incident
search.product: eADQiWindows 10XVcnh
ms.service: microsoft-365-security
ms.subservice: m365d
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
ms.collection:
- m365-security
- tier3
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.custom: api
ms.openlocfilehash: 37460a3d0f0f67ee907b8e7b214f859dc60e8dfe
ms.sourcegitcommit: 12af9e8e3a6eaa090fda9e98ccb831dff65863a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2022
ms.locfileid: "68066847"
---
# <a name="update-incidents-api"></a>API Mettre à jour les incidents

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> [!IMPORTANT]
> Certaines informations ont trait à un produit préalablement publié, qui peut être modifié de manière significative avant sa publication commerciale. Microsoft n’offre aucune garantie, explicite ou implicite, concernant les informations fournies ici.

## <a name="api-description"></a>Description de l’API

Mises à jour propriétés de l’incident existant. Les propriétés pouvant être mises à jour sont : `status`, `determination`, `classification`, `assignedTo`, `tags`et `comments`.

### <a name="quotas-resource-allocation-and-other-constraints"></a>Quotas, allocation de ressources et autres contraintes

1. Vous pouvez effectuer jusqu’à 50 appels par minute ou 1 500 appels par heure avant d’atteindre le seuil de limitation.
2. Vous ne pouvez définir la `determination` propriété que si `classification` elle a la valeur TruePositive.

Si votre demande est limitée, elle retourne un code de `429` réponse. Le corps de la réponse indique l’heure à laquelle vous pouvez commencer à passer de nouveaux appels.

## <a name="permissions"></a>Autorisations

L’une des autorisations suivantes est requise pour appeler cette API. Pour en savoir plus, notamment sur le choix des autorisations, consultez [Accéder aux API Microsoft 365 Defender](api-access.md).

Type d’autorisation|Autorisation|Nom d’affichage de l’autorisation
---|---|---
Application|Incident.ReadWrite.All|Lire et écrire tous les incidents
Déléguée (compte professionnel ou scolaire)|Incident.ReadWrite|Lire et écrire des incidents

> [!NOTE]
> Lors de l’obtention d’un jeton à l’aide des informations d’identification de l’utilisateur, l’utilisateur doit avoir l’autorisation de mettre à jour l’incident dans le portail.

## <a name="http-request"></a>Requête HTTP

```HTTP
PATCH /api/incidents/{id}
```

## <a name="request-headers"></a>En-têtes de demande

Nom|Type|Description
---|---|---
Autorisation|Chaîne|Porteur {token}. **Obligatoire**.
Content-Type|String|application/json. **Obligatoire**.

## <a name="request-body"></a>Corps de la demande

Dans le corps de la demande, fournissez les valeurs des champs qui doivent être mis à jour. Les propriétés existantes qui ne sont pas incluses dans le corps de la demande conservent leurs valeurs, sauf si elles doivent être recalculées en raison de modifications apportées aux valeurs associées. Pour de meilleures performances, vous devez omettre les valeurs existantes qui n’ont pas changé.

Propriété|Type|Description
---|---|---
status|Énum|Spécifie l’état actuel de l’incident. Les valeurs possibles sont : `Active`, `Resolved`et `Redirected`.
assignedTo|string|Propriétaire de l’incident.
classification|Énum|Spécification de l’incident. Les valeurs possibles sont : `TruePositive`, `Informational, expected activity`et `FalsePositive`.
Détermination|Énum|Spécifie la détermination de l’incident. <p>Les valeurs de détermination possibles pour chaque classification sont les suivantes : <br><li> <b>Vrai positif</b> : `Multistage attack` (MultiStagedAttack), `Malicious user activity` (MaliciousUserActivity), `Compromised account` (CompromisedUser) : envisagez de modifier le nom de l’énumération dans l’API publique en conséquence, `Malware` (Malware), `Phishing` (Phishing), `Unwanted software` (UnwantedSoftware) et `Other` (Other). <li> <b>Activité informationnelle et attendue :</b> `Security test` (SecurityTesting), `Line-of-business application` (LineOfBusinessApplication), `Confirmed activity` (ConfirmedUserActivity) : envisagez de modifier le nom de l’énumération dans l’API publique en conséquence et `Other` (Autre). <li>  <b>Faux positif :</b> `Not malicious` (Clean) : envisagez de modifier le nom de l’énumération dans l’API publique en conséquence , `Not enough data to validate` (InsufficientData) et `Other` (Autre).
étiquettes|liste de chaînes|Liste des balises d’incident.
comment|string|Commentaire à ajouter à l’incident.

>[!NOTE]
>Vers le 29 août 2022, les valeurs de détermination d’alerte précédemment prises en charge (« Apt » et « SecurityPersonnel ») seront déconseillées et ne seront plus disponibles via l’API.

## <a name="response"></a>Réponse

Si elle réussit, cette méthode retourne `200 OK`. Le corps de la réponse contiendra l’entité d’incident avec des propriétés mises à jour. Si un incident avec l’ID spécifié est introuvable, la méthode retourne `404 Not Found`.

## <a name="example"></a>Exemple

### <a name="request-example"></a>Exemple de requête

Voici un exemple de la requête.

```HTTP
 PATCH https://api.security.microsoft.com/api/incidents/{id}
```

### <a name="response-example"></a>Exemple de réponse

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
