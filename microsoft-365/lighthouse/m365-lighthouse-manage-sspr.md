---
title: Gérer la réinitialisation de mot de passe en libre-service dans Microsoft 365 Lighthouse
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
description: Pour les fournisseurs de services managés (MSP) utilisant Microsoft 365 Lighthouse, découvrez comment gérer la réinitialisation de mot de passe en libre-service.
ms.openlocfilehash: 59f33f6bd624b98dc51a1311c75d8dc7235f7805
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68728222"
---
# <a name="manage-self-service-password-reset-in-microsoft-365-lighthouse"></a>Gérer la réinitialisation de mot de passe en libre-service dans Microsoft 365 Lighthouse

Microsoft 365 Lighthouse permet aux partenaires de gérer la réinitialisation de mot de passe en libre-service (SSPR) Azure Active Directory (Azure AD). SSPR permet aux utilisateurs de modifier ou de réinitialiser leur mot de passe sans intervention de l’administrateur ou du support technique. Si le compte d’un utilisateur est verrouillé ou qu’il oublie son mot de passe, il peut suivre les invites pour se débloquer et se remettre au travail. Cette fonctionnalité réduit les appels au support technique et la perte de productivité lorsqu’un utilisateur ne peut pas se connecter à son appareil ou à une application.

## <a name="before-you-begin"></a>Avant de commencer

Les conditions suivantes doivent être remplies pour qu’un locataire apparaisse dans la liste :

- Le locataire client doit disposer d’une licence Azure AD Premium pour chaque utilisateur. Pour plus d’informations sur les licences qui prennent en charge SSPR, consultez [Conditions de licence pour la réinitialisation de mot de passe en libre-service Azure Active Directory](/azure/active-directory/authentication/concept-sspr-licensing).

- Le locataire du client doit être actif dans Lighthouse. Pour savoir comment déterminer si un locataire est actif, consultez [Vue d’ensemble de la page Windows 365 (PC cloud) dans Microsoft 365 Lighthouse](m365-lighthouse-tenants-page-overview.md).

## <a name="view-sspr-tenant-status"></a>Afficher l’état du locataire SSPR

- Dans le volet de navigation gauche de Lighthouse, sélectionnez **Réinitialisation du mot de passe** **des utilisateurs** > .

La page Réinitialisation du mot de passe fournit une vue d’ensemble des locataires qui ont activé SSPR via les paramètres recommandés, le nombre d’utilisateurs qui ne se sont pas inscrits à SSPR et une répartition détaillée par locataire de la progression du déploiement SSPR dans les organisations que vous gérez.

## <a name="enable-sspr-for-a-tenant"></a>Activer SSPR pour un locataire

1. Dans le volet de navigation gauche de Lighthouse, sélectionnez **Réinitialisation du mot de passe** **des utilisateurs** > .

2. Dans la page **Réinitialisation du mot de passe** , sélectionnez un locataire dans la liste pour ouvrir le volet d’informations.

3. Sélectionnez **Modifier les paramètres SSPR dans Azure Active Directory** pour accéder à Azure Active Directory (Azure AD).

4. Dans Azure AD, activez SSPR pour tous les utilisateurs ou sélectionnés. Pour plus d’informations, consultez [Tutoriel : Permettre aux utilisateurs de déverrouiller leur compte ou de réinitialiser leur mot de passe à l’aide de la réinitialisation de mot de passe en libre-service Azure Active Directory](/azure/active-directory/authentication/tutorial-enable-sspr).

## <a name="notify-users-to-register-for-sspr"></a>Avertir les utilisateurs de s’inscrire à SSPR

1. Dans le volet de navigation gauche de Lighthouse, sélectionnez **Réinitialisation du mot de passe** **des utilisateurs** > .

2. Dans la page **Réinitialisation du mot de passe** , sélectionnez un locataire dans la liste pour ouvrir le volet d’informations.

3. Sélectionnez les utilisateurs que vous souhaitez notifier.

4. Sélectionnez **Créer un e-mail**.

Lighthouse ouvre votre client de messagerie par défaut et préremplifie le message électronique avec des instructions pour s’inscrire à la réinitialisation de données SSPR. Tous les utilisateurs sélectionnés seront inclus sur la ligne cci. Si vous préférez envoyer un e-mail individuel aux utilisateurs, vous pouvez sélectionner l’icône d’e-mail en regard du nom d’utilisateur.

Si vous souhaitez utiliser un autre compte de messagerie, vous pouvez exporter la liste des utilisateurs vers un fichier. Vous pouvez également télécharger des exemples de modèles d’e-mail que vous pouvez personnaliser avec la personnalisation de votre entreprise.

## <a name="related-content"></a>Contenu associé

[Planifier un déploiement de réinitialisation de mot de passe en libre-service Azure Active Directory](/azure/active-directory/authentication/howto-sspr-deployment) (article)\
[Tutoriel : Permettre aux utilisateurs de déverrouiller leur compte ou de réinitialiser leur mot de passe à l’aide de la réinitialisation de mot de passe en libre-service Azure Active Directory](/azure/active-directory/authentication/tutorial-enable-sspr) (article)\
[Comment activer et configurer SSPR dans Azure AD](https://www.youtube.com/watch?v=rA8TvhNcCvQ) (vidéo)\
[Gérer l’authentification multifacteur dans Microsoft 365 Lighthouse](m365-lighthouse-manage-mfa.md) (article)
