---
title: Rechercher des appareils par API de balise
description: Rechercher tous les appareils qui contiennent une balise specifc
keywords: api, api pris en charge, obtenir, appareil, rechercher, rechercher un appareil, par balise, balise
search.product: eADQiWindows 10XVcnh
ms.prod: w10
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
ms.openlocfilehash: f8c6c289cca61e5a0891af04ef97831a27b341f3
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59177660"
---
# <a name="find-devices-by-tag-api"></a>Rechercher des appareils par API de balise

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :** [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/?linkid=2154037)

- Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>Description de l’API

Rechercher [des ordinateurs](machine.md) par [balise](machine-tags.md).

`startswith` est prise en charge.

## <a name="limitations"></a>Limites

1. Les limites de taux pour cette API sont de 100 appels par minute et de 1 500 appels par heure.

## <a name="permissions"></a>Autorisations

L’une des autorisations suivantes est nécessaire pour appeler cette API. Pour en savoir plus, notamment sur le choix des autorisations, voir [Utiliser Microsoft Defender pour les API de point de terminaison](apis-intro.md)

Type d’autorisation|Autorisation|Nom d’affichage de l’autorisation
:---|:---|:---
Application|Machine.Read.All|« Lire tous les profils d’ordinateur »
Application|Machine.ReadWrite.All|« Lire et écrire toutes les informations sur l’ordinateur »
Déléguée (compte professionnel ou scolaire)|Machine.Read|« Lire les informations sur l’ordinateur »
Déléguée (compte professionnel ou scolaire)|Machine.ReadWrite|« Lire et écrire des informations sur l’ordinateur »

> [!NOTE]
> Lors de l’obtention d’un jeton à l’aide des informations d’identification de l’utilisateur :
>
> - La réponse inclut uniquement les appareils accessibles par l’utilisateur en fonction des paramètres de groupe d’appareils (pour plus d’informations, voir Créer et gérer des groupes d’appareils). [](machine-groups.md)
> - L’utilisateur doit avoir au moins l’autorisation de rôle suivante : « Afficher les données » (voir Créer et gérer des rôles [pour](user-roles.md) plus d’informations)
> - La réponse inclut uniquement les appareils accessibles par l’utilisateur en fonction des paramètres de groupe d’appareils (pour plus d’informations, voir Créer et gérer des groupes d’appareils). [](machine-groups.md)

## <a name="http-request"></a>Requête HTTP

```http
GET /api/machines/findbytag?tag={tag}&useStartsWithFilter={true/false}
```

## <a name="request-headers"></a>En-têtes de demande

Nom|Type|Description
:---|:---|:---
Autorisation|Chaîne|Porteur {token}. **Obligatoire**.

## <a name="request-uri-parameters"></a>Paramètres d’URI de demande

Nom|Type|Description
:---|:---|:---
tag|Chaîne|Nom de la balise. **Obligatoire**.
useStartsWithFilter|Boolean|Si la valeur est true, la recherche recherche tous les appareils dont le nom de balise commence par la balise donnée dans la requête. Par défaut est faux. **Facultatif**.

## <a name="request-body"></a>Corps de la demande

Vide

## <a name="response"></a>Réponse

En cas de réussite - 200 OK avec la liste des ordinateurs dans le corps de la réponse.

## <a name="example"></a>Exemple

### <a name="request"></a>Demande

Voici un exemple de demande.

```http
GET https://api.securitycenter.microsoft.com/api/machines/findbytag?tag=testTag&useStartsWithFilter=true
```
