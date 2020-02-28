---
title: Qu’est-ce qui arrive dans le score de sécurité Microsoft ?
description: Décrit Microsoft Secure score dans le centre de sécurité Microsoft 365, la façon dont les détails sont calculés et les administrateurs de la sécurité qui peuvent s’y attendre.
keywords: sécurité, programmes malveillants, Microsoft 365, M365, Secure score, centre de sécurité, actions d’amélioration
ms.prod: microsoft-365-enterprise
ms.mktglfcycl: deploy
ms.localizationpriority: medium
f1.keywords:
- NOCSH
ms.author: ellevin
author: levinec
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
ms.topic: article
search.appverid:
- MOE150
- MET150
ms.openlocfilehash: 4d445d4c917a46b12592308f599570725ace8e9d
ms.sourcegitcommit: 6c7f6ef98c321c80a9254c10bbbb917895b5c156
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/27/2020
ms.locfileid: "42322563"
---
# <a name="whats-coming-in-microsoft-secure-score"></a>Qu’est-ce qui arrive dans le score de sécurité Microsoft ?

Pour faire en sorte que Microsoft Secure score un meilleur représentant de votre position de sécurité et améliore la convivialité, nous apportons des modifications dans le futur proche. Votre score et le score maximal possible seront modifiés. Toutefois, cela n’implique pas de modification de votre position de sécurité.

Pour en savoir plus sur les modifications récentes, consultez [la rubrique what’s New in Microsoft Secure score ?](microsoft-secure-score.md#whats-new)

## <a name="march-2nd-2020"></a>2nd mars 2020

### <a name="removing-improvement-actions-from-intune"></a>Suppression des actions d’amélioration d’Intune

Après une évaluation des actions de Microsoft Secure scores improved fournies par Intune, il a été décidé de ne pas fournir une représentation utile de la position de sécurité des appareils dans les organisations. Au lieu de se concentrer sur les stratégies, nous nous efforcerons de mettre en place des contrôles de sécurité qui évaluent directement l’état de configuration des appareils.

Les actions d’amélioration d’Intune suivantes seront supprimées :

- Activer la gestion des appareils mobiles Microsoft Intune
- Créer une stratégie de conformité Microsoft Intune pour Android
- Créer une stratégie de conformité Microsoft Intune pour Android pour le travail
- Créer une stratégie de protection des applications Microsoft Intune pour Android
- Créer une stratégie de protection des applications Microsoft Intune pour iOS
- Marquer les appareils sans aucune stratégie de conformité Microsoft Intune attribuée comme non conforme
- Créer une stratégie de conformité Microsoft Intune pour iOS
- Créer une stratégie de conformité Microsoft Intune pour macOS
- Créer une stratégie de conformité Microsoft Intune pour Windows
- Créer un profil de configuration Microsoft Intune pour Android
- Créer un profil de configuration Microsoft Intune pour Android pour le travail
- Créer un profil de configuration Microsoft Intune pour macOS
- Créer un profil de configuration Microsoft Intune pour iOS
- Créer un profil de configuration Microsoft Intune pour Windows
- Activer la détection jailbreak améliorée dans Microsoft Intune
- Exiger l’application des correctifs sur tous les appareils, les antivirus et les pare-feu activés
- Activer l’intégration de Windows Defender ATP dans Microsoft Intune
- Créer une stratégie de protection des informations Windows Microsoft Intune
- Exiger que tous les appareils disposent de configurations de sécurité avancées
- Vérifier toutes les semaines les périphériques bloqués

### <a name="removing-improvement-actions-that-dont-meet-expectations-for-reliable-measurement"></a>Suppression des actions d’amélioration qui ne répondent pas aux attentes en matière de mesure fiable 

Pour vous assurer que le score de sécurité de Microsoft est significatif et que chaque action d’amélioration est mesurable et fiable, nous supprimons les actions d’amélioration suivantes.

- Activer l’enregistrement des données d’audit
- Découverte des applications informatiques de clichés instantanés risquées et non conformes
- Passer en revue les autorisations & bloquer les applications OAuth à risque connectées à votre environnement
- Configurer le contrôle de version sur les bibliothèques de documents SharePoint Online

### <a name="mfa-improvement-action-updates"></a>Mises à jour de l’action d’amélioration MFA

Pour refléter la nécessité pour les entreprises de garantir la sécurité maximale lors de l’application des stratégies qui fonctionnent avec leur entreprise, le score de sécurité Microsoft supprime trois actions d’amélioration axées sur l’authentification multifacteur et en ajoutant deux.

Les trois qui seront supprimés :

- Inscrire tous les utilisateurs pour l’authentification multifacteur
- Exiger l’authentification multifacteur pour tous les utilisateurs
- Exiger l’authentification multifacteur pour les rôles privilège Azure AD

Nouvelles actions d’amélioration ajoutées :

- S’assurer que tous les utilisateurs peuvent effectuer l’authentification multifacteur pour un accès sécurisé
- Exiger MFA pour les rôles d’administration

 Ces nouvelles actions d’amélioration requièrent l’enregistrement de vos utilisateurs ou administrateurs pour l’authentification multifacteur (MFA) dans votre répertoire et l’établissement de l’ensemble approprié de stratégies répondant à vos besoins organisationnels. L’objectif principal est de la flexibilité tout en s’assurant que tous vos utilisateurs et administrateurs peuvent s’authentifier avec plusieurs facteurs ou des invites de vérification d’identité basées sur les risques. Cela peut prendre la forme d’avoir plusieurs stratégies qui appliquent des décisions délimitées ou de définir des paramètres de sécurité par défaut (à venir le 16 mars) qui permettent à Microsoft de décider du défi des utilisateurs pour l’authentification multifacteur.

### <a name="removing-review-improvement-actions"></a>Suppression des actions d’amélioration « révision »

L’un des principes du score de sécurité est que le score doit être standardisé et facile à mettre en relation. Les actions d’amélioration qui ne sont pas mesurables ou exploitables provoquent des confusions. Un score de sécurité Microsoft n’a de sens que si chaque recommandation peut avoir un effet clair sur le score. Examiner les actions d’amélioration ne sont pas mesurées de la même façon que les autres actions d’amélioration.  

Pour ces raisons, toutes les actions d’amélioration nécessitant une cadence de révision seront temporairement supprimées. Aucune action n’est nécessaire de votre part.

## <a name="march-16th-2020"></a>16 mars 2020

### <a name="removing-improvement-actions-that-dont-meet-expectations-for-reliable-measurement-or-dont-provide-a-useful-representation-of-security-posture"></a>Suppression des actions d’amélioration qui ne répondent pas aux attentes en matière de mesure fiable ou ne fournissent pas une représentation utile de la position de la sécurité

Pour vous assurer que le score de sécurité de Microsoft est significatif et que chaque action d’amélioration est mesurable et fiable, nous supprimons les actions d’amélioration suivantes.

- Stocker des documents utilisateur dans OneDrive entreprise
- Configurer des stratégies de pièces jointes approuvées ATP Office 365
- Configurer les liens fiables Office 365 pour vérifier les URL
- Ne pas autoriser la délégation de boîte aux lettres
- Autoriser les liens de partage d’invités anonymes pour les sites et les documents
- Activer la console de sécurité des applications Cloud

### <a name="supporting-security-defaults-for-azure-ad-improvement-actions"></a>Prise en charge des paramètres de sécurité par défaut pour les actions d’amélioration Azure AD

Le score de sécurité Microsoft mettra à jour les actions d’amélioration afin de prendre en charge les paramètres de [sécurité par défaut dans Azure ad](https://docs.microsoft.com/azure/active-directory/fundamentals/concept-fundamentals-security-defaults), ce qui facilite la protection de votre organisation à l’aide de paramètres de sécurité préconfigurés pour les attaques courantes.

Cela aura une incidence sur les actions d’amélioration suivantes :

- S’assurer que tous les utilisateurs peuvent effectuer l’authentification multifacteur pour un accès sécurisé
- Exiger MFA pour les rôles d’administration
- Activer la stratégie pour bloquer l’authentification héritée
