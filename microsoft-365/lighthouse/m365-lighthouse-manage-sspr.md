---
title: Gérer la réinitialisation de mot de passe en libre-service dans Microsoft 365 Lighthouse
f1.keywords: NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
ms-reviewer: ragovind
audience: Admin
ms.topic: article
ms.service: microsoft-365-lighthouse
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- M365-Lighthouse
search.appverid: MET150
description: Pour les fournisseurs de services gérés (MSP) qui utilisent Microsoft 365 Lighthouse, découvrez comment gérer la réinitialisation de mot de passe en libre-service.
ms.openlocfilehash: bcfbd9ad05a433fb9b98125fe6447d9086096a1a
ms.sourcegitcommit: 2b89bcff547e00be3d38dc8d1e6cbcf8f41eba42
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2022
ms.locfileid: "67599107"
---
# <a name="manage-self-service-password-reset-in-microsoft-365-lighthouse"></a>Gérer la réinitialisation de mot de passe en libre-service dans Microsoft 365 Lighthouse

Microsoft 365 Lighthouse permet aux partenaires de gérer la réinitialisation de mot de passe en libre-service (SSPR) Azure Active Directory (Azure AD). SSPR permet aux utilisateurs de modifier ou de réinitialiser leur mot de passe sans intervention de l’administrateur ou du support technique. Si le compte d’un utilisateur est verrouillé ou qu’il oublie son mot de passe, il peut suivre les invites pour se débloquer et reprendre le travail. Cette capacité réduit les appels au support technique et la perte de productivité lorsqu’un utilisateur ne peut pas se connecter à son appareil ou à une application.

## <a name="before-you-begin"></a>Avant de commencer

Les conditions suivantes doivent être remplies pour qu’un locataire apparaisse dans la liste :

- Le locataire client doit disposer d’une licence Azure AD Premium pour chaque utilisateur. Pour plus d’informations sur les licences qui prennent en charge la [réinitialisation de mot de passe en libre-service Azure Active Directory, consultez les exigences de licence](/azure/active-directory/authentication/concept-sspr-licensing).

- Le locataire client doit être actif dans Lighthouse. Pour savoir comment déterminer si un locataire est actif, consultez [vue d’ensemble de la page Windows 365 (PC cloud) dans Microsoft 365 Lighthouse](m365-lighthouse-tenants-page-overview.md).

## <a name="view-sspr-tenant-status"></a>Afficher l’état du locataire SSPR

- Dans le volet de navigation gauche de Lighthouse, sélectionnez **Réinitialisation du mot de passe** **utilisateur** > .

La page de réinitialisation de mot de passe fournit une vue d’ensemble des locataires qui ont activé la réinitialisation de mot de passe par le biais des paramètres recommandés, du nombre d’utilisateurs qui ne se sont pas inscrits à SSPR et d’une répartition détaillée par locataire de la progression du déploiement SSPR au sein des organisations que vous gérez.

## <a name="enable-sspr-for-a-tenant"></a>Activer SSPR pour un locataire

1. Dans le volet de navigation gauche de Lighthouse, sélectionnez **Réinitialisation du mot de passe** **utilisateur** > .

2. Dans la page **réinitialisation du mot de passe** , sélectionnez un locataire dans la liste pour ouvrir le volet d’informations.

3. Sélectionnez **Modifier les paramètres SSPR dans Azure Active Directory** pour accéder à Azure Active Directory (Azure AD).

4. Dans Azure AD, activez SSPR pour tous les utilisateurs ou les utilisateurs sélectionnés. Pour en savoir plus, consultez [tutoriel : Permettre aux utilisateurs de déverrouiller leur compte ou de réinitialiser des mots de passe à l’aide de la réinitialisation de mot de passe en libre-service Azure Active Directory](/azure/active-directory/authentication/tutorial-enable-sspr).

## <a name="notify-users-to-register-for-sspr"></a>Avertir les utilisateurs de s’inscrire à SSPR

1. Dans le volet de navigation gauche de Lighthouse, sélectionnez **Réinitialisation du mot de passe** **utilisateur** > .

2. Dans la page **réinitialisation du mot de passe** , sélectionnez un locataire dans la liste pour ouvrir le volet d’informations.

3. Sélectionnez les utilisateurs que vous souhaitez notifier.

4. Sélectionnez **Créer un e-mail**.

Lighthouse ouvre votre client de messagerie par défaut et préremplit l’e-mail avec des instructions pour s’inscrire à SSPR. Tous les utilisateurs sélectionnés seront inclus sur la ligne CCI. Si vous préférez envoyer des e-mails individuellement aux utilisateurs, vous pouvez sélectionner l’icône d’e-mail en regard du nom d’utilisateur.

Si vous souhaitez utiliser un autre compte de messagerie, vous pouvez exporter la liste des utilisateurs vers un fichier. Vous pouvez également télécharger des exemples de modèles de messagerie que vous pouvez personnaliser avec la personnalisation de votre entreprise.

## <a name="related-content"></a>Contenu associé

[Planifier un déploiement de réinitialisation de mot de passe en libre-service Azure Active Directory](/azure/active-directory/authentication/howto-sspr-deployment) (article)\
[Tutoriel : Permettre aux utilisateurs de déverrouiller leur compte ou de réinitialiser des mots de passe à l’aide de la réinitialisation de mot de passe en libre-service Azure Active Directory](/azure/active-directory/authentication/tutorial-enable-sspr) (article)\
[Comment activer et configurer SSPR dans Azure AD](https://www.youtube.com/watch?v=rA8TvhNcCvQ) (vidéo)\
[Gérer l’authentification multifacteur dans Microsoft 365 Lighthouse](m365-lighthouse-manage-mfa.md) (article)
