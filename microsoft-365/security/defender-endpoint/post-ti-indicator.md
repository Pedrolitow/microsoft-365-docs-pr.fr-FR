---
title: API d’indicateur d’soumission ou de mise à jour
description: Découvrez comment utiliser l’API d’indicateur d’soumission ou de mise à jour pour soumettre ou mettre à jour une nouvelle entité d’indicateur dans Microsoft Defender pour le point de terminaison.
keywords: api, api de graphique, api pris en charge, envoyer, ti, indicateur, mettre à jour
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
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 0adf9b74398cafb7bd326dbc9183588feb30ee13
ms.sourcegitcommit: c11d4a2b9cb891ba22e16a96cb9d6389f6482459
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2021
ms.locfileid: "61283664"
---
# <a name="submit-or-update-indicator-api"></a>API d’indicateur d’soumission ou de mise à jour

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez faire l’expérience de Defender for Endpoint ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)


[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>Description de l’API

Envoie ou met à jour la nouvelle [entité d’indicateur.](ti-indicator.md)

La notation CIDR pour les IPs n’est pas prise en charge.

## <a name="limitations"></a>Limites

1. Les limites de taux pour cette API sont de 100 appels par minute et de 1 500 appels par heure.
2. Il existe une limite de 15 000 indicateurs actifs par client.

## <a name="permissions"></a>Autorisations

L’une des autorisations suivantes est nécessaire pour appeler cette API. Pour en savoir plus, notamment sur le choix des autorisations, [consultez La](apis-intro.md) mise en place

Type d’autorisation|Autorisation|Nom d’affichage de l’autorisation
:---|:---|:---
Application|Ti.ReadWrite|« Lire et écrire des indicateurs »
Application|Ti.ReadWrite.All|« Lire et écrire tous les indicateurs »
Déléguée (compte professionnel ou scolaire)|Ti.ReadWrite|« Lire et écrire des indicateurs »

## <a name="http-request"></a>Requête HTTP

```http
POST https://api.securitycenter.microsoft.com/api/indicators
```

## <a name="request-headers"></a>En-têtes de demande

Nom|Type|Description
:---|:---|:---
Autorisation|String|Porteur {token}. **Obligatoire**.
Content-Type|string|application/json. **Obligatoire**.

## <a name="request-body"></a>Corps de la demande

Dans le corps de la demande, fournissons un objet JSON avec les paramètres suivants :

Paramètre|Type|Description
:---|:---|:---
indicatorValue|String|Identité de [l’entité Indicateur.](ti-indicator.md) **Obligatoire**
indicatorType|Énum|Type de l’indicateur. Les valeurs possibles sont les suivantes : « FileSha1 », « FileMd5 », « CertificateThumbprint », « FileSha256 », « IpAddress », « DomainName » et « Url ». **Obligatoire**
action|Énum|Action qui sera entreprise si l’indicateur est détecté dans l’organisation. Les valeurs possibles sont : « Alert », « Warn », « Block », « Audit », « BlockAndRemediate », « AlertAndBlock » et « Allowed ». **Obligatoire**. Le paramètre GenerateAlert doit avoir la valeur « TRUE » lors de la création d’une action avec « Audit ».
application|String|Application associée à l’indicateur. Ce champ fonctionne uniquement pour les nouveaux indicateurs. Il ne met pas à jour la valeur d’un indicateur existant. **Optional**
title|String|Titre de l’alerte de l’indicateur. **Obligatoire**
description|String|Description de l’indicateur. **Obligatoire**
expirationTime|DateTimeOffset|Heure d’expiration de l’indicateur. **Optional**
Sévérité |Énum|Gravité de l’indicateur. les valeurs possibles sont : « Informational », « Low », « Medium » et « High ». **Optional**
recommendedActions|String|Actions recommandées pour l’alerte d’indicateur TI. **Optional**
rbacGroupNames|String|Liste séparée par des virgules des noms de groupe RBAC à appliquer à l’indicateur. **Optional**

## <a name="response"></a>Réponse

- Si elle réussit, cette méthode renvoie le code de réponse [](ti-indicator.md) 200 - OK et l’entité d’indicateur créée/mise à jour dans le corps de la réponse.
- Si elle ne réussit pas : cette méthode retourne 400 - Demande non bonne. Une demande incorrecte indique généralement un corps incorrect.

## <a name="example"></a>Exemple

### <a name="request"></a>Demande

Voici un exemple de demande.

```http
POST https://api.securitycenter.microsoft.com/api/indicators
```

```json
{
    "indicatorValue": "220e7d15b011d7fac48f2bd61114db1022197f7f",
    "indicatorType": "FileSha1",
    "title": "test",
    "application": "demo-test",
    "expirationTime": "2020-12-12T00:00:00Z",
    "action": "AlertAndBlock",
    "severity": "Informational",
    "description": "test",
    "recommendedActions": "nothing",
    "rbacGroupNames": ["group1", "group2"]
}
```

## <a name="related-topic"></a>Rubrique connexe

- [Gérer des indicateurs](manage-indicators.md)
