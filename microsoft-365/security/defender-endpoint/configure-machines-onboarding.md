---
title: Intégrer des appareils à Microsoft Defender pour point de terminaison
description: Suivez l’intégration des appareils gérés par Intune pour Microsoft Defender pour point de terminaison et augmenter le taux d’intégration.
keywords: intégration, gestion Intune, Microsoft Defender pour point de terminaison, Microsoft Defender, Windows Defender, gestion de la configuration
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: siosulli
author: siosulli
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- tier2
ms.topic: article
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: eced2495ce75faa78fd7923b871b3a3b00f5fc3a
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68172244"
---
# <a name="get-devices-onboarded-to-microsoft-defender-for-endpoint"></a>Intégrer des appareils à Microsoft Defender pour point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-onboardconfigure-abovefoldlink)

Chaque appareil intégré ajoute un capteur de détection et de réponse de point de terminaison supplémentaire (EDR) et augmente la visibilité sur l’activité de violation dans votre réseau. L’intégration garantit également qu’un appareil peut être vérifié pour les composants vulnérables ainsi que les problèmes de configuration de sécurité et peut recevoir des actions de correction critiques pendant les attaques.

Avant de pouvoir suivre et gérer l’intégration des appareils :

- [Inscrire vos appareils à Intune la gestion](configure-machines.md#enroll-devices-to-intune-management)
- [Vérifiez que vous disposez des autorisations nécessaires](configure-machines.md#obtain-required-permissions)

Regardez cette vidéo pour découvrir comment intégrer facilement des clients à Microsoft Defender pour point de terminaison.
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4bGqr?rel=0]

## <a name="discover-and-track-unprotected-devices"></a>Découvrir et suivre les appareils non protégés

La carte **d’intégration** fournit une vue d’ensemble générale de votre taux d’intégration en comparant le nombre d’appareils Windows qui ont réellement été intégrés à Defender pour point de terminaison par rapport au nombre total d’appareils Windows gérés par Intune.

:::image type="content" source="images/secconmgmt_onboarding_card.png" alt-text="Carte d’intégration de la gestion de la configuration des appareils" lightbox="images/secconmgmt_onboarding_card.png":::

*Carte montrant les appareils intégrés par rapport au nombre total d’appareils Windows gérés par Intune*

> [!NOTE]
> Si vous avez utilisé Configuration Manager, le script d’intégration ou d’autres méthodes d’intégration qui n’utilisent pas de profils Intune, vous pouvez rencontrer des incohérences de données. Pour résoudre ces différences, créez un profil de configuration Intune correspondant pour l’intégration de Defender pour point de terminaison et attribuez ce profil à vos appareils.

## <a name="onboard-more-devices-with-intune-profiles"></a>Intégrer davantage d’appareils avec des profils Intune

Defender pour point de terminaison offre plusieurs options pratiques pour [l’intégration d’appareils Windows](onboard-configure.md). Toutefois, pour les appareils gérés par Intune, vous pouvez tirer parti de Intune profils pour déployer facilement le capteur Defender pour point de terminaison pour sélectionner des appareils, ce qui permet d’intégrer efficacement ces appareils au service.

Dans la carte **d’intégration**, sélectionnez **Intégrer d’autres appareils** pour créer et affecter un profil sur Intune. Le lien vous dirige vers la page de conformité de l’appareil sur Intune, qui fournit une vue d’ensemble similaire de votre état d’intégration.

:::image type="content" source="images/secconmgmt_onboarding_1deviceconfprofile.png" alt-text="Page de conformité des appareils Microsoft Defender pour point de terminaison sur la gestion des appareils Intune" lightbox="images/secconmgmt_onboarding_1deviceconfprofile.png":::

*Microsoft Defender pour point de terminaison page de conformité des appareils sur la gestion des appareils Intune*

> [!TIP]
> Vous pouvez également accéder à la page de conformité d’intégration de Defender pour point de terminaison dans microsoft [Portail Azure](https://portal.azure.com/) à partir de **Tous les services > Intune > conformité des appareils > Microsoft Defender ATP**.

> [!NOTE]
> Si vous souhaitez afficher les données d’appareil les plus récentes, cliquez sur **Liste des appareils sans capteur ATP**.

À partir de la page de conformité de l’appareil, créez un profil de configuration spécifiquement pour le déploiement du capteur Defender pour point de terminaison et attribuez ce profil aux appareils que vous souhaitez intégrer. Pour ce faire, vous pouvez :

- Sélectionnez **Créer un profil de configuration d’appareil pour configurer le capteur ATP** pour qu’il commence par un profil de configuration d’appareil prédéfini.
- Créez le profil de configuration de l’appareil à partir de zéro.

Pour plus d’informations, [consultez l’utilisation de Intune profils de configuration d’appareil pour intégrer des appareils à Defender pour point de terminaison](/intune/advanced-threat-protection#onboard-devices-by-using-a-configuration-profile).

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-onboardconfigure-belowfoldlink)

## <a name="related-topics"></a>Voir aussi

- [Vérifier que vos appareils sont correctement configurés](configure-machines.md)
- [Augmenter la conformité à la base de référence de sécurité Defender pour point de terminaison](configure-machines-security-baseline.md)
- [Optimiser le déploiement et les détections des règles ASR](configure-machines-asr.md)
