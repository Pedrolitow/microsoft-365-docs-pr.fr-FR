---
title: Gérer l’authentification multifacteur dans Microsoft 365 Lighthouse
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
description: Pour les fournisseurs de services gérés (MSP) qui utilisent Microsoft 365 Lighthouse, découvrez comment gérer l’authentification multifacteur.
ms.openlocfilehash: aa9d25ce633088d840a38e1927c4ebf3baef56b3
ms.sourcegitcommit: 23a53b5c5e372a2a7ad5e175850224d3d464f6dd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2022
ms.locfileid: "67056458"
---
# <a name="manage-multifactor-authentication-in-microsoft-365-lighthouse"></a>Gérer l’authentification multifacteur dans Microsoft 365 Lighthouse

Azure Active Directory (Azure AD) Multi-Factor Authentication (MFA) permet de protéger l’accès aux données et aux applications, fournissant une autre couche de sécurité à l’aide d’une deuxième forme d’authentification. L’onglet Authentification multifacteur fournit des informations détaillées sur l’état de l’activation de l’authentification multifacteur sur vos locataires. Sélectionnez un locataire dans la liste pour afficher plus de détails pour ce locataire, notamment les stratégies d’accès conditionnel nécessitant l’authentification multifacteur qui sont déjà configurées et les utilisateurs qui ne se sont pas encore inscrits à l’authentification multifacteur.

Pour les clients de petite et moyenne entreprise (SMB), Microsoft recommande d’activer au minimum [les paramètres de sécurité par défaut](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults) . Pour les scénarios plus complexes, vous pouvez utiliser [l’accès conditionnel](/azure/active-directory/conditional-access/overview) pour configurer des stratégies spécifiques.

## <a name="before-you-begin"></a>Avant de commencer

Les conditions suivantes doivent être remplies pour qu’un locataire apparaisse dans la liste :

- Le locataire client doit disposer d’une licence Azure AD Premium pour chaque utilisateur. Pour plus d’informations sur les licences qui prennent en charge l’authentification multifacteur, consultez [Fonctionnalités et licences pour Azure AD Multi-Factor Authentication](/azure/active-directory/authentication/concept-mfa-licensing).

- Le locataire client doit être actif dans Microsoft 365 Lighthouse. Pour savoir comment déterminer si un locataire est actif, consultez [Microsoft 365 Lighthouse vue d’ensemble de la liste de locataires](/microsoft-365/lighthouse/m365-lighthouse-tenant-list-overview).

## <a name="enable-mfa-for-a-tenant"></a>Activer l’authentification multifacteur pour un locataire

1. Dans le volet de navigation gauche de Lighthouse, sélectionnez **Authentification multifacteur** **Utilisateurs** > .

2. Sous l’onglet **Authentification multifacteur** , recherchez un locataire qui n’utilise pas l’authentification multifacteur, puis sélectionnez ce locataire pour ouvrir le volet des détails du locataire.

3. Sous l’onglet **Activation de l’authentification multifacteur** , sous **MFA avec paramètres de sécurité par défaut**, **sélectionnez Activer la sécurité par défaut**.

4. Sélectionnez **Enregistrer les modifications**.

Pour activer l’authentification multifacteur via l’accès conditionnel, consultez [Tutoriel : Sécuriser les événements de connexion utilisateur avec Azure AD Multi-Factor Authentication](/azure/active-directory/authentication/tutorial-enable-azure-mfa).

## <a name="notify-users-who-arent-registered-for-mfa"></a>Avertir les utilisateurs qui ne sont pas inscrits à l’authentification multifacteur

1. Dans le volet de navigation gauche de Lighthouse, sélectionnez **Authentification multifacteur** **Utilisateurs** > .

2. Sous l’onglet **Authentification multifacteur** , recherchez les locataires dont les utilisateurs ne sont pas inscrits à l’authentification multifacteur, puis sélectionnez le locataire pour ouvrir le volet d’informations du locataire.

3. Sélectionnez **Utilisateurs non inscrits à l’onglet MFA** .

4. Sélectionnez tous les autres utilisateurs de la liste qui doivent s’inscrire à l’authentification multifacteur, puis sélectionnez **Créer un e-mail**.

> [!TIP]
> Si l’un des comptes d’utilisateur de la liste est des comptes d’accès d’urgence ou des comptes de service pour lesquels vous ne souhaitez pas exiger l’authentification multifacteur, sélectionnez ces comptes d’utilisateur, puis **sélectionnez Exclure les utilisateurs**. Les comptes d’utilisateur exclus n’apparaissent plus dans la liste des utilisateurs non inscrits pour l’authentification multifacteur.

> [!NOTE]
> Si des comptes de boîte aux lettres partagés ou des comptes d’utilisateurs inactifs apparaissent dans la liste des utilisateurs non inscrits à l’authentification multifacteur, nous vous recommandons de bloquer la connexion pour ces comptes afin qu’ils n’apparaissent plus dans cette liste.


Lighthouse ouvre votre client de messagerie par défaut et préremplit le message électronique avec des instructions pour s’inscrire à l’authentification multifacteur. Tous les utilisateurs sélectionnés seront inclus sur la ligne CCI. Si vous préférez envoyer des e-mails individuellement aux utilisateurs, vous pouvez sélectionner l’icône d’e-mail en regard du nom d’utilisateur.

Si vous souhaitez utiliser un autre compte de messagerie, vous pouvez exporter la liste des utilisateurs vers un fichier. Vous pouvez également télécharger des exemples de modèles de messagerie que vous pouvez personnaliser avec la personnalisation de votre entreprise.

## <a name="next-steps"></a>Prochaines étapes

Une fois l’authentification multifacteur activée, vous pouvez activer la réinitialisation de mot de passe en libre-service Azure Active Directory (Azure AD). Cette fonctionnalité permet aux utilisateurs de modifier ou de réinitialiser leur mot de passe sans intervention de l’administrateur ou du support technique. Pour plus d’informations, consultez [Gérer la réinitialisation de mot de passe en libre-service dans Microsoft 365 Lighthouse](m365-lighthouse-manage-sspr.md).

## <a name="related-content"></a>Contenu associé

[Planifier un déploiement Azure Active Directory Multi-Factor Authentication](/azure/active-directory/authentication/howto-mfa-getstarted) (article)\
[Quelles sont les valeurs par défaut de sécurité ?](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults) (article)\
[Qu’est-ce que l’accès conditionnel ?](/azure/active-directory/conditional-access/overview) (article)\
[Découvrez comment convertir des utilisateurs de l’authentification multifacteur par utilisateur en accès conditionnel](/azure/active-directory/authentication/howto-mfa-getstarted#convert-users-from-per-user-mfa-to-conditional-access-based-mfa) (article)
