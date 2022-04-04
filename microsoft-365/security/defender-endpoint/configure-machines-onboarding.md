---
title: Obtenir des appareils intégrés à Microsoft Defender pour le point de terminaison
description: Suivez l’intégration des appareils gérés par Intune à Microsoft Defender pour endpoint et augmentez le taux d’intégration.
keywords: intégration, gestion Intune, Microsoft Defender pour le point de terminaison, Microsoft Defender, Windows Defender, gestion de la configuration
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 6caaddc208e6f73de0f49ff6d419c335848ae439
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64466320"
---
# <a name="get-devices-onboarded-to-microsoft-defender-for-endpoint"></a>Obtenir des appareils intégrés à Microsoft Defender pour le point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-onboardconfigure-abovefoldlink)

Chaque appareil intégré ajoute un capteur protection évolutive des points de terminaison (PEPT) et augmente la visibilité sur l’activité de violation dans votre réseau. L’intégration garantit également qu’un appareil peut être vérifié pour les composants vulnérables ainsi que les problèmes de configuration de sécurité et peut recevoir des actions de correction critiques pendant les attaques.

Avant de pouvoir suivre et gérer l’intégration d’appareils :

- [Inscrire vos appareils à la gestion Intune](configure-machines.md#enroll-devices-to-intune-management)
- [Vérifier que vous avez les autorisations nécessaires](configure-machines.md#obtain-required-permissions)

## <a name="discover-and-track-unprotected-devices"></a>Découvrir et suivre les appareils non protégés

La  carte d’intégration fournit une vue d’ensemble de votre taux d’intégration en comparant le nombre d’appareils Windows qui ont réellement intégré Defender pour endpoint au nombre total d’appareils Windows gérés par Intune.

:::image type="content" source="images/secconmgmt_onboarding_card.png" alt-text="Carte d’intégration de gestion de la configuration des appareils" lightbox="images/secconmgmt_onboarding_card.png":::

*Carte affichant les appareils intégrés par rapport au nombre total d’appareils gérés Windows Intune*

> [!NOTE]
> Si vous avez utilisé Configuration Manager, le script d’intégration ou d’autres méthodes d’intégration qui n’utilisent pas de profils Intune, vous pouvez rencontrer des incohérences de données. Pour résoudre ces incohérences, créez un profil de configuration Intune correspondant pour l’intégration de Defender for Endpoint et affectez ce profil à vos appareils.

## <a name="onboard-more-devices-with-intune-profiles"></a>Intégrer d’autres appareils avec des profils Intune

Defender pour le point de terminaison fournit plusieurs options pratiques pour [l’intégration Windows appareils.](onboard-configure.md) Toutefois, pour les appareils gérés par Intune, vous pouvez tirer parti des profils Intune pour déployer facilement le capteur Defender for Endpoint afin de sélectionner des appareils, ce qui permet d’intégrer efficacement ces appareils au service.

À partir de **la carte d’intégration** , sélectionnez **Intégrer d’autres appareils** pour créer et affecter un profil sur Intune. Le lien vous permet d’utiliser la page de conformité des appareils sur Intune, qui fournit une vue d’ensemble similaire de votre état d’intégration.

:::image type="content" source="images/secconmgmt_onboarding_1deviceconfprofile.png" alt-text="Page de conformité des appareils Microsoft Defender for Endpoint sur la gestion des appareils Intune" lightbox="images/secconmgmt_onboarding_1deviceconfprofile.png":::

*Page de conformité des appareils Microsoft Defender for Endpoint sur la gestion des appareils Intune*

> [!TIP]
> Vous pouvez également accéder à la page de conformité d’intégration defender pour point de terminaison dans le portail [Microsoft Azure](https://portal.azure.com/) à partir de Tous les **services > Conformité des appareils Intune > > Microsoft Defender ATP**.

> [!NOTE]
> Si vous souhaitez afficher les données d’appareil les plus récentes, cliquez sur Liste des appareils **sans capteur ATP**.

À partir de la page conformité des appareils, créez un profil de configuration spécifique pour le déploiement du capteur Defender for Endpoint et affectez ce profil aux appareils que vous souhaitez intégrer. Pour ce faire, vous pouvez :

- **Sélectionnez Créer un profil de configuration d’appareil pour configurer le capteur ATP** afin qu’il commence par un profil de configuration d’appareil prédéféré.
- Créez le profil de configuration de l’appareil de A à Z.

Pour plus d’informations, voir l’utilisation des profils de configuration d’appareil [Intune pour intégrer des appareils à Defender for Endpoint](/intune/advanced-threat-protection#onboard-devices-by-using-a-configuration-profile).

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-onboardconfigure-belowfoldlink)

## <a name="related-topics"></a>Sujets associés

- [Vérifier que vos appareils sont correctement configurés](configure-machines.md)
- [Renforcer la conformité à la ligne de base de sécurité de Defender for Endpoint](configure-machines-security-baseline.md)
- [Optimiser le déploiement et les détections des règles ASR](configure-machines-asr.md)
