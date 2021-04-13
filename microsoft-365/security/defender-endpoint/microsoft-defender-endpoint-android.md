---
title: Microsoft Defender ATP sur Android
ms.reviewer: ''
description: Décrit comment installer et utiliser Microsoft Defender ATP pour Android
keywords: microsoft, defender, atp, android, installation, déployer, désinstallation, intune
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
ms.openlocfilehash: 32c42691b3a2b43f9740da26084bf45af0ee80f5
ms.sourcegitcommit: 3fe7eb32c8d6e01e190b2b782827fbadd73a18e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/13/2021
ms.locfileid: "51687780"
---
# <a name="microsoft-defender-for-endpoint-on-android"></a>Microsoft Defender pour point de terminaison sur Android

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez découvrir Microsoft Defender pour le point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink)

Cette rubrique décrit comment installer, configurer, mettre à jour et utiliser Defender pour Endpoint pour Android.

> [!CAUTION]
> L'exécution d'autres produits de protection de point de terminaison tiers avec Defender pour Endpoint pour Android est susceptible de provoquer des problèmes de performances et des erreurs système imprévisibles.


## <a name="how-to-install-microsoft-defender-for-endpoint-on-android"></a>Comment installer Microsoft Defender pour le point de terminaison sur Android

### <a name="prerequisites"></a>Conditions préalables

-   **Pour les utilisateurs finaux**

    -   Licence Microsoft Defender pour point de terminaison attribuée à l'utilisateur final de l'application. Voir [microsoft Defender pour les conditions requises pour les licences de point de terminaison](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/minimum-requirements#licensing-requirements)

    -   L'application Portail d'entreprise Intune peut être téléchargée à partir de [Google Play](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal) et est disponible sur l'appareil Android.

        -   En outre, les appareils peuvent être inscrits [via](https://docs.microsoft.com/mem/intune/user-help/enroll-device-android-company-portal) l'application Portail d'entreprise Intune pour appliquer les stratégies de conformité des appareils Intune. Pour ce faire, l'utilisateur final doit se voir attribuer une licence Microsoft Intune.

    -   Pour plus d'informations sur l'attribution de licences, voir [Attribuer des licences aux utilisateurs.](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-groups-assign)
        

-   **Pour les administrateurs**

    -   Accès au portail Centre de sécurité Microsoft Defender.

        > [!NOTE]
        > Microsoft Intune est la seule solution de gestion des périphériques mobiles (MDM) prise en charge pour le déploiement de Microsoft Defender pour Endpoint sur Android. Actuellement, seuls les appareils inscrits sont pris en charge pour l'application de Defender for Endpoint pour les stratégies de conformité des appareils android dans Intune. 

    -   Accédez [au Centre d'administration Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431)pour déployer l'application sur les groupes d'utilisateurs inscrits dans votre organisation.

### <a name="system-requirements"></a>Configuration requise

-   Appareils Android exécutant Android 6.0 et version supérieure.
-   L'application Portail d'entreprise Intune est téléchargée à partir [de Google Play](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal) et installée. L'inscription des appareils est requise pour que les stratégies de conformité des appareils Intune soient appliquées.

### <a name="installation-instructions"></a>Instructions d'installation

Microsoft Defender pour Endpoint sur Android prend en charge l'installation sur les deux modes d'appareils inscrits : les modes Administrateur d'appareil et Android Entreprise hérités.
**Actuellement, les appareils personnels avec profil de travail et les inscriptions d'appareils utilisateur entièrement gérées par l'entreprise sont pris en charge dans Android Entreprise. La prise en charge d'autres modes Android Enterprise sera annoncée lorsque vous serez prêt.**

Le déploiement de Microsoft Defender pour Endpoint sur Android est via Microsoft Intune (MDM).
Pour plus d'informations, voir [Déployer Microsoft Defender pour endpoint sur Android avec Microsoft Intune.](android-intune.md)


> [!NOTE]
> **Microsoft Defender pour le point de terminaison sur Android est désormais disponible [sur Google Play.](https://play.google.com/store/apps/details?id=com.microsoft.scmx)** <br> Vous pouvez vous connecter à Google Play à partir d'Intune pour déployer l'application Microsoft Defender pour endpoint, sur les modes d'inscription Administrateur d'appareil et Android Entreprise. 

## <a name="how-to-configure-microsoft-defender-for-endpoint-on-android"></a>Comment configurer Microsoft Defender pour endpoint sur Android

Des instructions sur la configuration de Microsoft Defender pour endpoint sur les fonctionnalités Android sont disponibles dans [Configurer Microsoft Defender pour endpoint sur les fonctionnalités Android.](android-configure.md)



## <a name="related-topics"></a>Voir aussi
- [Déployer Microsoft Defender pour endpoint sur Android avec Microsoft Intune](android-intune.md)
- [Configurer Microsoft Defender pour le point de terminaison sur les fonctionnalités Android](android-configure.md)

