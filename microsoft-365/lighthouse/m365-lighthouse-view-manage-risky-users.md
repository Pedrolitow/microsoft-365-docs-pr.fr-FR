---
title: Afficher et gérer les utilisateurs à risque
f1.keywords: NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
audience: Admin
ms.topic: article
ms.prod: microsoft-365-lighthouse
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- M365-Lighthouse
search.appverid: MET150
description: Pour les fournisseurs de services gérés (MSP) utilisant Microsoft 365 Lighthouse, découvrez comment afficher et gérer les utilisateurs à risque.
ms.openlocfilehash: 708fc0576c85d9b8511ac6b31ed0398fae1b20d3
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63330846"
---
# <a name="view-and-manage-risky-users"></a>Afficher et gérer les utilisateurs à risque

Microsoft collecte et analyse des milliards de signaux de connectez-vous de l’utilisateur chaque jour. Ces signaux permettent de créer de bons modèles de comportement de la signature utilisateur et d’identifier les tentatives de se connectant potentiellement à risque. Azure Active Directory (Azure AD) Identity Protection utilise ces signaux pour passer en revue les tentatives de connectez-vous de l’utilisateur et prendre des mesures en cas d’activité suspecte.

Microsoft 365 Lighthouse permet de gérer les risques détectés par Azure AD Identity Protection en fournissant une vue unique des utilisateurs à risque sur tous vos clients gérés. Vous pouvez sécuriser rapidement les utilisateurs à risque en réinitialisation de leur mot de passe ou en les bloquant de se Microsoft 365 compte. Vous pouvez également afficher des informations pour mieux comprendre les risques d’un utilisateur et déterminer les étapes suivantes.

Azure AD Identity Protection identifie les risques de nombreux types, notamment :

- Fuites d’informations d’identification
- Utilisation d’adresses IP anonymes
- Voyages inhabituels
- Se connecté à partir d’appareils infectés
- Se signer à partir d’adresses IP avec une activité suspecte
- Se dédicacer à partir d’emplacements inconnus

## <a name="before-you-begin"></a>Avant de commencer

Les conditions suivantes doivent être remplies pour que les utilisateurs apparaissent dans la liste des utilisateurs à risque :

- Le client doit avoir une licence Azure AD Premium client pour chaque utilisateur. Pour plus d’informations sur les licences qui Azure AD Identity Protection, voir [Qu’est-ce que Identity Protection ?](/azure/active-directory/identity-protection/overview-identity-protection)

- Le client doit être actif dans Microsoft 365 Lighthouse. Pour déterminer si un client est actif, voir Microsoft 365 Lighthouse [page Des locataires.](m365-lighthouse-tenant-list-overview.md)

## <a name="review-detected-risks-and-take-action"></a>Examiner les risques détectés et prendre des mesures

Dans Azure AD Identity Protection, les détections de risque incluent les actions suspectes identifiées liées aux comptes d’utilisateurs Azure AD.

1. Dans le volet de navigation gauche de l’écran, sélectionnez **Utilisateurs**.

2. Sélectionnez **l’onglet Utilisateurs à** risque.

3. Examinez les utilisateurs de la liste avec un état à **risque.**

4. **Sélectionnez Afficher les détections de** risque pour obtenir des informations détaillées sur les risques détectés pour chaque utilisateur. Pour plus d’informations sur les types de risque et la détection, voir [Qu’est-ce qu’un risque ?](/azure/active-directory/identity-protection/concept-identity-protection-risks)

5. Pour chaque utilisateur, évaluez les détections de risque et sélectionnez l’une des actions suivantes, selon le cas :

    - Réinitialiser le mot de passe : modifiez ou réinitialisez le mot de passe de l’utilisateur.

    - Bloquer la connectez-vous : empêchez tout le monde de se connecter en tant qu’utilisateur.

    - Confirmer que l’utilisateur est compromis : définir l’état de risque sur Compromis confirmé.

    - Ignorer les risques pour l’utilisateur : définir l’état de risque sur ignorer.

## <a name="take-action-on-multiple-user-accounts-at-once"></a>Prendre des mesures sur plusieurs comptes d’utilisateurs à la fois

Pour prendre des mesures sur plusieurs utilisateurs affectés à la fois :

1. Sous **l’onglet Utilisateurs** à risque, sélectionnez l’ensemble d’utilisateurs sur qui vous souhaitez agir.

2. Choisissez l’une des actions suivantes à effectuer :

    - Réinitialiser le mot de passe

    - Bloquer la sign-in

    - Confirmer que l’utilisateur a été compromis

    - Ignorer les risques pour l’utilisateur

> [!NOTE]
> Si l’organisation que vous gérez possède une licence Azure AD Premium P2, il est recommandé d’activer les stratégies d’accès conditionnel basées sur les risques utilisateur. Pour plus d’informations, [voir Accès conditionnel : accès conditionnel basé sur les risques de l’utilisateur](/azure/active-directory/conditional-access/howto-conditional-access-policy-risk-user).

## <a name="related-content"></a>Contenu associé
[Didacticiel : Utiliser les détections de risque pour les utilisateurs](/azure/active-directory/authentication/tutorial-risk-based-sspr-mfa) qui se connectent pour déclencher Azure AD l’authentification multifacteur ou des modifications de mot de passe (article)\
[Qu’est-ce qu’un risque ?](/azure/active-directory/identity-protection/concept-identity-protection-risks) (article) \
[Corriger les risques et débloquer les utilisateurs](/azure/active-directory/identity-protection/howto-identity-protection-remediate-unblock) (article)
