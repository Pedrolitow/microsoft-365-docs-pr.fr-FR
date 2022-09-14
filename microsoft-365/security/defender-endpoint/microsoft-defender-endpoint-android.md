---
title: Microsoft Defender pour point de terminaison Android
ms.reviewer: ''
description: Décrit comment installer et utiliser Microsoft Defender pour point de terminaison sur Android
keywords: microsoft, defender, Microsoft Defender pour point de terminaison, android, installation, déploiement, désinstallation, intune
ms.service: microsoft-365-security
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
- m365-initiative-defender-endpoint
ms.topic: conceptual
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: 1f9f48e78fd45b0120bdccecd7315321dfef4d53
ms.sourcegitcommit: 9b133379196da2b3a4bb311b07ff274f43780f68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2022
ms.locfileid: "67691982"
---
# <a name="microsoft-defender-for-endpoint-on-android"></a>Microsoft Defender pour point de terminaison Android

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Cette rubrique explique comment installer, configurer, mettre à jour et utiliser Defender pour point de terminaison sur Android.

> [!CAUTION]
> L’exécution d’autres produits de protection de point de terminaison tiers avec Defender pour point de terminaison sur Android est susceptible de provoquer des problèmes de performances et des erreurs système imprévisibles.

## <a name="how-to-install-microsoft-defender-for-endpoint-on-android"></a>Comment installer Microsoft Defender pour point de terminaison sur Android

### <a name="prerequisites"></a>Prerequisites

- **Pour les utilisateurs finaux** :
  - Une licence Microsoft Intune doit être attribuée à l’utilisateur final. Pour plus d’informations sur l’attribution de licences, consultez [Affecter des licences aux utilisateurs](/azure/active-directory/users-groups-roles/licensing-groups-assign).
  - Une licence Microsoft Defender pour point de terminaison doit être attribuée aux utilisateurs de l’application. Pour plus d’informations sur l’attribution de licences, consultez [Microsoft Defender pour point de terminaison exigences en matière de licences](/microsoft-365/security/defender-endpoint/minimum-requirements#licensing-requirements).
  - Portail d'entreprise Intune application peut être téléchargée à partir de [Google Play](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal) et est disponible sur l’appareil Android.
  - En outre, les appareils peuvent être [inscrits](/mem/intune/user-help/enroll-device-android-company-portal) via l’application Portail d'entreprise Intune pour appliquer Intune stratégies de conformité des appareils. 

- **Pour les administrateurs** :
   - Accès au portail Microsoft 365 Defender.
   - Accédez au [Centre d’administration Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) pour :
     - Déployez l’application sur des groupes d’utilisateurs inscrits dans votre organisation.
     - Configurez Microsoft Defender pour point de terminaison signaux de risque dans la stratégie de protection des applications.
  
    > [!NOTE]
    >
    > - Microsoft Defender pour point de terminaison étend désormais la protection aux données d’une organisation au sein d’une application managée (GAM) pour les appareils qui ne sont pas inscrits à l’aide de la gestion des appareils mobiles (GPM), mais qui utilisent Intune pour gérer les applications mobiles. Il étend également ce support aux clients qui utilisent d’autres solutions de gestion de la mobilité d’entreprise, tout en continuant à utiliser Intune pour [la gestion des applications mobiles (MAM).](/mem/intune/apps/mam-faq)
    > - En outre, Microsoft Defender pour point de terminaison prend déjà en charge les appareils inscrits à l’aide de Intune gestion des appareils mobiles (GPM).

### <a name="network-requirements"></a>Configuration réseau requise

- Pour que Microsoft Defender pour point de terminaison sur Android fonctionnent lorsqu’ils sont connectés à un réseau, le pare-feu/proxy doit être configuré pour [permettre l’accès aux URL de service Microsoft Defender pour point de terminaison](configure-proxy-internet.md#enable-access-to-microsoft-defender-for-endpoint-service-urls-in-the-proxy-server).

### <a name="system-requirements"></a>Configuration requise

- Téléphones mobiles exécutant Android 6.0 et versions ultérieures. **Les téléphones mobiles exécutant Android go, tablettes et autres appareils mobiles exécutant Android ne sont actuellement pas pris en charge.**
- Portail d'entreprise Intune application est téléchargée à partir de [Google Play](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal) et installée. L’inscription des appareils est requise pour Intune stratégies de conformité des appareils à appliquer.

### <a name="installation-instructions"></a>Instructions d’installation

Microsoft Defender pour point de terminaison sur Android prend en charge l’installation sur les deux modes d’appareils inscrits : les modes Administrateur d’appareil hérité et Android Entreprise. **Actuellement, les appareils appartenant à l’utilisateur avec profil professionnel et les inscriptions d’appareils utilisateur entièrement gérés appartenant à l’entreprise sont pris en charge dans Android Enterprise. La prise en charge d’autres modes Android Entreprise sera annoncée lorsque vous serez prêt.**

- Le déploiement de Microsoft Defender pour point de terminaison sur Android se fait via Microsoft Intune (GPM). Pour plus d’informations, consultez [Déployer Microsoft Defender pour point de terminaison sur Android avec Microsoft Intune](android-intune.md).
- Installation de Microsoft Defender pour point de terminaison sur les appareils qui ne sont pas inscrits à l’aide de Intune gestion des appareils mobiles (GPM), consultez [Configurer Microsoft Defender pour point de terminaison signaux de risque dans la stratégie de protection des applications (MAM).](android-configure-mam.md)

> [!NOTE]
> **Microsoft Defender pour point de terminaison sur Android est disponible sur [Google Play](https://play.google.com/store/apps/details?id=com.microsoft.scmx) maintenant.**
>
> Vous pouvez vous connecter à Google Play à partir de Intune pour déployer Microsoft Defender pour point de terminaison application, entre les modes d’inscription Administrateur d’appareil et Android Enterprise.

## <a name="how-to-configure-microsoft-defender-for-endpoint-on-android"></a>Guide pratique pour configurer Microsoft Defender pour point de terminaison sur Android

Des conseils sur la configuration de Microsoft Defender pour point de terminaison sur les fonctionnalités Android sont disponibles dans [Configurer Microsoft Defender pour point de terminaison sur les fonctionnalités Android](android-configure.md).

## <a name="related-topics"></a>Voir aussi

- [Déployer Microsoft Defender pour point de terminaison Android via Microsoft Intune](android-intune.md)
- [Configurer Microsoft Defender pour point de terminaison pour des fonctionnalités Android](android-configure.md)
- [Notions de base de la gestion des applications mobiles (MAM)](/mem/intune/apps/app-management#mobile-application-management-mam-basics)
