---
title: Microsoft Defender pour point de terminaison iOS
ms.reviewer: ''
description: Décrit comment installer et utiliser Microsoft Defender pour endpoint sur iOS
keywords: microsoft, defender, Microsoft Defender for Endpoint, ios, overview, installation, deploy, uninstallation, intune
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 658aba2a3061e247c9be0aaa159708bb24e97a20649fa67c2ceba0aa127e48b3
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53894238"
---
# <a name="microsoft-defender-for-endpoint-on-ios"></a>Microsoft Defender pour point de terminaison iOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

**Microsoft Defender pour endpoint sur iOS** offre une protection contre le hameçonnage et les connexions réseau non sécurisées à partir de sites web, de courriers électroniques et d’applications. Toutes les alertes seront disponibles par le biais d’un seul volet de la Centre de sécurité Microsoft Defender. Le portail offre aux équipes de sécurité une vue centralisée des menaces sur les appareils iOS, ainsi que d’autres plateformes.

> [!CAUTION]
> L’exécution d’autres produits de protection des points de terminaison tiers avec Defender for Endpoint sur iOS est susceptible de provoquer des problèmes de performances et des erreurs système imprévisibles.

## <a name="pre-requisites"></a>Conditions préalables

**Pour les utilisateurs finaux**

- Licence Microsoft Defender pour point de terminaison attribuée à l’utilisateur final de l’application. Consultez [Microsoft Defender pour les conditions requises pour les licences de point de terminaison.](/microsoft-365/security/defender-endpoint/minimum-requirements#licensing-requirements)

- **Pour les appareils inscrits**: les appareils sont inscrits [via](/mem/intune/user-help/enroll-your-device-in-intune-ios) l’application Portail d’entreprise Intune pour appliquer les stratégies de conformité des appareils Intune. Pour ce faire, l’utilisateur final doit se voir attribuer Microsoft Intune licence.
    - Portail d’entreprise Intune’application peut être téléchargée à partir de [l’App Store d’Apple.](https://apps.apple.com/us/app/intune-company-portal/id719171358)
    - Notez qu’Apple n’autorise pas la redirection des utilisateurs à télécharger d’autres applications à partir de l’App Store et que cette étape doit donc être effectuée par l’utilisateur avant l’intégration à l’application Microsoft Defender pour endpoint.

- **Pour les appareils non inscrits**: les appareils sont inscrits auprès Azure Active Directory. Pour ce faire, l’utilisateur final doit être [Microsoft Authenticator’application.](https://apps.apple.com/app/microsoft-authenticator/id983156458)

- Pour plus d’informations sur l’attribution de licences, voir [Attribuer des licences aux utilisateurs.](/azure/active-directory/users-groups-roles/licensing-groups-assign)

**Pour les administrateurs**

- Accès au portail Centre de sécurité Microsoft Defender web.

- Accès à [Microsoft Endpoint Manager centre d’administration,](https://go.microsoft.com/fwlink/?linkid=2109431)pour déployer l’application pour les groupes d’utilisateurs inscrits dans votre organisation.

    > [!NOTE]
    > Microsoft Intune est la seule solution de gestion des points de terminaison unifiée (UEM) prise en charge pour le déploiement de Microsoft Defender pour Endpoint et l’application de Defender pour les stratégies de conformité des appareils liées aux points de terminaison dans Intune.

**Configuration requise**

- Appareil iOS exécutant iOS 11.0 et supérieur. iPad sont officiellement pris en charge à partir de la version 1.1.15010101 et versions antérieures.

- L’appareil est inscrit auprès de [l’application Portail d’entreprise Intune ou](https://apps.apple.com/us/app/intune-company-portal/id719171358) inscrit auprès Azure Active Directory via [Microsoft Authenticator](https://apps.apple.com/app/microsoft-authenticator/id983156458).

## <a name="installation-instructions"></a>Instructions d’installation

Le déploiement de Microsoft Defender pour Endpoint sur iOS peut être effectué via Microsoft Endpoint Manager (MEM) et les appareils supervisés et non pris en charge. Les utilisateurs finaux peuvent également installer directement l’application à partir de [l’App Store d’Apple.](https://aka.ms/mdatpiosappstore)
Pour plus d’informations, [voir Déployer Microsoft Defender pour endpoint sur iOS.](ios-install.md)

## <a name="resources"></a>Ressources

- Restez informé des prochaines publication en visitant les nouveautés de [Microsoft Defender pour Endpoint sur iOS](ios-whatsnew.md) ou notre [blog.](https://techcommunity.microsoft.com/t5/microsoft-defender-atp/bg-p/MicrosoftDefenderATPBlog/label-name/iOS)

- Fournir des commentaires via le système de commentaires dans l’application ou via [le portail SecOps](https://securitycenter.microsoft.com)

## <a name="next-steps"></a>Étapes suivantes

- [Déployer Microsoft Defender pour le point de terminaison sur iOS](ios-install.md)
- [Configurer Microsoft Defender pour endpoint sur les fonctionnalités iOS](ios-configure-features.md)
- [Configurer la stratégie de protection des applications pour inclure les signaux de risque de Point de terminaison Defender (MAM)](ios-install-unmanaged.md)
- [Configurer une stratégie d’accès conditionnel basée sur le score de risque de l’appareil de Microsoft Defender pour endpoint](ios-configure-features.md#conditional-access-with-defender-for-endpoint-on-ios)
