---
title: API de protection Microsoft contre les menaces prises en charge
description: API de protection Microsoft contre les menaces prises en charge
keywords: MTP, API, API
search.product: eADQiWindows 10XVcnh
ms.prod: microsoft-365-enterprise
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.openlocfilehash: 49fa182a6142748ca7769411fe74389f365ba75f
ms.sourcegitcommit: 9a275a13af3e063e80ce1bd3cd8142a095db92d2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2020
ms.locfileid: "47650270"
---
# <a name="supported-microsoft-threat-protection-apis"></a>API de protection Microsoft contre les menaces prises en charge 
**S’applique à :**
- Protection Microsoft contre les menaces

>[!IMPORTANT] 
>Certaines informations se rapportent à des produits précommercialisés susceptibles d’être modifiés de manière substantielle avant leur publication commerciale. Microsoft makes no warranties, express or implied, with respect to the information provided here.


### <a name="end-point-uris"></a>URI de point de terminaison :

- L’URI de la base de service est : https://api.security.microsoft.com <br>

>[!NOTE]
>Pour de meilleures performances, vous pouvez utiliser le serveur plus près de votre emplacement géographique :
> - api-us.security.microsoft.com
> - api-eu.security.microsoft.com
> - api-uk.security.microsoft.com

 - La ressource pour l’acquisition de jetons doit être : https://api.security.microsoft.com

 - Toutes les API sous ```/api``` chemin d’accès sont des API OData. p ```https://api.security.microsoft.com/api/incidents```

## <a name="list-of-available-apis"></a>Liste des API disponibles :

Rubrique | Description
:---|:---
[API de chasse avancée](api-advanced-hunting.md) | Exécuter des requêtes de chasse avancées à partir de l’API.
[API d’incident](api-incident.md) | Exécutez des appels d’API liés aux incidents, tels que : répertorier les incidents, mettre à jour l’incident et plus encore.
