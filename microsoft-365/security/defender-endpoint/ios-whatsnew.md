---
title: Nouveautés de Microsoft Defender pour Endpoint sur iOS
description: Découvrez les principales modifications apportées aux versions précédentes de Microsoft Defender pour Endpoint sur iOS.
keywords: microsoft, defender, Microsoft Defender pour point de terminaison, mac, installation, macos, whatsnew
ms.prod: m365-security
ms.mktglfcycl: security
ms.sitesec: library
ms.pagetype: security
ms.author: sunasing
author: sunasing
ms.localizationpriority: medium
manager: sunasing
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: reference
ms.technology: mde
ms.openlocfilehash: 723dc6a70d9a8d37ef05cb301c41f0fea3911da9
ms.sourcegitcommit: 007822d16e332522546e948f5c216327254a4d49
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/17/2022
ms.locfileid: "62879143"
---
# <a name="whats-new-in-microsoft-defender-for-endpoint-on-ios"></a>Nouveautés de Microsoft Defender pour Endpoint sur iOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

## <a name="improved-experience-on-supervised-ios-devices"></a>Expérience améliorée sur les appareils iOS supervisés

Microsoft Defender pour Endpoint sur iOS dispose désormais d’une capacité spécialisée sur les appareils iOS/iPadOS supervisés, étant donné les fonctionnalités de gestion accrues fournies par la plateforme sur ces types d’appareils. Il peut également fournir une protection Web **sans configuration d’un VPN local sur l’appareil**. Cela offre aux utilisateurs finaux une expérience transparente tout en étant protégé contre le hameçonnage et d’autres attaques basées sur le web. Pour plus d’informations, consultez [cette documentation](ios-install.md#complete-deployment-for-supervised-devices)

## <a name="microsoft-defender-for-endpoint-is-now-microsoft-defender-in-the-app-store"></a>Microsoft Defender pour le point de terminaison est désormais Microsoft Defender dans l’App Store

Microsoft Defender pour le point de terminaison est désormais disponible en **tant que Microsoft Defender** dans l’App Store. Avec cette mise à jour, l’application sera disponible en prévisualisation pour les **consommateurs de la région des États-Unis**. En fonction de la façon dont vous vous connectez à l’application avec votre compte personnel ou personnel, vous aurez accès aux fonctionnalités de Microsoft Defender pour point de terminaison ou aux fonctionnalités de Microsoft Defender pour les individus. Pour plus d’informations, [consultez ce blog](https://www.microsoft.com/microsoft-365/microsoft-defender-for-individuals).

## <a name="threat-and-vulnerability-management"></a>Gestion des menaces et des vulnérabilités

Le 25 janvier 2022, nous avons annoncé la disponibilité générale de la gestion des menaces et des vulnérabilités sur Android et iOS. Pour plus d’informations, [consultez la publication techcommunity ici](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/announcing-general-availability-of-vulnerability-management/ba-p/3071663).

## <a name="1124210103"></a>1.1.24210103

- Résolution des problèmes de connectivité Internet sur les appareils supervisés. Pour plus d’informations, [voir Deploy Defender for Endpoint sur les appareils iOS inscrits](ios-install.md).
- Corrections de bogues.

## <a name="1123250104"></a>1.1.23250104

- Optimisation des performances : testez les performances de la batterie avec cette version et faites-nous part de vos commentaires.
- Intégration zero touch pour les appareils **iOS** inscrits : avec cette version, l’aperçu de l’intégration zero touch pour les appareils inscrits via Microsoft Endpoint Manager (Intune) a été ajouté. Pour plus d’informations, [consultez cette documentation](ios-install.md#zero-touch-onboarding-of-microsoft-defender-for-endpoint-preview) pour plus d’informations sur l’installation et la configuration.
- **Contrôles de confidentialité** : configurez les contrôles de confidentialité pour le rapport d’alerte de hameçonnage. Pour plus d’informations, voir [Configurer les fonctionnalités iOS](ios-configure-features.md).

## <a name="1123010101"></a>1.1.23010101

- Résolutions de bogues et améliorations des performances 
  - Des optimisations des performances ont été réalisées dans cette version. Testez les performances de la batterie avec cette version et faites-nous part de vos commentaires.

## <a name="1120240103"></a>1.1.20240103
- Carte d’état de l’appareil : la carte d’état de l’appareil avertit les utilisateurs finaux des mises à jour logicielles en attente.
- Améliorations de la convivialité : les utilisateurs finaux peuvent désormais désactiver le VPN Defender pour point de terminaison à partir de l’application MSDefender elle-même. Avant cette mise à jour, les utilisateurs finaux deviez désactiver le VPN uniquement à partir de l’Paramètres’application.
- Corrections de bogues.

## <a name="1120020101"></a>1.1.20020101
- Améliorations de l’UX : Microsoft Defender pour point de terminaison a une nouvelle apparence.
- Corrections de bogues.

## <a name="1117240101"></a>1.1.17240101
- La prise en charge de la gestion des applications mobiles (MAM) via Intune est généralement disponible avec cette version. Pour plus d’informations, [voir Microsoft Defender pour les signaux de risque de point de terminaison disponibles pour vos stratégies de protection des applications](https://techcommunity.microsoft.com/t5/intune-customer-success/microsoft-defender-for-endpoint-risk-signals-available-for-your/ba-p/2186322)
- **La détection d’jailbreak** est généralement disponible. Pour plus d’informations, voir [La stratégie d’accès conditionnel de configuration basée sur les signaux de risque de l’appareil](ios-configure-features.md#conditional-access-with-defender-for-endpoint-on-ios).
- **La configuration automatique du profil VPN pour** les appareils inscrits via Microsoft Endpoint Manager (Intune) est généralement disponible. Pour plus d’informations, [voir profil VPN de configuration automatique pour les appareils iOS inscrits](ios-install.md#auto-onboarding-of-vpn-profile-simplified-onboarding).
- Corrections de bogues.

## <a name="1115140101"></a>1.1.15140101

- **La détection jailbreak** est en prévisualisation. Pour plus d’informations, voir [La stratégie d’accès conditionnel de configuration basée sur les signaux de risque de l’appareil](ios-configure-features.md#conditional-access-with-defender-for-endpoint-on-ios).
- **La configuration automatique du profil VPN** est en prévisualisation pour les appareils inscrits via Microsoft Endpoint Manager (Intune). Pour plus d’informations, [voir profil VPN de configuration automatique pour les appareils iOS inscrits](ios-install.md#auto-onboarding-of-vpn-profile-simplified-onboarding).
- Le nom du produit Microsoft Defender ATP a été mis à jour vers Microsoft Defender pour le point de terminaison dans l’App Store.
- Amélioration de l’expérience de la signature.
- Corrections de bogues.

## <a name="1115010101"></a>1.1.15010101

- Avec cette version, nous anifions la prise en charge des appareils iPadOS/iPad.
- Corrections de bogues.
