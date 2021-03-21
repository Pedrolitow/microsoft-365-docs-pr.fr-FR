---
title: Licence et conditions d’utilisation des API Microsoft 365 Defender
description: Description de la licence et des conditions d’utilisation des API dans Microsoft 365 Defender
keywords: api, api, licence, termes, api, juridique, avis, code de conduite
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
ms.openlocfilehash: 06926bc58f29fcf80d09819545e2455813f27a5f
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50922161"
---
# <a name="microsoft-365-defender-apis-license-and-terms-of-use"></a>Licence et conditions d’utilisation des API Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**

- Microsoft 365 Defender

> [!IMPORTANT]
> Certaines informations concernent des produits pré-publiés qui peuvent être considérablement modifiés avant leur commercialisation. Microsoft makes no warranties, express or implied, with respect to the information provided here.

## <a name="official-terms"></a>Termes officiels

Les API Microsoft 365 Defender sont régies par la licence et les [conditions d’utilisation](/legal/microsoft-apis/terms-of-use)des API Microsoft.

## <a name="legal-notices"></a>Avis juridiques

Microsoft et tous les collaborateurs vous accordent une licence pour la documentation Microsoft et d’autres contenus dans ce [référentiel,](https://github.com/MicrosoftDocs/microsoft-365-docs)sous la licence publique internationale Creative Commons Attribution 4.0. Pour plus d’informations, voir [le fichier LICENSE.](https://github.com/MicrosoftDocs/microsoft-365-docs/blob/public/LICENSE)

Microsoft, Windows, Microsoft Azure et/ou d’autres produits et services Microsoft référencés dans la documentation peuvent être des marques ou des marques déposées de Microsoft aux États-Unis et/ou dans d’autres pays.

Les licences pour ce projet ne vous accordent pas le droit d’utiliser des noms, des logos ou des marques Microsoft. Microsoft’s general trademark guidelines can be found at [Microsoft Trademarks](https://go.microsoft.com/fwlink/?LinkID=254653).

Les informations de confidentialité sont disponibles sur le site [Confidentialité de Microsoft.](https://privacy.microsoft.com)

Microsoft et tous les collaborateurs se réservent tous les autres droits, que ce soit sous leurs droits d’auteur, brevets ou marques respectives, que ce soit par implication, par défaut ou autrement.

## <a name="other-restrictions"></a>Autres restrictions

L’API de recherche avancée présente certaines limitations sur le nombre de résultats [renvoyés](/windows/security/threat-protection/microsoft-defender-atp/run-advanced-query-api#limitations) et sur les données qui peuvent être interrogés.

1. Vous ne pouvez interroger que les données des 30 derniers jours.
1. Les résultats incluent un maximum de 100 000 lignes.

### <a name="quotas-and-resource-allocation"></a>Quotas et allocation de ressources

Les API Microsoft 365 Defender ont des seuils de limitation.

- **API Incidents :** jusqu’à 50 appels par minute ou 1 500 appels par heure.
- **API de recherche avancée**: jusqu’à 15 appels par minute, 10 minutes d’exécution par heure et 4 heures d’exécution par jour.

Le code d’état de la réponse HTTP indiquant la limitation est `429` .

Si votre demande a été limitée, le corps de la réponse indique le moment où vous pouvez recommencer à effectuer des demandes.

## <a name="related-articles"></a>Articles connexes

- [Présentation des API Microsoft 365 Defender](api-overview.md)
- [API Microsoft 365 Defender prises en charge](api-supported.md)
- [Accéder aux API Microsoft 365 Defender](api-access.md)