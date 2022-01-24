---
title: API Microsoft 365 Defender prises en charge
description: API Microsoft 365 Defender prises en charge
keywords: Microsoft 365 Defender, API, api
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
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
ms.technology: m365d
ms.custom: api
ms.openlocfilehash: 1785186f778c489cb4a254fe39cc41921a4de86e
ms.sourcegitcommit: 6f3bc00a5cf25c48c61eb3835ac069e9f41dc4db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2022
ms.locfileid: "62171007"
---
# <a name="supported-microsoft-365-defender-apis"></a>API Microsoft 365 Defender prises en charge 

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**
- Microsoft 365 Defender

> [!IMPORTANT]
> Certaines informations ont trait à un produit préalablement publié, qui peut être modifié de manière significative avant sa publication commerciale. Microsoft n’offre aucune garantie, explicite ou implicite, concernant les informations fournies ici.

## <a name="list-of-available-apis"></a>Liste des API disponibles

Article | Description
-|-
[API de recherche avancée de menaces](api-advanced-hunting.md) | Exécutez des requêtes de recherche avancée.
[API d’incident](api-incident.md) | Liste et mise à jour des incidents, ainsi que d’autres tâches pratiques.
[API de diffusion en continu](streaming-api.md) | Expédiez des alertes et des événements en temps réel à mesure qu’ils se produisent dans un flux de données unique.

### <a name="endpoint-uris"></a>URL de point de terminaison

L’URI de base pour les deux API principales est : https://api.security.microsoft.com . Pour de meilleures performances, utilisez un serveur plus proche de votre géolocalisation :

- États-Unis : api-us.security.microsoft.com
- Europe : api-eu.security.microsoft.com
- Royaume-Uni : api-uk.security.microsoft.com

Les jetons peuvent être acquis en accédant à https://api.security.microsoft.com .

Toutes les API le long du `/api` chemin d’accès utilisent [le protocole OData](/odata/overview) ; par exemple, https://api.security.microsoft.com/api/incidents .

## <a name="related-articles"></a>Articles connexes

- [présentation Microsoft 365 Defender API de Microsoft 365 Defender’api](api-overview.md)
- [Accéder aux API Microsoft 365 Defender de données](api-access.md)
- [API de diffusion en continu](../defender-endpoint/raw-data-export.md)
- [En savoir plus sur les limites d’API et les licences](api-terms.md)
- [Comprendre les codes d’erreur](api-error-codes.md)
