---
title: Microsoft Defender pour point de terminaison iOS
ms.reviewer: ''
description: Décrit comment installer et utiliser Microsoft Defender pour point de terminaison sur iOS
keywords: microsoft, defender, Microsoft Defender pour point de terminaison, ios, vue d’ensemble, installation, déploiement, désinstallation, intune
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365-initiative-defender-endpoint
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: dcc67b2d2a9ad03dc1235eebd577e3525ab07a03
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2022
ms.locfileid: "64665929"
---
# <a name="microsoft-defender-for-endpoint-on-ios"></a>Microsoft Defender pour point de terminaison iOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

**Microsoft Defender pour point de terminaison sur iOS** offre une protection contre le hameçonnage et les connexions réseau non sécurisées à partir de sites web, d’e-mails et d’applications. Toutes les alertes seront disponibles via un seul volet de verre dans le portail Microsoft 365 Defender. Le portail offre aux équipes de sécurité une vue centralisée des menaces sur les appareils iOS, ainsi que d’autres plateformes.

> [!CAUTION]
> L’exécution d’autres produits de protection de point de terminaison tiers avec Defender pour point de terminaison sur iOS est susceptible de provoquer des problèmes de performances et des erreurs système imprévisibles.

## <a name="pre-requisites"></a>Conditions préalables

**Pour les utilisateurs finaux**

- Microsoft Defender pour point de terminaison licence attribuée aux utilisateurs finaux de l’application. Consultez [Microsoft Defender pour point de terminaison exigences en matière de licences](/microsoft-365/security/defender-endpoint/minimum-requirements#licensing-requirements).

- **Pour les appareils inscrits** :
    - Les appareils sont [inscrits](/mem/intune/user-help/enroll-your-device-in-intune-ios) via l’application Portail d'entreprise Intune pour appliquer Intune stratégies de conformité des appareils. Pour ce faire, l’utilisateur final doit se voir attribuer une licence Microsoft Intune.
    - Portail d'entreprise Intune application peut être téléchargée à partir du [App Store Apple](https://apps.apple.com/us/app/intune-company-portal/id719171358).
    
    >[!NOTE]
    >Apple n’autorise pas les utilisateurs à télécharger d’autres applications à partir de l’App Store. Cette étape doit donc être effectuée par l’utilisateur avant l’intégration à Microsoft Defender pour point de terminaison’application.)
    
    - Les appareils sont inscrits auprès de Azure Active Directory. Pour ce faire, l’utilisateur final doit être connecté via [Microsoft Authenticator’application](https://apps.apple.com/app/microsoft-authenticator/id983156458).

- **Pour les appareils non inscrits** : les appareils sont inscrits auprès de Azure Active Directory. Pour ce faire, l’utilisateur final doit être connecté via [Microsoft Authenticator’application](https://apps.apple.com/app/microsoft-authenticator/id983156458).

- Pour plus d’informations sur l’attribution de licences, consultez [Affecter des licences aux utilisateurs](/azure/active-directory/users-groups-roles/licensing-groups-assign).

**Pour les administrateurs**

- Accès au portail Microsoft 365 Defender.

- Accès au [centre d’administration Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), pour :
   - Déployez l’application sur des groupes d’utilisateurs inscrits dans votre organisation.
   - Configurer Microsoft Defender pour point de terminaison signaux de risque dans la stratégie de protection des applications (GAM)


    > [!NOTE]
    > - Microsoft Defender pour point de terminaison étend désormais la protection aux données d’une organisation au sein d’une application managée pour ceux qui n’utilisent pas la gestion des appareils mobiles (GPM), mais qui utilisent Intune pour gérer les applications mobiles. Il étend également ce support aux clients qui utilisent d’autres solutions de gestion de la mobilité d’entreprise, tout en continuant à utiliser Intune pour [la gestion des applications mobiles (MAM).](/mem/intune/apps/mam-faq)
    > - En outre, Microsoft Defender pour point de terminaison prend déjà en charge les appareils inscrits à l’aide de Intune gestion des appareils mobiles (GPM).  

**Configuration requise**

- Appareil iOS exécutant iOS 12.0 et versions ultérieures. Les iPad sont également pris en charge. *Notez qu’à compter du 31 mars 2022, la version minimale d’iOS prise en charge par Microsoft Defender pour point de terminaison sera iOS 13.0.*

- L’appareil est inscrit auprès de [l’application Portail d'entreprise Intune](https://apps.apple.com/us/app/intune-company-portal/id719171358) ou inscrit auprès de Azure Active Directory via [Microsoft Authenticator](https://apps.apple.com/app/microsoft-authenticator/id983156458) avec le même compte.

## <a name="installation-instructions"></a>Instructions d’installation

Le déploiement de Microsoft Defender pour point de terminaison sur iOS peut être effectué via Microsoft Endpoint Manager (MEM) et les appareils supervisés et non supervisés sont pris en charge. Les utilisateurs finaux peuvent également installer directement l’application à partir de [l’App Store Apple](https://aka.ms/mdatpiosappstore).

- Pour plus d’informations sur le déploiement sur des appareils inscrits via Microsoft Endpoint Manager ou Intune, consultez [Déployer Microsoft Defender pour point de terminaison sur iOS](ios-install.md).
- Pour plus d’informations sur l’utilisation de Defender pour point de terminaison dans la stratégie de protection des applications (MAM), consultez [Configurer la stratégie de protection des applications pour inclure les signaux de risque Defender pour point de terminaison (MAM)](ios-install-unmanaged.md)

## <a name="resources"></a>Ressources

- Restez informé des prochaines versions en visitant [les nouveautés de Microsoft Defender pour point de terminaison sur iOS](ios-whatsnew.md) ou notre [blog](https://techcommunity.microsoft.com/t5/microsoft-defender-atp/bg-p/MicrosoftDefenderATPBlog/label-name/iOS).

- Fournir des commentaires via le système de commentaires dans l’application ou via la [console de sécurité unifiée](https://security.microsoft.com)

## <a name="next-steps"></a>Prochaines étapes

- [Déployer Microsoft Defender pour point de terminaison sur iOS via Intune pour les appareils inscrits](ios-install.md)
- [Configurer la stratégie de protection des applications pour inclure les signaux de risque defender pour point de terminaison (MAM)](ios-install-unmanaged.md)
- [Configurer Microsoft Defender pour point de terminaison sur les fonctionnalités iOS](ios-configure-features.md)
- [Configurer la stratégie d’accès conditionnel en fonction du score de risque de l’appareil à partir de Microsoft Defender pour point de terminaison](ios-configure-features.md#conditional-access-with-defender-for-endpoint-on-ios)
- [Notions de base de la gestion des applications mobiles (MAM)](/mem/intune/apps/app-management#mobile-application-management-mam-basics)
