---
title: Comparer les plans de sécurité des points de terminaison Microsoft
description: Comparez les plans de sécurité des points de terminaison Microsoft, tels que Defender pour point de terminaison Plan 1 et Defender pour point de terminaison Plan 2. Découvrez les différences entre les plans et sélectionnez le plan qui répond aux besoins de votre organisation.
keywords: Defender pour point de terminaison, protection avancée contre les menaces, protection contre les points de terminaison, sécurité des points de terminaison, sécurité des appareils, cybersécurité
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: ITPro
ms.topic: overview
ms.date: 07/25/2022
ms.service: microsoft-365-security
ms.subservice: mde
ms.localizationpriority: medium
ms.reviewer: shlomi, efratka
f1.keywords: NOCSH
ms.collection:
- M365-security-compliance
- m365initiative-defender-endpoint
ms.openlocfilehash: 3340ec1b97cde08ed0aa7b3e74df3d0157d65474
ms.sourcegitcommit: 10e6abe740e27000e223378eb17d657a47555fa8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2022
ms.locfileid: "67481325"
---
# <a name="compare-microsoft-endpoint-security-plans"></a>Comparer les plans de sécurité des points de terminaison Microsoft

Les plans de sécurité des points de terminaison Microsoft, tels que Microsoft Defender pour point de terminaison et Microsoft 365 Defender, ont été conçus pour aider les organisations d’entreprise à prévenir, détecter, examiner et répondre aux menaces avancées. Microsoft Defender pour entreprises et Microsoft 365 Business Premium offrent des fonctionnalités similaires, optimisées pour les petites et moyennes entreprises. Ces plans fournissent une protection avancée contre les menaces avec la protection antivirus et anti-programme malveillant, l’atténuation des ransomwares, et bien plus encore, ainsi que la gestion centralisée et la création de rapports. 

Cet article vous aide à clarifier ce qui est inclus dans les plans suivants : 

- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [module complémentaire Gestion des vulnérabilités Microsoft Defender](../defender-vulnerability-management/index.yml)
- [Microsoft Defender pour entreprises](../defender-business/mdb-overview.md) et [Microsoft 365 Business Premium](../../business-premium/index.md)

> [!IMPORTANT]
> Cet article fournit un résumé des fonctionnalités de protection contre les menaces dans les plans de sécurité des points de terminaison Microsoft ; toutefois, il ne s’agit pas d’une description de service ou d’un document de contrat de licence. Pour plus d’informations, consultez les [instructions relatives aux licences Microsoft 365 pour la sécurité & la conformité](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

## <a name="compare-microsoft-endpoint-security-plans"></a>Comparer les plans de sécurité des points de terminaison Microsoft

Le tableau suivant récapitule ce qui est inclus dans les plans de sécurité des points de terminaison Microsoft.

| Planification | Inclus |
|:---|:---|
| [Defender pour point de terminaison Plan 1](defender-endpoint-plan-1.md) <sup>[[1](#fn1)]</sup> | <ul><li>[Protection de nouvelle génération](defender-endpoint-plan-1.md#next-generation-protection) (inclut le logiciel anti-programme malveillant et l’antivirus)</li><li>[Réduction de la surface d’attaque](defender-endpoint-plan-1.md#attack-surface-reduction)</li><li> [Actions de réponse manuelle](defender-endpoint-plan-1.md#manual-response-actions)</li><li>[Gestion centralisée](defender-endpoint-plan-1.md#centralized-management)</li><li>[Rapports de sécurité](defender-endpoint-plan-1.md#reporting)</li><li>[API](defender-endpoint-plan-1.md#apis)</li><li>[Prise en charge des appareils Windows 10, iOS, Android os et macOS](defender-endpoint-plan-1.md#cross-platform-support)</li></ul>|
| [Defender pour point de terminaison Plan 2](microsoft-defender-endpoint.md) <sup>[[2](#fn2)]</sup> | Toutes les fonctionnalités de Defender pour point de terminaison Plan 1, ainsi que :<ul><li>[Découverte d’appareils](device-discovery.md)</li><li>[Inventaire des appareils](machines-view-overview.md)</li><li>[Fonctionnalités de gestion des vulnérabilités Core Defender](../defender-vulnerability-management/defender-vulnerability-management-capabilities.md)</li><li>[Analyse des menaces](threat-analytics.md)</li><li>[Examen et réponse automatisés](automated-investigations.md)</li><li>[Repérage avancé](advanced-hunting-overview.md)</li><li>[Détection et réponse du point de terminaison](overview-endpoint-detection-response.md)</li><li>[Spécialistes des menaces Microsoft](microsoft-threat-experts.md)</li><li>Prise en charge des [plateformes Windows](configure-endpoints.md) (client et serveur) et [non Windows](configure-endpoints-non-windows.md) (macOS, iOS, Android et Linux)</li></ul> |
| [Module complémentaire Gestion des vulnérabilités Defender](../defender-vulnerability-management/defender-vulnerability-management-capabilities.md) | Autres fonctionnalités de gestion des vulnérabilités defender pour Defender pour le plan de point de terminaison 2 :<ul><li>[Évaluation des bases de référence de sécurité](../defender-vulnerability-management/tvm-security-baselines.md)</li><li>[Bloquer les applications vulnérables](../defender-vulnerability-management/tvm-block-vuln-apps.md)</li><li>[Extensions de navigateur](../defender-vulnerability-management/tvm-browser-extensions.md)</li><li>[Évaluation des certificats numériques](../defender-vulnerability-management/tvm-certificate-inventory.md)</li><li>[Analyse du partage réseau](../defender-vulnerability-management/tvm-network-share-assessment.md)</li><li>Prise en charge des [plateformes Windows](configure-endpoints.md) (client et serveur) et [non Windows](configure-endpoints-non-windows.md) (macOS, iOS, Android et Linux)</li></ul> |
| [Defender pour Entreprises](../defender-business/mdb-overview.md) <sup>[[3](#fn3)]</sup>  | [Les services optimisés pour les petites et moyennes entreprises](../defender-business/compare-mdb-m365-plans.md) sont les suivants : <ul><li>protection Email</li><li>Protection anti-courrier indésirable</li><li>Protection anti-programme malveillant</li><li>Protection de nouvelle génération</li><li>Réduction de la surface d'attaque</li><li>Détection et réponse du point de terminaison</li><li>Enquêtes et réponses automatisées </li><li>Gestion des vulnérabilités</li><li>Rapports centralisés</li><li>API (pour l’intégration avec des applications personnalisées ou des solutions de création de rapports)</li><li>[Intégration à Microsoft 365 Lighthouse](../defender-business/mdb-lighthouse-integration.md)</li></ul> |

(<a id="fn1">1</a>) Microsoft Defender pour point de terminaison plan 1 est disponible en tant qu’abonnement autonome pour les clients commerciaux et éducatifs. Il est également inclus dans Microsoft 365 E3/A3.

(<a id="fn2">2</a>) Microsoft Defender pour point de terminaison plan 2, précédemment appelé Microsoft Defender pour point de terminaison, est disponible en tant qu’abonnement autonome. Il est également inclus dans les plans suivants :

- Windows 11 Entreprise E5/A5
- Windows 10 Entreprise E5/A5
- Microsoft 365 E5/A5/G5 (qui inclut Windows 10 ou Windows 11 Entreprise E5)
- sécurité Microsoft 365 E5/A5/G5/F5
- Conformité & de sécurité Microsoft 365 F5

(<a id="fn3">3</a>) Microsoft Defender pour entreprises est disponible en tant qu’abonnement autonome pour les petites et moyennes entreprises. Il est également inclus dans le cadre de [Microsoft 365 Business Premium](/microsoft-365/business-premium). Ces plans offrent des fonctionnalités de sécurité avancées avec une configuration et une configuration simplifiées. Voir [Comparer les Microsoft Defender pour entreprises à Microsoft 365 Business Premium](/microsoft-365/security/defender-business/compare-mdb-m365-plans#compare-microsoft-defender-for-business-to-microsoft-365-business-premium).

## <a name="options-for-onboarding-servers"></a>Options d’intégration des serveurs

Defender pour point de terminaison Plan 1 et 2 (autonome), Defender entreprise (autonome) et Microsoft 365 Business Premium n’incluent pas de licences serveur. Pour intégrer des serveurs, choisissez parmi les options suivantes :

- **Microsoft Defender pour serveurs plan 1 ou Plan 2** dans le cadre de l’offre [Defender pour le cloud](/azure/defender-for-cloud/defender-for-cloud-introduction) . Pour en savoir plus. Consultez [vue d’ensemble de Microsoft Defender pour serveurs](/azure/defender-for-cloud/defender-for-servers-introduction).
- **Microsoft Defender pour entreprises serveurs (préversion)** pour les petites et moyennes entreprises. Consultez [Comment obtenir des serveurs Microsoft Defender entreprise (préversion).](../defender-business/get-defender-business-servers.md)

## <a name="mixed-licensing-scenarios"></a>Scénarios de licence mixte

Supposons que votre organisation utilise une combinaison d’abonnements de sécurité de point de terminaison Microsoft, tels que Defender pour point de terminaison Plan 1 et Defender pour point de terminaison Plan 2. **Actuellement, l’abonnement de sécurité de point de terminaison Microsoft le plus fonctionnel définit l’expérience de votre locataire**. Dans cet exemple, votre expérience client serait Defender pour point de terminaison Plan 2 pour tous les utilisateurs.

Toutefois, **vous pouvez contacter le support technique et demander un remplacement pour votre expérience client**. Autrement dit, vous pouvez demander un remplacement pour conserver l’expérience Defender pour point de terminaison Plan 1 pour tous les utilisateurs. 

- Pour plus d’informations sur les licences et les termes du produit, consultez [Licences et termes du produit pour les abonnements Microsoft 365](https://www.microsoft.com/licensing/terms/productoffering/Microsoft365/MCA).
- Pour plus d’informations sur la façon de contacter le support technique, consultez [Contact Microsoft Defender pour point de terminaison support](contact-support.md).

> [!TIP]
> Si votre organisation est une petite ou moyenne entreprise, consultez les articles suivants :
> - [Qu’est-ce que Microsoft Defender pour entreprises ?](../defender-business/mdb-overview.md)
> - [Comparez les fonctionnalités de sécurité dans les plans de Microsoft 365 pour les petites et moyennes entreprises](../defender-business/compare-mdb-m365-plans.md).

## <a name="start-a-trial"></a>Démarrer un essai

- Pour essayer Defender pour point de terminaison, accédez à la [page d’inscription à la version d’évaluation de Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?LinkID=2168109).
- Pour essayer le module complémentaire Gestion des vulnérabilités Microsoft Defender pour Defender pour point de terminaison Plan 2, visitez [https://aka.ms/AddonPreviewTrial](https://aka.ms/AddonPreviewTrial). 

## <a name="see-also"></a>Voir aussi

- [Prise en main de Microsoft Security (offres d’évaluation)](https://www.microsoft.com/security/business/get-started/start-free-trial)
- [Microsoft Defender pour point de terminaison](microsoft-defender-endpoint.md)
- [Microsoft Defender pour entreprises](../defender-business/mdb-overview.md) (protection des points de terminaison pour les petites et moyennes entreprises)
