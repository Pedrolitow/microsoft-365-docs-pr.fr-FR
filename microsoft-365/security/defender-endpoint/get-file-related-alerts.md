---
title: API Obtenir les alertes liées aux fichiers
description: Découvrez comment utiliser l’API Obtenir des alertes liées aux fichiers pour obtenir une collection d’alertes liées à un hachage de fichier donné dans Microsoft Defender pour le point de terminaison.
keywords: api, api de graphique, api pris en charge, obtenir, fichier, hachage
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
ms.openlocfilehash: b77946f4bfdb793ffbfdf102a7221df083fb92eb
ms.sourcegitcommit: 5d8de3e9ee5f52a3eb4206f690365bb108a3247b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2021
ms.locfileid: "52770296"
---
# <a name="get-file-related-alerts-api"></a>API Obtenir les alertes liées aux fichiers

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez découvrir Microsoft Defender pour le point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink) 

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]


## <a name="api-description"></a>Description de l’API
Récupère une collection d’alertes liées à un hachage de fichier donné.


## <a name="limitations"></a>Limitations
1. Les limites de taux pour cette API sont de 100 appels par minute et de 1 500 appels par heure.


## <a name="permissions"></a>Autorisations
L’une des autorisations suivantes est nécessaire pour appeler cette API. Pour en savoir plus, notamment sur le choix des autorisations, voir [Utiliser Defender pour les API de point de terminaison](apis-intro.md)

Type d’autorisation |   Autorisation  |   Nom d’affichage de l’autorisation
:---|:---|:---
Application |   Alert.Read.All |    « Lire toutes les alertes »
Application |   Alert.ReadWrite.All |   « Lire et écrire toutes les alertes »
Déléguée (compte professionnel ou scolaire) | Alert.Read | « Lire les alertes »
Déléguée (compte professionnel ou scolaire) | Alert.ReadWrite | « Lire et écrire des alertes »

>[!Note]
> Lors de l’obtention d’un jeton à l’aide des informations d’identification de l’utilisateur :
>- L’utilisateur doit avoir au moins l’autorisation de rôle suivante : « Afficher les données » (voir Créer et gérer des rôles [pour](user-roles.md) plus d’informations)
>- La réponse inclut uniquement les alertes, associées aux appareils, à qui [](machine-groups.md) l’utilisateur a accès, en fonction des paramètres de groupe d’appareils (voir Créer et gérer des groupes d’appareils pour plus d’informations)

## <a name="http-request"></a>Requête HTTP
```
GET /api/files/{id}/alerts
```

## <a name="request-headers"></a>En-têtes de demande

Nom | Type | Description
:---|:---|:---
Autorisation | String | Porteur {token}. **Obligatoire**.


## <a name="request-body"></a>Corps de la demande
Vide

## <a name="response"></a>Réponse
En cas de réussite et si le fichier existe : 200 - OK avec la liste [des](alerts.md) entités d’alerte dans le corps. Si le fichier n’existe pas - 404 - In trouvé.


## <a name="example"></a>Exemple

**Demande**

Voici un exemple de demande.

```http
GET https://api.securitycenter.microsoft.com/api/files/6532ec91d513acc05f43ee0aa3002599729fd3e1/alerts
```
