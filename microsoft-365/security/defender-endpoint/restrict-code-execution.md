---
title: Restreindre l’API d’exécution d’application
description: Utilisez cette API pour créer des appels liés à la restriction de l’exécution d’une application.
keywords: api, api graphe, api prises en charge, collecter le package d’investigation
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
ms.openlocfilehash: a50aa7c1771469f7ba55f93d02deaaee98824deb
ms.sourcegitcommit: 4e42bafee965446f44f7f57d1defed2b9b24fce8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2022
ms.locfileid: "68229391"
---
# <a name="restrict-app-execution-api"></a>Restreindre l’API d’exécution d’application

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>Description de l’API

Limitez l’exécution de toutes les applications sur l’appareil, à l’exception d’un ensemble prédéfini.

## <a name="limitations"></a>Limites

1. Les limites de débit pour cette API sont de 100 appels par minute et de 1 500 appels par heure.

[!include[Device actions note](../../includes/machineactionsnote.md)]


> [!IMPORTANT]
>
> - Cette action est disponible pour les appareils sur Windows 10, version 1709 ou ultérieure, et sur Windows 11.
> - Cette fonctionnalité est disponible si votre organisation utilise Microsoft Defender Antivirus.
> - Cette action doit répondre aux Windows Defender formats de stratégie d’intégrité du code Application Control et aux exigences de signature. Pour plus d’informations, consultez [les formats de stratégie d’intégrité du code et la signature](/windows/device-security/device-guard/requirements-and-deployment-planning-guidelines-for-device-guard#code-integrity-policy-formats-and-signing).

## <a name="permissions"></a>Autorisations

L’une des autorisations suivantes est requise pour appeler cette API. Pour en savoir plus, notamment sur le choix des autorisations, consultez [Utiliser Microsoft Defender pour point de terminaison API](apis-intro.md)

Type d’autorisation|Autorisation|Nom d’affichage de l’autorisation
:---|:---|:---
Application|Machine.RestrictExecution|'Restreindre l’exécution du code'
Déléguée (compte professionnel ou scolaire)|Machine.RestrictExecution|'Restreindre l’exécution du code'

> [!NOTE]
> Lors de l’obtention d’un jeton à l’aide des informations d’identification de l’utilisateur :
>
> - L’utilisateur doit disposer au moins de l’autorisation de rôle suivante : « Actions de correction actives » (voir [Créer et gérer des rôles](user-roles.md) pour plus d’informations)
> - L’utilisateur doit avoir accès à l’appareil, en fonction des paramètres du groupe d’appareils (voir [Créer et gérer des groupes d’appareils](machine-groups.md) pour plus d’informations)
>
> La création de groupes d’appareils est prise en charge dans Defender pour point de terminaison Plan 1 et Plan 2.  

## <a name="http-request"></a>Requête HTTP

```http
POST https://api.securitycenter.microsoft.com/api/machines/{id}/restrictCodeExecution
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
Commentaire|Chaîne|Commentaire à associer à l’action. **Obligatoire**.

## <a name="response"></a>Réponse

Si elle réussit, cette méthode renvoie le code de réponse 201 - Créé et [l’action de l’ordinateur](machineaction.md) dans le corps de la réponse.

Si vous envoyez plusieurs appels d’API pour restreindre l’exécution de l’application pour le même appareil, il retourne « Action de l’ordinateur en attente » ou HTTP 400 avec le message « L’action est déjà en cours ».

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

- Pour supprimer la restriction d’exécution de code d’un appareil, consultez [Supprimer la restriction d’application](unrestrict-code-execution.md).
