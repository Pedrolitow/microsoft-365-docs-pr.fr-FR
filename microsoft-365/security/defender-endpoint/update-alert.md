---
title: Mettre à jour l’API d’entité d’alerte
description: Découvrez comment mettre à jour une alerte Microsoft Defender pour point de terminaison à l’aide de cette API. Vous pouvez mettre à jour l’état, la détermination, la classification et les propriétés assignedTo.
keywords: api, api graphe, api prises en charge, get, alert, information, id
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
ms.topic: article
ms.subservice: mde
ms.custom: api
search.appverid: met150
ms.openlocfilehash: 99f17d9aacb67214703a4af2647385fa1778e88a
ms.sourcegitcommit: 4e42bafee965446f44f7f57d1defed2b9b24fce8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2022
ms.locfileid: "68221761"
---
# <a name="update-alert"></a>Mettre à jour une alerte

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!Include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!Include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>Description de l’API
Mises à jour propriétés de [l’alerte](alerts.md) existante.

La soumission de **commentaire** est disponible avec ou sans mise à jour des propriétés.

Les propriétés pouvant être mises à jour sont : `status`, `determination`, `classification`et `assignedTo`.

## <a name="limitations"></a>Limites

1. Vous pouvez mettre à jour les alertes disponibles dans l’API. Pour plus d’informations, consultez [Alertes de liste](get-alerts.md).
2. Les limites de débit pour cette API sont de 100 appels par minute et de 1 500 appels par heure.

## <a name="permissions"></a>Autorisations

L’une des autorisations suivantes est requise pour appeler cette API. Pour en savoir plus, notamment sur le choix des autorisations, consultez [Utiliser Microsoft Defender pour point de terminaison API](apis-intro.md)

Type d’autorisation|Autorisation|Nom d’affichage de l’autorisation
:---|:---|:---
Application|Alerts.ReadWrite.All|« Lire et écrire toutes les alertes »
Déléguée (compte professionnel ou scolaire)|Alert.ReadWrite|« Lire et écrire des alertes »

> [!NOTE]
> Lors de l’obtention d’un jeton à l’aide des informations d’identification de l’utilisateur :
>
> - L’utilisateur doit disposer au moins de l’autorisation de rôle suivante : « Investigation des alertes » (pour plus d’informations, consultez [Créer et gérer des rôles](user-roles.md) )
> - L’utilisateur doit avoir accès à l’appareil associé à l’alerte, en fonction des paramètres du groupe d’appareils (pour plus d’informations, consultez [Créer et gérer des groupes d’appareils](machine-groups.md)
>
> La création de groupes d’appareils est prise en charge dans Defender pour point de terminaison Plan 1 et Plan 2.

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

Dans le corps de la demande, fournissez les valeurs des champs pertinents qui doivent être mis à jour.

Les propriétés existantes qui ne sont pas incluses dans le corps de la demande conservent leurs valeurs précédentes ou sont recalculées en fonction des modifications apportées à d’autres valeurs de propriété.

Pour de meilleures performances, vous ne devez pas inclure les valeurs existantes qui n’ont pas changé.

Propriété|Type|Description|
:---|:---|:---
État|Chaîne|Spécifie l’état actuel de l’alerte. Les valeurs de propriété sont : « New », « InProgress » et « Resolved ».|
assignedTo|Chaîne|Propriétaire de l’alerte|
Classification|Chaîne|Spécifie la spécification de l’alerte. Les valeurs de propriété sont : `TruePositive`, `Informational, expected activity`et `FalsePositive`.|
Détermination|Chaîne|Spécifie la détermination de l’alerte. <p>Les valeurs de détermination possibles pour chaque classification sont les suivantes : <br><li> <b>Vrai positif</b> : `Multistage attack` (MultiStagedAttack), `Malicious user activity` (MaliciousUserActivity), `Compromised account` (CompromisedUser) : envisagez de modifier le nom de l’énumération dans l’API publique en conséquence, `Malware` (Malware), `Phishing` (Phishing), `Unwanted software` (UnwantedSoftware) et `Other` (Other). <li> <b>Activité informationnelle et attendue :</b> `Security test` (SecurityTesting), `Line-of-business application` (LineOfBusinessApplication), `Confirmed activity` (ConfirmedUserActivity) : envisagez de modifier le nom de l’énumération dans l’API publique en conséquence et `Other` (Autre). <li>  <b>Faux positif :</b> `Not malicious` (Clean) : envisagez de modifier le nom de l’énumération dans l’API publique en conséquence , `Not enough data to validate` (InsufficientData) et `Other` (Autre).|
Commentaire|Chaîne|Commentaire à ajouter à l’alerte.|

>[!NOTE]
>Vers le 29 août 2022, les valeurs de détermination d’alerte précédemment prises en charge (« Apt » et « SecurityPersonnel ») seront déconseillées et ne seront plus disponibles via l’API.

## <a name="response"></a>Réponse

Si elle réussit, cette méthode retourne 200 OK et l’entité [d’alerte](alerts.md) dans le corps de la réponse avec les propriétés mises à jour. Si l’alerte avec l’ID spécifié est introuvable - 404 Introuvable.

## <a name="example"></a>Exemple

### <a name="request"></a>Demande

Voici un exemple de la requête.

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
