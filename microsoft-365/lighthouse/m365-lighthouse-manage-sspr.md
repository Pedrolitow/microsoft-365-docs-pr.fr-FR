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
ms.openlocfilehash: b8367d2ed2c088d56425b08c6da5dfd55fcd84b8
ms.sourcegitcommit: 2ea2105d40b60a87fc9aa30f392a73a3a9db6d99
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2021
ms.locfileid: "61128603"
---
# <a name="manage-self-service-password-reset"></a>Gérer la réinitialisation du mot de passe libre-service

> [!NOTE]
> Les fonctionnalités décrites dans cet article sont en prévisualisation, peuvent faire l’objet de changements et sont uniquement disponibles pour les partenaires qui répondent aux [exigences.](m365-lighthouse-requirements.md) Si votre organisation n’a pas Microsoft 365 Lighthouse, [consultez s’inscrire pour Microsoft 365 Lighthouse](m365-lighthouse-sign-up.md).

Microsoft 365 Lighthouse permet aux partenaires de gérer la réinitialisation Azure Active Directory mot de passe en libre-service (Azure AD) en libre-service (SSPR). SSPR permet aux utilisateurs de modifier ou de réinitialiser leur mot de passe sans intervention de l’administrateur ou du service d’aide. Si le compte d’un utilisateur est verrouillé ou s’il oublie son mot de passe, il peut suivre des invites pour se débloquer et revenir au travail. Cette possibilité réduit les appels du service d’aide et la perte de productivité lorsqu’un utilisateur ne peut pas se connecter à son appareil ou à une application.

## <a name="before-you-begin"></a>Avant de commencer

Les conditions suivantes doivent être remplies pour qu’un client apparaisse dans la liste :

- Le client doit avoir une licence Azure AD Premium client pour chaque utilisateur. Pour plus d’informations sur les licences qui la prise en charge de SSPR, voir La gestion des licences requise pour Azure Active Directory réinitialisation du mot de passe [en libre-service.](/azure/active-directory/authentication/concept-sspr-licensing)

- Le client doit être actif au sein de l’équipe de gestion. Pour savoir comment déterminer si un client est actif, voir Microsoft 365 Lighthouse [page des locataires.](m365-lighthouse-tenants-page-overview.md)

## <a name="view-sspr-tenant-status"></a>Afficher l’état du client SSPR

1. Dans le volet de navigation de gauche de l’écran de sélection, sélectionnez **Utilisateurs.**

2. Sélectionnez **l’onglet Réinitialisation du mot** de passe.

L’onglet Réinitialisation du mot de passe fournit une vue d’ensemble des clients qui ont activé SSPR via les paramètres recommandés, le nombre d’utilisateurs qui ne se sont pas inscrits à SSPR et une répartition détaillée par locataire de l’avancement du déploiement SSPR au sein des organisations que vous gérez.

## <a name="enable-sspr-for-a-tenant"></a>Activer SSPR pour un client

1. Dans le volet de navigation de gauche de l’écran, sélectionnez **Utilisateurs.**

2. Sélectionnez **l’onglet Réinitialisation du mot** de passe.

3. Dans la liste des locataires, sélectionnez un client pour ouvrir le volet d’informations.

4. Sélectionnez **Modifier les paramètres SSPR dans Azure Active Directory** pour Azure Active Directory (Azure AD).

5. Dans Azure AD, activez SSPR pour tous les utilisateurs ou les utilisateurs sélectionnés. Pour en savoir plus, consultez le didacticiel : permettre aux utilisateurs de déverrouiller leur compte ou de réinitialiser leurs mots de passe à l’aide Azure Active Directory réinitialisation du mot de passe [en libre-service.](/azure/active-directory/authentication/tutorial-enable-sspr)

## <a name="notify-users-to-register-for-sspr"></a>Avertir les utilisateurs de s’inscrire à SSPR

1. Dans le volet de navigation de gauche de l’écran, sélectionnez **Utilisateurs.**

2. Sélectionnez **l’onglet Réinitialisation du mot** de passe.

3. Dans la liste des locataires, sélectionnez un client pour ouvrir le volet d’informations.

4. Sélectionnez les utilisateurs que vous souhaitez notifier.

5. Sélectionnez **Créer un e-mail.**

Ce dernier ouvre votre client de messagerie par défaut et pré-insé dans le message électronique avec des instructions pour s’inscrire à SSPR. Tous les utilisateurs sélectionnés seront inclus sur la ligne BcC. Si vous préférez envoyer un e-mail à des utilisateurs individuels, vous pouvez sélectionner l’icône de courrier en côté du nom d’utilisateur.

Si vous souhaitez utiliser un autre compte de messagerie, vous pouvez exporter la liste des utilisateurs vers un fichier. Vous pouvez également télécharger des exemples de modèles de courrier électronique que vous pouvez personnaliser avec la personnalisation de votre entreprise.

## <a name="related-content"></a>Contenu connexe

[Planifier un déploiement Azure Active Directory réinitialisation](/azure/active-directory/authentication/howto-sspr-deployment) de mot de passe en libre-service (article)\
[Didacticiel : Permettre aux utilisateurs de déverrouiller](/azure/active-directory/authentication/tutorial-enable-sspr) leur compte ou de réinitialiser leurs mots de passe à l’aide Azure Active Directory réinitialisation du mot de passe libre-service (article)\
[Comment activer et configurer SSPR](https://www.youtube.com/watch?v=rA8TvhNcCvQ) dans Azure AD (vidéo)\
[Gérer l’authentification multifacteur](m365-lighthouse-manage-mfa.md) (article)
