---
title: API Obtenir les alertes liées au domaine
description: Découvrez comment utiliser l’API Obtenir les alertes liées au domaine pour récupérer les alertes liées à une adresse de domaine donnée dans Microsoft Defender pour le point de terminaison.
keywords: api, api de graphique, api pris en charge, obtenir, domaine, associé, alertes
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
ms.openlocfilehash: b67b97ac115057b0e17bfd492e6330a13ee9e213
ms.sourcegitcommit: c11d4a2b9cb891ba22e16a96cb9d6389f6482459
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2021
ms.locfileid: "61284636"
---
# <a name="get-domain-related-alerts-api"></a>API Obtenir les alertes liées au domaine

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>Description de l’API

Récupère une collection d’alertes [liées](alerts.md) à une adresse de domaine donnée.

## <a name="limitations"></a>Limites

- Vous pouvez interroger la dernière mise à jour des alertes en fonction de votre période de rétention configurée.
- Les limites de taux pour cette API sont de 100 appels par minute et de 1 500 appels par heure.

## <a name="permissions"></a>Autorisations

L’une des autorisations suivantes est nécessaire pour appeler cette API. Pour en savoir plus, notamment sur le choix des autorisations, voir [Utiliser Microsoft Defender pour les API de point de terminaison](apis-intro.md)

Type d’autorisation|Autorisation|Nom d’affichage de l’autorisation
:---|:---|:---
Application|Alert.Read.All|« Lire toutes les alertes »
Application|Alert.ReadWrite.All|« Lire et écrire toutes les alertes »
Déléguée (compte professionnel ou scolaire)|Alert.Read|« Lire les alertes »
Déléguée (compte professionnel ou scolaire)|Alert.ReadWrite|« Lire et écrire des alertes »

> [!NOTE]
> Lors de l’obtention d’un jeton à l’aide des informations d’identification de l’utilisateur :
>
> - L’utilisateur doit avoir au moins l’autorisation de rôle suivante : « Afficher les données » (voir Créer et gérer des rôles [pour](user-roles.md) plus d’informations)
> - La réponse inclut uniquement les alertes, associées aux appareils, à qui [](machine-groups.md) l’utilisateur a accès, en fonction des paramètres de groupe d’appareils (voir Créer et gérer des groupes d’appareils pour plus d’informations)

## <a name="http-request"></a>Requête HTTP

```http
GET /api/domains/{domain}/alerts
```

## <a name="request-headers"></a>En-têtes de demande

|En-tête|Valeur|
|---|---|
|Autorisation|String|

## <a name="request-body"></a>Corps de la demande

Vide

## <a name="response"></a>Réponse

En cas de réussite et si le domaine existe : 200 - OK avec la liste des entités [d’alerte.](alerts.md) Si le domaine n’existe pas : 200 - OK avec un ensemble vide.

## <a name="example"></a>Exemple

### <a name="request"></a>Demande

Voici un exemple de la demande.

```http
GET https://api.securitycenter.microsoft.com/api/domains/client.wns.windows.com/alerts
```
