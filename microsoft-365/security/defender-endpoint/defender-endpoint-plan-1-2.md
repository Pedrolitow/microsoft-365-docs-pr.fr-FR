---
title: Comparer Microsoft Defender pour point de terminaison plans
description: Comparez Defender pour point de terminaison Plan 1 à Plan 2. Découvrez les différences entre les plans et sélectionnez le plan qui répond aux besoins de votre organisation.
keywords: Defender pour point de terminaison, protection avancée contre les menaces, protection contre les points de terminaison
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: ITPro
ms.topic: overview
ms.date: 06/17/2022
ms.prod: m365-security
ms.technology: mdep1
ms.localizationpriority: medium
ms.reviewer: shlomi, efratka
f1.keywords: NOCSH
ms.collection:
- M365-security-compliance
- m365initiative-defender-endpoint
ms.openlocfilehash: e1cf2647ac8308d30b82e69cbb288fde330fdc5a
ms.sourcegitcommit: 0c87abc17fbfe8aa43d61510101acdad0d491cd2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/05/2022
ms.locfileid: "66612192"
---
# <a name="compare-microsoft-defender-for-endpoint-plans"></a>Comparer Microsoft Defender pour point de terminaison plans

Microsoft Defender pour point de terminaison est une plate-forme de sécurité de point de terminaison d’entreprise conçue pour aider les réseaux d’entreprise à prévenir, détecter, examiner et répondre aux menaces avancées. Defender pour point de terminaison fournit une protection avancée contre les menaces qui inclut l’antivirus, les logiciels anti-programme malveillant, l’atténuation des ransomwares et bien plus encore, ainsi que la gestion centralisée et la création de rapports. Vous pouvez choisir parmi les options suivantes pour Microsoft Defender pour point de terminaison :

- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Gestion des vulnérabilités de Microsoft Defender](../defender-vulnerability-management/index.yml)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Vous pouvez utiliser cet article pour clarifier la protection fournie par les différentes fonctionnalités disponibles dans Defender pour point de terminaison Plan 1, Defender pour point de terminaison Plan 2, le nouveau module complémentaire Gestion des vulnérabilités Defender et Microsoft 365 Defender.

## <a name="compare-defender-for-endpoint-plans"></a>Comparer les plans Defender pour point de terminaison

Le tableau suivant récapitule ce qui est inclus dans chaque plan Defender pour point de terminaison.

| Prévision | Inclus |
|:---|:---|
| [Defender pour Endpoint Plan 1](defender-endpoint-plan-1.md) | <ul><li>[Protection de nouvelle génération](defender-endpoint-plan-1.md#next-generation-protection) (inclut le logiciel anti-programme malveillant et l’antivirus)</li><li>[Réduction de la surface d’attaque](defender-endpoint-plan-1.md#attack-surface-reduction)</li><li> [Actions de réponse manuelle](defender-endpoint-plan-1.md#manual-response-actions)</li><li>[Gestion centralisée](defender-endpoint-plan-1.md#centralized-management)</li><li>[Rapports de sécurité](defender-endpoint-plan-1.md#reporting)</li><li>[API](defender-endpoint-plan-1.md#apis)</li><li>[Prise en charge des appareils Windows 10, iOS, Android os et macOS](defender-endpoint-plan-1.md#cross-platform-support)</li></ul>|
| [Defender pour point de terminaison Plan 2](microsoft-defender-endpoint.md) | Toutes les fonctionnalités de Defender pour point de terminaison Plan 1, ainsi que :<ul><li>[Découverte d’appareils](device-discovery.md)</li><li>[Inventaire des appareils](machines-view-overview.md)</li><li>[Fonctionnalités de gestion des vulnérabilités Core Defender](../defender-vulnerability-management/defender-vulnerability-management-capabilities.md)</li><li>[Analyse des menaces](threat-analytics.md)</li><li>[Examen et réponse automatisés](automated-investigations.md)</li><li>[Repérage avancé](advanced-hunting-overview.md)</li><li>[Détection et réponse du point de terminaison](overview-endpoint-detection-response.md)</li><li>[Spécialistes des menaces Microsoft](microsoft-threat-experts.md)</li><li>Prise en charge des [plateformes Windows](configure-endpoints.md) (client et serveur) et [non Windows](configure-endpoints-non-windows.md) (macOS, iOS, Android et Linux)</li></ul> |
| [Module complémentaire Gestion des vulnérabilités Defender](../defender-vulnerability-management/defender-vulnerability-management-capabilities.md) | Fonctionnalités de gestion des vulnérabilités Defender supplémentaires pour Defender pour le plan de point de terminaison 2 :<ul><li>[Évaluation des bases de référence de sécurité](../defender-vulnerability-management/tvm-security-baselines.md)</li><li>[Bloquer les applications vulnérables](../defender-vulnerability-management/tvm-block-vuln-apps.md)</li><li>[Extensions de navigateur](../defender-vulnerability-management/tvm-browser-extensions.md)</li><li>[Évaluation des certificats numériques](../defender-vulnerability-management/tvm-certificate-inventory.md)</li><li>[Analyse du partage réseau](../defender-vulnerability-management/tvm-network-share-assessment.md)</li><li>Prise en charge des [plateformes Windows](configure-endpoints.md) (client et serveur) et [non Windows](configure-endpoints-non-windows.md) (macOS, iOS, Android et Linux)</li></ul> |
| [Microsoft 365 Defender](../defender/microsoft-365-defender.md) | Les services sont les suivants : <ul><li>[Defender pour point de terminaison Plan 2](microsoft-defender-endpoint.md)</li><li>[Gestion des vulnérabilités Microsoft Defender](../defender-vulnerability-management/defender-vulnerability-management.md)</li><li>[Microsoft Defender pour Office 365](../office-365-security/overview.md)</li><li>[Microsoft Defender pour l’identité](/defender-for-identity/)</li><li>[Microsoft Defender for Cloud Apps](/cloud-app-security/)</li></ul>|

> [!IMPORTANT]
> Les versions autonomes de Defender pour point de terminaison Plan 1 et Plan 2 n’incluent pas de licences serveur. Pour intégrer des serveurs, tels que des points de terminaison exécutant Windows Server ou Linux, vous avez besoin de Defender pour serveurs Plan 1 ou Plan 2 dans le cadre de l’offre [Defender pour cloud](/azure/defender-for-cloud/defender-for-cloud-introduction) . Pour en savoir plus. Consultez [vue d’ensemble de Microsoft Defender pour serveurs](/azure/defender-for-cloud/defender-for-servers-introduction).

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

- Pour essayer le plan Defender pour point de terminaison, accédez à la [page d’inscription à la version d’évaluation de Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?LinkID=2168109).
- Pour essayer le module complémentaire Gestion des vulnérabilités Microsoft Defender pour Defender pour point de terminaison Plan 2, visitez [https://aka.ms/AddonPreviewTrial](https://aka.ms/AddonPreviewTrial). 

## <a name="see-also"></a>Voir aussi

- [Prise en main de Microsoft Security (offres d’évaluation)](https://www.microsoft.com/security/business/get-started/start-free-trial)

- [Microsoft Defender pour entreprises](../defender-business/mdb-overview.md) (protection des points de terminaison pour les petites et moyennes entreprises)