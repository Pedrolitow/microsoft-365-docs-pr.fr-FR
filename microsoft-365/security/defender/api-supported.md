---
title: API Microsoft 365 Defender prises en charge
description: API Microsoft 365 Defender prises en charge
keywords: Microsoft 365 Defender, API, API
search.product: eADQiWindows 10XVcnh
ms.service: microsoft-365-security
ms.subservice: m365d
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
ms.collection:
- m365-security
- tier3
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.custom: api
ms.openlocfilehash: c43f2f3d60fe5e73984be8721750a29bcfc10740
ms.sourcegitcommit: 12af9e8e3a6eaa090fda9e98ccb831dff65863a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2022
ms.locfileid: "68077950"
---
# <a name="supported-microsoft-365-defender-apis"></a>API Microsoft 365 Defender prises en charge 

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**
- Microsoft 365 Defender

> [!IMPORTANT]
> Certaines informations ont trait à un produit préalablement publié, qui peut être modifié de manière significative avant sa publication commerciale. Microsoft n’offre aucune garantie, explicite ou implicite, concernant les informations fournies ici.

## <a name="list-of-available-apis"></a>Liste des API disponibles

Article | Description
-|-
[API de recherche avancée de menaces](api-advanced-hunting.md) | Exécutez des requêtes de chasse avancées.
[API d’incident](api-incident.md) | Répertoriez et mettez à jour les incidents, ainsi que d’autres tâches pratiques.
[API de diffusion en continu](streaming-api.md) | Envoyez des événements et des alertes en temps réel au fur et à mesure qu’ils se produisent dans un flux de données unique.

### <a name="endpoint-uris"></a>URI de point de terminaison

L’URI de base pour les deux API principales est : https://api.security.microsoft.com. Pour de meilleures performances, utilisez un serveur plus proche de votre géolocalisation :

- Le États-Unis : api-us.security.microsoft.com
- Europe : api-eu.security.microsoft.com
- Royaume-Uni : api-uk.security.microsoft.com

Les jetons peuvent être acquis en accédant https://api.security.microsoft.comà .

Toutes les API le long du `/api` chemin d’accès utilisent le protocole [OData](/odata/overview) ; par exemple, https://api.security.microsoft.com/api/incidents.

## <a name="related-articles"></a>Articles connexes

- [Vue d’ensemble des API Microsoft 365 Defender](api-overview.md)
- [Accéder aux API Microsoft 365 Defender](api-access.md)
- [API de diffusion en continu](../defender-endpoint/raw-data-export.md)
- [En savoir plus sur les limites d’API et les licences](api-terms.md)
- [Comprendre les codes d’erreur](api-error-codes.md)
