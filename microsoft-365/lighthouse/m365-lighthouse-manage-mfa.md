---
title: Gérer l’authentification multifacteur
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
description: Pour les fournisseurs de services gérés (MSP) utilisant Microsoft 365 Lighthouse, découvrez comment gérer l’authentification multifacteur.
ms.openlocfilehash: 5ab430e464fb2d20f9a911818f9fd6cb077d849e
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63326130"
---
# <a name="manage-multifactor-authentication"></a>Gérer l’authentification multifacteur

Azure Active Directory (Azure AD) Multi-Factor Authentication (MFA) permet de protéger l’accès aux données et aux applications, en fournissant une autre couche de sécurité à l’aide d’une deuxième forme d’authentification. L’onglet Authentification multifacteur fournit des informations détaillées sur l’état de l’authentification multifacteur pour tous vos locataires. Sélectionnez n’importe quel client dans la liste pour voir plus de détails sur ce client, notamment les stratégies d’accès conditionnel qui requièrent l’ation MFA qui sont déjà configurées et les utilisateurs qui n’ont pas encore été inscrits à l’mf.

Pour les petites et moyennes entreprises (SMB), Microsoft recommande d’activer au minimum les [paramètres](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults) de sécurité par défaut. Pour des scénarios plus complexes, vous [pouvez utiliser](/azure/active-directory/conditional-access/overview) l’accès conditionnel pour configurer des stratégies spécifiques.

## <a name="before-you-begin"></a>Avant de commencer

Les conditions suivantes doivent être remplies pour qu’un client apparaisse dans la liste :

- Le client doit avoir une licence Azure AD Premium client pour chaque utilisateur. Pour plus d’informations sur les licences qui la prise en charge de l’authentification multifacteur, voir [Fonctionnalités et licences pour Azure AD multifacteur](/azure/active-directory/authentication/concept-mfa-licensing).

- Le client doit être actif dans Microsoft 365 Lighthouse. Pour savoir comment déterminer si un client est actif, voir Microsoft 365 Lighthouse [liste des locataires](/microsoft-365/lighthouse/m365-lighthouse-tenant-list-overview).

## <a name="enable-mfa-for-a-tenant"></a>Activer l’mf pour un client

1. Dans le volet de navigation gauche de l’écran, sélectionnez **Utilisateurs**.

2. Sélectionnez **l’onglet Authentification multifacteur** .

3. Dans la liste des locataires, sélectionnez un client pour ouvrir le volet d’informations.

4. Sous **l’onglet d’enablement mFA** , sous **MFA avec paramètres de** sécurité par défaut, sélectionnez **Activer les paramètres de sécurité par défaut**.

5. Sélectionnez **Enregistrer les modifications**.

Pour activer l’authentification multifacteur via l’accès conditionnel, voir Didacticiel : Sécuriser les événements de Azure AD utilisateur avec [l’authentification multifacteur](/azure/active-directory/authentication/tutorial-enable-azure-mfa).

## <a name="notify-users-who-arent-registered-for-mfa"></a>Avertir les utilisateurs qui ne sont pas inscrits à l’mf

1. Dans le volet de navigation gauche de l’écran, sélectionnez **Utilisateurs**.

2. Sélectionnez **l’onglet Authentification multifacteur** .

3. Dans la liste des locataires, sélectionnez un client pour ouvrir le volet d’informations.

4. Sous **l’onglet Utilisateur non inscrit à l’fa MFA** , sélectionnez les utilisateurs que vous souhaitez notifier.

5. Sélectionnez **Créer un e-mail**.

Ce dernier ouvre votre client de messagerie par défaut et pré-insé dans le message électronique avec des instructions pour s’inscrire à l’uc-MFA. Tous les utilisateurs sélectionnés seront inclus sur la ligne  BcC. Si vous préférez envoyer un e-mail à des utilisateurs individuels, vous pouvez sélectionner l’icône de courrier en côté du nom d’utilisateur.

Si vous souhaitez utiliser un autre compte de messagerie, vous pouvez exporter la liste des utilisateurs vers un fichier. Vous pouvez également télécharger des exemples de modèles de courrier électronique que vous pouvez personnaliser avec la personnalisation de votre entreprise.

## <a name="next-steps"></a>Étapes suivantes

Une fois l’ation MFA activée, vous pouvez activer la réinitialisation Azure Active Directory mot de passe en libre-service (Azure AD) en libre-service. Cette fonctionnalité permet aux utilisateurs de modifier ou de réinitialiser leur mot de passe sans intervention de l’administrateur ou du service d’aide. Pour plus d’informations, voir [Gérer la réinitialisation du mot de passe en libre-service](m365-lighthouse-manage-sspr.md).

## <a name="related-content"></a>Contenu associé

[Planifier un déploiement Azure Active Directory Multi-Factor Authentication](/azure/active-directory/authentication/howto-mfa-getstarted) (article)\
[Que sont les paramètres de sécurité par défaut ?](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults) (article)\
[Qu’est-ce que l’accès conditionnel ?](/azure/active-directory/conditional-access/overview) (article)\
[Découvrez comment convertir des utilisateurs de l’fa MFA par utilisateur en accès conditionnel](/azure/active-directory/authentication/howto-mfa-getstarted#convert-users-from-per-user-mfa-to-conditional-access-based-mfa) (article)
