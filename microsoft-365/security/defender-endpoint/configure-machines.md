---
title: Vérifier que vos appareils sont correctement configurés
description: Configurez correctement les appareils pour renforcer la résilience globale contre les menaces et améliorer votre capacité à détecter les attaques et à y répondre.
keywords: intégré, gestion Intune, Microsoft Defender pour le point de terminaison, Microsoft Defender, Windows Defender, réduction de la surface d'attaque, réduction de la surface d'attaque, réduction de la surface d'attaque, ligne de base de sécurité
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: lomayor
author: lomayor
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 3fd58ee17b2cb86c0bcc858b9b0fd57c12ac501e
ms.sourcegitcommit: a8d8cee7df535a150985d6165afdfddfdf21f622
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2021
ms.locfileid: "51932810"
---
# <a name="ensure-your-devices-are-configured-properly"></a>Vérifier que vos appareils sont correctement configurés

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

>Vous souhaitez faire l'expérience de Defender pour point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-onboardconfigure-abovefoldlink)

Avec des appareils correctement configurés, vous pouvez renforcer la résilience globale contre les menaces et améliorer votre capacité à détecter les attaques et à y répondre. La gestion de la configuration de la sécurité permet de s'assurer que vos appareils :

- Intégration à Microsoft Defender pour le point de terminaison
- Meet or exceed the Defender for Endpoint security baseline configuration
- Mettre en place des atténuations de la surface d'attaque stratégique

Cliquez **sur Gestion de la** configuration dans le menu de navigation pour ouvrir la page Gestion de la configuration des appareils.

![Page Gestion de la configuration de la sécurité](images/secconmgmt_main.png)<br>
*Page Gestion de la configuration des appareils*

Vous pouvez suivre l'état de configuration au niveau de l'organisation et prendre rapidement des mesures en réponse à une couverture d'intégration médiocre, à des problèmes de conformité et à des atténuations de surface d'attaque mal optimisées via des liens directs et profonds vers des pages de gestion des appareils sur Microsoft Intune et le Centre de sécurité Microsoft 365.

Pour ce faire, vous bénéficiez des avantages de :
- Visibilité complète des événements sur vos appareils
- Veille fiable sur les menaces et technologies puissantes d'apprentissage des appareils pour le traitement des événements bruts et l'identification de l'activité de violation et des indicateurs de menace
- Pile complète de fonctionnalités de sécurité configurées pour arrêter efficacement l'installation de programmes malveillants, le piratage de fichiers et de processus système, l'exfiltration de données et d'autres activités contre les menaces
- Optimisation des atténuations de la surface d'attaque, optimisation des défenses stratégiques contre l'activité des menaces tout en réduisant l'impact sur la productivité

## <a name="enroll-devices-to-intune-management"></a>Inscrire des appareils à la gestion Intune

La gestion de la configuration des appareils fonctionne en étroite collaboration avec la gestion des appareils Intune pour établir l'inventaire des appareils de votre organisation et la configuration de sécurité de référence. Vous pourrez suivre et gérer les problèmes de configuration sur les appareils Windows 10 gérés par Intune.

Avant de pouvoir vous assurer que vos appareils sont correctement configurés, inscrivez-les à la gestion Intune. L'inscription Intune est robuste et offre plusieurs options d'inscription pour les appareils Windows 10. Pour plus d'informations sur les options d'inscription Intune, voir la configuration de [l'inscription pour les appareils Windows.](https://docs.microsoft.com/intune/windows-enroll)

>[!NOTE]
>Pour inscrire des appareils Windows à Intune, les administrateurs doivent avoir déjà reçu des licences. [En savoir plus sur l'attribution de licences pour l'inscription des appareils.](https://docs.microsoft.com/intune/licenses-assign)

>[!TIP] 
>Pour optimiser la gestion des appareils via Intune, [connectez Intune à Defender pour endpoint.](https://docs.microsoft.com/intune/advanced-threat-protection#enable-windows-defender-atp-in-intune)

## <a name="obtain-required-permissions"></a>Obtenir les autorisations requises
Par défaut, seuls les utilisateurs qui ont reçu le rôle Administrateur général ou Administrateur du service Intune sur Azure AD peuvent gérer et affecter les profils de configuration d'appareil nécessaires à l'intégration des appareils et au déploiement de la ligne de base de sécurité.

Si d'autres rôles vous ont été attribués, assurez-vous que vous avez les autorisations nécessaires :

- Autorisations complètes sur les configurations d'appareil
- Autorisations complètes sur les lignes de base de sécurité
- Autorisations de lecture des stratégies de conformité des appareils
- Autorisations de lecture pour l'organisation

![Autorisations requises sur Intune](images/secconmgmt_intune_permissions.png)<br>
*Autorisations de configuration d'appareil sur Intune*

>[!TIP] 
>Pour en savoir plus sur l'attribution d'autorisations sur Intune, découvrez [la création de rôles personnalisés.](https://docs.microsoft.com/intune/create-custom-role#to-create-a-custom-role)

## <a name="in-this-section"></a>Dans cette section
Rubrique | Description
:---|:---
[Obtenir des appareils intégrés à Defender pour le point de terminaison](configure-machines-onboarding.md)| Suivre l'état d'intégration des appareils gérés par Intune et intégrer d'autres appareils via Intune. 
[Renforcer la conformité à la ligne de base de sécurité de Defender for Endpoint](configure-machines-security-baseline.md) | Assurer le suivi de la conformité et de la non-conformité des lignes de base. Déployez la ligne de base de sécurité sur d'autres appareils gérés par Intune.
[Optimiser le déploiement et les détections de règles asr](configure-machines-asr.md) | Examinez le déploiement des règles et ajustez les détections à l'aide des outils d'analyse d'impact dans le Centre de sécurité Microsoft 365.

>Vous souhaitez faire l'expérience de Defender pour point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-onboardconfigure-belowfoldlink)
