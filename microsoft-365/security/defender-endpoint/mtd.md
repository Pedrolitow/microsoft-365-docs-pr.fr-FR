---
title: Microsoft Defender pour le point de terminaison - Défense contre les menaces mobiles
ms.reviewer: ''
description: Vue d’ensemble de la défense contre les menaces mobiles dans Microsoft Defender pour le point de terminaison
keywords: mobile, defender, Microsoft Defender pour le point de terminaison, ios, mtd, android, sécurité
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: sunasing
author: sunasing
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 8de50b9f06f05c012cc2b4c789838612d98abe62
ms.sourcegitcommit: 3140e2866de36d57a27d27f70d47e8167c9cc907
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2021
ms.locfileid: "60556887"
---
# <a name="microsoft-defender-for-endpoint---mobile-threat-defense"></a>Microsoft Defender pour le point de terminaison - Défense contre les menaces mobiles

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Microsoft Defender pour point de terminaison sur Android et iOS est notre solution de défense contre les menaces **mobiles (MTD).** En règle générale, les entreprises sont proactives pour protéger les PC contre les vulnérabilités et les attaques, tandis que les appareils mobiles ne sont souvent pas surveillés et non protégés. Lorsque les plateformes mobiles ont une protection intégrée telle que l’isolation des applications et les magasins d’applications grand public, ces plateformes restent vulnérables aux attaques basées sur le web ou à d’autres attaques sophistiquées. À mesure que de plus en plus d’employés utilisent des appareils pour travailler et accéder à des informations sensibles, il est impératif que les entreprises déploient une solution MTD pour protéger les appareils et vos ressources contre les attaques de plus en plus sophistiquées sur les mobiles.

## <a name="key-capabilities"></a>Fonctionnalités clés

Microsoft Defender pour point de terminaison sur Android et iOS fournit les fonctionnalités clés ci-dessous, pour plus d’informations sur les dernières fonctionnalités et avantages, lisez nos [annonces.](https://aka.ms/mdeblog)

<br>

|Fonctionnalité|Description|
|---|---|
|Web Protection|Anti-hameçonnage, blocage des connexions réseau non sécurisées et prise en charge des indicateurs personnalisés.|
|Protection contre les programmes malveillants (Android uniquement)|Analyse des applications malveillantes.|
|Détection de jailbreak (iOS uniquement)|Détection d’appareils jailbreakés.|
|Alerte unifiée|Alertes de toutes les plateformes dans la console de sécurité M365 unifiée|
|Accès conditionnel, lancement conditionnel|Blocage des appareils à risque d’accéder aux ressources d’entreprise. Les signaux de risque defender pour les points de terminaison peuvent également être ajoutés aux stratégies de protection des applications (MAM)|
|Intégration à Microsoft Tunnel|Peut s’intégrer Microsoft Tunnel, une solution de passerelle VPN pour activer la sécurité et la connectivité dans une seule application. Disponible uniquement sur Android actuellement|

Toutes ces fonctionnalités sont disponibles pour les titulaires de licences Microsoft Defender pour les points de terminaison. Pour plus d’informations, voir [Conditions requises pour les licences.](minimum-requirements.md#licensing-requirements)

## <a name="overview-and-deploy"></a>Vue d’ensemble et déploiement

Le déploiement de Microsoft Defender pour Point de terminaison sur mobile peut être effectué via Microsoft Endpoint Manager (MEM). Regardez cette vidéo pour obtenir une vue d’ensemble rapide des fonctionnalités et du déploiement de MTD :

<br/>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWMpiC]

Pour plus d’informations, consultez les liens ci-dessous.

**Android :** [Microsoft Defender pour point de terminaison sur Android](microsoft-defender-endpoint-android.md)

**iOS :** [Microsoft Defender pour point de terminaison sur iOS](microsoft-defender-endpoint-ios.md)

### <a name="pilot-evaluation"></a>Évaluation pilote

Lors de l’évaluation de la défense contre les menaces mobiles avec Microsoft Defender pour le point de terminaison, vous pouvez vérifier que certains critères sont satisfaits avant de poursuivre le déploiement du service sur un plus grand nombre d’appareils. Vous pouvez définir les critères de sortie et vous assurer qu’ils sont satisfaits avant de déployer largement.

Cela permet de réduire les problèmes potentiels qui peuvent survenir lors du déploiement du service. Voici quelques tests et critères de sortie qui peuvent vous aider :

- Les appareils s’affiche dans la liste d’inventaire des appareils : après l’intégration réussie de Defender for Endpoint sur l’appareil mobile, vérifiez que l’appareil est répertorié dans l’inventaire des appareils dans la [console de sécurité.](https://security.microsoft.com)

- Exécutez un test de détection de programmes malveillants sur un appareil Android : installez n’importe quelle application de test antivirus à partir de Google Play Store et vérifiez qu’elle est détectée par Microsoft Defender pour endpoint. Voici un exemple d’application qui peut être utilisée pour ce test : [Test virus](https://play.google.com/store/apps/details?id=com.androidantivirus.testvirus). Notez que sur les Enterprise Android avec un profil de travail, seul le profil de travail est pris en charge.

- Exécutez un test de hameçonnage : recherchez et vérifiez qu’il est bloqué https://smartscreentestratings2.net par Microsoft Defender for Endpoint. Notez que sur les Enterprise Android avec un profil de travail, seul le profil de travail est pris en charge.

- Les alertes apparaissent dans le tableau de bord : vérifiez que les alertes pour les tests de détection ci-dessus apparaissent sur la [console de sécurité.](https://security.microsoft.com)

## <a name="deployment-best-practices"></a>Meilleures pratiques de déploiement

### <a name="end-user-onboarding"></a>Intégration de l’utilisateur final

- [Configurer l’accès conditionnel](android-configure.md#conditional-access-with-defender-for-endpoint-on-android)pour appliquer l’intégration des utilisateurs : cela peut être appliqué pour garantir que les utilisateurs finaux sont intégrés à l’application Microsoft Defender pour endpoint après le déploiement. Regardez cette vidéo pour obtenir une démonstration rapide sur la configuration de l’accès conditionnel avec les signaux de risque de Defender for Endpoint. 

  <br/>

  > [!VIDEO https://www.microsoft.com/videoplayer/embed/RWMwR1]

### <a name="simplify-onboarding"></a>Simplifier l’intégration

- [Android Enterprise - Configurer VPN toujours en service](android-intune.md#auto-setup-of-always-on-vpn).
- [iOS : configuration automatique du profil VPN](ios-install.md#auto-onboarding-of-vpn-profile-simplified-onboarding)

## <a name="configure"></a>Configurer

- [Configurer les fonctionnalités Android](android-configure.md)
- [Configurer des fonctionnalités iOS](ios-configure-features.md)
- [Configurer le mode Supervisé pour les appareils iOS supervisés](ios-install.md#configure-microsoft-defender-for-endpoint-for-supervised-mode)

## <a name="resources"></a>Ressources

- [Microsoft Defender pour point de terminaison Android](microsoft-defender-endpoint-android.md)
- [Microsoft Defender pour point de terminaison iOS](microsoft-defender-endpoint-ios.md)
- Restez informé des prochaines publication en lisant [nos annonces.](https://aka.ms/mdeblog)
