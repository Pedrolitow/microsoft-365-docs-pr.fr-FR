---
title: Vérifier que vos appareils sont correctement configurés
description: Configurez correctement les appareils pour renforcer la résilience globale contre les menaces et améliorer votre capacité à détecter et à répondre aux attaques.
keywords: intégration, gestion Intune, Microsoft Defender pour point de terminaison, Microsoft Defender, Windows Defender, réduction de la surface d’attaque, ASR, base de référence de sécurité
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.custom: admindeeplinkDEFENDER
ms.topic: conceptual
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: ad0cc865362578597620fa4658c83c79dc7ebf02
ms.sourcegitcommit: 9b133379196da2b3a4bb311b07ff274f43780f68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2022
ms.locfileid: "67702971"
---
# <a name="ensure-your-devices-are-configured-properly"></a>Vérifier que vos appareils sont correctement configurés

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-onboardconfigure-abovefoldlink)

Avec des appareils correctement configurés, vous pouvez renforcer la résilience globale contre les menaces et améliorer votre capacité à détecter et à répondre aux attaques. La gestion de la configuration de la sécurité permet de s’assurer que vos appareils :

- Intégrer à Microsoft Defender pour point de terminaison
- Respecter ou dépasser la configuration de base de référence de sécurité Defender pour point de terminaison
- Mettre en place des atténuations de la surface d’attaque stratégique

Cliquez sur **Gestion de la configuration** dans le menu de navigation pour ouvrir la page gestion de la configuration des appareils.

:::image type="content" source="images/secconmgmt_main.png" alt-text="Page Gestion de la configuration de la sécurité" lightbox="images/secconmgmt_main.png":::

*Page gestion de la configuration des appareils*

Vous pouvez suivre l’état de la configuration au niveau de l’organisation et prendre rapidement des mesures en réponse à une couverture d’intégration médiocre, à des problèmes de conformité et à des atténuations de surface d’attaque mal optimisées via des liens directs et approfondis vers des pages de gestion des appareils sur Microsoft Intune et <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portail</a>.

Ce faisant, vous bénéficiez des avantages suivants :

- Visibilité complète des événements sur vos appareils
- Renseignement sur les menaces robuste et puissantes technologies d’apprentissage des appareils pour le traitement des événements bruts et l’identification de l’activité de violation et des indicateurs de menace
- Une pile complète de fonctionnalités de sécurité configurées pour arrêter efficacement l’installation d’implants malveillants, le détournement de fichiers système et de processus, l’exfiltration de données et d’autres activités de menace
- Optimisation des atténuations de la surface d’attaque, optimisation des défenses stratégiques contre l’activité de menace tout en réduisant l’impact sur la productivité

## <a name="enroll-devices-to-intune-management"></a>Inscrire des appareils à la gestion Intune

La gestion de la configuration des appareils fonctionne en étroite collaboration avec Intune gestion des appareils pour établir l’inventaire des appareils de votre organisation et la configuration de la sécurité de référence. Vous serez en mesure de suivre et de gérer les problèmes de configuration sur les appareils Windows gérés par Intune.

Avant de pouvoir vous assurer que vos appareils sont correctement configurés, inscrivez-les à Intune gestion. Intune’inscription est robuste et offre plusieurs options d’inscription pour les appareils Windows. Pour plus d’informations sur Intune options d’inscription, consultez la [configuration de l’inscription pour les appareils Windows](/intune/windows-enroll).

> [!NOTE]
> Pour inscrire des appareils Windows à Intune, les administrateurs doivent avoir déjà reçu des licences. [En savoir plus sur l'attribution de licences pour l'inscription d’appareils](/intune/licenses-assign).

> [!TIP]
> Pour optimiser la gestion des appareils via Intune, [connectez-vous Intune à Defender pour point de terminaison](/intune/advanced-threat-protection#enable-windows-defender-atp-in-intune).

## <a name="obtain-required-permissions"></a>Obtenir les autorisations requises

Par défaut, seuls les utilisateurs qui ont reçu le rôle Administrateur général ou Administrateur de service Intune sur Azure AD peuvent gérer et affecter les profils de configuration d’appareil nécessaires pour l’intégration des appareils et le déploiement de la base de référence de sécurité.

Si d’autres rôles vous ont été attribués, vérifiez que vous disposez des autorisations nécessaires :

- Autorisations complètes sur les configurations d’appareil
- Autorisations complètes sur les bases de référence de sécurité
- Lire les autorisations sur les stratégies de conformité des appareils
- Autorisations de lecture pour l’organisation

:::image type="content" source="images/secconmgmt_intune_permissions.png" alt-text="Autorisations requises sur intune" lightbox="images/secconmgmt_intune_permissions.png":::

*Autorisations de configuration d’appareil sur Intune*

> [!TIP]
> Pour en savoir plus sur l’attribution d’autorisations sur Intune, [consultez la création de rôles personnalisés](/intune/create-custom-role#to-create-a-custom-role).

## <a name="in-this-section"></a>Dans cette section

Rubrique|Description
:---|:---
[Obtenir les appareils intégrés à Defender pour point de terminaison](configure-machines-onboarding.md)|Suivez l’état d’intégration des appareils gérés par Intune et intègrez davantage d’appareils via Intune. 
[Augmenter la conformité à la base de référence de sécurité Defender pour point de terminaison](configure-machines-security-baseline.md)|Effectuer le suivi de la conformité et de la non-conformité de la ligne de base. Déployez la base de référence de sécurité sur d’autres appareils gérés par Intune.
[Optimiser le déploiement et les détections des règles ASR](configure-machines-asr.md)|Passez en revue le déploiement de règles et ajustez les détections à l’aide des outils d’analyse d’impact dans <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portail</a>.

> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-onboardconfigure-belowfoldlink)
