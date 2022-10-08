---
title: Microsoft Defender pour entreprises guide de l’utilisateur d’évaluation
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: Admin
ms.topic: how-to
ms.collection:
- m365-security
- tier1
ms.localizationpriority: high
ms.date: 10/07/2022
ms.service: microsoft-365-security
ms.subservice: mdb
search.appverid:
- MOE150
- MET150
description: Tirez le meilleur parti de votre version d’évaluation de Defender entreprise avec ce guide. Installez-vous rapidement et commencez à utiliser vos nouvelles capacités de sécurité.
ms.custom: trial-playbook
ms.openlocfilehash: 290c5eb2f6ced1816a7955fc8528a3c6cadcccc2
ms.sourcegitcommit: 9f5cf8cf8a2e25cfd07b23b7f6d7f9d138a9cd16
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2022
ms.locfileid: "68501529"
---
# <a name="trial-user-guide-microsoft-defender-for-business"></a>Guide de l’utilisateur d’évaluation : Microsoft Defender pour entreprises

**Bienvenue dans le guide de l’utilisateur de la version d’évaluation de Defender for Business !**

Ce guide vous aidera à configurer et à utiliser les fonctionnalités clés de votre version d’évaluation gratuite. À l’aide des recommandations de cet article de l’équipe Microsoft Defender, découvrez comment Defender entreprise peut vous aider à élever votre sécurité, de la protection antivirus traditionnelle à la protection de nouvelle génération, à la détection et à la réponse des points de terminaison, ainsi qu’à la gestion des vulnérabilités.

## <a name="what-is-defender-for-business"></a>Qu’est-ce que Defender pour les PME ?

Defender pour entreprise est une nouvelle solution de sécurité des terminaux conçue spécialement pour les petites et moyennes entreprises comptant jusqu'à 300 employés. Avec cette solution de sécurité des terminaux, les appareils de votre entreprise sont bien protégés contre les ransomwares, les logiciels malveillants, le hameçonnage et d'autres menaces.

:::image type="content" source="media/mdb-offering-overview.png" alt-text="Fonctionnalités et capacités de Defender pour entreprise.":::

**Mettons-nous au travail.**

## <a name="set-up-your-trial"></a>Organisez votre essai

Voici comment mettre en place votre abonnement d'essai :

1. [Ajouter des utilisateurs et attribuer des licences](#step-1-add-users-and-assign-licenses).
2. [Visitez le portail Microsoft 365 Defender](#step-2-visit-the-microsoft-365-defender-portal).
3. [Utiliser l'assistant d'installation](#step-3-use-the-setup-wizard-in-defender-for-business-recommended).
4. [Installation et configuration de Defender pour entreprises](#step-4-set-up-and-configure-defender-for-business).

### <a name="step-1-add-users-and-assign-licenses"></a>Étape 1 : Ajouter des utilisateurs et attribuer des licences

Une fois que vous êtes inscrit à Defender pour entreprise, la première étape consiste à **[ajouter des utilisateurs et à attribuer des licences](mdb-add-users.md)**.

> [!NOTE]
> Vous devez être un administrateur global pour effectuer cette tâche. La personne qui a inscrit votre entreprise à Microsoft 365 ou à Defender pour entreprise est l'administrateur global par défaut. [En savoir plus sur les rôles et les autorisations](mdb-roles-permissions.md).

### <a name="step-2-visit-the-microsoft-365-defender-portal"></a>Étape 2 : Visitez le portail Microsoft 365 Defender

Le portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) est le guichet unique où vous utilisez et gérez Defender pour entreprise. Il comprend des rappels pour vous aider à démarrer, des cartes qui présentent des informations pertinentes et une barre de navigation qui permet d'accéder facilement aux différentes fonctions et capacités.

- **[Visitez le portail Microsoft 365 Defender](mdb-get-started.md)**.
- **[Explorez la barre de navigation](mdb-get-started.md#the-navigation-bar)** située à gauche de l'écran pour accéder à vos incidents, consulter les rapports et gérer vos stratégies et paramètres de sécurité.

### <a name="step-3-use-the-setup-wizard-in-defender-for-business-recommended"></a>Étape 3 : utiliser l'assistant de configuration de Defender pour entreprises (recommandé)

Defender pour entreprise a été conçu pour faire gagner du temps et de l'énergie aux petites et moyennes entreprises. Vous pouvez effectuer l'installation et la configuration initiales à l'aide d'un assistant d'installation. L'assistant de configuration vous aide à accorder l'accès à votre équipe de sécurité, à configurer les notifications par courriel pour votre équipe de sécurité et à intégrer les appareils Windows de votre entreprise. **[Utiliser l'assistant d'installation](mdb-use-wizard.md)**.

> [!NOTE]
> Vous ne pouvez utiliser l'assistant de configuration qu'une seule fois.

#### <a name="setup-wizard-flow-what-to-expect"></a>Flux de l'assistant de configuration : à quoi s'attendre

> [!TIP]
> **L'utilisation de l'assistant d'installation est facultative** (Voir [Ce qui se passe si je n’utilise pas l’Assistant ?](mdb-use-wizard.md#what-happens-if-i-dont-use-the-wizard)). Si vous choisissez de ne pas utiliser l’Assistant ou si l’Assistant est fermé avant la fin de votre processus d’installation, vous pouvez effectuer le processus d’installation et de configuration vous-même. Consultez [l’étape 4 : Configurer et configurer Defender entreprise](#step-4-set-up-and-configure-defender-for-business).

1. **[Attribuer des autorisations aux utilisateurs](mdb-roles-permissions.md#view-or-edit-role-assignments)**. Accordez à votre équipe de sécurité l'accès au portail Microsoft 365 Defender.

2. **[Configurez des notifications](mdb-email-notifications.md#view-and-edit-email-notifications)** par e-mail pour votre équipe de sécurité.

3. **[Embarquer et configurer les appareils Windows](mdb-onboard-devices.md)**. L'intégration immédiate des appareils permet de les protéger dès le premier jour.

   > [!NOTE]
   > Lorsque vous utilisez l'assistant d'installation, le système détecte si vous avez des appareils Windows qui sont déjà inscrits dans Intune. Il vous sera demandé si vous souhaitez utiliser l'intégration automatique pour tous ou certains de ces appareils. Vous pouvez embarquer tous les appareils Windows en même temps ou sélectionner des appareils spécifiques dans un premier temps, puis ajouter d'autres appareils par la suite. [En savoir plus sur l' onboarding automatique](mdb-use-wizard.md#what-is-automatic-onboarding).

   Pour embarquer d'autres appareils, voir [l'étape 4](#step-4-set-up-and-configure-defender-for-business).

4. **[Afficher et modifier vos stratégies de sécurité](mdb-configure-security-settings.md)**. Defender pour entreprise comprend des stratégies de sécurité par défaut pour une protection de nouvelle génération et une protection par pare-feu qui peuvent être appliquées aux appareils de votre entreprise. Ces stratégies de sécurité préconfigurées utilisent des paramètres recommandés, de sorte que vous êtes protégé dès que vos appareils sont intégrés à Defender pour entreprise. Et vous pouvez modifier les stratégies ou en créer de nouvelles.

### <a name="step-4-set-up-and-configure-defender-for-business"></a>Étape 4 : Installation et configuration de Defender pour entreprise

Si vous choisissez de ne pas utiliser l'assistant d'installation, consultez le [diagramme suivant qui décrit le processus](mdb-setup-configuration.md#the-setup-and-configuration-process) global d'installation et de configuration de Defender pour entreprise.

[:::image type="content" source="media/mdb-setup-process-2.png" alt-text="Processus d'installation et de configuration de Defender pour entreprise.":::](mdb-setup-configuration.md)

Si vous avez utilisé l’Assistant Installation, mais que vous devez intégrer d’autres appareils, tels que des appareils non Windows, passez directement à [l’étape 4](mdb-onboard-devices.md) de la procédure suivante :

1. **[Passez en revue les conditions requises](mdb-requirements.md)** pour configurer et utiliser Defender pour entreprise.

2. **[Attribuez des rôles et des autorisations](mdb-roles-permissions.md)** dans le portail Microsoft 365 Defender.

   - [En savoir plus sur les rôles dans Defender pour entreprises](mdb-roles-permissions.md#roles-in-defender-for-business). 
   - [Afficher ou modifier les attributions de rôles pour votre équipe de sécurité](mdb-roles-permissions.md#view-or-edit-role-assignments).

3. **[Configurez des notifications](mdb-email-notifications.md)** par courriel pour votre équipe de sécurité.

   - [Découvrez les types de notifications par e-mail](mdb-email-notifications.md#types-of-email-notifications).
   - [Afficher et modifier les paramètres de notification par e-mail](mdb-email-notifications.md#view-and-edit-email-notifications).

4. **[Appareils embarqués](mdb-onboard-devices.md)**. Pour intégrer des clients Windows et Mac, vous pouvez utiliser un script local.

5. **[Afficher et configurer vos stratégies de sécurité](mdb-configure-security-settings.md)**. Après avoir intégré les appareils de votre entreprise à Defender pour entreprise, l'étape suivante consiste à afficher et à modifier vos stratégies et paramètres de sécurité. 

Defender entreprise inclut des stratégies de sécurité préconfigurées qui utilisent les paramètres recommandés. Mais vous pouvez modifier les paramètres en fonction des besoins de votre entreprise.

Les stratégies de sécurité à examiner et à configurer sont les suivantes :

- [Stratégies de protection de nouvelle génération](mdb-configure-security-settings.md#view-or-edit-your-next-generation-protection-policies) qui déterminent la protection antivirus et anti-programme malveillant pour les appareils de votre entreprise
- [Protection et règles de pare-feu](mdb-configure-security-settings.md#view-or-edit-your-firewall-policies-and-custom-rules) qui déterminent le trafic réseau autorisé à circuler vers et depuis les appareils de votre entreprise
- [Filtrage de contenu web](mdb-configure-security-settings.md#set-up-web-content-filtering)qui empêche les utilisateurs de visiter certains sites web (URL) en fonction de catégories, telles que le contenu pour adultes ou la responsabilité légale
- [Fonctionnalités avancées](mdb-configure-security-settings.md#review-settings-for-advanced-features) telles que l’investigation automatisée, la réponse et la détection et la réponse de point de terminaison (EDR) en mode bloc

## <a name="start-using-defender-for-business"></a>Commencez à utiliser Defender pour entreprises

Pour les 30 prochains jours, voici les conseils de l’équipe produit sur les principales fonctionnalités à essayer :

1. [Utilisez votre tableau de bord Gestion des vulnérabilités Microsoft Defender](#1-use-the-defender-vulnerability-management-dashboard). 

2. [Visualiser et répondre aux menaces détectées](#2-view-and-respond-to-detected-threats).

3. [Examiner les stratégies de sécurité](#3-review-security-policies).

4. [Préparez-vous à la gestion continue de la sécurité](#4-prepare-for-ongoing-security-management).

5. [Essayez le didacticiel Document Drops Backdoor](#5-try-the-document-drops-backdoor-tutorial).

### <a name="1-use-the-defender-vulnerability-management-dashboard"></a>1. Utiliser le tableau de bord Gestion des vulnérabilités Defender

Defender entreprise inclut un tableau de bord de gestion des vulnérabilités Defender conçu pour économiser du temps et des efforts de votre équipe de sécurité. Découvrez comment [utiliser votre tableau de bord Gestion des vulnérabilités Defender](mdb-view-tvm-dashboard.md).

- Consultez votre score d'exposition, qui est associé aux appareils de votre organisation.
- Consultez vos principales recommandations en matière de sécurité, telles que la résolution des problèmes de communication avec les appareils, l'activation de la protection par pare-feu ou la mise à jour des définitions de l'antivirus Microsoft Defender.
- Visualisez les activités de remédiation, comme les fichiers qui ont été envoyés en quarantaine ou les vulnérabilités trouvées sur les appareils.

### <a name="2-view-and-respond-to-detected-threats"></a>2. Afficher et répondre aux menaces détectées

Lorsque des menaces sont détectées et que des alertes sont déclenchées, des incidents sont créés. L'équipe de sécurité de votre organisation peut consulter et gérer les incidents dans le portail Microsoft 365 Defender. Découvrez comment [afficher et répondre aux menaces détectées](mdb-view-manage-incidents.md). 

- [Afficher et gérer les incidents](mdb-view-manage-incidents.md).
- [Répondre aux menaces et les atténuer](mdb-respond-mitigate-threats.md).
- [Revoir les actions de médiation dans le Centre d'action](mdb-review-remediation-actions.md).
- [Afficher et utiliser les rapports](mdb-reports.md).

### <a name="3-review-security-policies"></a>3. Examiner les stratégies de sécurité

Dans Defender pour entreprise, les paramètres de sécurité sont configurés par le biais de stratégies qui sont appliquées aux appareils. Defender entreprise inclut des stratégies préconfigurées pour protéger les appareils de votre entreprise dès qu’ils sont intégrés, en protégeant votre organisation contre les menaces de sécurité d’identité, d’appareil, d’application et de document. 

Découvrez comment [passer en revue les stratégies de sécurité](mdb-view-edit-create-policies.md).

### <a name="4-prepare-for-ongoing-security-management"></a>4. Préparer la gestion continue de la sécurité

De nouveaux événements liés à la sécurité, tels que la détection d'une menace sur un appareil, l'ajout de nouveaux appareils et l'entrée ou le départ d'employés de l'organisation, vous obligeront à gérer la sécurité. Dans Defender pour entreprise, vous disposez de plusieurs moyens pour gérer la sécurité des appareils.

- [Affichez une liste des appareils](mdb-manage-devices.md#view-the-list-of-onboarded-devices) embarqués pour connaître leur niveau de risque, leur niveau d'exposition et leur état de santé.
- [Prendre des mesures sur un appareil](mdb-manage-devices.md#take-action-on-a-device-that-has-threat-detections) qui a détecté des menaces.
- [Intégrer un appareil à Defender pour entreprise](mdb-manage-devices.md#onboard-a-device).
- [Désinstaller un appareil de Defender pour entreprise](mdb-manage-devices.md#offboard-a-device).

### <a name="5-try-the-document-drops-backdoor-tutorial"></a>5. Essayez le didacticiel sur les suppressions de porte dérobée de document

Découvrez rapidement le fonctionnement de Defender Entreprise en essayant un didacticiel.

Simuler une attaque qui introduit des programmes malveillants basés sur des fichiers sur un appareil de test. Le didacticiel explique comment utiliser le fichier de simulation et ce qu’il faut surveiller dans le portail Microsoft 365 Defender.

>[!NOTE]
> Ce didacticiel nécessite l’installation de Microsoft Word sur votre appareil de test.

Pour accéder au didacticiel, procédez comme suit :

1. Accédez au [Portail Microsoft 365 Defender](https://security.microsoft.com) et connectez-vous.

2. Dans le volet de navigation, sous **Points de terminaison**, choisissez **Didacticiels**.

3. Choisissez **La porte dérobée du document**.

## <a name="additional-resources"></a>Ressources supplémentaires

- [Aperçu de Defender pour entreprises](mdb-overview.md).
- [Tutoriels et simulations dans Defender pour entreprises](mdb-tutorials.md)
- [Vidéo : Une protection de niveau entreprise pour les petites et moyennes entreprises](https://youtu.be/umhUNzMqZto)
- [Obtenir Defender pour les PME](get-defender-business.md)
