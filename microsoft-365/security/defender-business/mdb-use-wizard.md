---
title: Utiliser l’Assistant pour configurer Microsoft Defender entreprise (prévisualisation)
description: Defender for Business inclut un processus de configuration et de configuration similaire à celui de l’Assistant. Utilisez l’Assistant pour gagner du temps et des efforts.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: article
ms.date: 02/16/2022
ms.prod: m365-security
ms.technology: mdb
localization_priority: Normal
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.custom: intro-get-started
ms.openlocfilehash: 26bf8e46ba79094f74fe542f932921d4f1c2a50d
ms.sourcegitcommit: 007822d16e332522546e948f5c216327254a4d49
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/17/2022
ms.locfileid: "62879131"
---
# <a name="use-the-wizard-to-set-up-microsoft-defender-for-business-preview"></a>Utiliser l’Assistant pour configurer Microsoft Defender entreprise (prévisualisation)

> [!IMPORTANT]
> Microsoft Defender pour Entreprise est désormais en prévisualisation et sera progressivement mis en place pour les clients [](https://aka.ms/mdb-preview) et les partenaires qui s’y connectent pour le demander. Nous intégrerons un ensemble initial de clients et de partenaires dans les prochaines semaines et développerons la prévisualisation jusqu’à la disponibilité générale. Notez que la prévisualisation sera lancée avec un [ensemble initial de scénarios](mdb-tutorials.md#try-these-preview-scenarios) et que nous ajouterons régulièrement des fonctionnalités.
> 
> Certaines informations de cet article concernent les produits/services pré-publiés qui peuvent être considérablement modifiés avant leur publication commerciale. Microsoft n’offre aucune garantie, expressément ou implicite, pour les informations fournies ici. 

Microsoft Defender pour Entreprise (prévisualisation) a été conçu pour économiser du temps et des efforts pour les petites et moyennes entreprises grâce à une expérience similaire à celle d’un Assistant pour la configuration initiale. Cet article décrit les étapes de l’Assistant et vos options de configuration manuelle de Defender for Business.

:::image type="content" source="media/mdb-wizard-start.png" alt-text="Capture d’écran de l’écran d’accueil de l’Assistant pour configurer Defender entreprise.":::

## <a name="overview-of-the-wizard"></a>Vue d’ensemble de l’Assistant

L’Assistant est conçu pour vous aider à configurer Defender pour Entreprise rapidement et efficacement. L’Assistant vous fait suivre les étapes suivantes :

1. **Attribuer des autorisations utilisateur**. Dans cette étape, vous accordez à votre équipe de sécurité l’accès au portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)). L’accès au portail est accordé par le biais de rôles qui impliquent certaines autorisations. [En savoir plus sur les rôles et les autorisations](mdb-roles-permissions.md).

   - Un administrateur global peut afficher et modifier tous les paramètres de votre Microsoft 365 client. 
   - Un administrateur de sécurité peut afficher et modifier les paramètres de sécurité. 
   - Un lecteur de sécurité peut uniquement afficher des informations dans les rapports. 

2. **Configurer les notifications par courrier électronique**. Dans cette étape, vous déterminez qui doit recevoir des notifications par courrier électronique en cas de vulnérabilité détectée ou d’une nouvelle alerte. Les notifications par courrier électronique peuvent aider à informer votre équipe de sécurité, même si elle n’est pas à son bureau. [En savoir plus sur les notifications par courrier électronique](mdb-email-notifications.md). 

3. **Intégrer et configurer Windows appareils.** Au cours de cette étape, vous pouvez intégrer rapidement les appareils Windows de votre organisation à Defender for Business. L’intégration immédiate d’appareils permet de protéger ces appareils dès le premier jour. 

   - Si vous utilisez déjà Microsoft Intune (partie de Microsoft Endpoint Manager) et que votre organisation dispose d’appareils inscrits dans Endpoint Manager, vous êtes invité à utiliser l’intégration automatique pour une partie ou la plupart de vos appareils Windows inscrits. L’intégration automatique définit une connexion entre Endpoint Manager et Defender pour Entreprise, puis intègre Windows appareils à Defender pour Entreprise en toute transparence.

   - Si vous n’utilisez pas déjà Endpoint Manager ou si vous avez des appareils non Windows inscrits dans Endpoint Manager, vous pouvez intégrer manuellement des appareils à Defender for Business (prévisualisation). 

   - Voir [Appareils intégrés à Microsoft Defender pour Entreprises (prévisualisation).](mdb-onboard-devices.md)
   
4. **Configurez vos stratégies de sécurité**. Defender pour les entreprises inclut des stratégies de sécurité par défaut qui peuvent être appliquées aux appareils de votre organisation. Ces stratégies par défaut utilisent les paramètres recommandés et sont conçues pour fournir une protection forte pour vos appareils. Toutefois, vous pouvez également créer vos propres stratégies de sécurité si vous le souhaitez. Et, si vous utilisez déjà Endpoint Manager, vous pouvez continuer à l’utiliser pour gérer vos stratégies de sécurité. 

   - [En savoir plus sur la configuration simplifiée](mdb-simplified-configuration.md).
   - [Choisissez l’endroit où gérer les stratégies et les appareils de sécurité](mdb-configure-security-settings.md#choose-where-to-manage-security-policies-and-devices).

## <a name="what-happens-if-i-dont-use-the-wizard"></a>Que se passe-t-il si je n’utilise pas l’Assistant ?

Si vous choisissez de ne pas utiliser l’Assistant, ou si vous quittez l’Assistant avant la fin de votre processus d’installation, vous pouvez toujours terminer votre installation et votre processus de configuration vous-même. Voir [Installer et configurer Microsoft Defender entreprise (prévisualisation)](mdb-setup-configuration.md) pour parcourir les étapes.

## <a name="next-steps"></a>Prochaines étapes

- [Commencer à utiliser le portail Microsoft 365 Defender web](mdb-get-started.md)

- [Utiliser votre tableau de bord gestion & des menaces et des vulnérabilités](mdb-view-tvm-dashboard.md)