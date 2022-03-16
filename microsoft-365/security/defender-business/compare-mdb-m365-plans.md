---
title: Comparer les fonctionnalités de sécurité Microsoft 365 plans pour les petites et moyennes entreprises
description: Comprendre les différences entre Defender pour Entreprise et Defender pour le point de terminaison. Le fait de connaître les informations incluses dans chaque plan peut vous aider à prendre une décision éclairée pour votre entreprise.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: reference
ms.date: 03/15/2022
ms.prod: m365-security
ms.technology: mdb
localization_priority: Normal
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- m365-initiative-defender-business
- m365-security-compliance
ms.openlocfilehash: edad91bde18b4bf9a86e0ab02ffc28df675f4c10
ms.sourcegitcommit: a216617d6ff27fe7d3089a047fbeaac5d72fd25c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2022
ms.locfileid: "63512501"
---
# <a name="compare-microsoft-defender-for-business-to-microsoft-365-business-premium"></a>Comparer Microsoft Defender entreprise à Microsoft 365 Business Premium

> [!IMPORTANT]
> Microsoft Defender for Business est en déploiement [Microsoft 365 Business Premium clients,](../../business-premium/index.md) à partir du 1er mars 2022. Defender for Business as a standalone subscription is in preview, and will roll out gradually to customers and IT Partners who [sign-up here](https://aka.ms/mdb-preview) to request it. La [prévisualisation inclut un ensemble initial de scénarios](mdb-tutorials.md#try-these-preview-scenarios) et nous ajouterons régulièrement des fonctionnalités.
> 
> Certaines informations de cet article concernent les produits/services pré-publiés qui peuvent être considérablement modifiés avant leur publication commerciale. Microsoft n’offre aucune garantie, expressément ou implicite, pour les informations fournies ici. 

Microsoft offre un large éventail de solutions et de services cloud, notamment plusieurs plans pour les petites et moyennes entreprises. Par exemple, [Microsoft 365 Business Premium](../../business/microsoft-365-business-overview.md) inclut des fonctionnalités de sécurité et de gestion des appareils, ainsi que des fonctionnalités de productivité, telles que Office applications. Cet article est conçu pour clarifier les fonctionnalités de sécurité, telles que la protection des appareils, qui sont incluses dans Microsoft 365 Business Premium, Microsoft Defender pour Entreprise et Microsoft Defender pour le point de terminaison.

Microsoft Defender pour Entreprises est disponible sous la mesure d’une offre autonome ou dans le cadre d’Microsoft 365 Business Premium (à partir du 1er mars 2022).

>
> **Avez-vous un peu de temps ?**
> Veuillez consulter notre <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">courte enquête sur Microsoft Defender entreprise</a>. Vos commentaires sont les bienvenus.
>

**Utilisez cet article pour** :

- [Comparer Microsoft Defender entreprise (autonome) à Microsoft 365 Business Premium](#compare-security-features-in-microsoft-defender-for-business-to-microsoft-365-business-premium)
- [Comparer Defender pour Entreprise (autonome) à Microsoft Defender pour les offres d’entreprise de point de terminaison](#compare-microsoft-defender-for-business-to-microsoft-defender-for-endpoint-plans-1-and-2)

**Vous n’avez pas besoin d’un abonnement Microsoft 365 pour acheter et utiliser Microsoft Defender pour les entreprises.** Microsoft Defender pour Entreprises est inclus dans Microsoft 365 Business Premium, et il est disponible en tant que solution de sécurité autonome pour les petites et moyennes entreprises. Si vous avez déjà Microsoft 365 Business Basic standard, envisagez d’ajouter la mise à niveau vers Microsoft 365 Business Premium ou l’ajout de Microsoft Defender pour les entreprises pour obtenir davantage de fonctionnalités de protection contre les menaces. 

## <a name="compare-security-features-in-microsoft-defender-for-business-to-microsoft-365-business-premium"></a>Comparer les fonctionnalités de sécurité de Microsoft Defender pour les entreprises à Microsoft 365 Business Premium

> [!NOTE]
> Cet article est destiné à fournir une vue d’ensemble des fonctionnalités de protection contre les menaces incluses dans Microsoft Defender entreprise (en tant que plan autonome) et Microsoft 365 Business Premium (qui inclut Defender for Business). Cet article n’est pas destiné à servir de description de service ou de document de contrat de licence. Pour plus d’informations, [voir Microsoft 365 licences pour la conformité & sécurité](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance)

**À compter du 1er mars 2022, Defender entreprise commence à se déployer dans le cadre de Microsoft 365 Business Premium. Defender for Business as a standalone offering is still in preview.**

Le tableau suivant compare les fonctionnalités de sécurité et les fonctionnalités de Defender for Business (autonome) à Microsoft 365 Business Premium. 

 <br/><br/>

| Fonctionnalité/fonctionnalité | [Microsoft Defender pour les PME](mdb-overview.md)<br/>(autonome ; actuellement en prévisualisation) | [Microsoft 365 Business Premium](../../business/microsoft-365-business-overview.md)<br/>(inclut Defender pour les entreprises) |
|:---|:---|:---|
| Protection de la messagerie | Oui <br/>- [Analyse du courrier électronique avec Antivirus Microsoft Defender](../defender-endpoint/configure-advanced-scan-types-microsoft-defender-antivirus.md) | Oui <br/>- [Exchange Online Protection](../office-365-security/exchange-online-protection-overview.md) <br/>- [Analyse du courrier électronique avec Antivirus Microsoft Defender](../defender-endpoint/configure-advanced-scan-types-microsoft-defender-antivirus.md) |
| Protection contre lepam | Oui <br/>- Pour les appareils | Oui <br/>- Pour les appareils<br/>- Pour Microsoft 365 de courrier électronique, tel que des messages et des pièces jointes |
| Protection anti-programme malveillant | Oui<br/>- Pour les appareils | Oui <br/>- Pour les appareils<br/>- Pour Microsoft 365 de courrier électronique, tel que des messages et des pièces jointes |
| [Protection de nouvelle génération](../defender-endpoint/microsoft-defender-antivirus-in-windows-10.md) <br/> (protection antivirus et anti-programme malveillant) | Oui<br/>- Antivirus Microsoft Defender est inclus dans Windows 10 et ultérieures  | Oui <br/>- Antivirus Microsoft Defender est inclus dans Windows 10 et ultérieures<br/>- Stratégies de protection nouvelle génération pour les appareils intégrés |
| [Réduction de la surface d’attaque](../defender-endpoint/overview-attack-surface-reduction.md) <br/>(Règles de asr dans Windows 10 ou ultérieure et protection pare-feu) | Oui  | Oui  |
| [Détection et réponse du point de terminaison](../defender-endpoint/overview-endpoint-detection-response.md) <br/>(détection basée sur le comportement et actions de réponse manuelle) | Oui | Oui |
| [Examen et réponse automatisés](../defender-endpoint/automated-investigations.md) | Oui | Oui |
| [Gestion des menaces et des vulnérabilités](../defender-endpoint/tvm-dashboard-insights.md) | Oui | Oui |
| Gestion centralisée et rapports  | Oui  | Oui  |
| [API](../defender-endpoint/apis-intro.md) <br/>(pour l’intégration avec des applications personnalisées ou des solutions de création de rapports)  | Oui | Oui |


## <a name="compare-microsoft-defender-for-business-to-microsoft-defender-for-endpoint-plans-1-and-2"></a>Comparer Microsoft Defender entreprise à Microsoft Defender pour les plans de point de terminaison 1 et 2

Defender pour les entreprises apporte des fonctionnalités de qualité professionnelle de Defender for Endpoint aux petites et moyennes entreprises. 

Le tableau suivant compare les fonctionnalités de sécurité de Defender pour Entreprise à Microsoft Defender pour les plans de point de terminaison 1 et 2. <br/><br/>

| Fonctionnalité/fonctionnalité | [Defender pour les entreprises](mdb-overview.md) (prévisualisation) | [Defender pour Endpoint Plan 1](../defender-endpoint/defender-endpoint-plan-1.md) | [Defender for Endpoint Plan 2](../defender-endpoint/microsoft-defender-endpoint.md) |
|:---|:---|:---|
| [Gestion centralisée](../defender-endpoint/manage-atp-post-migration.md) <sup>[[1](#fn1)]</sup> | Oui | Oui | Oui |
| [Configuration simplifiée du client](mdb-simplified-configuration.md) | Oui | Non | Non |
| [Gestion des menaces et des vulnérabilités](../defender-endpoint/next-gen-threat-and-vuln-mgt.md) | Oui | Non | Oui |
| [Fonctionnalités de réduction de la surface d’attaque](../defender-endpoint/overview-attack-surface-reduction.md) | Oui | Oui | Oui |
| [Protection de nouvelle génération](../defender-endpoint/next-generation-protection.md) | Oui | Oui | Oui |
| [Détection et réponse du point de terminaison](../defender-endpoint/overview-endpoint-detection-response.md) | Oui <sup>[[2](#fn2)]</sup> | Non | Oui |
| [Examen et réponse automatisés](../defender-endpoint/automated-investigations.md) | Oui <sup>[[2](#fn2)]</sup> | Non | Oui |
| [Recherche de menaces](../defender-endpoint/advanced-hunting-overview.md) et rétention des données pendant six mois | Non | Non | Oui |
| [Analyses de menaces](../defender-endpoint/threat-analytics.md) | Oui <sup>[[2](#fn2)]</sup> | Non | Oui |
| [Prise en charge sur plusieurs plateformes](../defender-endpoint/minimum-requirements.md) <br/>(Windows, macOS, iOS et android OS) | Oui <sup>[[3](#fn3)]</sup> | Oui | Oui |
| [Spécialistes des menaces Microsoft](../defender-endpoint/microsoft-threat-experts.md) | Non | Non | Oui |
| API partenaires | Oui | Oui | Oui |
| [Microsoft 365 Lighthouse’intégration](../../lighthouse/m365-lighthouse-overview.md) <br/>(Pour afficher les incidents de sécurité entre les clients) | Oui | Non | Non |

(<a id="fn1">1</a>) Intégrer et gérer les appareils dans le portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) ou avec un autre outil, tel que Microsoft Endpoint Manager ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)).

(<a id="fn2">2</a>) Ces fonctionnalités sont optimisées pour les petites et moyennes entreprises.

(<a id="fn3">3</a>) Pendant le programme d’aperçu, les Windows clients sont pris en charge dans le portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)).

## <a name="next-steps"></a>Prochaines étapes

- [Voir les conditions requises pour Microsoft Defender pour les entreprises](mdb-requirements.md)

- [Obtenir Microsoft Defender pour les entreprises](get-defender-business.md)

- [Découvrez comment installer et configurer Microsoft Defender pour les entreprises](mdb-setup-configuration.md) 
