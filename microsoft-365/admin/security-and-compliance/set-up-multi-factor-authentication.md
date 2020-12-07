---
title: Configurer l'authentification multifacteur pour les utilisateurs
f1.keywords:
- NOCSH
ms.author: sirkkuw
author: sirkkuw
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Priority
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
- BEA160
- GEA150
ms.assetid: 8f0454b2-f51a-4d9c-bcde-2c48e41621c6
description: Découvrez comment configurer l’authentification multifacteur pour votre organisation.
monikerRange: o365-worldwide
ms.openlocfilehash: db858cbd4242a096261942fd12b911ecff43f71f
ms.sourcegitcommit: c1dd5be42fe0c5dcc7c05817c941edd9076febf8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2020
ms.locfileid: "49558209"
---
# <a name="set-up-multi-factor-authentication"></a>Configurer Multi-factor Authentification (MFA)

En fonction de votre compréhension de [l’authentification multifacteur (MFA) et de sa prise en charge dans Microsoft 365](multi-factor-authentication-microsoft-365.md), le moment est venu de la configurer et de la déployer dans votre organisation.

> [!IMPORTANT]
> Si vous avez acheté votre abonnement ou une version d’évaluation après le 21 octobre 2019 et que vous êtes, de manière, invité à fournir une authentification multifacteur lors de la connexion, [les valeurs de sécurité par défaut](https://docs.microsoft.com/azure/active-directory/fundamentals/concept-fundamentals-security-defaults) ont été automatiquement activées pour votre abonnement.

## <a name="before-you-begin"></a>Avant de commencer

- Vous devez être un administrateur général pour gérer l’authentification multifacteur. Pour plus d’informations, consultez [À propos des rôles d’administrateur](../add-users/about-admin-roles.md).
- Si l’authentification multifacteur par utilisateur héritée est activée, [Désactivez l'authentification multifacteur par utilisateur héritée](#turn-off-legacy-per-user-mfa).
- Si vous avez des clients Office 2013 sur des appareils Windows, [activer l’authentification moderne pour les clients Office 2013](https://docs.microsoft.com/microsoft-365/admin/security-and-compliance/enable-modern-authentication).
- Avancé : si vous avez des services d’annuaire tiers avec les services de fédération Active Directory (AD FS), configurez le serveur Microsoft Azure Multi-Factor Authentication. Pour plus d’informations, consultez les [scénarios avancés avec l’Authentification multifacteur Azure AD et les solutions VPN tierces](https://docs.microsoft.com/azure/active-directory/authentication/howto-mfaserver-nps-vpn).

## <a name="turn-security-defaults-on-or-off"></a>Activer ou désactiver les paramètres de sécurité par défaut

Pour la plupart des organisations, les valeurs de sécurité par défaut offrent un niveau de sécurité de connexion supplémentaire. Pour plus d’informations, voir [Présentation des paramètres de sécurité par défaut](https://docs.microsoft.com/azure/active-directory/fundamentals/concept-fundamentals-security-defaults)

Si votre abonnement est nouveau, les paramètres par défaut de sécurité peuvent déjà être activés automatiquement.

Pour activer ou désactiver les paramètres de sécurité par défaut, accédez au volet **Propriétés** pour Azure Active Directory (Azure AD) dans le Portail Azure.

1. Connectez-vous au [Centre d'administration Microsoft 365](https://admin.microsoft.com) avec des informations d'identification d'administrateur général.
2. Dans le volet de navigation gauche, sélectionnez **Afficher tout** puis sous **Centres d’administration**, sélectionnez **Azure Active Directory**.
3. Dans le **centre d’administration Azure Active Directory** sélectionnez **Azure Active Directory** \> **Propriétés**.
4. Au bas de la page, sélectionnez **Gérer les paramètres de sécurité par défaut**.
5. Sélectionnez **Oui** pour activer les paramètres de sécurité par défaut ou **Non** pour désactiver les paramètres de sécurité par défaut, puis choisissez **Enregistrer**.

Si vous utilisez [stratégies d’accès conditionnel de référence](https://docs.microsoft.com/azure/active-directory/conditional-access/concept-baseline-protection), vous serez invité à les désactiver avant de passer à l’utilisation des paramètres de sécurité par défaut.

1. Accédez à la [page des stratégies d’accès conditionnel](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConditionalAccessBlade/Policies).
2. Sélectionnez chaque stratégie de référence sur **Activé** et définissez **Activer la stratégie** sur **Désactivé**.
3. Accédez à la [page des propriétés d'Azure Active Directory](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Properties).
4. Au bas de la page, sélectionnez **Gérer les paramètres de sécurité par défaut**.
5. Sélectionnez **Oui** pour activer les paramètres de sécurité par défaut et **Non** pour désactiver les paramètres de sécurité par défaut, puis choisissez **Enregistrer**.

## <a name="use-conditional-access-policies"></a>Utiliser les stratégies d’accès conditionnel

Si votre organisation a des besoins de sécurité de connexion plus granulaires, les stratégies d’accès conditionnel peuvent vous offrir davantage de contrôle. L’accès conditionnel vous permet de créer et de définir des stratégies qui réagissent aux événements de connexion et de demander des actions supplémentaires avant qu’un utilisateur ne soit autorisé à accéder à une application ou un service.

> [!IMPORTANT]
> Désactivez les paramètres par défaut d'authentification multifacteur et de Sécurité par personne avant d'activer les stratégies d'Accès Conditionnel.

L’accès conditionnel est disponible pour les clients qui ont acheté Azure AD Premium P1 ou les licences qui incluent cette offre, telles que Microsoft 365 Business Premium et Microsoft 365 E3. Pour en savoir plus, consultez [Créer une stratégie d’accès conditionnel](https://docs.microsoft.com/azure/active-directory/authentication/tutorial-enable-azure-mfa).

L’accès conditionnel basé sur les risques est disponible via une licence Azure AD Premium P2, ou les licences qui l’incluent, telles que Microsoft 365 E5. Pour en savoir plus, consultez l'article [Accès conditionnel basé sur les risques](https://docs.microsoft.com/azure/active-directory/conditional-access/howto-conditional-access-policy-risk).

Pour plus d’informations sur Azure AD P1 et P2, voir [Tarification Azure Active Directory](https://azure.microsoft.com/pricing/details/active-directory/).

### <a name="turn-on-modern-authentication-for-your-organization"></a>Activer Authentification moderne pour votre organisation

Pour la plupart des abonnements, l'authentification moderne est automatiquement activée, mais si vous avez acheté votre abonnement il y a longtemps, il se peut qu'elle ne le soit pas. Celle-ci doit être activée avant que l’authentification multifacteur fonctionne convenablement avec les applications Office.

1. Dans le Centre d’administration Microsoft 365, dans le volet de navigation gauche, sélectionnez **Paramètres** \> **Paramètres d’organisation**.
1. Sous l’onglet **Services**, sélectionnez **Authentification moderne**, puis, dans le volet **Authentification moderne**, assurez-vous que l’option **Activer l’authentification moderne** est sélectionnée. Sélectionnez **Save Changes (Enregistrer les modifications)**.

### <a name="turn-off-legacy-per-user-mfa"></a>Désactiver l’authentification multifacteur par utilisateur héritée

Si vous avez déjà activé l’authentification multifacteur (MFA) par utilisateur, vous devez désactiver cette fonctionnalité avant d’activer les paramètres de Sécurité par défaut.

1. Dans le Centre d’administration Microsoft 365, dans le volet de navigation gauche, sélectionnez **Utilisateurs** \> **Utilisateurs actifs**.
1. Sur la page **Utilisateurs actifs**, sélectionnez **Authentification multifacteur**.
1. Sur la page d'authentification multifacteur, sélectionnez chaque utilisateur et définissez son état d'authentification multifacteur sur **Désactivé**.

## <a name="next-steps"></a>Étapes suivantes

- [Comment s’inscrire à leur méthode de vérification supplémentaire](https://support.microsoft.com/office/ace1d096-61e5-449b-a875-58eb3d74de14)
- [Qu’est-ce que l’authentification multifacteur](https://support.microsoft.com/help/4577374/what-is-multifactor-authentication) ?
- [Comment se connecter après l’inscription](https://support.microsoft.com/office/2b856342-170a-438e-9a4f-3c092394d3cb)
- [Comment modifier leur méthode de vérification supplémentaire](https://support.microsoft.com/office/956ec8d0-7081-4518-a701-f8414cc20831)
