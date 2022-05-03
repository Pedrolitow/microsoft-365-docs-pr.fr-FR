---
title: Utiliser l’Assistant Installation dans Microsoft Defender pour les PME
description: Defender entreprise facilite l’installation avec un Assistant qui s’exécute la première fois que vous utilisez Defender entreprise. Découvrez le fonctionnement de l’Assistant Installation.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: article
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.custom: intro-get-started
ms.openlocfilehash: 042f20cce0e0d30195ed241b376bf304abeaa2aa
ms.sourcegitcommit: f30616b90b382409f53a056b7a6c8be078e6866f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2022
ms.locfileid: "65172779"
---
# <a name="use-the-setup-wizard-in-microsoft-defender-for-business"></a>Utiliser l’Assistant Installation dans Microsoft Defender pour les PME

Microsoft Defender pour les PME a été conçu pour économiser du temps et des efforts aux petites et moyennes entreprises. Par exemple, vous pouvez effectuer l’installation et la configuration initiales avec un Assistant Installation. L’Assistant Installation vous guide tout au long de l’octroi de l’accès à votre équipe de sécurité, de la configuration des notifications par e-mail pour votre équipe de sécurité et de l’intégration des appareils Windows de votre entreprise.

>
> **Avez-vous un peu de temps ?**
> Veuillez prendre notre <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">courte enquête sur la sécurité</a>. Vos commentaires sont les bienvenus.
>

> [!TIP]
> L’utilisation de l’Assistant Installation est facultative. Vous pouvez choisir de travailler manuellement via le processus d’installation et de configuration. Pour en savoir plus, reportez-vous à la rubrique :
> - [Que se passe-t-il si je n’utilise pas l’Assistant ?](#what-happens-if-i-dont-use-the-wizard)
> - [Comment configurer et configurer Microsoft Defender pour les PME](mdb-setup-configuration.md)

## <a name="how-to-start-the-setup-wizard"></a>Comment démarrer l’Assistant Installation

L’Assistant Installation est conçu pour s’exécuter la première fois qu’une personne de votre entreprise se connecte au portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)). 

Si votre entreprise a utilisé Microsoft 365 Business Premium, l’Assistant Configuration de Defender Entreprise s’exécute la première fois qu’une personne accède à **l’inventaire** **EndpointsDevice** > . 

L’écran de démarrage de l’Assistant Installation ressemble à l’image suivante :

:::image type="content" source="media/mdb-wizard-start.png" alt-text="Capture d’écran de l’écran d’accueil de l’Assistant pour configurer Defender entreprise.":::

## <a name="the-setup-wizard-flow"></a>Flux de l’Assistant Installation

> [!IMPORTANT]
> Vous devez être administrateur général pour exécuter l’Assistant Installation. La personne qui a inscrit votre entreprise pour Microsoft 365 ou pour Microsoft Defender pour les PME est un administrateur général par défaut.

L’Assistant Installation est conçu pour vous aider à configurer Defender entreprise rapidement et efficacement. L’Assistant vous guide tout au long des étapes suivantes :

1. **Attribuez des autorisations utilisateur**. Dans cette étape, vous accordez à votre équipe de sécurité l’accès au portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)). Ce portail vous permet, avec votre équipe de sécurité, de gérer vos fonctionnalités de sécurité, d’afficher les alertes et d’effectuer les actions nécessaires sur les menaces détectées. L’accès au portail est accordé par le biais de rôles qui impliquent certaines autorisations.

   Dans Defender Entreprise, les membres de votre équipe de sécurité peuvent se faire attribuer l’un des trois rôles suivants :<br/>
   
   - **Administrateur général** : un administrateur général peut afficher et modifier tous les paramètres de votre locataire Microsoft 365. L’administrateur général effectue la configuration initiale de l’abonnement Microsoft 365 de votre entreprise. 
   - **Administrateur de sécurité** : un administrateur de sécurité peut afficher et modifier les paramètres de sécurité, et prendre des mesures lorsque des menaces sont détectées.
   - **Lecteur de sécurité** : un lecteur de sécurité peut afficher des informations dans des rapports, mais ne peut pas modifier les paramètres de sécurité. 

   [En savoir plus sur les rôles et les autorisations](mdb-roles-permissions.md). 

2. **Configurez les notifications par e-mail**. Dans cette étape, vous pouvez configurer des notifications par e-mail pour votre équipe de sécurité. Ensuite, lorsqu’une alerte est générée ou qu’une nouvelle vulnérabilité est détectée, votre équipe de sécurité ne la manque pas, même si elle est loin de son bureau. [En savoir plus sur les notifications par e-mail](mdb-email-notifications.md). 

3. **Intégrer et configurer Windows appareils**. Dans cette étape, vous pouvez intégrer rapidement les appareils Windows de votre entreprise à Defender for Business. L’intégration immédiate des appareils permet de protéger ces appareils dès le premier jour. 

   - **Si vous utilisez déjà Microsoft Intune** et que votre entreprise dispose d’appareils inscrits dans Intune, vous serez invité à indiquer si vous souhaitez utiliser [l’intégration automatique](#what-is-automatic-onboarding) pour une partie ou la totalité de vos appareils Windows inscrits. L’intégration automatique configure une connexion entre Intune et Defender entreprise, puis intègre Windows appareils à Defender entreprise en toute transparence. 
   - **Si vous n’utilisez pas encore Intune**, vous pouvez [intégrer des appareils à Defender entreprise](mdb-onboard-devices.md). 
   
   [En savoir plus sur l’intégration d’appareils à Microsoft Defender pour les PME](mdb-onboard-devices.md).
   
4. **Configurez vos stratégies de sécurité**. Defender entreprise inclut des stratégies de sécurité par défaut pour la protection de nouvelle génération et la protection pare-feu qui peuvent être appliquées aux appareils de votre entreprise. Ces stratégies par défaut utilisent les paramètres recommandés et sont conçues pour fournir une protection renforcée pour vos appareils. Vous pouvez également créer vos propres stratégies de sécurité. Et, si vous utilisez déjà Intune, vous pouvez continuer à utiliser le centre d’administration Microsoft Endpoint Manager pour gérer vos stratégies de sécurité.

   [Affichez et modifiez vos stratégies et paramètres de sécurité](mdb-configure-security-settings.md).

## <a name="what-is-automatic-onboarding"></a>Qu’est-ce que l’intégration automatique ?

L’intégration automatique est un moyen simplifié d’intégrer des appareils Windows à Defender entreprise. L’intégration automatique est disponible uniquement pour Windows appareils déjà inscrits dans Microsoft Intune. 

Pendant que vous utilisez l’Assistant Installation, le système détecte si Windows appareils sont déjà inscrits dans Intune. Vous serez invité à indiquer si vous souhaitez utiliser l’intégration automatique pour tous ou certains de ces appareils. Vous pouvez intégrer tous les appareils Windows à la fois, ou sélectionner des appareils spécifiques pour commencer, puis ajouter d’autres appareils ultérieurement. 

Pour intégrer d’autres appareils, consultez [Intégrer des appareils à Microsoft Defender pour les PME](mdb-onboard-devices.md).

> [!TIP]
> - Nous vous recommandons de sélectionner l’option « Tous les appareils inscrits ». De cette façon, lorsque Windows appareils sont inscrits dans Intune ultérieurement, ils sont automatiquement intégrés à Defender for Business. 
> - Si vous gérez des stratégies et des paramètres de sécurité dans le centre d’administration Endpoint Manager, nous vous recommandons de basculer vers le portail Microsoft 365 Defender pour gérer vos appareils, stratégies et paramètres. Pour plus d’informations, consultez [Choisir où gérer les stratégies de sécurité et les appareils](mdb-configure-security-settings.md#choose-where-to-manage-security-policies-and-devices).

## <a name="what-happens-if-i-dont-use-the-wizard"></a>Que se passe-t-il si je n’utilise pas l’Assistant ?

L’utilisation de l’Assistant Installation est facultative. Si vous choisissez de ne pas utiliser l’Assistant ou si l’Assistant est fermé avant la fin de votre processus d’installation, vous pouvez effectuer le processus d’installation et de configuration vous-même. 

Consultez [Configurer et configurer Microsoft Defender pour les PME](mdb-setup-configuration.md) pour parcourir les étapes suivantes :

1. **[Attribuez des rôles et des autorisations](mdb-roles-permissions.md)** afin que votre équipe de sécurité puisse accéder au portail Microsoft 365 Defender et l’utiliser ([https://security.microsoft.com](https://security.microsoft.com)).

2. **[Configurez des notifications par e-mail pour votre équipe de sécurité afin](mdb-email-notifications.md)** qu’elles soient en boucle sur les nouvelles alertes ou vulnérabilités.

3. **[Intégrer des appareils](mdb-onboard-devices.md)** afin qu’ils soient protégés par Defender entreprise.

4. **[Gérez vos stratégies de sécurité](mdb-configure-security-settings.md)**, qui incluent la protection de nouvelle génération, la protection pare-feu et le filtrage de contenu web.

## <a name="next-steps"></a>Prochaines étapes

- [Intégrer d’autres appareils à Microsoft Defender pour les PME](mdb-onboard-devices.md)
- [Afficher et modifier vos stratégies et paramètres de sécurité dans Microsoft Defender pour les PME](mdb-configure-security-settings.md)