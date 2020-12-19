---
title: Licence et conditions d’utilisation de l’API Microsoft 365 Defender
description: Description de la licence et des conditions d’utilisation des API dans Microsoft 365 Defender
keywords: API, API, licence, termes, API, légal, notifications, code de conduite
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
ms.openlocfilehash: d9b3c48e4b9e89ef7648086b05c9fdd9f078f51e
ms.sourcegitcommit: d6b1da2e12d55f69e4353289e90f5ae2f60066d0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/19/2020
ms.locfileid: "49719297"
---
# <a name="microsoft-365-defender-apis-license-and-terms-of-use"></a>Licence et conditions d’utilisation de l’API Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**

- Microsoft 365 Defender

> [!IMPORTANT]
> Certaines informations se rapportent à des produits précommercialisés susceptibles d’être modifiés de manière substantielle avant leur publication commerciale. Microsoft makes no warranties, express or implied, with respect to the information provided here.

## <a name="official-terms"></a>Termes officiels

Les API Microsoft 365 Defender sont régies par la [licence et les conditions d’utilisation de l’API Microsoft](https://docs.microsoft.com/legal/microsoft-apis/terms-of-use).

## <a name="legal-notices"></a>Mentions légales

Microsoft et tous les contributeurs vous accordent une licence à la documentation Microsoft et à d’autres contenus dans [ce référentiel](https://github.com/MicrosoftDocs/microsoft-365-docs), sous la licence publique internationale 4,0 de Creative. Pour plus d’informations, reportez-vous au fichier de [licence](https://github.com/MicrosoftDocs/microsoft-365-docs/blob/public/LICENSE) .

Microsoft, Windows, Microsoft Azure et/ou d’autres produits et services Microsoft mentionnés dans la documentation peuvent être des marques ou des marques déposées de Microsoft aux États-Unis et/ou dans d’autres pays.

Les licences pour ce projet ne vous permettent pas de vous accorder des droits d’utilisation des noms, logos ou marques de Microsoft. Les directives générales de la marque Microsoft sont disponibles dans les [marques Microsoft](https://go.microsoft.com/fwlink/?LinkID=254653).

Les informations de confidentialité sont disponibles auprès de [Microsoft](https://privacy.microsoft.com).

Microsoft et tous les contributeurs réservent tous les autres droits, en vertu de leurs droits d’auteur, brevets ou marques de brevet respectifs, par implication, estoppel ou autre.

## <a name="other-restrictions"></a>Autres restrictions

L’API de chasse avancée présente certaines [limitations](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/run-advanced-query-api#limitations) quant au nombre de résultats renvoyés et aux données qui peuvent être interrogées.

1. Vous ne pouvez demander des données qu’au cours des 30 derniers jours.
1. Les résultats incluent un maximum de 100 000 lignes.

### <a name="quotas-and-resource-allocation"></a>Quotas et allocation des ressources

Les API Microsoft 365 Defender ont des seuils de limitation.

- **API des incidents**: jusqu’à 50 appels par minute ou 1500 appels par heure.
- **API de chasse avancée**: jusqu’à 15 appels par minute, 10 minutes de temps d’exécution par heure et 4 heures de temps d’exécution par jour.

Le code d’état de réponse HTTP indiquant la limitation est `429` .

Si votre requête a été limitée, le corps de la réponse indiquera le moment où vous pouvez relancer les demandes.

## <a name="related-articles"></a>Articles connexes

- [Vue d’ensemble des API Microsoft 365 Defender](api-overview.md)
- [API Microsoft 365 Defender prises en charge](api-supported.md)
- [Accéder aux API Microsoft 365 Defender](api-access.md)
