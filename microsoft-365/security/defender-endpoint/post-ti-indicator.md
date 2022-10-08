---
title: API d’envoi ou de mise à jour de l’indicateur
description: Découvrez comment utiliser l’API Envoyer ou Mettre à jour l’indicateur pour envoyer ou mettre à jour une nouvelle entité d’indicateur dans Microsoft Defender pour point de terminaison.
keywords: api, api graphe, api prises en charge, submit, ti, indicator, update
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
- tier2
ms.topic: article
ms.subservice: mde
ms.custom: api
search.appverid: met150
ms.openlocfilehash: 1afe71e8a25b0c623be2039c471c75d707c5c50a
ms.sourcegitcommit: 4e42bafee965446f44f7f57d1defed2b9b24fce8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2022
ms.locfileid: "68226534"
---
# <a name="submit-or-update-indicator-api"></a>API d’envoi ou de mise à jour de l’indicateur

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)


[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>Description de l’API

Envoie ou Mises à jour nouvelle entité [d’indicateur](ti-indicator.md).

La notation CIDR pour les adresses IP n’est pas prise en charge.

## <a name="limitations"></a>Limites

1. Les limites de débit pour cette API sont de 100 appels par minute et de 1 500 appels par heure.
2. Il existe une limite de 15 000 indicateurs actifs par locataire.

## <a name="permissions"></a>Autorisations

L’une des autorisations suivantes est requise pour appeler cette API. Pour en savoir plus, notamment sur le choix des autorisations, consultez [Prise en main](apis-intro.md)

Type d’autorisation|Autorisation|Nom d’affichage de l’autorisation
:---|:---|:---
Application|Ti.ReadWrite|« Indicateurs de lecture et d’écriture »
Application|Ti.ReadWrite.All|« Lire et écrire tous les indicateurs »
Déléguée (compte professionnel ou scolaire)|Ti.ReadWrite|« Indicateurs de lecture et d’écriture »

## <a name="http-request"></a>Requête HTTP

```http
POST https://api.securitycenter.microsoft.com/api/indicators
```

## <a name="request-headers"></a>En-têtes de demande

Nom|Type|Description
:---|:---|:---
Autorisation|Chaîne|Porteur {token}. **Obligatoire**.
Content-Type|string|application/json. **Obligatoire**.

## <a name="request-body"></a>Corps de la demande

Dans le corps de la demande, fournissez un objet JSON avec les paramètres suivants :

Paramètre|Type|Description
:---|:---|:---
indicatorValue|Chaîne|Identité de l’entité [Indicateur](ti-indicator.md) . **Obligatoire**
indicatorType|Énum|Type de l’indicateur. Les valeurs possibles sont : « FileSha1 », « FileMd5 », « CertificateThumbprint », « FileSha256 », « IpAddress », « DomainName » et « Url ». **Obligatoire**
action|Énum|Action qui sera effectuée si l’indicateur est détecté dans l’organisation. Les valeurs possibles sont : « Alert », « Warn », « Block », « Audit », « BlockAndRemediate », « AlertAndBlock » et « Allowed ». **Obligatoire**. Le paramètre « GenerateAlert » doit être défini sur « TRUE » lors de la création d’une action avec « Audit ».
application|Chaîne|Application associée à l’indicateur. Ce champ fonctionne uniquement pour les nouveaux indicateurs. Il ne met pas à jour la valeur sur un indicateur existant. **Optional**
title|Chaîne|Titre de l’alerte d’indicateur. **Obligatoire**
description|Chaîne|Description de l’indicateur. **Obligatoire**
expirationTime|DateTimeOffset|Heure d’expiration de l’indicateur. **Optional**
Sévérité |Énum|Gravité de l’indicateur. Les valeurs possibles sont : « Informational », « Low », « Medium » et « High ». **Optional**
recommendedActions|Chaîne|Actions recommandées pour les alertes d’indicateur TI. **Optional**
rbacGroupNames|Chaîne|Liste séparée par des virgules des noms de groupes RBAC auxquels l’indicateur serait appliqué. **Optional**
educateUrl|Chaîne|URL de notification/support personnalisée. Pris en charge pour les types d’actions Bloquer et Avertir pour les indicateurs d’URL. **Optional**
generateAlert|Énum|**True** si la génération d’alerte est requise, **False** si cet indicateur ne doit pas générer d’alerte.
## <a name="response"></a>Réponse

- Si elle réussit, cette méthode renvoie le code de réponse 200 - OK et l’entité [Indicateur](ti-indicator.md) créée/mise à jour dans le corps de la réponse.
- Si elle ne réussit pas : cette méthode retourne 400 - Requête incorrecte. Une requête incorrecte indique généralement un corps incorrect.

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
