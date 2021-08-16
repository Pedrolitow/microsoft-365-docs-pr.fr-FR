---
title: API Restreindre l’exécution de l’application
description: Utilisez cette API pour créer des appels liés à la restriction de l’exécution d’une application.
keywords: api, api de graphique, api pris en charge, collecter un package d’enquête
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
ms.openlocfilehash: 2eda900a659879fcfe07052e8b51ba3e5a03e633
ms.sourcegitcommit: a0185d6b0dd091db6e1e1bfae2f68ab0e3cf05e5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2021
ms.locfileid: "58257705"
---
# <a name="restrict-app-execution-api"></a>API Restreindre l’exécution de l’application

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

**S’applique à :** [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/?linkid=2154037)

- Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>Description de l’API

Limiter l’exécution de toutes les applications sur l’appareil à l’exception d’un ensemble prédéféré.

## <a name="limitations"></a>Limites

1. Les limites de taux pour cette API sont de 100 appels par minute et de 1 500 appels par heure.

[!include[Device actions note](../../includes/machineactionsnote.md)]


> [!IMPORTANT]
>
> - Cette action est disponible pour les appareils Windows 10 version 1709 ou ultérieure.
> - Cette fonctionnalité est disponible si votre organisation utilise Antivirus Microsoft Defender.
> - Cette action doit respecter les formats de stratégie d Windows Defender’intégrité du code application Control et les exigences de signature. Pour plus d’informations, voir [Formats de stratégie d’intégrité du code et signature.](/windows/device-security/device-guard/requirements-and-deployment-planning-guidelines-for-device-guard#code-integrity-policy-formats-and-signing)

## <a name="permissions"></a>Autorisations

L’une des autorisations suivantes est nécessaire pour appeler cette API. Pour en savoir plus, notamment sur le choix des autorisations, voir [Utiliser Microsoft Defender pour les API de point de terminaison](apis-intro.md)

Type d’autorisation|Autorisation|Nom d’affichage de l’autorisation
:---|:---|:---
Application|Machine.RestrictExecution|« Restreindre l’exécution du code »
Déléguée (compte professionnel ou scolaire)|Machine.RestrictExecution|« Restreindre l’exécution du code »

> [!NOTE]
> Lors de l’obtention d’un jeton à l’aide des informations d’identification de l’utilisateur :
>
> - L’utilisateur doit avoir au moins l’autorisation de rôle suivante : « Actions de correction actives » (pour plus d’informations, voir Créer et gérer [des](user-roles.md) rôles)
> - L’utilisateur doit avoir accès à l’appareil, en fonction des paramètres de groupe d’appareils (voir Créer et gérer des groupes d’appareils [pour](machine-groups.md) plus d’informations)

## <a name="http-request"></a>Requête HTTP

```http
POST https://api.securitycenter.microsoft.com/api/machines/{id}/restrictCodeExecution
```

## <a name="request-headers"></a>En-têtes de demande

Nom|Type|Description
:---|:---|:---
Autorisation|String
|Porteur {token}. **Obligatoire**.
Content-Type|string|application/json. **Obligatoire**.

## <a name="request-body"></a>Corps de la demande

Dans le corps de la demande, fournissons un objet JSON avec les paramètres suivants :

Paramètre|Type|Description
:---|:---|:---
Commentaire|Chaîne|Commentaire à associer à l’action. **Obligatoire**.

## <a name="response"></a>Réponse

Si elle réussit, cette méthode renvoie 201 : code de réponse créé et action de [l’ordinateur](machineaction.md) dans le corps de la réponse.

## <a name="example"></a>Exemple

### <a name="request"></a>Demande

Voici un exemple de demande.

```http
POST https://api.securitycenter.microsoft.com/api/machines/1e5bc9d7e413ddd7902c2932e418702b84d0cc07/restrictCodeExecution 
```

```json
{
  "Comment": "Restrict code execution due to alert 1234"
}
```

- Pour supprimer la restriction d’exécution du code d’un appareil, voir [Supprimer la restriction d’application.](unrestrict-code-execution.md)
