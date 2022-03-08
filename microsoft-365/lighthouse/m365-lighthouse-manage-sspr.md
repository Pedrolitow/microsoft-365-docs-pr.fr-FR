---
title: Gérer la réinitialisation du mot de passe libre-service
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
description: Pour les fournisseurs de services gérés (MSP) utilisant Microsoft 365 Lighthouse, découvrez comment gérer la réinitialisation de mot de passe en libre-service.
ms.openlocfilehash: f9f8ef9a3c81281629c378fb4b55cd4c9a839c1d
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63311562"
---
# <a name="manage-self-service-password-reset"></a>Gérer la réinitialisation du mot de passe libre-service

Microsoft 365 Lighthouse permet aux partenaires de gérer Azure Active Directory réinitialisation du mot de passe en libre-service (Azure AD) en libre-service (SSPR). SSPR permet aux utilisateurs de modifier ou de réinitialiser leur mot de passe sans intervention de l’administrateur ou du service d’aide. Si le compte d’un utilisateur est verrouillé ou s’il oublie son mot de passe, il peut suivre des invites pour se débloquer et revenir au travail. Cette possibilité réduit les appels du service d’aide et la perte de productivité lorsqu’un utilisateur ne peut pas se connecter à son appareil ou à une application.

## <a name="before-you-begin"></a>Avant de commencer

Les conditions suivantes doivent être remplies pour qu’un client apparaisse dans la liste :

- Le client doit avoir une licence Azure AD Premium client pour chaque utilisateur. Pour plus d’informations sur les licences qui la prise en charge de SSPR, consultez la Azure Active Directory de licences pour la [réinitialisation du mot de passe libre-service](/azure/active-directory/authentication/concept-sspr-licensing).

- Le client doit être actif au sein de l’équipe de gestion. Pour savoir comment déterminer si un client est actif, voir Microsoft 365 Lighthouse [page Tenants.](m365-lighthouse-tenants-page-overview.md)

## <a name="view-sspr-tenant-status"></a>Afficher l’état du client SSPR

1. Dans le volet de navigation de gauche de l’écran, sélectionnez **Utilisateurs**.

2. Sélectionnez **l’onglet Réinitialisation du mot** de passe.

L’onglet Réinitialisation du mot de passe fournit une vue d’ensemble des clients qui ont activé SSPR via les paramètres recommandés, le nombre d’utilisateurs qui ne se sont pas inscrits à SSPR et une répartition détaillée par locataire de l’avancement du déploiement SSPR au sein des organisations que vous gérez.

## <a name="enable-sspr-for-a-tenant"></a>Activer SSPR pour un client

1. Dans le volet de navigation gauche de l’écran, sélectionnez **Utilisateurs**.

2. Sélectionnez **l’onglet Réinitialisation du mot** de passe.

3. Dans la liste des locataires, sélectionnez un client pour ouvrir le volet d’informations.

4. **Sélectionnez Modifier les paramètres SSPR dans Azure Active Directory** pour Azure Active Directory (Azure AD).

5. Dans Azure AD, activez SSPR pour tous les utilisateurs ou les utilisateurs sélectionnés. Pour en savoir plus, consultez le didacticiel : permettre aux [utilisateurs de déverrouiller](/azure/active-directory/authentication/tutorial-enable-sspr) leur compte ou de réinitialiser leurs mots de passe à l’aide Azure Active Directory réinitialisation du mot de passe libre-service.

## <a name="notify-users-to-register-for-sspr"></a>Avertir les utilisateurs de s’inscrire à SSPR

1. Dans le volet de navigation gauche de l’écran, sélectionnez **Utilisateurs**.

2. Sélectionnez **l’onglet Réinitialisation du mot** de passe.

3. Dans la liste des locataires, sélectionnez un client pour ouvrir le volet d’informations.

4. Sélectionnez les utilisateurs que vous souhaitez notifier.

5. Sélectionnez **Créer un e-mail**.

Ce dernier ouvre votre client de messagerie par défaut et pré-insé dans le message électronique avec des instructions pour s’inscrire à SSPR. Tous les utilisateurs sélectionnés seront inclus sur la ligne  BcC. Si vous préférez envoyer un e-mail à des utilisateurs individuels, vous pouvez sélectionner l’icône de courrier en côté du nom d’utilisateur.

Si vous souhaitez utiliser un autre compte de messagerie, vous pouvez exporter la liste des utilisateurs vers un fichier. Vous pouvez également télécharger des exemples de modèles de courrier électronique que vous pouvez personnaliser avec la personnalisation de votre entreprise.

## <a name="related-content"></a>Contenu associé

[Planifier un déploiement Azure Active Directory réinitialisation de mot de passe en libre-service](/azure/active-directory/authentication/howto-sspr-deployment) (article)\
[Didacticiel : Permettre aux utilisateurs de déverrouiller](/azure/active-directory/authentication/tutorial-enable-sspr) leur compte ou de réinitialiser leurs mots de passe à l’Azure Active Directory réinitialisation du mot de passe libre-service (article)\
[Comment activer et configurer SSPR dans Azure AD](https://www.youtube.com/watch?v=rA8TvhNcCvQ) (vidéo)\
[Gérer l’authentification multifacteur](m365-lighthouse-manage-mfa.md) (article)
