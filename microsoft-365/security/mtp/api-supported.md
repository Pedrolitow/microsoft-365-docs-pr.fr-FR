---
title: API Microsoft 365 Defender prises en charge
description: API Microsoft 365 Defender prises en charge
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
ms.openlocfilehash: dbb7613dae3755b0fb794a3d68b5b424d765cc62
ms.sourcegitcommit: d6b1da2e12d55f69e4353289e90f5ae2f60066d0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/19/2020
ms.locfileid: "49719321"
---
# <a name="supported-microsoft-365-defender-apis"></a>API Microsoft 365 Defender prises en charge 

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**
- Microsoft 365 Defender

> [!IMPORTANT]
> Certaines informations se rapportent à des produits précommercialisés susceptibles d’être modifiés de manière substantielle avant leur publication commerciale. Microsoft makes no warranties, express or implied, with respect to the information provided here.

## <a name="list-of-available-apis"></a>Liste des API disponibles

Article | Description
-|-
[API de recherche avancée de menaces](api-advanced-hunting.md) | Exécuter des requêtes de chasse avancées.
[API d’incident](api-incident.md) | Répertorier et mettre à jour les incidents, ainsi que d’autres tâches pratiques.

### <a name="endpoint-uris"></a>URI de point de terminaison

L’URI de base pour les deux API principales est : https://api.security.microsoft.com . Pour de meilleures performances, utilisez un serveur plus près de votre géolocalisation :

- États-Unis : api-us.security.microsoft.com
- Europe : api-eu.security.microsoft.com
- Royaume-Uni : api-uk.security.microsoft.com

Les jetons peuvent être obtenus en accédant à https://api.security.microsoft.com .

Toutes les API sur le `/api` chemin d’accès utilisent le protocole [OData](https://docs.microsoft.com/odata/overview) , par exemple, https://api.security.microsoft.com/api/incidents .

## <a name="related-articles"></a>Articles connexes

- [Vue d’ensemble des API Microsoft 365 Defender](api-overview.md)
- [Accéder aux API de protection contre les menaces Microsoft](api-access.md)
- [En savoir plus sur les limites d’API et la gestion des licences](api-terms.md)
- [Comprendre les codes d’erreur](api-error-codes.md)
