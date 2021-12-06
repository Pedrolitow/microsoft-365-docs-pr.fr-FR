---
title: Activer l’intégration de Microsoft Defender pour IoT dans Microsoft Defender pour endpoint
description: Permettre à Microsoft Defender pour l’intégration IoT d’obtenir une visibilité axée sur les appareils IoT/OT dans les zones du réseau où MDE n’est pas déployé
keywords: activer un connecteur siem, un siem, un connecteur, des informations de sécurité et des événements
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: siosulli
author: siosulli
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: a5e62e982603ef62d4b2d0c8d0edf21223e3b98c
ms.sourcegitcommit: 2a4dddf7c655b44b17d4fd7f5e1e5d8a6e2b7aef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/06/2021
ms.locfileid: "61312013"
---
# <a name="enable-microsoft-defender-for-iot-integration"></a>Activer Microsoft Defender pour l’intégration IoT

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!include[Prerelease information](../../includes/prerelease.md)]

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-enablesiem-abovefoldlink)

Microsoft Defender pour le point de terminaison peut désormais s’intégrer à Microsoft Defender pour IoT. Cette intégration étend vos fonctionnalités de découverte d’appareils avec les fonctionnalités de surveillance sans agent fournies par Microsoft Defender pour IoT. Cela permet de sécuriser les appareils IoT d’entreprise connectés aux réseaux informatiques, tels que les appareils VoIP (Voice over Internet Protocol), les imprimantes et les appareils photo. Il permet aux organisations de tirer parti d’une solution intégrée unique qui sécurisation l’ensemble de leur infrastructure IoT et des technologies opérationnelles. Pour plus d’informations, [voir Microsoft Defender pour IoT.](/azure/defender-for-iot/organizations/overview)

Avec cette intégration activée, Microsoft Defender pour point de terminaison gagne en visibilité pour vous aider à localiser, identifier et sécuriser les appareils IoT dans votre réseau. Les appareils IoT découverts par Microsoft Defender pour IoT ou Microsoft Defender pour point de terminaison seront synchronisés automatiquement sur les deux portails. Vous aurez ainsi une vue unifiée de l’inventaire complet de votre ot/IoT, ainsi que du reste de vos appareils informatiques (stations de travail, serveurs et appareils mobiles).

Microsoft Defender pour IoT inclut également un capteur réseau déployable qui fournit une source de données supplémentaire. La configuration d’un capteur réseau dans le cadre de votre intégration vous offre la vue la plus complète de vos appareils IoT et ot, en particulier pour les segments réseau où les capteurs Microsoft Defender pour les points de terminaison ne sont pas présents et lorsque les employés accèdent aux informations à distance.

## <a name="prerequisites"></a>Configuration requise

Pour activer Microsoft Defender pour IoT, l’utilisateur doit avoir les rôles suivants :

- Administrateur général du client dans Azure Active Directory
- Administrateur de sécurité pour l’abonnement Azure qui sera utilisé pour l’intégration de Microsoft Defender pour IoT

## <a name="enabling-the-microsoft-defender-for-iot-integration"></a>Activation de Microsoft Defender pour l’intégration IoT

1. Dans le volet de navigation du portail, sélectionnez Paramètres détection d’appareil [https://security.microsoft.com](https://security.microsoft.com/)  \>  \> **Microsoft Defender pour IoT**.

    ![Image de la configuration de l’intégration IoT.](images/enable-defender-for-iot.png)

2. **Sélectionnez un abonnement Azure dans** la liste des abonnements disponibles dans votre client Azure Active Directory et sélectionnez **Enregistrer.**

## <a name="set-up-a-network-sensor"></a>Configurer un capteur réseau

Avec un abonnement Azure sélectionné, vous pouvez ajouter un capteur réseau.

Pour ajouter un capteur réseau, sous Configurer les capteurs **réseau,** choisissez le lien **Microsoft Defender pour IoT.** Cela vous permet d’intégrer le processus de configuration du capteur dans le portail Azure. Pour plus d’informations, voir [Gérer les capteurs avec Defender pour IoT dans le portail Azure.](/azure/defender-for-iot/organizations/how-to-manage-sensors-on-the-cloud)

## <a name="turn-off-subscription-integration"></a>Désactiver l’intégration des abonnements

Vous pouvez désactiver l’intégration d’abonnement Azure à partir de la page des paramètres De Microsoft Defender pour IoT dans le [https://security.microsoft.com](https://security.microsoft.com/) portail. Une fois que vous avez éteint l’abonnement, vous ne verrez plus les appareils IoT détectés par Microsoft Defender pour IoT dans l’inventaire des appareils Microsoft Defender for Endpoint.

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble de la découverte d’appareils](configure-device-discovery.md)
- [Forum aux questions sur la découverte d’appareils](device-discovery-faq.md)
