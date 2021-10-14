---
title: Microsoft Defender pour point de terminaison Android
ms.reviewer: ''
description: Décrit comment installer et utiliser Microsoft Defender pour endpoint sur Android
keywords: microsoft, defender, Microsoft Defender pour le point de terminaison, android, installation, déployer, désinstaller, intune
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: b7bb40d4990d5bd68d3ee56149506374c5e0c6fb
ms.sourcegitcommit: be074f57e33c811bb3857043152825209bc8af07
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2021
ms.locfileid: "60334529"
---
# <a name="microsoft-defender-for-endpoint-on-android"></a>Microsoft Defender pour point de terminaison Android

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Cette rubrique décrit comment installer, configurer, mettre à jour et utiliser Defender pour Endpoint sur Android.

> [!CAUTION]
> L’exécution d’autres produits de protection des points de terminaison tiers avec Defender for Endpoint sur Android est susceptible de provoquer des problèmes de performances et des erreurs système imprévisibles.

## <a name="how-to-install-microsoft-defender-for-endpoint-on-android"></a>Comment installer Microsoft Defender pour le point de terminaison sur Android

### <a name="prerequisites"></a>Conditions préalables

- **Pour les utilisateurs finaux**:
  - Licence Microsoft Defender pour point de terminaison attribuée à l’utilisateur final de l’application. Voir [microsoft Defender pour les conditions requises pour les licences de point de terminaison](/microsoft-365/security/defender-endpoint/minimum-requirements#licensing-requirements)
  - Portail d'entreprise Intune’application peut être téléchargée à partir [de Google Play](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal) et est disponible sur l’appareil Android.
  - En outre, les appareils peuvent être inscrits [via](/mem/intune/user-help/enroll-device-android-company-portal) l’application Portail d'entreprise Intune pour appliquer des stratégies de conformité des appareils Intune. Pour ce faire, l’utilisateur final doit se voir attribuer Microsoft Intune licence.
  - Pour plus d’informations sur l’attribution de licences, voir [Attribuer des licences aux utilisateurs.](/azure/active-directory/users-groups-roles/licensing-groups-assign)

- **Pour les administrateurs**
   - Accès au portail Microsoft 365 Defender web.
   - Accéder [Microsoft Endpoint Manager centre d’administration à](https://go.microsoft.com/fwlink/?linkid=2109431)
       - Déployez l’application pour les groupes d’utilisateurs inscrits dans votre organisation.
       - Configurez Microsoft Defender pour les signaux de risque de point de terminaison dans la stratégie de protection des applications.
  
    > [!NOTE]
    > - Microsoft Defender pour le point de terminaison étend désormais la protection aux données d’une organisation au sein d’une application gérée (MAM) pour les appareils qui ne sont pas inscrits à l’aide de la gestion des périphériques mobiles (MDM), mais qui utilisent Intune pour gérer les applications mobiles. Il étend également cette prise en charge aux clients qui utilisent d’autres solutions de gestion de la mobilité d’entreprise, tout en utilisant Intune pour la gestion des applications mobiles [(MAM).](/mem/intune/apps/mam-faq)
    > - En outre, Microsoft Defender pour endpoint prend déjà en charge les appareils inscrits à l’aide de la gestion des périphériques mobiles (MDM) Intune.


### <a name="network-requirements"></a>Configuration réseau requise

- Pour que Microsoft Defender pour le point de terminaison sur Android fonctionne lorsqu’il est connecté à un réseau, le pare-feu/proxy doit être configuré pour permettre l’accès aux URL du service Microsoft Defender pour les points de [terminaison.](configure-proxy-internet.md#enable-access-to-microsoft-defender-for-endpoint-service-urls-in-the-proxy-server)

### <a name="system-requirements"></a>Configuration requise

- Téléphones mobiles exécutant Android 6.0 et version supérieure. **Les tablettes et autres appareils mobiles exécutant Android ne sont actuellement pas pris en charge.**
- Portail d'entreprise Intune’application est téléchargée à partir [de Google Play](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal) et installée. L’inscription des appareils est requise pour que les stratégies de conformité des appareils Intune soient appliquées.

### <a name="installation-instructions"></a>Instructions d’installation

Microsoft Defender pour Endpoint sur Android prend en charge l’installation sur les deux modes d’appareils inscrits : l’administrateur d’appareil hérité et les modes Enterprise Android. **Actuellement, les appareils personnels avec profil de travail et les inscriptions d’appareils utilisateur entièrement gérées par l’entreprise sont pris en charge dans Android Enterprise. La prise en charge des autres modes Enterprise Android sera annoncée lorsque vous serez prêt.**

- Le déploiement de Microsoft Defender pour Endpoint sur Android s’effectue via Microsoft Intune (MDM). Pour plus d’informations, voir [Déployer Microsoft Defender pour endpoint sur Android avec Microsoft Intune](android-intune.md).
- Installation de Microsoft Defender pour endpoint sur les appareils qui ne sont pas inscrits à l’aide de la gestion des périphériques mobiles Intune (MDM), voir Configurer Microsoft Defender pour les signaux de risque de point de terminaison dans la stratégie de protection des applications [(MAM).](android-configure-mam.md)

> [!NOTE]
> **Microsoft Defender pour le point de terminaison sur Android est désormais disponible [sur Google Play.](https://play.google.com/store/apps/details?id=com.microsoft.scmx)**
>
> Vous pouvez vous connecter à Google Play à partir d’Intune pour déployer l’application Microsoft Defender pour Endpoint, sur les modes d’inscription de l’administrateur d’appareil et Enterprise Android.

## <a name="how-to-configure-microsoft-defender-for-endpoint-on-android"></a>Comment configurer Microsoft Defender pour endpoint sur Android

Des instructions sur la configuration de Microsoft Defender pour le point de terminaison sur les fonctionnalités Android sont disponibles dans Configurer Microsoft Defender pour le point de terminaison [sur les fonctionnalités Android.](android-configure.md)

## <a name="related-topics"></a>Voir aussi

- [Déployer Microsoft Defender pour point de terminaison Android via Microsoft Intune](android-intune.md)
- [Configurer Microsoft Defender pour point de terminaison pour des fonctionnalités Android](android-configure.md)
- [Informations de base sur la gestion des applications mobiles (MAM)](/mem/intune/apps/app-management#mobile-application-management-mam-basics)
