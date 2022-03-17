---
title: Utiliser l’Assistant pour configurer Microsoft Defender pour les entreprises
description: Defender for Business inclut un processus de configuration et de configuration similaire à celui de l’Assistant. Utilisez l’Assistant pour gagner du temps et des efforts.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: article
ms.date: 03/15/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.custom: intro-get-started
ms.openlocfilehash: 243630a43d75a4530024e246fbea57f26a51d06b
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2022
ms.locfileid: "63525791"
---
# <a name="use-the-wizard-to-set-up-microsoft-defender-for-business"></a>Utiliser l’Assistant pour configurer Microsoft Defender pour les entreprises

> [!IMPORTANT]
> Microsoft Defender for Business est en déploiement [Microsoft 365 Business Premium clients,](../../business-premium/index.md) à partir du 1er mars 2022. Defender for Business as a standalone subscription is in preview, and will roll out gradually to customers and IT Partners who [sign-up here](https://aka.ms/mdb-preview) to request it. La [prévisualisation inclut un ensemble initial de scénarios](mdb-tutorials.md#try-these-preview-scenarios) et nous ajouterons régulièrement des fonctionnalités.
> 
> Certaines informations de cet article concernent les produits/services pré-publiés qui peuvent être considérablement modifiés avant leur publication commerciale. Microsoft n’offre aucune garantie, expressément ou implicite, pour les informations fournies ici. 

Microsoft Defender pour Entreprises a été conçu pour économiser du temps et des efforts pour les petites et moyennes entreprises grâce à une expérience similaire à celle d’un Assistant pour la configuration initiale. Cet article décrit les étapes de l’Assistant et vos options de configuration manuelle de Defender for Business.

:::image type="content" source="media/mdb-wizard-start.png" alt-text="Capture d’écran de l’écran d’accueil de l’Assistant pour configurer Defender entreprise.":::

>
> **Avez-vous un peu de temps ?**
> Veuillez consulter notre <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">courte enquête sur Microsoft Defender entreprise</a>. Vos commentaires sont les bienvenus.
>

## <a name="overview-of-the-wizard"></a>Vue d’ensemble de l’Assistant

L’Assistant est conçu pour vous aider à configurer Defender pour Entreprise rapidement et efficacement. L’Assistant vous fait suivre les étapes suivantes :

1. **Attribuer des autorisations utilisateur**. Dans cette étape, vous accordez à votre équipe de sécurité l’accès au portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)). L’accès au portail est accordé par le biais de rôles qui impliquent certaines autorisations. [En savoir plus sur les rôles et les autorisations](mdb-roles-permissions.md).

   - Un administrateur global peut afficher et modifier tous les paramètres de votre Microsoft 365 client. 
   - Un administrateur de sécurité peut afficher et modifier les paramètres de sécurité. 
   - Un lecteur de sécurité peut uniquement afficher des informations dans les rapports. 

2. **Intégrer et configurer Windows appareils.** Au cours de cette étape, vous pouvez intégrer rapidement les appareils Windows de votre entreprise à Defender for Business. L’intégration immédiate d’appareils permet de protéger ces appareils dès le premier jour. Pour [plus d’informations, voir Appareils](mdb-onboard-devices.md) intégrés à Microsoft Defender entreprise.

   - Si vous utilisez déjà Microsoft Intune (partie de Microsoft Endpoint Manager) et que votre entreprise dispose d’appareils inscrits dans Endpoint Manager, vous êtes invité à utiliser l’intégration automatique pour une partie ou la plupart de vos [](mdb-onboard-devices.md#automatic-onboarding-for-windows-devices-enrolled-in-microsoft-endpoint-manager) appareils Windows inscrits. L’intégration automatique définit une connexion entre Endpoint Manager et Defender pour Entreprise, puis intègre Windows appareils à Defender pour Entreprise en toute transparence.

   - Si vous n’utilisez pas déjà Endpoint Manager ou si vous avez des appareils non Windows inscrits dans Endpoint Manager, vous pouvez intégrer manuellement des appareils à [Defender for Business](mdb-onboard-devices.md#local-script-in-defender-for-business). 
   
3. **Configurez vos stratégies de sécurité**. Defender pour les entreprises inclut des stratégies de sécurité par défaut pour la protection nouvelle génération et la protection pare-feu qui peuvent être appliquées aux appareils de votre entreprise. Ces stratégies par défaut utilisent les paramètres recommandés et sont conçues pour fournir une protection forte pour vos appareils. 

   Vous pouvez également créer vos propres stratégies de sécurité si vous le souhaitez. Et, si vous utilisez déjà Endpoint Manager, vous pouvez continuer à l’utiliser pour gérer vos stratégies de sécurité. 

   Pour plus d’informations, voir [Afficher et modifier vos stratégies et paramètres de sécurité](mdb-configure-security-settings.md).

## <a name="what-happens-if-i-dont-use-the-wizard"></a>Que se passe-t-il si je n’utilise pas l’Assistant ?

Si vous choisissez de ne pas utiliser l’Assistant, ou si l’Assistant est fermé avant la fin de votre processus d’installation, vous pouvez toujours terminer votre installation et votre processus de configuration vous-même. 

[Consultez Installer et configurer Microsoft Defender entreprise](mdb-setup-configuration.md) pour passer en compte les étapes suivantes :

1. [Attribuez des rôles et des autorisations](mdb-roles-permissions.md) afin que votre équipe de sécurité puisse accéder au portail Microsoft 365 Defender () et l’utiliser.[https://security.microsoft.com](https://security.microsoft.com)

2. [Configurer des notifications par courrier électronique pour votre](mdb-email-notifications.md) équipe de sécurité afin qu’elle soit en boucle sur les nouvelles alertes ou vulnérabilités.

3. [Intégrer des](mdb-onboard-devices.md) appareils afin qu’ils sont protégés par Defender entreprise.

4. [Gérez vos stratégies de sécurité](mdb-configure-security-settings.md), qui incluent la protection nouvelle génération, la protection pare-feu et le filtrage de contenu web.

## <a name="next-steps"></a>Prochaines étapes

- [Configurer des notifications par courrier électronique pour votre équipe de sécurité](mdb-email-notifications.md)

- [Commencer à utiliser le portail Microsoft 365 Defender web](mdb-get-started.md)

- [Utiliser votre tableau de bord gestion & des menaces et des vulnérabilités](mdb-view-tvm-dashboard.md)