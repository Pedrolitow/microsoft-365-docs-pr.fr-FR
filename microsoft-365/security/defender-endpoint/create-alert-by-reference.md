---
title: Créer une alerte à partir de l’API d’événement
description: Découvrez comment utiliser l’API Créer une alerte pour créer une alerte en haut de l’événement dans Microsoft Defender pour le point de terminaison.
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
ms.openlocfilehash: 8b05dde015bc96e1ccd3f80e25c416a371e03199
ms.sourcegitcommit: 5d8de3e9ee5f52a3eb4206f690365bb108a3247b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2021
ms.locfileid: "52772388"
---
# <a name="create-alert-api"></a>CRÉER une API d’alerte

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

- Vous souhaitez découvrir Microsoft Defender pour le point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink) 

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]


## <a name="api-description"></a>Description de l’API
Crée une [alerte en](alerts.md) haut de **l’événement.**
<br>**Microsoft Defender for Endpoint Event est** requis pour la création de l’alerte.
<br>Vous devez fournir 3 paramètres à partir de l’événement dans la demande : l’heure de l’événement, **l’ID** de l’ordinateur et **l’ID de rapport.** Voir l’exemple ci-dessous.
<br>Vous pouvez utiliser un événement trouvé dans l’API de recherche avancée ou le portail.
<br>S’il existe une alerte ouverte sur le même appareil avec le même titre, la nouvelle alerte créée est fusionnée avec elle.
<br>Un examen automatique démarre automatiquement sur les alertes créées via l’API.


## <a name="limitations"></a>Limitations
1. Les limites de taux pour cette API sont de 15 appels par minute.


## <a name="permissions"></a>Autorisations

L’une des autorisations suivantes est nécessaire pour appeler cette API. Pour en savoir plus, notamment sur le choix des autorisations, voir [Utiliser Microsoft Defender pour les API de point de terminaison](apis-intro.md)

Type d’autorisation |   Autorisation  |   Nom d’affichage de l’autorisation
:---|:---|:---
Application |   Alerts.ReadWrite.All |  « Lire et écrire toutes les alertes »
Déléguée (compte professionnel ou scolaire) | Alert.ReadWrite | « Lire et écrire des alertes »

>[!Note]
> Lors de l’obtention d’un jeton à l’aide des informations d’identification de l’utilisateur :
>- L’utilisateur doit avoir au moins l’autorisation de rôle suivante : « Enquête sur les alertes » (voir Créer et gérer des rôles [pour](user-roles.md) plus d’informations)
>- L’utilisateur doit avoir accès à l’appareil associé à l’alerte, en fonction des paramètres de groupe d’appareils (voir Créer et gérer des groupes d’appareils [pour](machine-groups.md) plus d’informations)

## <a name="http-request"></a>Requête HTTP

```
POST https://api.securitycenter.microsoft.com/api/alerts/CreateAlertByReference
```

## <a name="request-headers"></a>En-têtes de demande

Nom | Type | Description
:---|:---|:---
Autorisation | String | Porteur {token}. **Obligatoire**.
Content-Type | String | application/json. **Obligatoire**.

## <a name="request-body"></a>Corps de la demande

Dans le corps de la demande, fournissons les valeurs suivantes (toutes sont obligatoires) :

Propriété | Type | Description
:---|:---|:---
eventTime | DateTime(UTC) | Heure précise de l’événement en tant que chaîne, tel qu’obtenu à partir d’un chasse avancée. Par exemple, ```2018-08-03T16:45:21.7115183Z``` **obligatoire**.
reportId | String | ReportId de l’événement, tel qu’obtenu à partir d’un chasse avancée. **Obligatoire**.
machineId | String | ID de l’appareil sur lequel l’événement a été identifié. **Obligatoire**.
Sévérité  | String | Gravité de l’alerte. Les valeurs de propriété sont : « Low » (faible), « Medium » (moyen) et « High » (élevé). **Obligatoire**.
title | String | Titre de l’alerte. **Obligatoire**.
description | String | Description de l’alerte. **Obligatoire**.
recommendedAction| String | Action recommandée par le responsable de la sécurité lors de l’analyse de l’alerte. **Obligatoire**.
category| String | Catégorie de l’alerte. Les valeurs de propriété sont : « General », « CommandAndControl », « Collection », « CredentialAccess », « DefenseEvasion », « Discovery », « Exfiltration », « Exploit », « Execution », « InitialAccess », « LateralMovement », « Malware », « Persistence », « PrivilegeEscalation », « Ransomware », « SuspiciousActivity » **Required**.

## <a name="response"></a>Réponse

Si elle réussit, cette méthode renvoie 200 OK et un nouvel objet [d’alerte](alerts.md) dans le corps de la réponse. Si l’événement avec les propriétés spécifiées (_reportId_, _eventTime_ et _machineId_) est in trouvé - 404 - In trouvé.

## <a name="example"></a>Exemple

**Demande**

Voici un exemple de demande.

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
