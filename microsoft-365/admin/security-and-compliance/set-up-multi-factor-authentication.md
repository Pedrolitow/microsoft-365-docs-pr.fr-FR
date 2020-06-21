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
localization_priority: Normal
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
ms.openlocfilehash: a8e84746a577b95307d325047f0822e8eb3786f0
ms.sourcegitcommit: 659adf65d88ee44f643c471e6202396f1ffb6576
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "44779940"
---
# <a name="set-up-multi-factor-authentication"></a>Configurer Multi-factor Authentification (MFA)
  
En fonction de votre compréhension de [Multi-Factor Authentication (MFA) et de sa prise en charge dans Microsoft 365](multi-factor-authentication-microsoft-365.md), il est temps de le configurer et de le déployer dans votre organisation.

Avant de commencer, déterminez si ces conditions spéciales s’appliquent à vous et prenez les mesures appropriées :

- Si vous avez des clients Office 2013 sur des appareils Windows, [activez l’authentification moderne](https://docs.microsoft.com/microsoft-365/admin/security-and-compliance/enable-modern-authentication).

- Si vous disposez de services d’annuaire tiers avec Active Directory Federation Services (AD FS), configurez le serveur Azure MFA. Pour plus d’informations, consultez la rubrique [scénarios avancés avec Azure Multi-Factor Authentication et des solutions VPN tierces](https://docs.microsoft.com/azure/active-directory/authentication/howto-mfaserver-nps-vpn) .


Tous les autres utilisateurs seront invités à effectuer une authentification supplémentaire si nécessaire. Pour plus d’informations, consultez la [section méthodes et paramètres de vérification à deux facteurs](https://docs.microsoft.com/azure/active-directory/user-help/multi-factor-authentication-end-user-manage-settings#turn-on-two-factor-verification-prompts-on-a-trusted-device).

=======
## <a name="step-1-decide-on-the-method-of-requiring-your-users-to-use-mfa"></a>Étape 1 : décider de la méthode d’utilisation de l’authentification multifacteur par les utilisateurs

> [!NOTE]
> Vous devez être un administrateur général pour configurer ou modifier l’authentification multifacteur. Il existe trois façons de demander à vos utilisateurs d’utiliser l’authentification multifacteur pour les connexions. Pour plus d’informations, consultez la [prise en charge MFA dans Microsoft 365](multi-factor-authentication-microsoft-365.md) .

- Paramètres de sécurité par défaut (recommandé pour les petites entreprises)

  Si vous avez acheté votre abonnement ou une version d’évaluation après le 21 octobre 2019 et que vous êtes invité de manière inattendue à utiliser l’authentification multifacteur, les [paramètres de sécurité par défaut](https://docs.microsoft.com/azure/active-directory/fundamentals/concept-fundamentals-security-defaults) ont été automatiquement activés pour votre abonnement.
  
  Tous les nouveaux abonnements Microsoft 365 auront automatiquement des paramètres de sécurité par défaut activés. Cela signifie que chaque utilisateur devra configurer MFA et installer l’application Microsoft Authenticator sur son appareil mobile.

  Tous les utilisateurs doivent utiliser l’application Microsoft Authenticator comme méthode de vérification supplémentaire et l’authentification héritée est bloquée. 

- Stratégies d’accès conditionnel (recommandé pour les entreprises)

  Les utilisateurs choisissent la méthode de vérification supplémentaire lors de l’inscription MFA.

- Compte par utilisateur (non recommandé)

  Les utilisateurs choisissent la méthode de vérification supplémentaire lors de l’inscription MFA.

## <a name="step-2-test-mfa-on-your-pilot-users"></a>Étape 2. Test MFA sur vos utilisateurs pilotes

Si vous utilisez des stratégies d’accès conditionnel ou l’authentification multifacteur (MFA) par utilisateur (non recommandé), sélectionnez les utilisateurs pilotes de votre entreprise ou organisation pour tester l’inscription et les connexions MFA. Par exemple :

- Pour les stratégies d’accès conditionnel, créez un groupe d’utilisateurs pilotes et une stratégie qui requiert l’authentification multifacteur pour les membres du groupe et pour toutes les applications. Ensuite, ajoutez les comptes de votre utilisateur pilote au groupe.

- Pour l’authentification multifacteur par utilisateur, activez une authentification multifacteur (MFA) pour les comptes d’utilisateur de vos utilisateurs pilotes un par un.

Collaborez avec vos utilisateurs pilotes pour répondre à des questions et des problèmes afin de préparer un déploiement en douceur pour votre organisation.

## <a name="step-3-inform-your-organization-that-mfa-is-coming"></a>Étape 3. Informer votre organisation de l’arrivée à l’authentification multifacteur

Utilisez des notifications par courrier électronique, des affiches de couloir, des réunions d’équipe ou une formation formelle pour vous assurer que vos employés comprennent :

- Pourquoi la MFA est-elle nécessaire pour les connexions ?
- [Comment s’inscrire pour obtenir une autre méthode de vérification](https://support.microsoft.com/office/ace1d096-61e5-449b-a875-58eb3d74de14)
- [Comment se connecter après l’inscription](https://support.microsoft.com/office/2b856342-170a-438e-9a4f-3c092394d3cb)
- [Comment modifier la méthode de vérification supplémentaire](https://support.microsoft.com/office/956ec8d0-7081-4518-a701-f8414cc20831)
- [Comment traiter des situations comme un nouveau téléphone intelligent ?](https://support.microsoft.com/office/6951be76-af50-49a4-847f-21391eaa59f2)

Plus important encore, assurez-vous que vos employés comprennent ***quand les exigences MFA doivent être imposées*** afin de ne pas les surcharger.

## <a name="step-4-roll-out-the-mfa-requirement-to-your-organization-or-users"></a>Étape 4. Déployer l’authentification multifacteur (MFA) pour votre organisation ou vos utilisateurs

En fonction de la méthode d’authentification multifacteur que vous avez choisie, déployez l’authentification MFA auprès des employés au-delà de vos testeurs pilotes.

### <a name="security-defaults"></a>Paramètres de sécurité par défaut

Vous activez ou désactivez les paramètres de sécurité par défaut dans le volet des **Propriétés** d’Azure Active Directory (Azure AD) dans le portail Azure.

1.  Connectez-vous au [Centre d’administration 365 de Microsoft](https://admin.microsoft.com) avec les informations d’identification d’administrateur général.
2.  Accédez à la [page Propriétés Azure Active Directory](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Properties).
3.  Au bas de la page, sélectionnez **Gérer les paramètres de sécurité par défaut**.
4.  Choisissez **Oui** pour activer les paramètres de sécurité par défaut et **non** pour désactiver les paramètres de sécurité par défaut, puis cliquez sur **Enregistrer**.

Si vous avez utilisé des [stratégies d’accès conditionnel de référence](https://docs.microsoft.com/azure/active-directory/conditional-access/concept-baseline-protection), voici comment vous pouvez utiliser les paramètres de sécurité par défaut.

1.  Accédez à la [page des stratégies d’accès conditionnel](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConditionalAccessBlade/Policies).
2.  Choisissez chaque stratégie de planification qui est **activée** et définissez **activer la stratégie** sur **désactivé**.
2.  Accédez à la [page Propriétés Azure Active Directory](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Properties).
4.  Au bas de la page, sélectionnez **Gérer les paramètres de sécurité par défaut**.
5.  Choisissez **Oui** pour activer les paramètres de sécurité par défaut et **non** pour désactiver les paramètres de sécurité par défaut, puis cliquez sur **Enregistrer**.

### <a name="conditional-access-policies"></a>Stratégies d’accès conditionnel

Créez, configurez et activez les stratégies appropriées qui incluent le groupe d’utilisateurs qui nécessitent l’authentification MFA pour la connexion.

### <a name="per-user-mfa-not-recommended"></a>Authentification multifacteur par utilisateur (non recommandé)

Activez les comptes d’utilisateur pour MFA correspondant à votre déploiement.

### <a name="supporting-your-employees"></a>Prise en charge de vos employés

À mesure que vos employés s’inscrivent et commencent à se connecter avec l’authentification multifacteur, assurez-vous que vos spécialistes informatiques, votre service informatique ou le support technique peuvent répondre rapidement à des questions et résoudre les problèmes.

Consultez cet article pour obtenir des [informations sur la résolution des problèmes de connexion MFA](https://support.microsoft.com/office/6951be76-af50-49a4-847f-21391eaa59f2). 


