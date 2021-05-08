---
title: Microsoft Defender pour point de terminaison Android
ms.reviewer: ''
description: Décrit comment installer et utiliser Microsoft Defender pour endpoint sur Android
keywords: microsoft, defender, Microsoft Defender pour le point de terminaison, android, installation, déployer, désinstaller, intune
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 3f8a8c04f608096e5c226d6899fbbd983bd8d8c1
ms.sourcegitcommit: ff20f5b4e3268c7c98a84fb1cbe7db7151596b6d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2021
ms.locfileid: "52246427"
---
# <a name="microsoft-defender-for-endpoint-on-android"></a>Microsoft Defender pour point de terminaison Android

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez découvrir Microsoft Defender pour le point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink)

Cette rubrique décrit comment installer, configurer, mettre à jour et utiliser Defender pour Endpoint sur Android.

> [!CAUTION]
> L’exécution d’autres produits de protection des points de terminaison tiers avec Defender for Endpoint sur Android est susceptible de provoquer des problèmes de performances et des erreurs système imprévisibles.


## <a name="how-to-install-microsoft-defender-for-endpoint-on-android"></a>Comment installer Microsoft Defender pour le point de terminaison sur Android

### <a name="prerequisites"></a>Configuration requise

-   **Pour les utilisateurs finaux**

    -   Licence Microsoft Defender pour point de terminaison attribuée à l’utilisateur final de l’application. Voir [microsoft Defender pour les conditions requises pour les licences de point de terminaison](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/minimum-requirements#licensing-requirements)

    -   Portail d’entreprise Intune’application peut être téléchargée à partir [de Google Play](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal) et est disponible sur l’appareil Android.

        -   En outre, les appareils peuvent être inscrits [via](https://docs.microsoft.com/mem/intune/user-help/enroll-device-android-company-portal) l’application Portail d’entreprise Intune pour appliquer des stratégies de conformité des appareils Intune. Pour ce faire, l’utilisateur final doit se voir attribuer Microsoft Intune licence.

    -   Pour plus d’informations sur l’attribution de licences, voir [Attribuer des licences aux utilisateurs.](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-groups-assign)
        

-   **Pour les administrateurs**

    -   Accès au portail Centre de sécurité Microsoft Defender web.

        > [!NOTE]
        > Microsoft Intune est la seule solution de gestion des périphériques mobiles (MDM) prise en charge pour le déploiement de Microsoft Defender pour Endpoint sur Android. Actuellement, seuls les appareils inscrits sont pris en charge pour l’application de Defender for Endpoint sur les stratégies de conformité des appareils android dans Intune. 

    -   Accédez [Microsoft Endpoint Manager centre d’administration,](https://go.microsoft.com/fwlink/?linkid=2109431)pour déployer l’application pour les groupes d’utilisateurs inscrits dans votre organisation.
        
### <a name="network-requirements"></a>Configuration réseau requise

- Pour que Microsoft Defender pour le point de terminaison sur Android fonctionne lorsqu’il est connecté à un réseau, le pare-feu/proxy doit être configuré pour permettre l’accès aux URL du service Microsoft Defender pour les points de [terminaison.](configure-proxy-internet.md#enable-access-to-microsoft-defender-for-endpoint-service-urls-in-the-proxy-server)

### <a name="system-requirements"></a>Configuration requise

-   Appareils Android exécutant Android 6.0 et version supérieure.
-   Portail d’entreprise Intune’application est téléchargée à partir [de Google Play](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal) et installée. L’inscription des appareils est requise pour que les stratégies de conformité des appareils Intune soient appliquées.

### <a name="installation-instructions"></a>Instructions d’installation

Microsoft Defender pour Endpoint sur Android prend en charge l’installation sur les deux modes d’appareils inscrits : l’administrateur d’appareil hérité et les modes Enterprise Android.
**Actuellement, les appareils personnels avec profil de travail et les inscriptions d’appareils utilisateur entièrement gérées par l’entreprise sont pris en charge dans Android Enterprise. La prise en charge des autres modes Enterprise Android sera annoncée lorsque vous serez prêt.**

Le déploiement de Microsoft Defender pour Endpoint sur Android s’effectue via Microsoft Intune (MDM).
Pour plus d’informations, voir [Déployer Microsoft Defender pour endpoint sur Android avec Microsoft Intune](android-intune.md).


> [!NOTE]
> **Microsoft Defender pour le point de terminaison sur Android est désormais disponible [sur Google Play.](https://play.google.com/store/apps/details?id=com.microsoft.scmx)** <br> Vous pouvez vous connecter à Google Play à partir d’Intune pour déployer l’application Microsoft Defender pour Endpoint, sur les modes d’inscription de l’administrateur d’appareil et Enterprise Android. 

## <a name="how-to-configure-microsoft-defender-for-endpoint-on-android"></a>Comment configurer Microsoft Defender pour endpoint sur Android

Des instructions sur la configuration de Microsoft Defender pour le point de terminaison sur les fonctionnalités Android sont disponibles dans Configurer Microsoft Defender pour le point de terminaison [sur les fonctionnalités Android.](android-configure.md)



## <a name="related-topics"></a>Voir aussi
- [Déployer Microsoft Defender pour point de terminaison Android via Microsoft Intune](android-intune.md)
- [Configurer Microsoft Defender pour point de terminaison pour des fonctionnalités Android](android-configure.md)

