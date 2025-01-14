---
title: Nouveautés de Microsoft Defender pour point de terminaison sur iOS
description: Découvrez les principales modifications apportées aux versions précédentes de Microsoft Defender pour point de terminaison sur iOS.
keywords: microsoft, defender, Microsoft Defender pour point de terminaison, mac, installation, macos, whatsnew
ms.service: microsoft-365-security
ms.mktglfcycl: security
ms.sitesec: library
ms.pagetype: security
ms.author: sunasing
author: sunasing
ms.localizationpriority: medium
manager: sunasing
audience: ITPro
ms.collection:
- m365-security
- tier3
ms.topic: reference
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: e725a6ee7f39593a5a8eeff7c6e5885552a59624
ms.sourcegitcommit: a20d30f4e5027f90d8ea4cde95d1d5bacfdd2b5e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2022
ms.locfileid: "68768520"
---
# <a name="whats-new-in-microsoft-defender-for-endpoint-on-ios"></a>Nouveautés de Microsoft Defender pour point de terminaison sur iOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

## <a name="vulnerability-assessment-of-apps"></a>Évaluation des vulnérabilités des applications

L’évaluation des vulnérabilités des applications sur Microsoft Defender pour point de terminaison pour iOS est désormais en préversion publique. Defender pour point de terminaison sur iOS prend en charge les évaluations des vulnérabilités des applications uniquement pour les appareils inscrits (GPM). Pour plus d’informations, consultez [Configurer l’évaluation des vulnérabilités des applications](/microsoft-365/security/defender-endpoint/ios-configure-features#configure-vulnerability-assessment-of-apps). Si vous souhaitez participer à la préversion, partagez le nom et l’ID de votre locataire avec nous : mdatpmobile@microsoft.com.

## <a name="network-protection"></a>Protection réseau

La protection réseau sur Microsoft Defender pour point de terminaison est désormais disponible. La protection réseau offre une protection contre les menaces non fiables Wi-Fi associées, le matériel non autorisé comme les appareils ananas et avertit l’utilisateur si une menace associée est détectée. Les utilisateurs voient également une expérience guidée pour se connecter à des réseaux sécurisés et changer de réseau lorsqu’ils sont connectés à une connexion non sécurisée.

Il inclut plusieurs contrôles d’administration pour offrir de la flexibilité, comme la possibilité de configurer la fonctionnalité à partir du centre de Administration Microsoft Endpoint Manager. Les administrateurs peuvent également activer les contrôles de confidentialité pour configurer les données envoyées par Defender pour point de terminaison à partir d’appareils iOS. Pour plus d’informations, consultez [Configurer la protection réseau](/microsoft-365/security/defender-endpoint/ios-configure-features#configure-network-protection).

La protection réseau pour iOS est déjà activée pour votre locataire. Les utilisateurs finaux qui testent la fonctionnalité de protection réseau peuvent installer la préversion de l’application via TestFlight. Accédez à https://aka.ms/mdeiospp sur l’appareil iOS. Cela vous invite à installer l’application TestFlight sur votre appareil ou à ouvrir TestFlight si elle est déjà installée. Dans l’application TestFlight, suivez les instructions à l’écran pour installer Microsoft Defender Point de terminaison. Vérifiez que le numéro de version de MDE est 1.1.33070102.

## <a name="privacy-controls"></a>Contrôles de confidentialité

Microsoft Defender pour point de terminaison sur iOS active les contrôles de confidentialité pour les administrateurs et les utilisateurs finaux. Cela inclut les contrôles pour les appareils inscrits (GPM) et non inscrits (GAM). Les administrateurs peuvent configurer la confidentialité dans le rapport d’alerte d’hameçonnage, tandis que les utilisateurs finaux peuvent configurer les informations partagées avec leur organisation.

## <a name="optional-permissions-and-disable-web-protection"></a>Autorisations facultatives et désactiver la protection web

Microsoft Defender pour point de terminaison sur iOS active les **autorisations facultatives** dans le flux d’intégration. Actuellement, les autorisations requises par MDE sont obligatoires dans le flux d’intégration. Avec cette fonctionnalité, l’administrateur peut déployer MDE sur des appareils BYOD sans appliquer **l’autorisation VPN** obligatoire lors de l’intégration. Les utilisateurs finaux peuvent intégrer l’application sans les autorisations obligatoires et peuvent passer en revue ces autorisations ultérieurement. Cette fonctionnalité est actuellement présente uniquement pour les appareils inscrits (GPM).

Avec **Désactiver la protection web**, les clients qui ne souhaitent pas configurer un VPN peuvent configurer pour désactiver **la protection web** et déployer MDE sans cette fonctionnalité. D’autres fonctionnalités MDE continueront de fonctionner. Cette configuration est disponible pour les appareils inscrits (MDM) ainsi que pour les appareils non inscrits (GAM).

## <a name="integration-with-tunnel"></a>Intégration à Tunnel

Microsoft Defender pour point de terminaison sur iOS peuvent désormais s’intégrer à Microsoft Tunnel, une solution de passerelle VPN pour activer la sécurité et la connectivité dans une seule application.  L’intégration à Tunnel offre une expérience VPN plus simple et sécurisée sur iOS avec une seule application. Cette fonctionnalité était auparavant disponible uniquement sur Android. Pour plus d’informations, [consultez le billet techcommunity ici](https://techcommunity.microsoft.com/t5/microsoft-endpoint-manager-blog/what-s-new-in-microsoft-endpoint-manager-2204-april-edition/ba-p/3297995)

## <a name="improved-experience-on-supervised-ios-devices"></a>Amélioration de l’expérience sur les appareils iOS supervisés

Microsoft Defender pour point de terminaison sur iOS dispose désormais d’une capacité spécialisée sur les appareils iOS/iPadOS supervisés, compte tenu des fonctionnalités de gestion accrues fournies par la plateforme sur ces types d’appareils. Il peut également fournir une protection web **sans configurer de VPN local sur l’appareil**. Cela offre aux utilisateurs finaux une expérience transparente tout en étant protégés contre le hameçonnage et d’autres attaques web. Pour plus d’informations, consultez [cette documentation](ios-install.md#complete-deployment-for-supervised-devices).

## <a name="microsoft-defender-for-endpoint-is-now-microsoft-defender-in-the-app-store"></a>Microsoft Defender pour point de terminaison est maintenant Microsoft Defender dans l’App Store

Microsoft Defender pour point de terminaison est désormais disponible en tant que **Microsoft Defender** dans l’App Store. Avec cette mise à jour, l’application sera disponible en préversion pour **les consommateurs de la région États-Unis**. En fonction de la façon dont vous vous connectez à l’application avec votre compte professionnel ou personnel, vous aurez accès aux fonctionnalités pour Microsoft Defender pour point de terminaison ou aux fonctionnalités de Microsoft Defender pour les particuliers. Pour plus d’informations, consultez [ce billet de blog](https://www.microsoft.com/microsoft-365/microsoft-defender-for-individuals).

## <a name="vulnerability-management"></a>Gestion des vulnérabilités

Le 25 janvier 2022, nous avons annoncé la disponibilité générale de la gestion des vulnérabilités sur Android et iOS. Pour plus d’informations, consultez [le billet techcommunity ici](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/announcing-general-availability-of-vulnerability-management/ba-p/3071663).

## <a name="1128250101"></a>1.1.28250101
- **Intégration à Tunnel** : Microsoft Defender pour point de terminaison sur iOS peuvent désormais s’intégrer à Microsoft Tunnel, une solution de passerelle VPN pour activer la sécurité et la connectivité dans une seule application. Pour plus d’informations, consultez [Vue d’ensemble de Microsoft Tunnel](/mem/intune/protect/microsoft-tunnel-overview).
- **L’intégration sans contact pour les appareils iOS inscrits** via Microsoft Endpoint Manager (Intune) est en disponibilité générale. Pour plus d’informations, consultez [Intégration sans contact de Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/ios-install#zero-touch-onboarding-of-microsoft-defender-for-endpoint).
- Corrections de bogues.

## <a name="1124210103"></a>1.1.24210103

- Résolution des problèmes de connectivité Internet sur les appareils supervisés. Pour plus d’informations, consultez [Déployer Defender pour point de terminaison sur des appareils iOS inscrits](ios-install.md).
- Corrections de bogues.

## <a name="1123250104"></a>1.1.23250104

- Optimisations des performances : testez les performances de la batterie avec cette version et faites-nous part de vos commentaires.
- **Intégration sans contact pour les appareils iOS inscrits** : avec cette version, la préversion de l’intégration zero-touch pour les appareils inscrits via Microsoft Endpoint Manager (Intune) a été ajoutée. Pour plus d’informations, consultez cette [documentation](ios-install.md#zero-touch-onboarding-of-microsoft-defender-for-endpoint) pour plus d’informations sur l’installation et la configuration.
- **Contrôles de confidentialité** : configurez les contrôles de confidentialité pour le rapport d’alerte d’hameçonnage. Pour plus d’informations, consultez [Configurer les fonctionnalités iOS](ios-configure-features.md).

## <a name="1123010101"></a>1.1.23010101

- Correctifs de bogues et améliorations des performances 
  - Des optimisations des performances ont été effectuées dans cette version. Testez les performances de la batterie avec cette version et faites-nous part de vos commentaires.

## <a name="1120240103"></a>1.1.20240103
- Carte d’intégrité de l’appareil : la carte d’intégrité de l’appareil informe les utilisateurs finaux des mises à jour logicielles en attente.
- Améliorations de la facilité d’utilisation : les utilisateurs finaux peuvent désormais désactiver le VPN Defender pour point de terminaison à partir de l’application Microsoft Defender elle-même. Avant cette mise à jour, les utilisateurs finaux devaient désactiver le VPN uniquement à partir de l’application Paramètres.
- Corrections de bogues.

## <a name="1120020101"></a>1.1.20020101
- Améliorations de l’expérience utilisateur : Microsoft Defender pour point de terminaison a une nouvelle apparence.
- Corrections de bogues.

## <a name="1117240101"></a>1.1.17240101
- La prise en charge de la gestion des applications mobiles (MAM) via Intune est généralement disponible avec cette version. Pour plus d’informations, consultez [Microsoft Defender pour point de terminaison signaux de risque disponibles pour vos stratégies de Protection d'applications](https://techcommunity.microsoft.com/t5/intune-customer-success/microsoft-defender-for-endpoint-risk-signals-available-for-your/ba-p/2186322)
- **La détection de jailbreak** est en disponibilité générale. Pour plus d’informations, consultez [Configurer une stratégie d’accès conditionnel basée sur les signaux de risque de l’appareil](ios-configure-features.md#conditional-access-with-defender-for-endpoint-on-ios).
- **La configuration automatique du profil VPN** pour les appareils inscrits via Microsoft Endpoint Manager (Intune) est généralement disponible. Pour plus d’informations, consultez Configuration automatique du [profil VPN pour les appareils iOS inscrits](ios-install.md#auto-onboarding-of-vpn-profile-simplified-onboarding).
- Corrections de bogues.

## <a name="1115140101"></a>1.1.15140101

- **La détection de jailbreak** est en préversion. Pour plus d’informations, consultez [Configurer une stratégie d’accès conditionnel basée sur les signaux de risque de l’appareil](ios-configure-features.md#conditional-access-with-defender-for-endpoint-on-ios).
- **La configuration automatique du profil VPN** est en préversion pour les appareils inscrits via Microsoft Endpoint Manager (Intune). Pour plus d’informations, consultez Configuration automatique du [profil VPN pour les appareils iOS inscrits](ios-install.md#auto-onboarding-of-vpn-profile-simplified-onboarding).
- Le nom du produit Microsoft Defender ATP a maintenant été mis à jour pour Microsoft Defender pour point de terminaison dans l’App Store.
- Expérience de connexion améliorée.
- Corrections de bogues.

## <a name="1115010101"></a>1.1.15010101

- Avec cette version, nous annonçons la prise en charge des appareils iPadOS/iPad.
- Corrections de bogues.
