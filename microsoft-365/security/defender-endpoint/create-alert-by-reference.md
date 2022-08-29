---
title: Créer une alerte à partir de l’API d’événement
description: Découvrez comment utiliser l’API Créer une alerte pour créer une alerte en plus de l’événement dans Microsoft Defender pour point de terminaison.
keywords: api, api graphe, api prises en charge, get, alert, information, id
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.custom: api
ms.openlocfilehash: 9a211034b164381226df0d5d79d0d709db3c2e98
ms.sourcegitcommit: 217108c59be41b01963a393b4f16d137636fe6a8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/12/2022
ms.locfileid: "67326736"
---
# <a name="create-alert-api"></a>Créer une API d’alerte

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]


## <a name="api-description"></a>Description de l’API

Crée une [alerte](alerts.md) en plus de **l’événement**.

- **Microsoft Defender pour point de terminaison’événement** est requis pour la création de l’alerte.
- Vous devez fournir trois paramètres de l’événement dans la requête : **l’heure de l’événement**, **l’ID** de machine et **l’ID de rapport**. Voir l’exemple ci-dessous.
- Vous pouvez utiliser un événement trouvé dans l’API de repérage avancé ou le portail.
- S’il existe une alerte ouverte sur le même appareil avec le même titre, la nouvelle alerte créée est fusionnée avec elle.
- Une investigation automatique démarre automatiquement sur les alertes créées via l’API.

## <a name="limitations"></a>Limites

1. Les limitations de débit pour cette API sont de 15 appels par minute.

## <a name="permissions"></a>Autorisations

L’une des autorisations suivantes est requise pour appeler cette API. Pour en savoir plus, notamment sur le choix des autorisations, consultez [Utiliser Microsoft Defender pour point de terminaison API](apis-intro.md)

Type d’autorisation | Autorisation | Nom d’affichage de l’autorisation
:---|:---|:---
Application | Alert.ReadWrite.All | « Lire et écrire toutes les alertes »
Déléguée (compte professionnel ou scolaire) | Alert.ReadWrite | « Lire et écrire des alertes »

> [!NOTE]
> Lors de l’obtention d’un jeton à l’aide des informations d’identification de l’utilisateur :
>
> - L’utilisateur doit disposer au moins de l’autorisation de rôle suivante : « Investigation des alertes » (pour plus d’informations, consultez [Créer et gérer des rôles](user-roles.md) )
> - L’utilisateur doit avoir accès à l’appareil associé à l’alerte, en fonction des paramètres du groupe d’appareils (pour plus d’informations, consultez [Créer et gérer des groupes d’appareils](machine-groups.md)

## <a name="http-request"></a>Requête HTTP

```http
POST https://api.securitycenter.microsoft.com/api/alerts/CreateAlertByReference
```

## <a name="request-headers"></a>En-têtes de demande

Nom|Type|Description
:---|:---|:---
Autorisation | Chaîne | Porteur {token}. **Obligatoire**.
Content-Type | String | application/json. **Obligatoire**.

## <a name="request-body"></a>Corps de la demande

Dans le corps de la demande, fournissez les valeurs suivantes (toutes sont requises) :

Propriété | Type | Description
:---|:---|:---
eventTime | DateTime(UTC) | Heure précise de l’événement sous forme de chaîne, obtenue à partir d’une chasse avancée. Par exemple,  ```2018-08-03T16:45:21.7115183Z``` **Obligatoire**.
reportId | Chaîne | ReportId de l’événement, tel qu’obtenu à partir de la chasse avancée. **Obligatoire**.
machineId | Chaîne | ID de l’appareil sur lequel l’événement a été identifié. **Obligatoire**.
Sévérité  | Chaîne | Gravité de l’alerte. Les valeurs de propriété sont : « Low », « Medium » et « High ». **Obligatoire**.
title | Chaîne | Titre de l’alerte. **Obligatoire**.
description | Chaîne | Description de l’alerte. **Obligatoire**.
recommendedAction| Chaîne | L’agent de sécurité doit effectuer cette action lors de l’analyse de l’alerte. **Obligatoire**.
category| String | Catégorie de l’alerte. Les valeurs de propriété sont : « General », « CommandAndControl », « Collection », « CredentialAccess », « DefenseEvasion », « Discovery », « Exfiltration », « Exploit », « Execution », « InitialAccess », « LateralMovement », « Malware », « Persistence », « PrivilegeEscalation », « Ransomware », « SuspiciousActivity » **Requis**.

## <a name="response"></a>Réponse

Si elle réussit, cette méthode renvoie 200 OK et un nouvel objet [d’alerte](alerts.md) dans le corps de la réponse. Si l’événement avec les propriétés spécifiées (_reportId_, _eventTime_ et _machineId_) est introuvable - 404 Introuvable.

## <a name="example"></a>Exemple

### <a name="request"></a>Demande

Voici un exemple de la requête.

```http
POST https://api.securitycenter.microsoft.com/api/alerts/CreateAlertByReference
```

```json
{
    "machineId": "1e5bc9d7e413ddd7902c2932e418702b84d0cc07",
    "severity": "Low",
    "title": "example",
    "description": "example alert",
    "recommendedAction": "nothing",
    "eventTime": "2018-08-03T16:45:21.7115183Z",
    "reportId": "20776",
    "category": "Exploit"
}
```
