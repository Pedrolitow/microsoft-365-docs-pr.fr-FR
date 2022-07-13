---
title: Étape 7 Promouvoir votre environnement d’évaluation Microsoft 365 Defender en production
description: Utilisez cet article pour promouvoir vos versions d’évaluation de MDI, MDO, MDE et Defender pour Cloud Apps vers votre environnement en direct dans Microsoft 365 Defender ou M365D.
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: bcarter
author: brendacarter
f1.keywords:
- NOCSH
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
- m365solution-evalutatemtp
- zerotrust-solution
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 769a70177ada62b4dbb505a8363fe3bdbfc4a59a
ms.sourcegitcommit: 61b22df76e0f81e5ef11c587b129287886151c79
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/12/2022
ms.locfileid: "66748734"
---
# <a name="step-7-promote-your-microsoft-365-defender-evaluation-environment-to-production"></a>Étape 7 Promouvoir votre environnement d’évaluation Microsoft 365 Defender en production

**S’applique à :**
- Microsoft 365 Defender

Pour promouvoir votre environnement d’évaluation Microsoft 365 Defender en production, commencez par acheter la licence nécessaire. Suivez les étapes décrites dans [Créer l’environnement d’évaluation](eval-create-eval-environment.md) et achetez la licence Office 365 E5 (au lieu de sélectionner Démarrer l’essai gratuit).

Ensuite, effectuez toute configuration supplémentaire et développez vos groupes pilotes jusqu’à ce que ceux-ci aient atteint la production complète.

## <a name="microsoft-defender-for-identity"></a>Microsoft Defender pour l’identité

Defender pour Identity ne nécessite aucune configuration supplémentaire. Assurez-vous simplement que vous avez acheté les licences nécessaires et installé le capteur sur tous vos contrôleurs de domaine Active Directory et serveurs Services ADFS (AD FS).

## <a name="microsoft-defender-for-office-365"></a>Microsoft Defender pour Office 365

Après avoir évalué ou piloté MDO avec succès, il peut être promu dans l’ensemble de votre environnement de production.

1. Achetez et approvisionnez les licences nécessaires et attribuez-les à vos utilisateurs de production.
2. Réexélez les configurations de stratégie de base recommandées (Standard ou Strict) sur votre domaine de messagerie de production ou des groupes d’utilisateurs spécifiques.
3. Vous pouvez éventuellement créer et configurer des stratégies MDO personnalisées sur votre domaine de messagerie de production ou des groupes d’utilisateurs.  Toutefois, n’oubliez pas que toutes les stratégies de base affectées sont toujours prioritaires sur les stratégies personnalisées.
4. Mettez à jour l’enregistrement MX public pour votre domaine de messagerie de production afin qu’il soit résolu directement en EOP.
5. Désactivez les passerelles SMTP tierces et désactivez ou supprimez les connecteurs EXO associés à ce relais.

## <a name="microsoft-defender-for-endpoint"></a>Microsoft Defender pour point de terminaison

Pour promouvoir Microsoft Defender pour point de terminaison environnement d’évaluation d’un pilote à la production, il vous suffit d’intégrer d’autres points de terminaison au service à l’aide des [outils et méthodes pris en charge](../defender-endpoint/onboard-configure.md).

Utilisez les instructions générales suivantes pour intégrer davantage d’appareils à Microsoft Defender pour point de terminaison.

1. Vérifiez que l’appareil répond aux [exigences minimales](../defender-endpoint/minimum-requirements.md).
2. Selon l’appareil, suivez les étapes de configuration fournies dans la section d’intégration du portail Defender pour point de terminaison.
3. Utilisez l’outil de gestion et la méthode de déploiement appropriés pour vos appareils.
4. Exécutez un test de détection pour vérifier que les appareils sont correctement intégrés et signalent au service.

## <a name="microsoft-defender-for-cloud-apps"></a>Microsoft Defender for Cloud Apps

Microsoft Defender for Cloud Apps ne nécessite aucune configuration supplémentaire. Assurez-vous simplement que vous avez acheté les licences nécessaires. Si vous avez étendu le déploiement à certains groupes d’utilisateurs, augmentez l’étendue de ces groupes jusqu’à ce que vous atteigniez l’échelle de production.
