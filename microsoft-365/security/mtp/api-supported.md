---
title: API Microsoft 365 Defender prises en charge
description: API Microsoft 365 Defender prises en charge
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
ms.openlocfilehash: b7c0accf2d649d4ad6177260294922ee17783f2c
ms.sourcegitcommit: 815229e39a0f905d9f06717f00dc82e2a028fa7c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2020
ms.locfileid: "48844959"
---
# <a name="supported-microsoft-365-defender-apis"></a>API Microsoft 365 Defender prises en charge 

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**
- Microsoft 365 Defender

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
[API de recherche avancée de menaces](api-advanced-hunting.md) | Exécuter des requêtes de chasse avancées à partir de l’API.
[API d’incident](api-incident.md) | Exécutez des appels d’API liés aux incidents, tels que : répertorier les incidents, mettre à jour l’incident et plus encore.
