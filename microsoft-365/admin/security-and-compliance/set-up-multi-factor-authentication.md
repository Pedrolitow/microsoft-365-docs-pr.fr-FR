---
title: Configurer l'authentification multi-facteurs pour les utilisateurs
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
- admindeeplinkMAC
- adminvideo
- business_assist
search.appverid:
- BCS160
- MET150
- MOE150
- BEA160
- GEA150
ms.assetid: 8f0454b2-f51a-4d9c-bcde-2c48e41621c6
description: Découvrez comment configurer l’authentification multi-facteurs pour votre organisation.
monikerRange: o365-worldwide
ms.openlocfilehash: faac2f052b7c184a967f916cca433dfaef6866c7
ms.sourcegitcommit: db1e48af88995193f15bbd5962f5101a6088074b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2022
ms.locfileid: "65637337"
---
# <a name="set-up-multifactor-authentication-for-microsoft-365"></a>Configurer l'authentification multifactorielle pour Microsoft 365

L’authentification multifacteur signifie que vous et vos employés devez fournir plusieurs méthodes pour vous connecter à Microsoft 365 est l’un des moyens les plus simples de sécuriser votre entreprise. Basé sur votre compréhension de [l’authentification multi-facteurs (MFA) et de sa prise en charge dans Microsoft 365](multi-factor-authentication-microsoft-365.md), c’est le moment de la configurer et de la déployer dans votre organisation. 

> [!IMPORTANT]
> Si vous avez acheté votre abonnement ou une version d’évaluation après le 21 octobre 2019 et que vous êtes, de manière, invité à fournir une authentification multifacteur lors de la connexion, [les valeurs de sécurité par défaut](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults) ont été automatiquement activées pour votre abonnement.

> [!TIP]
> Si vous avez besoin d’aide pour suivre les étapes de cette rubrique, envisagez de [collaborer avec un spécialiste des petites entreprises Microsoft](https://go.microsoft.com/fwlink/?linkid=2186871). Avec Aide aux entreprises, vos employés et vous avez accès 24 heures sur 24 aux spécialistes des petites entreprises à mesure que vous développez votre entreprise, de l’intégration à l’utilisation quotidienne.

## <a name="watch-turn-on-multifactor-authentication"></a>Regarder : activer l’authentification multifacteur

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE2MuO3?autoplay=false]

1. Accédez au Centre d'administration Microsoft 365 sur <a href="https://admin.microsoft.com/ " target="_blank">https://admin.microsoft.com</a>.
1. Sélectionnez **Afficher tout**, puis **Azure Active Directory Centre d’administration**.
1. Sélectionnez **Azure Active Directory**, **Propriétés**, **Gérer les paramètres de sécurité par défaut**.
1. Sous **Activer les paramètres de sécurité par défaut**, sélectionnez **Oui**, puis **Enregistrer**.

## <a name="before-you-begin"></a>Avant de commencer

- Pour gérer le MFA, vous devez être administrateur général. Pour plus d’informations, voir [À propos des rôles d’administrateur](../add-users/about-admin-roles.md).
- Si l’authentification multifacteur par utilisateur héritée est activée, [Désactivez l'authentification multifacteur par utilisateur héritée](#turn-off-legacy-per-user-mfa).
- Si vous avez des clients Office 2013 sur des appareils Windows, [activer l’authentification moderne pour les clients Office 2013](./enable-modern-authentication.md).
- Avancé : si vous avez des services d’annuaire tiers avec les services de fédération Active Directory (AD FS), configurez le serveur Microsoft Azure Multi-Factor Authentication. Consultez [scénarios avancés avec Azure Active Directory Multifactor Authentication et les solutions VPN tierces](/azure/active-directory/authentication/howto-mfaserver-nps-vpn) pour plus d’informations.

### <a name="turn-off-legacy-per-user-mfa"></a>Désactiver l’authentification multifacteur par utilisateur héritée

Si vous avez déjà activé l’authentification multifacteur (MFA) par utilisateur, vous devez désactiver cette fonctionnalité avant d’activer les paramètres de Sécurité par défaut.

1. Dans le Centre d’administration Microsoft 365, dans le volet de navigation gauche, sélectionnez **Utilisateurs** \> **Utilisateurs actifs**.
1. Sur la page **Utilisateurs actifs**, sélectionnez **Authentification multifacteur**.
1. Sur la page d'authentification multifacteur, sélectionnez chaque utilisateur et définissez son état d'authentification multifacteur sur **Désactivé**.

## <a name="turn-security-defaults-on-or-off"></a>Activer ou désactiver les paramètres de sécurité par défaut

Pour la plupart des organisations, les valeurs de sécurité par défaut offrent un niveau de sécurité de connexion supplémentaire. Pour plus d’informations, voir [Présentation des paramètres de sécurité par défaut](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults)

Si votre abonnement est nouveau, les paramètres par défaut de sécurité peuvent déjà être activés automatiquement.

Pour activer ou désactiver les paramètres de sécurité par défaut, accédez au volet **Propriétés** pour Azure Active Directory (Azure AD) dans le Portail Azure.

1. Connectez-vous au [Centre d'administration Microsoft 365](https://admin.microsoft.com) avec des informations d'identification d'administrateur général.
2. Dans le volet de navigation gauche, sélectionnez **Afficher tout** puis sous **Centres d’administration**, sélectionnez **Azure Active Directory**.
3. Dans le **centre d’administration Azure Active Directory** sélectionnez **Azure Active Directory** \> **Propriétés**.
4. Au bas de la page, sélectionnez **Gérer les paramètres de sécurité par défaut**.
5. Sélectionnez **Oui** pour activer les paramètres de sécurité par défaut ou **Non** pour désactiver les paramètres de sécurité par défaut, puis choisissez **Enregistrer**.

Si vous utilisez [bases de référence d’accès conditionnel](/azure/active-directory/conditional-access/concept-baseline-protection), vous serez invité à les désactiver avant de passer à l’utilisation des paramètres de sécurité par défaut.

1. Accédez à la [page des stratégies d’accès conditionnel](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConditionalAccessBlade/Policies).
2. Sélectionnez chaque stratégie de référence sur **Activé** et définissez **Activer la stratégie** sur **Désactivé**.
3. Accédez à la [page des propriétés d'Azure Active Directory](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Properties).
4. Au bas de la page, sélectionnez **Gérer les paramètres de sécurité par défaut**.
5. Sélectionnez **Oui** pour activer les paramètres de sécurité par défaut et **Non** pour désactiver les paramètres de sécurité par défaut, puis choisissez **Enregistrer**.

## <a name="use-conditional-access-policies"></a>Utiliser les stratégies d’accès conditionnel

Si votre organisation a des besoins de sécurité de connexion plus granulaires, les stratégies d’accès conditionnel peuvent vous offrir davantage de contrôle. L’accès conditionnel vous permet de créer et de définir des stratégies qui réagissent aux événements de connexion et de demander des actions supplémentaires avant qu’un utilisateur ne soit autorisé à accéder à une application ou un service.

> [!IMPORTANT]
> Désactivez les paramètres par défaut d'authentification multifacteur et de Sécurité par personne avant d'activer les stratégies d'Accès Conditionnel.

L’accès conditionnel est disponible pour les clients qui ont acheté Azure AD Premium P1 ou les licences qui incluent cette offre, telles que Microsoft 365 Business Premium et Microsoft 365 E3. Pour plus d’informations, voir [créer une stratégie d’accès conditionnel](/azure/active-directory/authentication/tutorial-enable-azure-mfa).

L’accès conditionnel basé sur les risques est disponible via une licence Azure AD Premium P2, ou les licences qui l’incluent, telles que Microsoft 365 E5. Pour plus d'informations, consultez [Accès conditionnel basé sur le risque](/azure/active-directory/conditional-access/howto-conditional-access-policy-risk).

Pour plus d’informations sur Azure AD P1 et P2, voir [Tarification Azure Active Directory](https://azure.microsoft.com/pricing/details/active-directory/).

### <a name="turn-on-modern-authentication-for-your-organization"></a>Activer Authentification moderne pour votre organisation

Pour la plupart des abonnements, l’authentification moderne est automatiquement activée, mais si vous avez acheté votre abonnement avant août 2017, il est probable que vous devrez activer l’authentification moderne pour que les fonctionnalités comme l’authentification multi-facteurs fonctionnent dans les clients Windows comme Outlook.


1. Dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centre d’administration Microsoft 365</a>, dans le menu de gauche, sélectionnez **Paramètres** \> **Paramètres d’organisation**.
2. Sous l’onglet **Services**, sélectionnez **Authentification moderne**, puis dans le volet **Authentification moderne**, vérifiez que l’option **Activer l’authentification moderne** est sélectionnée. Choisissez **Enregistrer les modifications**.


## <a name="next-steps"></a>Étapes suivantes

- [Comment s’inscrire à leur méthode de vérification supplémentaire](https://support.microsoft.com/office/ace1d096-61e5-449b-a875-58eb3d74de14)
- [Qu’est-ce que l’authentification multifacteur](https://support.microsoft.com/help/4577374/what-is-multifactor-authentication) ?
- [Comment se connecter après l’inscription](https://support.microsoft.com/office/2b856342-170a-438e-9a4f-3c092394d3cb)
- [Comment modifier leur méthode de vérification supplémentaire](https://support.microsoft.com/office/956ec8d0-7081-4518-a701-f8414cc20831)

## <a name="related-content"></a>Contenu connexe

[Configurer l’authentification multifacteur](set-up-multi-factor-authentication.md) (vidéo)

[Activer l’authentification multifacteur pour votre téléphone](https://support.microsoft.com/office/ace1d096-61e5-449b-a875-58eb3d74de14)
