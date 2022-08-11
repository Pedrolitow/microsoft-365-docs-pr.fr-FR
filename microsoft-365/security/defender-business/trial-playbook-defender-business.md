---
title: Manuel d'essai de Microsoft Defender pour entreprise
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: Admin
ms.topic: article
ms.collection: m365-security-compliance
ms.localizationpriority: high
ms.date: 08/10/2022
ms.prod: m365-security
ms.technology: mdb
search.appverid:
- MOE150
- MET150
description: Tirez le meilleur parti de votre essai de Defender pour entreprise grâce à ce guide. Installez-vous rapidement et commencez à utiliser vos nouvelles capacités de sécurité.
ms.custom: trial-playbook
ms.openlocfilehash: 3b588dba1ee1a3df5719ece9c2db50e76acf36b2
ms.sourcegitcommit: 771f7bbb241f910b3e16b4d1f9bbd9c0c8c6fa34
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/11/2022
ms.locfileid: "67309480"
---
# <a name="trial-playbook-microsoft-defender-for-business"></a>Manuel d'essai : Microsoft Defender pour entreprise

**Bienvenue au guide d'essai de Defender pour entreprises**

Ce manuel est un guide simple qui vous aidera à tirer le meilleur parti de votre essai gratuit de 30 jours. Utilisez les recommandations de cet article de l'équipe Microsoft Defender pour apprendre comment Defender pour entreprise peut vous aider à élever votre sécurité de la protection antivirus traditionnelle à la protection de nouvelle génération, à la détection et à la réponse des points d'extrémité, et à la gestion des menaces et des vulnérabilités.

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
> **L'utilisation de l'assistant d'installation est facultative** (Voir [Que se passe-t-il si je n'utilise pas l'assistant ?](mdb-use-wizard.md#what-happens-if-i-dont-use-the-wizard)) Si vous choisissez de ne pas utiliser l'assistant, ou si l'assistant est fermé avant la fin du processus d'installation, vous pouvez terminer le processus d'installation et de configuration par vous-même. Voir [l'étape 4](#step-4-set-up-and-configure-defender-for-business). 

1. **[Attribuer des autorisations aux utilisateurs](mdb-roles-permissions.md#view-or-edit-role-assignments)**. Accordez à votre équipe de sécurité l'accès au portail Microsoft 365 Defender.

2. **[Configurez des notifications](mdb-email-notifications.md#view-and-edit-email-notifications)** par e-mail pour votre équipe de sécurité.

3. **[Embarquer et configurer les appareils Windows](mdb-onboard-devices.md)**. L'intégration immédiate des appareils permet de les protéger dès le premier jour.

   > [!NOTE]
   > Lorsque vous utilisez l'assistant d'installation, le système détecte si vous avez des appareils Windows qui sont déjà inscrits dans Intune. Il vous sera demandé si vous souhaitez utiliser l'intégration automatique pour tous ou certains de ces appareils. Vous pouvez embarquer tous les appareils Windows en même temps ou sélectionner des appareils spécifiques dans un premier temps, puis ajouter d'autres appareils par la suite. [En savoir plus sur l' onboarding automatique](mdb-use-wizard.md#what-is-automatic-onboarding).
   
   Pour embarquer d'autres appareils, voir [l'étape 4](#step-4-set-up-and-configure-defender-for-business).

4.  **[Afficher et modifier vos stratégies de sécurité](mdb-configure-security-settings.md)**. Defender pour entreprise comprend des stratégies de sécurité par défaut pour une protection de nouvelle génération et une protection par pare-feu qui peuvent être appliquées aux appareils de votre entreprise. Ces stratégies de sécurité préconfigurées utilisent des paramètres recommandés, de sorte que vous êtes protégé dès que vos appareils sont intégrés à Defender pour entreprise. Et vous pouvez modifier les stratégies ou en créer de nouvelles.

### <a name="step-4-set-up-and-configure-defender-for-business"></a>Étape 4 : Installation et configuration de Defender pour entreprise

Si vous choisissez de ne pas utiliser l'assistant d'installation, consultez le [diagramme suivant qui décrit le processus](mdb-setup-configuration.md#the-setup-and-configuration-process) global d'installation et de configuration de Defender pour entreprise.

[:::image type="content" source="media/mdb-setup-process-2.png" alt-text="Processus d'installation et de configuration de Defender pour entreprise.":::](mdb-setup-configuration.md)

Si vous avez utilisé l'assistant d'installation mais que vous devez embarquer plus d'appareils, tels que des appareils non-Windows, passez directement à l'étape 4 de la procédure suivante :

1. **[Passez en revue les conditions requises](mdb-requirements.md)** pour configurer et utiliser Defender pour entreprise. 

2. **[Attribuez des rôles et des autorisations](mdb-roles-permissions.md)** dans le portail Microsoft 365 Defender.

   - [En savoir plus sur les rôles dans Defender pour entreprises](mdb-roles-permissions.md#roles-in-defender-for-business). 
   - [Afficher ou modifier les attributions de rôles pour votre équipe de sécurité](mdb-roles-permissions.md#view-or-edit-role-assignments).

3. **[Configurez des notifications](mdb-email-notifications.md)** par courriel pour votre équipe de sécurité.

   - [Découvrez les types de notifications par e-mail](mdb-email-notifications.md#types-of-email-notifications).
   - [Afficher et modifier les paramètres de notification par e-mail](mdb-email-notifications.md#view-and-edit-email-notifications).

4. **[Appareils embarqués](mdb-onboard-devices.md)**. Avec Defender pour entreprise, vous avez le choix entre plusieurs options pour l'intégration des appareils de votre entreprise. Tout d'abord, sélectionnez le système d'exploitation que vous souhaitez embarquer.

   | Type d’appareil | Méthodes d'embarquement |
   |:---|:---|
   | [Clients Windows](mdb-onboard-devices.md) | Choisissez l'une des options suivantes pour intégrer des appareils clients Windows à Defender pour entreprises :<ul><li>Script local (pour l'intégration manuelle des appareils dans le portail Microsoft 365 Defender)</li><li>Stratégie de groupe (si vous utilisez déjà la stratégie de groupe et préférez cette méthode)</li><li>Microsoft Intune (si vous utilisez déjà Intune et préférez continuer à l’utiliser)</li></ul> |
   | [Mac](mdb-onboard-devices.md) | Choisissez l'une des options suivantes pour le Mac embarqué :<ul><li>Script local pour Mac (*recommandé*)</li><li>Microsoft Intune pour Mac </li></ul><p>Nous vous recommandons d'utiliser un script local pour embarquer le Mac. Bien que vous puissiez [configurer l'inscription des appareils Mac dans Intune](/mem/intune/enrollment/macos-enroll), le script local est la méthode la plus simple pour intégrer Mac à Defender pour entreprise. |
   | Serveurs Windows et Linux | *La possibilité d'embarquer une instance de Windows Server ou de Linux Server est actuellement en phase d'essai et nécessite une licence supplémentaire.*. Voir les articles suivants pour en savoir plus : <ul><li>[Defender pour les besoins de l'entreprise](mdb-requirements.md)</li><li>[Transférer les appareils vers Defender pour entreprise](mdb-onboard-devices.md)</li></ul> |
   | [Appareils mobiles](mdb-onboard-devices.md) | Utilisez Microsoft Intune pour intégrer des appareils mobiles, tels que des appareils Android et iOS/iPadOS. Voir les ressources suivantes pour obtenir de l'aide pour inscrire ces appareils dans Intune :<ul><li>[Inscrire des appareils Android](/mem/intune/enrollment/android-enroll)</li><li>[Inscrire les appareils iOS ou iPadOS](/mem/intune/enrollment/ios-enroll)</li></ul> |

5. **[Afficher et configurer vos stratégies de sécurité](mdb-configure-security-settings.md)**. Après avoir intégré les appareils de votre entreprise à Defender pour entreprise, l'étape suivante consiste à afficher et à modifier vos stratégies et paramètres de sécurité. Defender pour entreprise comprend des stratégies de sécurité préconfigurées qui utilisent des paramètres recommandés. Mais vous pouvez modifier les paramètres en fonction des besoins de votre entreprise.

   | Opération | Description |
   |:---|:---|
   | [Choisissez où gérer vos stratégies et appareils de sécurité](mdb-configure-security-settings.md#choose-where-to-manage-security-policies-and-devices). | Si vous sélectionnez [le processus de configuration](mdb-simplified-configuration.md) simplifié , vous pouvez afficher et gérer vos stratégies de sécurité dans le portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)). Mais vous n'êtes pas limité à cette option. Si vous avez utilisé [Intune](/mem/intune/protect/) , vous pouvez continuer à utiliser le centre d'administration de Microsoft Endpoint Manager pour gérer vos stratégies de sécurité et vos appareils. |
   | [Visualisez ou modifiez vos stratégies de protection de nouvelle génération](mdb-configure-security-settings.md#view-or-edit-your-next-generation-protection-policies). | Les paramètres de protection de nouvelle génération comprennent la protection en temps réel, le blocage à première vue, la protection du réseau, les actions à entreprendre sur les applications potentiellement indésirables et les analyses antivirus programmées.  |
   | [Afficher ou modifier vos stratégies de pare-feu](mdb-configure-security-settings.md#view-or-edit-your-firewall-policies-and-custom-rules). | La protection par pare-feu détermine quel trafic réseau est autorisé à circuler vers et depuis les appareils de votre entreprise. [Les règles personnalisées](mdb-custom-rules-firewall.md) peuvent être utilisées pour définir des exceptions à vos stratégies de pare-feu. |
   | [Configurer le filtrage du contenu Web](mdb-configure-security-settings.md#set-up-web-content-filtering). | Le filtrage du contenu Web permet à votre équipe de sécurité de suivre et de réguler l'accès aux sites Web en fonction de leurs catégories de contenu, telles que le contenu pour adultes, la bande passante élevée, la responsabilité légale, les loisirs ou les catégories non classées. |
   | [Examiner les paramètres des fonctions avancées](mdb-configure-security-settings.md#review-settings-for-advanced-features). | Dans Defender pour entreprise, les fonctions de sécurité sont préconfigurées selon les paramètres recommandés. Vous pouvez revoir et modifier les paramètres en fonction des besoins de votre entreprise. <br/><br/>Pour accéder aux paramètres des fonctions avancées, dans le portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)), allez dans **Paramètres** > **Endpoints** > **Général** > **Fonctions avancées**. |
   | [Afficher et modifier d'autres paramètres](mdb-configure-security-settings.md#access-your-settings-in-the-microsoft-365-defender-portal) dans le portail Microsoft 365 Defender. | Outre les politiques de sécurité qui sont appliquées aux appareils, il existe d'autres paramètres que vous pouvez afficher et modifier dans Defender pour entreprise. Par exemple, vous spécifiez le fuseau horaire à utiliser, et vous pouvez embarquer (ou débarquer) des appareils. |

## <a name="start-using-defender-for-business"></a>Commencez à utiliser Defender pour entreprises

Au cours des 30 prochains jours, nous vous recommandons de tester vos nouvelles capacités de sécurité, comme décrit dans les sections suivantes :

- [Utilisez votre tableau de bord de gestion des menaces et des vulnérabilités](#use-the-threat--vulnerability-management-dashboard) 
- [Visualiser et répondre aux menaces détectées](#view-and-respond-to-detected-threats)
- [Examiner les stratégies de sécurité](#review-security-policies).
- [Se préparer à la gestion continue de la sécurité](#prepare-for-ongoing-security-management)

### <a name="use-the-threat--vulnerability-management-dashboard"></a>Utilisez le tableau de bord de gestion des menaces et des vulnérabilités.

Defender pour entreprise comprend un tableau de bord de gestion des menaces et des vulnérabilités, conçu pour faire gagner du temps et de l'énergie à votre équipe de sécurité. [Utilisez votre tableau de bord de gestion des menaces et des vulnérabilités](mdb-view-tvm-dashboard.md).

- Consultez votre score d'exposition, qui est associé aux appareils de votre organisation.
- Consultez vos principales recommandations en matière de sécurité, telles que la résolution des problèmes de communication avec les appareils, l'activation de la protection par pare-feu ou la mise à jour des définitions de l'antivirus Microsoft Defender.
- Visualisez les activités de remédiation, comme les fichiers qui ont été envoyés en quarantaine ou les vulnérabilités trouvées sur les appareils.

### <a name="view-and-respond-to-detected-threats"></a>Visualiser et répondre aux menaces détectées

Lorsque des menaces sont détectées et que des alertes sont déclenchées, des incidents sont créés. L'équipe de sécurité de votre organisation peut consulter et gérer les incidents dans le portail Microsoft 365 Defender. [Visualiser et répondre aux menaces détectées](mdb-view-manage-incidents.md). 

- [Afficher et gérer les incidents](mdb-view-manage-incidents.md).
- [Répondre aux menaces et les atténuer](mdb-respond-mitigate-threats.md).
- [Revoir les actions de médiation dans le Centre d'action](mdb-review-remediation-actions.md).
- [Afficher et utiliser les rapports](mdb-reports.md).

### <a name="review-security-policies"></a>Examiner les stratégies de sécurité

Dans Defender pour entreprise, les paramètres de sécurité sont configurés par le biais de stratégies qui sont appliquées aux appareils. Defender pour entreprise inclut des stratégies préconfigurées pour aider à protéger les appareils de votre entreprise dès qu'ils sont intégrés, protégeant ainsi votre organisation contre les menaces de sécurité liées aux identités, aux appareils, aux applications et aux documents. [Examiner les stratégies de sécurité](mdb-view-edit-create-policies.md).

- [Découvrez vos stratégies par défaut](mdb-view-edit-create-policies.md#default-policies-in-defender-for-business).
- [Consultez vos stratégies existantes](mdb-view-edit-create-policies.md#view-your-existing-policies).
- [Comprendre l'ordre des stratégies](mdb-policy-order.md). 
- [Comprendre les paramètres de configuration de la prochaine génération](mdb-next-gen-configuration-settings.md).
- [Vérifiez les paramètres par défaut de votre pare-feu](mdb-firewall.md#default-firewall-settings-in-defender-for-business).
- [Comprendre les paramètres du pare-feu que vous pouvez configurer](mdb-firewall.md#firewall-settings-you-can-configure-in-defender-for-business).
- [Configurer le filtrage du contenu Web](mdb-configure-security-settings.md#set-up-web-content-filtering). Le filtrage du contenu Web permet à votre équipe de sécurité de suivre et de réguler l'accès aux sites Web en fonction de leurs catégories de contenu. Elle n'est pas activée par défaut, vous devez donc la configurer si vous souhaitez que votre organisation dispose de cette fonctionnalité.
  
### <a name="prepare-for-ongoing-security-management"></a>Se préparer à la gestion continue de la sécurité

De nouveaux événements liés à la sécurité, tels que la détection d'une menace sur un appareil, l'ajout de nouveaux appareils et l'entrée ou le départ d'employés de l'organisation, vous obligeront à gérer la sécurité. Dans Defender pour entreprise, vous disposez de plusieurs moyens pour gérer la sécurité des appareils.

- [Affichez une liste des appareils](mdb-manage-devices.md#view-the-list-of-onboarded-devices) embarqués pour connaître leur niveau de risque, leur niveau d'exposition et leur état de santé.
- [Prendre des mesures sur un appareil](mdb-manage-devices.md#take-action-on-a-device-that-has-threat-detections) qui a détecté des menaces.
- [Intégrer un appareil à Defender pour entreprise](mdb-manage-devices.md#onboard-a-device).
- [Désinstaller un appareil de Defender pour entreprise](mdb-manage-devices.md#offboard-a-device).

## <a name="additional-resources"></a>Ressources supplémentaires

- [Aperçu de Defender pour entreprises](mdb-overview.md).
- [Tutoriels et simulations dans Defender pour entreprises](mdb-tutorials.md)
- [Vidéo : Une protection de niveau entreprise pour les petites et moyennes entreprises](https://youtu.be/umhUNzMqZto)
- [Obtenir Defender pour les PME](get-defender-business.md)
