---
title: Microsoft Defender pour point de terminaison - Mobile Threat Defense
ms.reviewer: ''
description: Vue d’ensemble de la défense contre les menaces mobiles dans Microsoft Defender pour point de terminaison
keywords: mobile, defender, Microsoft Defender pour point de terminaison, ios, mtd, android, sécurité
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
- m365-initiative-defender-endpoint
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 83da2034a04da85849383700204174110ceffa57
ms.sourcegitcommit: 7e0094ddff54bcbe5d691dba58d4c4fb86f8b1a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2022
ms.locfileid: "65188523"
---
# <a name="microsoft-defender-for-endpoint---mobile-threat-defense"></a>Microsoft Defender pour point de terminaison - Mobile Threat Defense

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Microsoft Defender pour point de terminaison sur Android et iOS est notre **solution de défense contre les menaces mobiles (MTD).** En règle générale, les entreprises se montrent proactives pour protéger les ordinateurs contre les vulnérabilités et attaques, alors que les appareils mobiles restent souvent non supervisés et non protégés. Lorsque les plateformes mobiles disposent d’une protection intégrée telle que l’isolation des applications et les magasins d’applications grand public contrôlés, ces plateformes restent vulnérables aux attaques basées sur le web ou à d’autres attaques sophistiquées. Comme de plus en plus d’employés utilisent des appareils pour travailler et accéder à des informations sensibles, il est impératif que les entreprises déploient une solution MTD pour protéger les appareils et vos ressources contre les attaques de plus en plus sophistiquées sur les mobiles.

## <a name="key-capabilities"></a>Fonctionnalités clés

Microsoft Defender pour point de terminaison sur Android et iOS fournit les fonctionnalités clés ci-dessous. Pour plus d’informations sur les dernières fonctionnalités et avantages, consultez nos [annonces](https://aka.ms/mdeblog).

<br>

|Fonctionnalité|Description|
|---|---|
|Web Protection|Anti-hameçonnage, blocage des connexions réseau non sécurisées et prise en charge des indicateurs personnalisés.|
|Protection contre les programmes malveillants (Android uniquement)|Recherche d’applications malveillantes.|
|Détection jailbreak (iOS uniquement)|Détection d’appareils jailbreakés.|
|Gestion des menaces et des vulnérabilités (TVM) |Évaluation des vulnérabilités des appareils mobiles intégrés. Visitez cette [page](next-gen-threat-and-vuln-mgt.md) pour en savoir plus sur Gestion des menaces et des vulnérabilités dans Microsoft Defender pour point de terminaison. *Notez que sur iOS, seules les vulnérabilités de système d’exploitation sont prises en charge dans cette préversion.*|
|Alertes unifiées|Alertes de toutes les plateformes dans la console de sécurité M365 unifiée|
|Accès conditionnel, lancement conditionnel|Empêcher les appareils à risque d’accéder aux ressources d’entreprise. Les signaux de risque Defender pour point de terminaison peuvent également être ajoutés aux stratégies de protection des applications (MAM)|
|Contrôles de confidentialité. En préversion (voir la note ci-dessous)|Configurez la confidentialité dans les rapports sur les menaces en contrôlant les données envoyées par Microsoft Defender pour point de terminaison. *Notez que les contrôles de confidentialité sont actuellement disponibles uniquement pour les appareils inscrits. Les contrôles pour les appareils non inscrits seront ajoutés ultérieurement*|
|Intégration à Microsoft Tunnel|Peut s’intégrer à Microsoft Tunnel, une solution de passerelle VPN pour activer la sécurité et la connectivité dans une seule application. Disponible sur Android et désormais en disponibilité générale sur iOS également.|

Toutes ces fonctionnalités sont disponibles pour Microsoft Defender pour point de terminaison titulaires de licence. Pour plus d’informations, consultez [Les exigences en matière de licences](minimum-requirements.md#licensing-requirements).


## <a name="overview-and-deploy"></a>Vue d’ensemble et déploiement

Le déploiement de Microsoft Defender pour point de terminaison sur mobile peut être effectué via Microsoft Endpoint Manager (MEM). Regardez cette vidéo pour obtenir une vue d’ensemble rapide des fonctionnalités mtd et du déploiement :

<br/>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWMpiC]

### <a name="deploy"></a>Déployer

Le tableau suivant récapitule comment déployer Microsoft Defender pour point de terminaison sur Android et iOS. Pour obtenir une documentation détaillée, consultez 
- [Vue d’ensemble des Microsoft Defender pour point de terminaison sur Android](microsoft-defender-endpoint-android.md) et
- [Vue d’ensemble de Microsoft Defender pour point de terminaison iOS](microsoft-defender-endpoint-ios.md)

**Android**

|Type d’inscription     |Détails      |
|--------------------|-------------|
|Android Enterprise avec Intune Endpoint Manager unifiée (Microsoft Endpoint Manager)|[Déployer sur des appareils android Enterprise inscrits](android-intune.md#deploy-on-android-enterprise-enrolled-devices)|
|Administrateur d’appareil avec Intune Endpoint Manager unifiée (Microsoft Endpoint Manager)|[Déployer sur des appareils inscrits par l’administrateur d’appareil](android-intune.md#deploy-on-device-administrator-enrolled-devices)|
|Appareils BYOD OR non managés gérés par d’autres Gestionnaires de points de terminaison unifiés / Stratégie de protection des applications d’installation (MAM)|[Configurer les signaux de risque Defender dans la stratégie de protection des applications (MAM)](android-configure-mam.md)|

**iOS**

|Type d’inscription     |Détails      |
|--------------------|-------------|
|Appareils supervisés avec Intune Endpoint Manager unifiée (Microsoft Endpoint Manager)|1. [Déployer en tant qu’application du Store iOS](ios-install.md)<br/>2. [Configurer la protection web sans VPN pour les appareils iOS supervisés](ios-install.md#complete-deployment-for-supervised-devices)|
|Appareils non supervisés (BYOD) inscrits avec Intune UEM (Microsoft Endpoint Manager)|[Déployer en tant qu’application du Store iOS](ios-install.md)|
|Appareils BYOD OR non managés gérés par d’autres uems / Stratégie de protection des applications de configuration (MAM)|[Configurer les signaux de risque Defender dans la stratégie de protection des applications (MAM)](ios-install-unmanaged.md)|

### <a name="end-user-onboarding"></a>Intégration des utilisateurs finaux

- [Configurer l’intégration sans interaction tactile pour les appareils inscrits sur iOS](ios-install.md#zero-touch-onboarding-of-microsoft-defender-for-endpoint) : les administrateurs peuvent configurer l’installation sans contact pour intégrer en mode silencieux Microsoft Defender pour point de terminaison sur les appareils iOS inscrits sans que l’utilisateur doive ouvrir l’application. 

- [Configurer l’accès conditionnel pour appliquer l’intégration des utilisateurs](android-configure.md#conditional-access-with-defender-for-endpoint-on-android) : cela peut être appliqué pour garantir que les utilisateurs finaux sont intégrés à l’application Microsoft Defender pour point de terminaison après le déploiement. Regardez cette vidéo pour une démonstration rapide de la configuration de l’accès conditionnel avec les signaux de risque Defender pour point de terminaison. 

  <br/>

  > [!VIDEO https://www.microsoft.com/videoplayer/embed/RWMwR1]

### <a name="simplify-onboarding"></a>Simplifier l’intégration

- [iOS - intégration Zero-Touch](ios-install.md#zero-touch-onboarding-of-microsoft-defender-for-endpoint)
- [Android Enterprise - Configurer le VPN Always-on](android-intune.md#auto-setup-of-always-on-vpn).
- [iOS - Configuration automatique du profil VPN](ios-install.md#auto-onboarding-of-vpn-profile-simplified-onboarding)

## <a name="pilot-evaluation"></a>Évaluation pilote

Lors de l’évaluation de la défense contre les menaces mobiles avec Microsoft Defender pour point de terminaison, vous pouvez vérifier que certains critères sont remplis avant de continuer à déployer le service sur un plus grand ensemble d’appareils. Vous pouvez définir les critères de sortie et vous assurer qu’ils sont satisfaits avant de déployer largement.

Cela permet de réduire les problèmes potentiels qui peuvent survenir lors du déploiement du service. Voici quelques tests et critères de sortie qui peuvent vous aider :

- Les appareils apparaissent dans la liste d’inventaire des appareils : après avoir réussi l’intégration de Defender pour point de terminaison sur l’appareil mobile, vérifiez que l’appareil est répertorié dans l’inventaire des appareils dans la [console de sécurité](https://security.microsoft.com).

- Exécutez un test de détection de programmes malveillants sur un appareil Android : installez n’importe quelle application antivirus de test à partir de Google Play Store et vérifiez qu’elle est détectée par Microsoft Defender pour point de terminaison. Voici un exemple d’application qui peut être utilisé pour ce test : [Tester le virus](https://play.google.com/store/apps/details?id=com.androidantivirus.testvirus). Notez que sur Android Enterprise avec un profil professionnel, seul le profil professionnel est pris en charge.

- Exécuter un test d’hameçonnage : accédez à https://smartscreentestratings2.net et vérifiez qu’il est bloqué par Microsoft Defender pour point de terminaison. Notez que sur Android Enterprise avec un profil professionnel, seul le profil professionnel est pris en charge.

- Les alertes apparaissent dans le tableau de bord : vérifiez que les alertes pour les tests de détection ci-dessus apparaissent sur la [console de sécurité](https://security.microsoft.com).

## <a name="configure"></a>Configurer

- [Configurer les fonctionnalités Android](android-configure.md)
- [Configurer des fonctionnalités iOS](ios-configure-features.md)
- [Configurer la protection web sans VPN pour les appareils iOS supervisés](ios-install.md#complete-deployment-for-supervised-devices)

## <a name="resources"></a>Ressources

- [Microsoft Defender pour point de terminaison Android](microsoft-defender-endpoint-android.md)
- [Microsoft Defender pour point de terminaison iOS](microsoft-defender-endpoint-ios.md)
- Restez informé des prochaines versions en lisant nos [annonces](https://aka.ms/mdeblog).

