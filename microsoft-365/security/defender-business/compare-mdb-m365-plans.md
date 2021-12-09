---
title: Comparer Microsoft Defender entreprise à d’autres plans Microsoft 365 de gestion
description: Comprendre les différences entre Defender pour Entreprise et Defender pour le point de terminaison. Le fait de connaître les informations incluses dans chaque plan peut vous aider à prendre une décision éclairée pour votre entreprise.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: reference
ms.date: 12/08/2021
ms.prod: m365-security
ms.technology: mdb
localization_priority: Normal
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: ad945c9e1c3ab5d680aa873d3447527e13cb4979
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/09/2021
ms.locfileid: "61375262"
---
# <a name="compare-microsoft-defender-for-business-to-microsoft-365-business-premium"></a>Comparer Microsoft Defender entreprise à Microsoft 365 Business Premium

> [!IMPORTANT]
> Certaines informations de cet article concernent les produits/services pré-publiés qui peuvent être considérablement modifiés avant leur publication commerciale. Microsoft n’offre aucune garantie, expressément ou implicite, pour les informations fournies ici. Cet article inclut des liens vers du contenu en ligne qui peut décrire certaines fonctionnalités qui ne sont pas incluses dans Microsoft Defender pour Entreprises (prévisualisation).

Microsoft offre un large éventail de solutions et de services cloud, y compris plusieurs plans pour les petites et moyennes entreprises. Par exemple, [Microsoft 365 Business Premium](../../business/microsoft-365-business-overview.md) inclut des fonctionnalités de sécurité et de gestion des appareils, ainsi que des fonctionnalités de productivité, telles que Office applications. 

**Utilisez cet article pour**:

- [Comparer Microsoft Defender entreprise (prévisualisation) à Microsoft 365 Business Premium](#compare-security-features-in-microsoft-defender-for-business-to-microsoft-365-business-premium)
- [Comparer Defender pour Entreprise à Microsoft Defender pour les offres d’entreprise de point de terminaison](#compare-microsoft-defender-for-business-to-microsoft-defender-for-endpoint-plans-1-and-2)


**Vous n’avez pas besoin d’un abonnement Microsoft 365 pour acheter et utiliser Microsoft Defender pour les entreprises.** Microsoft Defender pour les entreprises est une solution de sécurité autonome pour les petites et moyennes entreprises. Si vous avez déjà un autre abonnement (par exemple, Microsoft 365 Business Basic ou Standard), envisagez d’ajouter Microsoft Defender pour les entreprises pour obtenir des fonctionnalités de protection contre les menaces supplémentaires. 

> [!TIP]
> Si votre entreprise est une petite ou moyenne entreprise (300 utilisateurs ou moins) et que vous souhaitez vous inscrire au programme d’aperçu de Microsoft Defender entreprise, visitez [https://aka.ms/MDB-Preview](https://aka.ms/MDB-Preview) . Pour plus d’informations, [voir Obtenir Microsoft Defender pour Entreprise.](get-defender-business.md)

## <a name="compare-security-features-in-microsoft-defender-for-business-to-microsoft-365-business-premium"></a>Comparer les fonctionnalités de sécurité de Microsoft Defender pour les Microsoft 365 Business Premium

> [!NOTE]
> Cet article est destiné à fournir une vue d’ensemble des fonctionnalités de protection contre les menaces incluses dans Microsoft Defender pour Entreprises et Microsoft 365 Business Premium. Cet article n’est pas destiné à servir de description de service ou de document de contrat de licence. Pour plus d’informations, [voir Microsoft 365 licences pour la conformité & sécurité](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance)

Le tableau suivant compare les fonctionnalités et fonctionnalités de sécurité de Defender for Business Microsoft 365 Business Premium tandis que Defender entreprise est en prévisualisation. Lorsque Defender entreprise devient généralement disponible, il est inclus dans Microsoft 365 Business Premium. <br/><br/>

| Fonctionnalité/fonctionnalité | [Microsoft Defender pour les entreprises](mdb-overview.md) | [Microsoft 365 Business Premium](../../business/microsoft-365-business-overview.md) |
|:---|:---|:---|
| Protection de la messagerie | Oui[(analyse du courrier](../defender-endpoint/configure-advanced-scan-types-microsoft-defender-antivirus.md) électronique Antivirus Microsoft Defender) | Oui ([Exchange Online Protection](../office-365-security/exchange-online-protection-overview.md)) |
| Protection contre lepam | Oui (pour les appareils) | Oui (pour Microsoft 365 de courrier électronique, tels que les messages et les pièces jointes) |
| Protection anti-programme malveillant | Oui (pour les appareils) | Oui (pour Microsoft 365 de courrier électronique, tels que les messages et les pièces jointes) |
| [Protection de nouvelle génération](../defender-endpoint/microsoft-defender-antivirus-in-windows-10.md) <br/> (protection antivirus et anti-programme malveillant) | Oui (Antivirus Microsoft Defender est inclus dans Windows 10 et ultérieures)  | Oui (Antivirus Microsoft Defender est inclus dans Windows 10 et ultérieures) |
| [Réduction de la surface d’attaque](../defender-endpoint/overview-attack-surface-reduction.md) <br/>(règles de réduction de la surface d’attaque et autres protections)  | Oui (règles de réduction de la surface d’attaque intégrées Windows 10 et ultérieures, ainsi que les fonctionnalités gérées de manière centralisée) | Oui (règles de réduction de la surface d’attaque intégrées Windows 10 et ultérieures) |
| [Détection et réponse du point de terminaison](../defender-endpoint/overview-endpoint-detection-response.md) | Oui. Inclus : <br/>- Détection basée sur le comportement <br/>- Actions de réponse manuelles <br/>- Réponse en direct   | Non |
| [Examen et réponse automatisés](../defender-endpoint/automated-investigations.md) | Oui | Non |
| [Gestion des menaces et des vulnérabilités](../defender-endpoint/tvm-dashboard-insights.md) | Oui | Non |
| Gestion centralisée et rapports | Oui. Vous pouvez intégrer Windows appareils clients et les gérer dans le portail Microsoft 365 Defender ( ), ou choisir de gérer les appareils [https://security.microsoft.com](https://security.microsoft.com) dans Microsoft Endpoint Manager ( [https://endpoint.microsoft.com](https://endpoint.microsoft.com) ). | Oui. Vous pouvez gérer Windows clients dans le Centre d'administration Microsoft 365 ( [https://admin.microsoft.com](https://admin.microsoft.com) ). Les appareils doivent être intégrés dans Microsoft Endpoint Manager ( [https://endpoint.microsoft.com](https://endpoint.microsoft.com) ). |
| [API](../defender-endpoint/apis-intro.md) <br/>(vous permet d’intégrer des applications personnalisées ou des solutions de création de rapports)  | Oui | Oui |



## <a name="compare-microsoft-defender-for-business-to-microsoft-defender-for-endpoint-plans-1-and-2"></a>Comparer Microsoft Defender entreprise à Microsoft Defender pour les plans de point de terminaison 1 et 2

Defender pour les entreprises apporte des fonctionnalités de qualité professionnelle de Defender for Endpoint aux petites et moyennes entreprises. Le tableau suivant compare les fonctionnalités de sécurité de Defender pour Entreprise à Microsoft Defender pour les plans de point de terminaison 1 et 2. <br/><br/>

| Fonctionnalité/fonctionnalité | [Defender pour les entreprises](mdb-overview.md) | [Defender pour Endpoint Plan 1](../defender-endpoint/defender-endpoint-plan-1.md) | [Defender for Endpoint Plan 2](../defender-endpoint/microsoft-defender-endpoint.md) |
|:---|:---|:---|
| [Gestion centralisée](../defender-endpoint/manage-atp-post-migration.md) <sup>[[1](#fn1)]</sup> | Oui | Oui | Oui |
| [Configuration simplifiée du client](mdb-simplified-configuration.md) | Oui | Non | Non |
| [Gestion des menaces et des vulnérabilités](../defender-endpoint/next-gen-threat-and-vuln-mgt.md) | Oui | Non | Oui |
| [Fonctionnalités de réduction de la surface d’attaque](../defender-endpoint/overview-attack-surface-reduction.md) | Oui | Oui | Oui |
| [Protection de nouvelle génération](../defender-endpoint/next-generation-protection.md) | Oui | Oui | Oui |
| [Détection et réponse du point de terminaison](../defender-endpoint/overview-endpoint-detection-response.md) | Oui <sup>[[2](#fn2)]</sup> | Non | Oui |
| [Examen et réponse automatisés](../defender-endpoint/automated-investigations.md) | Oui <sup>[[2](#fn2)]</sup> | Non | Oui |
| [Recherche de menaces](../defender-endpoint/advanced-hunting-overview.md) et rétention des données pendant 6 mois | Non | Non | Oui |
| [Analyses de menaces](../defender-endpoint/threat-analytics.md) | Oui <sup>[[2](#fn2)]</sup> | Non | Oui |
| [Prise en charge sur plusieurs plateformes](../defender-endpoint/minimum-requirements.md) <br/>(Windows, macOS, iOS et android OS) | Oui <sup>[[3](#fn3)]</sup> | Oui | Oui |
| [Spécialistes des menaces Microsoft](../defender-endpoint/microsoft-threat-experts.md) | Non | Non | Oui |
| API partenaires | Oui | Oui | Oui |
| [Microsoft 365 Lighthouse’intégration](../../lighthouse/m365-lighthouse-overview.md) <br/>(Pour afficher les incidents de sécurité entre les clients) | Oui | Non | Non |

(<a id="fn1">1</a>) Intégrer et gérer les appareils dans le portail Microsoft 365 Defender ( ) ou avec un autre outil, tel que [https://security.microsoft.com](https://security.microsoft.com) Microsoft Endpoint Manager ( [https://endpoint.microsoft.com](https://endpoint.microsoft.com) ).

(<a id="fn2">2</a>) Ces fonctionnalités sont optimisées pour les petites et moyennes entreprises.

(<a id="fn3">3</a>) Pendant le programme d’aperçu, les Windows clients sont pris en charge dans le portail Microsoft 365 Defender ( [https://security.microsoft.com](https://security.microsoft.com) ).

## <a name="next-steps"></a>Prochaines étapes

- [Voir les conditions requises pour Microsoft Defender pour les entreprises](mdb-requirements.md)

- [Découvrez comment installer et configurer Microsoft Defender pour les entreprises](mdb-setup-configuration.md) 