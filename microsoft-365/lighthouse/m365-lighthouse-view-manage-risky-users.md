---
title: Afficher et gérer les utilisateurs à risque dans Microsoft 365 Lighthouse
f1.keywords: NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
ms.reviewer: ragovind
audience: Admin
ms.topic: article
ms.service: microsoft-365-lighthouse
ms.localizationpriority: medium
ms.collection:
- Tier1
- scotvorg
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- M365-Lighthouse
search.appverid: MET150
description: Pour les fournisseurs de services managés (MSP) utilisant Microsoft 365 Lighthouse, découvrez comment afficher et gérer les utilisateurs à risque.
ms.openlocfilehash: 7588e8409345cc871249af391b3cd3f5914bc981
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68726043"
---
# <a name="view-and-manage-risky-users-in-microsoft-365-lighthouse"></a>Afficher et gérer les utilisateurs à risque dans Microsoft 365 Lighthouse

Microsoft collecte et analyse des billions de signaux de connexion utilisateur chaque jour. Ces signaux sont utilisés pour créer de bons modèles de comportement de connexion utilisateur et identifier les tentatives de connexion à risque potentielles. Azure Active Directory (Azure AD) Identity Protection utilise ces signaux pour passer en revue les tentatives de connexion des utilisateurs et prendre des mesures en cas d’activité suspecte.

Microsoft 365 Lighthouse permet de gérer les risques détectés par Azure AD Identity Protection en fournissant une vue unique des utilisateurs à risque sur tous vos locataires gérés. Vous pouvez rapidement sécuriser les utilisateurs à risque en réinitialisant leur mot de passe ou en les empêchant de se connecter à leur compte Microsoft 365. Vous pouvez également afficher des insights pour mieux comprendre le risque d’un utilisateur et déterminer les étapes suivantes.

Azure AD Identity Protection identifie les risques de nombreux types, notamment :

- Fuites d’informations d’identification
- Utilisation de l’adresse IP anonyme
- Voyage atypique
- Connexion à partir d’appareils infectés
- Connexion à partir d’adresses IP avec une activité suspecte
- Connexion à partir d’emplacements inconnus

## <a name="before-you-begin"></a>Avant de commencer

Les conditions suivantes doivent être remplies pour que les utilisateurs puissent apparaître dans la liste des utilisateurs à risque :

- Le locataire client doit disposer d’une licence Azure AD Premium pour chaque utilisateur. Pour plus d’informations sur les licences qui prennent en charge Azure AD Identity Protection, consultez [Qu’est-ce qu’Identity Protection ?](/azure/active-directory/identity-protection/overview-identity-protection)

- Le locataire client doit être actif dans Microsoft 365 Lighthouse. Pour déterminer si un locataire est actif, consultez [Vue d’ensemble de la page Windows 365 (PC cloud) dans Microsoft 365 Lighthouse](m365-lighthouse-tenant-list-overview.md).

## <a name="review-detected-risks-and-take-action"></a>Passer en revue les risques détectés et prendre des mesures

Dans Azure AD Identity Protection, les détections de risques incluent toutes les actions suspectes identifiées liées aux comptes d’utilisateur dans Azure AD.

1. Dans le volet de navigation gauche de Lighthouse, sélectionnez **Utilisateurs Utilisateurs** > **à risque**.

2. Dans la page **Utilisateurs à risque** , passez en revue les utilisateurs de la liste dont l’état de risque est **At risk**.

3. Sélectionnez **Afficher les détections de risques** pour obtenir des informations détaillées sur les risques détectés pour chaque utilisateur. Pour plus d’informations sur les types de risques et la détection, consultez [Qu’est-ce que le risque ?](/azure/active-directory/identity-protection/concept-identity-protection-risks).

4. Pour chaque utilisateur, évaluez les détections de risques et sélectionnez l’une des actions suivantes, le cas échéant :

    - Réinitialiser le mot de passe : modifiez ou réinitialisez le mot de passe de l’utilisateur.

    - Bloquer la connexion : empêcher quiconque de se connecter en tant qu’utilisateur.

    - Confirmer la compromission de l’utilisateur : définissez l’état de risque sur Confirmé compromis.

    - Ignorer le risque de l’utilisateur : définissez l’état de risque sur Ignoré.

## <a name="take-action-on-multiple-user-accounts-at-once"></a>Effectuer des actions sur plusieurs comptes d’utilisateur à la fois

Pour prendre des mesures sur plusieurs utilisateurs affectés à la fois :

1. Dans le volet de navigation gauche de Lighthouse, sélectionnez **Utilisateurs Utilisateurs** > **à risque**.

2. Dans la page **Utilisateurs à risque** , sélectionnez l’ensemble d’utilisateurs sur lesquels vous souhaitez effectuer une action.

3. Choisissez l’une des actions suivantes à effectuer :

    - Réinitialiser le mot de passe

    - Bloquer la connexion

    - Confirmer que l’utilisateur est compromis

    - Ignorer le risque de l’utilisateur

> [!NOTE]
> Si l’organisation que vous gérez dispose d’une licence Azure AD Premium P2, il est recommandé d’activer les stratégies d’accès conditionnel basées sur les risques de l’utilisateur. Pour plus d’informations, consultez [Accès conditionnel : Accès conditionnel basé sur les risques de l’utilisateur](/azure/active-directory/conditional-access/howto-conditional-access-policy-risk-user).

## <a name="related-content"></a>Contenu associé
[Tutoriel : Utiliser des détections de risques pour les connexions utilisateur afin de déclencher des modifications de mot de passe ou d’authentification multifacteur Azure AD](/azure/active-directory/authentication/tutorial-risk-based-sspr-mfa) (article)\
[Qu’est-ce que le risque ?](/azure/active-directory/identity-protection/concept-identity-protection-risks) (article) \
[Corriger les risques et débloquer les utilisateurs](/azure/active-directory/identity-protection/howto-identity-protection-remediate-unblock) (article)