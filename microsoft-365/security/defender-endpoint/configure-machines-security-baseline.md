---
title: Augmenter la conformité à la base de référence de sécurité Microsoft Defender pour point de terminaison
description: La base de référence de sécurité Microsoft Defender pour point de terminaison définit des contrôles de sécurité pour fournir une protection optimale.
keywords: gestion Intune, Microsoft Defender pour point de terminaison, Microsoft Defender, Microsoft Defender pour point de terminaison ASR, base de référence de sécurité
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- tier3
ms.topic: conceptual
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: f1e244d3c144705e5c4697fba29d688742c8e72a
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68623804"
---
# <a name="increase-compliance-to-the-microsoft-defender-for-endpoint-security-baseline"></a>Augmenter la conformité à la base de référence de sécurité Microsoft Defender pour point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-onboardconfigure-abovefoldlink)

Les bases de référence de sécurité garantissent que les fonctionnalités de sécurité sont configurées conformément aux conseils des experts en sécurité et des administrateurs système Windows experts. Lorsqu’elle est déployée, la base de référence de sécurité Defender pour point de terminaison définit les contrôles de sécurité Defender pour point de terminaison pour fournir une protection optimale.

Pour comprendre les bases de référence de sécurité et la façon dont elles sont affectées sur Intune à l’aide de profils de configuration, [lisez ce FAQ](/intune/security-baselines#q--a).

Avant de pouvoir déployer et suivre la conformité aux bases de référence de sécurité :

- [Inscrire vos appareils à Intune la gestion](configure-machines.md#enroll-devices-to-intune-management)
- [Vérifiez que vous disposez des autorisations nécessaires](configure-machines.md#obtain-required-permissions)

## <a name="compare-the-microsoft-defender-for-endpoint-and-the-windows-intune-security-baselines"></a>Comparer les bases de référence de sécurité Microsoft Defender pour point de terminaison et Windows Intune

La base de référence de sécurité Windows Intune fournit un ensemble complet de paramètres recommandés nécessaires pour configurer en toute sécurité les appareils exécutant Windows, notamment les paramètres du navigateur, les paramètres PowerShell et les paramètres de certaines fonctionnalités de sécurité telles que Microsoft Defender Antivirus. En revanche, la ligne de base defender pour point de terminaison fournit des paramètres qui optimisent tous les contrôles de sécurité dans la pile Defender pour point de terminaison, y compris les paramètres de détection et de réponse des points de terminaison (EDR), ainsi que les paramètres également disponibles dans la base de référence de sécurité windows Intune. Pour plus d’informations sur chaque ligne de base, consultez :

- [Paramètres de base de référence de sécurité Windows pour Intune](/intune/security-baseline-settings-windows)
- [Microsoft Defender pour point de terminaison paramètres de base de référence pour Intune](/intune/security-baseline-settings-defender-atp)

Les appareils intégrés à Defender pour point de terminaison devraient être déployés sur les deux lignes de base : la ligne de base de sécurité Windows Intune pour sécuriser initialement Windows, puis la ligne de base de sécurité de Defender pour point de terminaison comme couche supplémentaire pour configurer de manière optimale les contrôles de sécurité Defender pour point de terminaison. Pour tirer parti des données les plus récentes sur les risques et les menaces et réduire les conflits à mesure que les lignes de base évoluent, appliquez toujours les dernières versions des lignes de base sur tous les produits dès leur publication.

> [!NOTE]
> La base de référence de sécurité Defender pour point de terminaison a été optimisée pour les appareils physiques et n’est actuellement pas recommandée pour une utilisation sur des machines virtuelles ou des points de terminaison VDI. Certains paramètres de la base de référence peuvent impacter les sessions interactives à distance sur les environnements virtualisés.

## <a name="monitor-compliance-to-the-defender-for-endpoint-security-baseline"></a>Surveiller la conformité à la base de référence de sécurité Defender pour point de terminaison

La carte **de base de référence de sécurité** sur [la gestion de la configuration des appareils](configure-machines.md) fournit une vue d’ensemble de la conformité entre les Windows 10 et les appareils Windows 11 auxquels la base de référence de sécurité Defender pour point de terminaison a été attribuée.

:::image type="content" source="images/secconmgmt_baseline_card.png" alt-text="Carte de base de référence de sécurité" lightbox="images/secconmgmt_baseline_card.png":::

*Carte indiquant la conformité à la base de référence de sécurité Defender pour point de terminaison*

Chaque appareil reçoit l’un des types d’état suivants :

- **Correspond à la ligne de base** : les paramètres de l’appareil correspondent à tous les paramètres de la base de référence.
- **Ne correspond pas à la ligne de base** : au moins un paramètre d’appareil ne correspond pas à la ligne de base.
- **Mal configuré** : au moins un paramètre de base de référence n’est pas correctement configuré sur l’appareil et est en conflit, erreur ou état en attente.
- **Non applicable** : au moins un paramètre de base de référence n’est pas applicable sur l’appareil.

Pour passer en revue des appareils spécifiques, **sélectionnez Configurer la base de référence de sécurité** sur la carte. Cela vous amène à Intune la gestion des appareils. À partir de là, sélectionnez **l’état de l’appareil** pour les noms et les états des appareils.

> [!NOTE]
> Vous pouvez rencontrer des différences dans les données agrégées affichées sur la page de gestion de la configuration des appareils et celles affichées sur les écrans de vue d’ensemble dans Intune.

## <a name="review-and-assign-the-microsoft-defender-for-endpoint-security-baseline"></a>Examiner et affecter la base de référence de sécurité Microsoft Defender pour point de terminaison

La gestion de la configuration des appareils surveille uniquement la conformité de base de référence des appareils Windows 10 et Windows 11 qui ont été affectés spécifiquement à la base de référence de sécurité Microsoft Defender pour point de terminaison. Vous pouvez facilement examiner la ligne de base et l’affecter aux appareils sur Intune gestion des appareils.

1. Sélectionnez **Configurer la base de référence de sécurité** sur la carte **base de référence de sécurité** pour accéder à Intune gestion des appareils. Une vue d’ensemble similaire de la conformité de la base de référence s’affiche.

   > [!TIP]
   > Vous pouvez également accéder à la base de référence de sécurité Defender pour point de terminaison dans microsoft Portail Azure à partir de **toutes les bases de référence de sécurité de l’appareil > Intune > de tous les services > de sécurité > Microsoft Defender base de référence ATP**.

2. Créez un profil.

   :::image type="content" source="images/secconmgmt_baseline_intuneprofile1.png" alt-text="L’onglet Créer un profil dans la vue d’ensemble de la base de référence de sécurité Microsoft Defender pour point de terminaison sur Intune" lightbox="images/secconmgmt_baseline_intuneprofile1.png":::<br>
   *Microsoft Defender pour point de terminaison vue d’ensemble de la base de référence de sécurité sur Intune*

3. Lors de la création du profil, vous pouvez examiner et ajuster des paramètres spécifiques sur la base de référence.

   :::image type="content" source="images/secconmgmt_baseline_intuneprofile2.png" alt-text="Options de base de référence de sécurité lors de la création du profil sur Intune" lightbox="images/secconmgmt_baseline_intuneprofile2.png":::<br>
   *Options de base de référence de sécurité lors de la création du profil sur Intune*

4. Affectez le profil au groupe d’appareils approprié.

   :::image type="content" source="images/secconmgmt_baseline_intuneprofile3.png" alt-text="Profils de base de référence de sécurité sur Intune" lightbox="images/secconmgmt_baseline_intuneprofile3.png":::<br>
   *Affectation du profil de base de référence de sécurité sur Intune*

5. Créez le profil pour l’enregistrer et le déployer sur le groupe d’appareils affecté.

   :::image type="content" source="images/secconmgmt_baseline_intuneprofile4.png" alt-text="Affectation de la base de référence de sécurité sur Intune" lightbox="images/secconmgmt_baseline_intuneprofile4.png":::<br>
   *Création du profil de base de référence de sécurité sur Intune*

> [!TIP]
> Les bases de référence de sécurité sur Intune offrent un moyen pratique de sécuriser et de protéger vos appareils de manière complète. [En savoir plus sur les bases de référence de sécurité sur Intune](/intune/security-baselines).

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-onboardconfigure-belowfoldlink)

## <a name="related-topics"></a>Voir aussi

- [Vérifier que vos appareils sont correctement configurés](configure-machines.md)
- [Intégrer des appareils à Microsoft Defender pour point de terminaison](configure-machines-onboarding.md)
- [Optimiser le déploiement et les détections des règles ASR](configure-machines-asr.md)
