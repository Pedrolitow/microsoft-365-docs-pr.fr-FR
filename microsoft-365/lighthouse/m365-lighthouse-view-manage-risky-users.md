---
title: Afficher et gérer les utilisateurs à risque dans Microsoft 365 Lighthouse
f1.keywords: NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
ms-reviewer: ragovind
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
description: Pour les fournisseurs de services gérés (MSP) qui utilisent Microsoft 365 Lighthouse, découvrez comment afficher et gérer les utilisateurs à risque.
ms.openlocfilehash: 45c91ec0871393f69e7a166cc8582f149479ad1b
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/10/2022
ms.locfileid: "66011835"
---
# <a name="view-and-manage-risky-users-in-microsoft-365-lighthouse"></a>Afficher et gérer les utilisateurs à risque dans Microsoft 365 Lighthouse

Microsoft collecte et analyse des billions de signaux de connexion utilisateur chaque jour. Ces signaux sont utilisés pour aider à créer de bons modèles de comportement de connexion utilisateur et à identifier les tentatives de connexion potentiellement risquées. Azure Active Directory (Azure AD) Identity Protection utilise ces signaux pour examiner les tentatives de connexion des utilisateurs et prendre des mesures en cas d’activité suspecte.

Microsoft 365 Lighthouse permet de gérer les risques détectés par Azure AD Identity Protection en fournissant une vue unique des utilisateurs à risque sur tous vos locataires gérés. Vous pouvez rapidement sécuriser les utilisateurs à risque en réinitialisant leur mot de passe ou en les empêchant de se connecter à leur compte Microsoft 365. Vous pouvez également afficher des insights pour mieux comprendre le risque d’un utilisateur et déterminer les étapes suivantes.

Azure AD Identity Protection identifie les risques de nombreux types, notamment :

- Fuites d’informations d’identification
- Utilisation d’adresses IP anonymes
- Voyage atypique
- Connexion à partir d’appareils infectés
- Connexion à partir d’adresses IP avec une activité suspecte
- Connexion à partir d’emplacements inconnus

## <a name="before-you-begin"></a>Avant de commencer

Les conditions suivantes doivent être remplies pour que les utilisateurs puissent apparaître dans la liste des utilisateurs à risque :

- Le locataire client doit disposer d’une licence Azure AD Premium pour chaque utilisateur. Pour plus d’informations sur les licences qui prennent en charge Azure AD Identity Protection, consultez [Qu’est-ce qu’Identity Protection ?](/azure/active-directory/identity-protection/overview-identity-protection)

- Le locataire client doit être actif dans Microsoft 365 Lighthouse. Pour déterminer si un locataire est actif, consultez [vue d’ensemble de la page Windows 365 (PC cloud) dans Microsoft 365 Lighthouse](m365-lighthouse-tenant-list-overview.md).

## <a name="review-detected-risks-and-take-action"></a>Examiner les risques détectés et prendre des mesures

Dans Azure AD Identity Protection, les détections de risques incluent toutes les actions suspectes identifiées liées aux comptes d’utilisateur dans Azure AD.

1. Dans le volet de navigation gauche de Lighthouse, sélectionnez **Utilisateurs**.

2. Sélectionnez l’onglet **Utilisateurs risqués** .

3. Passez en revue les utilisateurs de la liste avec un état de risque **à risque**.

4. Sélectionnez **Afficher les détections de risque** pour obtenir des informations détaillées sur les risques détectés pour chaque utilisateur. Pour plus d’informations sur les types de risques et la détection, consultez [Qu’est-ce que le risque ?](/azure/active-directory/identity-protection/concept-identity-protection-risks)

5. Pour chaque utilisateur, évaluez les détections de risques et sélectionnez l’une des actions suivantes, le cas échéant :

    - Réinitialiser le mot de passe : modifiez ou réinitialisez le mot de passe de l’utilisateur.

    - Bloquer la connexion : empêcher quiconque de se connecter en tant qu’utilisateur.

    - Confirmer que l’utilisateur est compromis : définissez l’état de risque sur confirmé compromis.

    - Ignorer le risque de l’utilisateur : définissez l’état de risque sur ignoré.

## <a name="take-action-on-multiple-user-accounts-at-once"></a>Prendre des mesures sur plusieurs comptes d’utilisateurs à la fois

Pour prendre des mesures sur plusieurs utilisateurs affectés à la fois :

1. Sous l’onglet **Utilisateurs à risque** , sélectionnez l’ensemble des utilisateurs sur lesquels vous souhaitez effectuer une action.

2. Choisissez l’une des actions suivantes à effectuer :

    - Réinitialiser le mot de passe

    - Bloquer la connexion

    - Confirmer que l’utilisateur est compromis

    - Ignorer le risque de l’utilisateur

> [!NOTE]
> Si l’organisation que vous gérez dispose d’une licence Azure AD Premium P2, il est recommandé d’activer les stratégies d’accès conditionnel basées sur les risques utilisateur. Pour plus d’informations, consultez [Accès conditionnel : Accès conditionnel basé sur les risques utilisateur](/azure/active-directory/conditional-access/howto-conditional-access-policy-risk-user).

## <a name="related-content"></a>Contenu connexe
[Tutoriel : Utiliser les détections de risque pour les connexions utilisateur pour déclencher l’authentification multifacteur Azure AD ou des modifications de mot de passe](/azure/active-directory/authentication/tutorial-risk-based-sspr-mfa) (article)\
[Qu’est-ce que le risque ?](/azure/active-directory/identity-protection/concept-identity-protection-risks) (article) \
[Corriger les risques et débloquer les utilisateurs](/azure/active-directory/identity-protection/howto-identity-protection-remediate-unblock) (article)
