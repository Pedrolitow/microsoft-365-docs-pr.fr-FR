---
title: Utiliser l’Assistant Installation dans Microsoft Defender pour les PME
description: Defender entreprise inclut un processus de configuration et d’installation de type Assistant. Utilisez l’Assistant pour gagner du temps et des efforts.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: article
ms.date: 04/08/2022
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
ms.openlocfilehash: ad070273567d350973037f1ac5a0192036d22187
ms.sourcegitcommit: dd5fc139affb4cba4089cbdb2c478968b680699a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2022
ms.locfileid: "64746642"
---
# <a name="use-the-setup-wizard-in-microsoft-defender-for-business"></a>Utiliser l’Assistant Installation dans Microsoft Defender pour les PME

> [!IMPORTANT]
> Microsoft Defender pour les PME est déployée pour [Microsoft 365 Business Premium](../../business-premium/index.md) clients, à compter du 1er mars 2022. Defender entreprise en tant qu’abonnement autonome est en préversion et sera déployé progressivement pour les clients et les partenaires informatiques qui [s’inscrivent ici](https://aka.ms/mdb-preview) pour le demander. La préversion inclut un [ensemble initial de scénarios](mdb-tutorials.md#try-these-preview-scenarios), et nous ajouterons régulièrement des fonctionnalités.
> 
> Certaines informations contenues dans cet article concernent des produits/services prédéfinis qui peuvent être considérablement modifiés avant leur publication commerciale. Microsoft n’offre aucune garantie, expresse ou implicite, pour les informations fournies ici. 

Microsoft Defender pour les PME a été conçu pour économiser du temps et des efforts aux petites et moyennes entreprises grâce à une expérience similaire à celle de l’Assistant pour l’installation et la configuration initiales. L’Assistant Installation vous guide tout au long de l’octroi de l’accès à votre équipe de sécurité, de la configuration des notifications par e-mail pour votre équipe de sécurité et de l’intégration des appareils Windows de votre entreprise.

:::image type="content" source="media/mdb-wizard-start.png" alt-text="Capture d’écran de l’écran d’accueil de l’Assistant pour configurer Defender entreprise.":::

>
> **Avez-vous un peu de temps ?**
> Veuillez prendre notre <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">court sondage sur Microsoft Defender pour les PME</a>. Vos commentaires sont les bienvenus.
>

## <a name="overview-of-the-setup-wizard"></a>Vue d’ensemble de l’Assistant Installation

> [!IMPORTANT]
> Avant de commencer, assurez-vous que vous avez déjà ajouté des utilisateurs à votre abonnement Microsoft 365. Pour obtenir de l’aide sur cette tâche, consultez [Ajouter des utilisateurs et attribuer des licences en même temps](../../admin/add-users/add-users.md).

L’Assistant est conçu pour vous aider à configurer Defender entreprise rapidement et efficacement. L’Assistant vous guide tout au long des étapes suivantes :

1. **Attribuez des autorisations utilisateur**. Dans cette étape, vous accordez à votre équipe de sécurité l’accès au portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)). Ce portail vous permet, avec votre équipe de sécurité, de gérer vos fonctionnalités de sécurité, d’afficher les alertes et d’effectuer les actions nécessaires sur les menaces détectées. L’accès au portail est accordé par le biais de rôles qui impliquent certaines autorisations.

   Dans Defender entreprise, les membres de votre équipe de sécurité peuvent se faire attribuer l’un des trois rôles suivants :<br/>
   
      - **Administrateur général** : un administrateur général peut afficher et modifier tous les paramètres de votre locataire Microsoft 365. L’administrateur général effectue la configuration initiale de l’abonnement Microsoft 365 de votre entreprise. 
      - **Administrateur de sécurité** : un administrateur de sécurité peut afficher et modifier les paramètres de sécurité, et prendre des mesures lorsque des menaces sont détectées.
      - **Lecteur de sécurité** : un lecteur de sécurité peut afficher des informations dans les rapports, mais ne peut pas modifier les paramètres de sécurité. 
      
      [En savoir plus sur les rôles et les autorisations](mdb-roles-permissions.md). 

2. **Configurez les notifications par e-mail**. Dans cette étape, vous pouvez configurer des notifications par e-mail pour votre équipe de sécurité. Ensuite, lorsqu’une alerte est générée ou qu’une nouvelle vulnérabilité est détectée, votre équipe de sécurité n’en parle pas même si elle est loin de son bureau. 

   [En savoir plus sur les notifications par e-mail](mdb-email-notifications.md). 

3. **Intégrer et configurer Windows appareils**. Dans cette étape, vous pouvez intégrer rapidement les appareils Windows de votre entreprise à Defender for Business. L’intégration immédiate des appareils permet de protéger ces appareils dès le premier jour. 

   - **Si vous utilisez déjà Microsoft Endpoint Manager** (ce qui inclut Microsoft Intune) et que votre entreprise dispose d’appareils inscrits dans Endpoint Manager, vous serez invité à indiquer si vous souhaitez utiliser [l’intégration automatique](mdb-onboard-devices.md#automatic-onboarding-for-windows-devices-enrolled-in-microsoft-endpoint-manager) pour une partie ou la totalité de vos appareils Windows inscrits. L’intégration automatique configure une connexion entre Endpoint Manager et Defender entreprise, puis intègre Windows appareils à Defender entreprise en toute transparence. 
   - **Si vous n’utilisez pas encore Endpoint Manager**, vous pouvez [intégrer des appareils à Defender entreprise à l’aide d’un script local](mdb-onboard-devices.md#local-script-in-defender-for-business). 
   
   En [savoir plus sur l’intégration d’appareils à Microsoft Defender pour les PME](mdb-onboard-devices.md).
   
4. **Configurez vos stratégies de sécurité**. Defender entreprise inclut des stratégies de sécurité par défaut pour la protection de nouvelle génération et la protection pare-feu qui peuvent être appliquées aux appareils de votre entreprise. Ces stratégies par défaut utilisent les paramètres recommandés et sont conçues pour fournir une protection renforcée pour vos appareils. Vous pouvez également créer vos propres stratégies de sécurité. Et, si vous utilisez déjà Endpoint Manager, vous pouvez continuer à l’utiliser pour gérer vos stratégies de sécurité.

   Pour en savoir plus, consultez [Afficher et modifier vos stratégies et paramètres de sécurité](mdb-configure-security-settings.md). |

## <a name="what-happens-if-i-dont-use-the-wizard"></a>Que se passe-t-il si je n’utilise pas l’Assistant ?

L’utilisation de l’Assistant Installation est facultative. Si vous choisissez de ne pas utiliser l’Assistant ou si l’Assistant est fermé avant la fin de votre processus d’installation, vous pouvez effectuer le processus d’installation et de configuration vous-même. Consultez [Configurer et configurer Microsoft Defender pour les PME](mdb-setup-configuration.md) pour parcourir les étapes suivantes :

1. **[Attribuez des rôles et des autorisations](mdb-roles-permissions.md)** afin que votre équipe de sécurité puisse accéder au portail Microsoft 365 Defender et l’utiliser ([https://security.microsoft.com](https://security.microsoft.com)).

2. **[Configurez des notifications par e-mail pour votre équipe de sécurité afin](mdb-email-notifications.md)** qu’elles soient en boucle sur les nouvelles alertes ou vulnérabilités.

3. **[Intégrer des appareils](mdb-onboard-devices.md)** afin qu’ils soient protégés par Defender entreprise.

4. **[Gérez vos stratégies de sécurité](mdb-configure-security-settings.md)**, qui incluent la protection de nouvelle génération, la protection pare-feu et le filtrage de contenu web.

## <a name="next-steps"></a>Prochaines étapes

- [Configurer des notifications par e-mail pour votre équipe de sécurité](mdb-email-notifications.md)

- [Démarrage à l’aide du portail Microsoft 365 Defender](mdb-get-started.md)

- [Utiliser votre tableau de bord Threat & Vulnerability Management](mdb-view-tvm-dashboard.md)