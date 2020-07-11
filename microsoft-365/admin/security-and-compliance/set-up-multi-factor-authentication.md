---
title: Configurer l'authentification multifacteur pour les utilisateurs
f1.keywords:
- NOCSH
ms.author: sirkkuw
author: sirkkuw
manager: mnirkhe
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
ms.openlocfilehash: 56ca51e77b2ba4fa370a2814a7be9df1393c29dc
ms.sourcegitcommit: 3951147f74510e2ead6c11ceab92854f0937426b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/08/2020
ms.locfileid: "45083537"
---
# <a name="set-up-multi-factor-authentication"></a>Configurer Multi-factor Authentification (MFA)
  
En fonction de votre compréhension de [l’authentification multifacteur (MFA) et de sa prise en charge dans Microsoft 365](multi-factor-authentication-microsoft-365.md), le moment est venu de la configurer et de la déployer dans votre organisation.

Avant de commencer, déterminez si ces conditions spéciales s’appliquent à votre situation et effectuez l’action appropriée :

- Si vous avez des clients Office 2013 sur des appareils Windows, [activer l’authentification moderne](https://docs.microsoft.com/microsoft-365/admin/security-and-compliance/enable-modern-authentication).

- Si vous avez des services d’annuaire tiers avec les Services de fédération Active Directory (AD FS), configurez le serveur d’Authentification multifacteur Azure. Pour plus d’informations, voir les [scénarios avancés avec l’Authentification multifacteur Azure et les solutions VPN tierces](https://docs.microsoft.com/azure/active-directory/authentication/howto-mfaserver-nps-vpn).

Tous les autres utilisateurs seront invités à effectuer une authentification supplémentaire si nécessaire. Si vous souhaitez obtenir plus d’informations, veuillez visiter la [Méthode et les paramètres de vérification à deux facteurs](https://docs.microsoft.com/azure/active-directory/user-help/multi-factor-authentication-end-user-manage-settings#turn-on-two-factor-verification-prompts-on-a-trusted-device).

## <a name="step-1-decide-on-the-method-of-requiring-your-users-to-use-mfa"></a>Étape 1 : décider de la méthode consistant à exiger des utilisateurs qu’ils utilisent l’authentification multifacteur (MFA)

> [!NOTE]
> Vous devez être un administrateur général pour configurer ou modifier l’authentification multifacteur (MFA). Trois méthodes s’offrent à vous pour exiger de vos utilisateurs qu’ils utilisent l’authentification multifacteur pour les connexions. Pour plus d’informations, voir [Prise en charge de l’authentification multifacteur dans Microsoft 365](multi-factor-authentication-microsoft-365.md).

- Paramètres de sécurité par défaut (recommandés pour les petites entreprises)

  Si vous avez acheté votre abonnement ou une version d’évaluation après le 21 octobre 2019 et que vous êtes, de manière inattendue, invité à fournir une authentification multifacteur, [les valeurs de sécurité par défaut](https://docs.microsoft.com/azure/active-directory/fundamentals/concept-fundamentals-security-defaults) ont été automatiquement activées pour votre abonnement.
  
  Les paramètres de sécurité par défaut sont automatiquement activés avec tout nouvel abonnement Microsoft 365. Chaque utilisateur doit ainsi configurer l’authentification multifacteur (MFA) et installer l’application Microsoft Authenticator sur son appareil mobile.

  Tous les utilisateurs doivent utiliser l’application Microsoft Authenticator en tant que méthode de vérification supplémentaire et l’authentification héritée est bloquée. 

- Stratégies d’accès conditionnel (recommandé pour les entreprises)

  Les utilisateurs choisissent la méthode de vérification supplémentaire pendant l’inscription à l’authentification multifacteur (MFA).

- Compte par utilisateur (non recommandé)

  Les utilisateurs choisissent la méthode de vérification supplémentaire pendant l’inscription à l’authentification multifacteur (MFA).

## <a name="step-2-test-mfa-on-your-pilot-users"></a>Étape 2. Tester l’authentification multifacteur (MFA) sur vos utilisateurs pilotes

Si vous utilisez des stratégies d’accès conditionnel ou l’authentification multifacteur (MFA) par utilisateur (non recommandé), sélectionnez les utilisateurs pilotes au sein de votre entreprise ou organisation pour tester l’inscription à l’authentification multifacteur et les connexions. Par exemple :

- Pour les stratégies d’accès conditionnel, créez un groupe d’utilisateurs pilotes et une stratégie nécessitant une authentification multifacteur (MFA) pour les membres du groupe et toutes les applications. Ajoutez ensuite les comptes de vos utilisateurs pilotes au groupe.

- Pour l’authentification multifacteur (MFA) par utilisateur, activez-la pour les comptes d’utilisateurs de vos utilisateurs pilotes l’un après l’autre.

Collaborez avec vos utilisateurs pilotes pour répondre aux questions et problèmes afin de préparer un déploiement parfait pour votre organisation.

## <a name="step-3-inform-your-organization-that-mfa-is-coming"></a>Étape 3. Informez votre organisation que l’authentification multifacteur arrive bientôt

Utilisez des notifications par courrier électronique, des affiches dans les couloirs, des réunions d’équipe ou une formation officielle afin de vérifier que vos employés comprennent :

- Pourquoi l’authentification multifacteur est exigée pour les connexions
- [Comment s’inscrire à leur méthode de vérification supplémentaire](https://support.microsoft.com/office/ace1d096-61e5-449b-a875-58eb3d74de14)
- [Comment se connecter après l’inscription](https://support.microsoft.com/office/2b856342-170a-438e-9a4f-3c092394d3cb)
- [Comment modifier leur méthode de vérification supplémentaire](https://support.microsoft.com/office/956ec8d0-7081-4518-a701-f8414cc20831)
- [Comment gérer les situations telles qu’un nouveau smartphone](https://support.microsoft.com/office/6951be76-af50-49a4-847f-21391eaa59f2)

Assurez-vous surtout que vos employés sachent ***à quel moment l’authentification multifacteur va être imposée*** afin qu’ils ne soient pas surpris.

## <a name="step-4-roll-out-the-mfa-requirement-to-your-organization-or-users"></a>Étape 4. Déployer les conditions pour l’authentification multifacteur (MFA) pour votre organisation ou vos utilisateurs

Selon la méthode d’exigence choisie de l’authentification multifacteur, déployez l’authentification multifacteur (MFA) auprès des employés au-delà de vos testeurs pilotes.

### <a name="security-defaults"></a>Paramètres de sécurité par défaut

Pour activer ou désactiver les paramètres de sécurité par défaut, accédez au volet **Propriétés** pour Azure Active Directory (Azure AD) dans le Portail Azure.

1.  Connectez-vous au [Centre d'administration Microsoft 365](https://admin.microsoft.com) avec des informations d'identification d'administrateur général.
2.  Accédez à la [page des propriétés d'Azure Active Directory](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Properties).
3.  Au bas de la page, sélectionnez **Gérer les paramètres de sécurité par défaut**.
4.  Sélectionnez **Oui** pour activer les paramètres de sécurité par défaut et **Non** pour désactiver les paramètres de sécurité par défaut, puis choisissez **Enregistrer**.

Si vous utilisez des [stratégies d’accès conditionnel de référence](https://docs.microsoft.com/azure/active-directory/conditional-access/concept-baseline-protection), voici comment vous pouvez utiliser les paramètres de sécurité par défaut.

1.  Accédez à la [page des stratégies d’accès conditionnel](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConditionalAccessBlade/Policies).
2.  Sélectionnez chaque stratégie de référence sur **Activé** et définissez **Activer la stratégie** sur **Désactivé**.
2.  Accédez à la [page des propriétés d'Azure Active Directory](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Properties).
4.  Au bas de la page, sélectionnez **Gérer les paramètres de sécurité par défaut**.
5.  Sélectionnez **Oui** pour activer les paramètres de sécurité par défaut et **Non** pour désactiver les paramètres de sécurité par défaut, puis choisissez **Enregistrer**.

### <a name="conditional-access-policies"></a>Stratégies d’accès conditionnel

Créez, configurez et activez les stratégies appropriées qui incluent le groupe d’utilisateurs qui ont besoin de l’authentification multifacteur pour se connecter.

### <a name="per-user-mfa-not-recommended"></a>Authentification multifacteur (MFA) par utilisateur (non recommandé)

Activez les comptes d’utilisateur pour l’authentification multifacteur (MFA) correspondant à votre déploiement.

### <a name="supporting-your-employees"></a>Support de vos employés

Au fur et à mesure que vos employés s’inscrivent et commencent à se connecter avec l’authentification multifacteur, assurez-vous que vos spécialistes informatiques, votre service informatique ou votre support technique peuvent répondre aux questions et résoudre rapidement des problèmes.

Consultez cet article pour des [informations sur la résolution des problèmes liés aux connexions via l’authentification multifacteur (MFA)](https://support.microsoft.com/office/6951be76-af50-49a4-847f-21391eaa59f2). 


