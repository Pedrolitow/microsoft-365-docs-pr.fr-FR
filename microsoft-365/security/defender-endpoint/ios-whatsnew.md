---
title: Nouveautés de Microsoft Defender pour point de terminaison sur iOS
description: Découvrez les principales modifications apportées aux versions précédentes de Microsoft Defender pour point de terminaison sur iOS.
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
ms.openlocfilehash: 7f3a687eb365813192948e48514bf7384cc584d0
ms.sourcegitcommit: 7e0094ddff54bcbe5d691dba58d4c4fb86f8b1a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2022
ms.locfileid: "65188202"
---
# <a name="whats-new-in-microsoft-defender-for-endpoint-on-ios"></a>Nouveautés de Microsoft Defender pour point de terminaison sur iOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)


## <a name="integration-with-tunnel"></a>Intégration à Tunnel
Microsoft Defender pour point de terminaison sur iOS peut désormais s’intégrer à Microsoft Tunnel, une solution de passerelle VPN pour activer la sécurité et la connectivité dans une seule application.  L’intégration à Tunnel offre une expérience VPN plus simple et sécurisée sur iOS avec une seule application. Cette fonctionnalité était auparavant disponible uniquement sur Android. Pour plus d’informations, [consultez le billet techcommunity ici](https://techcommunity.microsoft.com/t5/microsoft-endpoint-manager-blog/what-s-new-in-microsoft-endpoint-manager-2204-april-edition/ba-p/3297995)

## <a name="improved-experience-on-supervised-ios-devices"></a>Amélioration de l’expérience sur les appareils iOS supervisés

Microsoft Defender pour point de terminaison sur iOS dispose désormais d’une capacité spécialisée sur les appareils iOS/iPadOS supervisés, compte tenu des fonctionnalités de gestion accrues fournies par la plateforme sur ces types d’appareils. Il peut également fournir une protection web **sans configurer de VPN local sur l’appareil**. Cela offre aux utilisateurs finaux une expérience transparente tout en étant protégés contre le hameçonnage et d’autres attaques basées sur le web. Pour plus d’informations, consultez [cette documentation](ios-install.md#complete-deployment-for-supervised-devices)

## <a name="microsoft-defender-for-endpoint-is-now-microsoft-defender-in-the-app-store"></a>Microsoft Defender pour point de terminaison est désormais Microsoft Defender dans l’App Store

Microsoft Defender pour point de terminaison est désormais disponible en tant que **Microsoft Defender** dans l’App Store. Avec cette mise à jour, l’application sera disponible en préversion pour **les consommateurs de la région des États-Unis**. En fonction de la façon dont vous vous connectez à l’application avec votre compte professionnel ou personnel, vous avez accès aux fonctionnalités de Microsoft Defender pour point de terminaison ou aux fonctionnalités de Microsoft Defender pour les particuliers. Pour plus d’informations, consultez [ce blog](https://www.microsoft.com/en-us/microsoft-365/microsoft-defender-for-individuals).

## <a name="threat-and-vulnerability-management"></a>Gestion des menaces et des vulnérabilités

Le 25 janvier 2022, nous avons annoncé la disponibilité générale de la gestion des menaces et des vulnérabilités sur Android et iOS. Pour plus d’informations, consultez [le billet techcommunity ici](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/announcing-general-availability-of-vulnerability-management/ba-p/3071663).


## <a name="1128250101"></a>1.1.28250101
- **Intégration à Tunnel** - Microsoft Defender pour point de terminaison sur iOS peut désormais s’intégrer à Microsoft Tunnel, une solution de passerelle VPN pour activer la sécurité et la connectivité dans une seule application. Pour plus d’informations, consultez [La vue d’ensemble de Microsft Tunnel](/mem/intune/protect/microsoft-tunnel-overview).
- **L’intégration sans interaction tactile pour les appareils iOS inscrits** via Microsoft Endpoint Manager (Intune) est généralement disponible. Pour plus d’informations, consultez [l’intégration tactile Zero de Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/ios-install#zero-touch-onboarding-of-microsoft-defender-for-endpoint).
- Corrections de bogues.


## <a name="1124210103"></a>1.1.24210103

- Résolution des problèmes de connectivité Internet sur les appareils supervisés. Pour plus d’informations, consultez [Déployer Defender pour point de terminaison sur les appareils iOS inscrits](ios-install.md).
- Corrections de bogues.

## <a name="1123250104"></a>1.1.23250104

- Optimisation des performances : testez les performances de la batterie avec cette version et faites-nous part de vos commentaires.
- **Intégration sans contact pour les appareils iOS inscrits** : avec cette version, la préversion de l’intégration zero-touch pour les appareils inscrits via Microsoft Endpoint Manager (Intune) a été ajoutée. Pour plus d’informations, consultez cette [documentation](ios-install.md#zero-touch-onboarding-of-microsoft-defender-for-endpoint) pour plus d’informations sur l’installation et la configuration.
- **Contrôles de confidentialité** : configurez les contrôles de confidentialité pour le rapport d’alerte de hameçonnage. Pour plus d’informations, consultez [Configurer les fonctionnalités iOS](ios-configure-features.md).

## <a name="1123010101"></a>1.1.23010101

- Correctifs de bogues et améliorations des performances 
  - Des optimisations des performances ont été effectuées dans cette version. Testez les performances de la batterie avec cette version et faites-nous part de vos commentaires.

## <a name="1120240103"></a>1.1.20240103
- Carte d’intégrité de l’appareil : la carte Intégrité de l’appareil informe les utilisateurs finaux des mises à jour logicielles en attente.
- Améliorations de l’utilisation : les utilisateurs finaux peuvent désormais désactiver le VPN Defender pour point de terminaison à partir de l’application MSDefender elle-même. Avant cette mise à jour, les utilisateurs finaux devaient désactiver le VPN uniquement à partir de l’application Paramètres.
- Corrections de bogues.

## <a name="1120020101"></a>1.1.20020101
- Améliorations de l’expérience utilisateur : Microsoft Defender pour point de terminaison a une nouvelle apparence.
- Corrections de bogues.

## <a name="1117240101"></a>1.1.17240101
- La prise en charge de la gestion des applications mobiles (GAM) via Intune est généralement disponible avec cette version. Pour plus d’informations, consultez [Microsoft Defender pour point de terminaison signaux de risque disponibles pour vos stratégies de Protection d'applications](https://techcommunity.microsoft.com/t5/intune-customer-success/microsoft-defender-for-endpoint-risk-signals-available-for-your/ba-p/2186322)
- **La détection de jailbreak** est généralement disponible. Pour plus d’informations, consultez [la stratégie d’accès conditionnel d’installation basée sur les signaux de risque de l’appareil](ios-configure-features.md#conditional-access-with-defender-for-endpoint-on-ios).
- **La configuration automatique du profil VPN** pour les appareils inscrits via Microsoft Endpoint Manager (Intune) est généralement disponible. Pour plus d’informations, consultez [profil VPN de configuration automatique pour les appareils iOS inscrits](ios-install.md#auto-onboarding-of-vpn-profile-simplified-onboarding).
- Corrections de bogues.

## <a name="1115140101"></a>1.1.15140101

- **La détection de jailbreak** est en préversion. Pour plus d’informations, consultez [la stratégie d’accès conditionnel d’installation basée sur les signaux de risque de l’appareil](ios-configure-features.md#conditional-access-with-defender-for-endpoint-on-ios).
- **La configuration automatique du profil VPN** est en préversion pour les appareils inscrits via Microsoft Endpoint Manager (Intune). Pour plus d’informations, consultez [profil VPN de configuration automatique pour les appareils iOS inscrits](ios-install.md#auto-onboarding-of-vpn-profile-simplified-onboarding).
- Le nom du produit Microsoft Defender ATP a été mis à jour pour Microsoft Defender pour point de terminaison dans l’App Store.
- Amélioration de l’expérience de connexion.
- Corrections de bogues.

## <a name="1115010101"></a>1.1.15010101

- Avec cette version, nous annoncons la prise en charge des appareils iPadOS/iPad.
- Corrections de bogues.
