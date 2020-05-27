---
title: Multi-Factor Authentication pour Microsoft 365
f1.keywords:
- NOCSH
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 043807b2-21db-4d5c-b430-c8a6dee0e6ba
ROBOTS: NOINDEX, NOFOLLOW
description: Découvrez l’authentification multifacteur dans Microsoft 365.
ms.openlocfilehash: eba9ae38dbc17a22abb5d5ef92b8cd30a827ae11
ms.sourcegitcommit: 87eff6e8a08cec3cb0464a3b765434717584a4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/26/2020
ms.locfileid: "44371451"
---
# <a name="multi-factor-authentication-for-microsoft-365"></a>Multi-Factor Authentication pour Microsoft 365

Les mots de passe constituent la méthode la plus courante pour authentifier une connexion à un ordinateur ou un service en ligne, mais ils sont également les plus vulnérables. Les utilisateurs peuvent choisir des mots de passe faciles à utiliser et utiliser les mêmes mots de passe pour plusieurs connexions à différents ordinateurs et services.

Pour fournir un niveau de sécurité supplémentaire pour les connexions, vous devez utiliser l’authentification multifacteur (MFA), qui utilise à la fois un mot de passe, qui doit être fort, et une méthode de vérification supplémentaire basée sur :

- Tout ce dont vous disposez avec vous n’est pas facile à dupliquer, comme un téléphone intelligent.
- Il s’agit d’un article que vous disposez de manière unique et biologique, comme vos empreintes digitales, face ou autre attribut biométrique.

La méthode de vérification supplémentaire n’est utilisée qu’une fois que le mot de passe de l’utilisateur a été vérifié. Avec l’authentification multifacteur, même si un mot de passe utilisateur fort est compromis, l’agresseur ne dispose pas de votre téléphone intelligent ou de votre empreinte digitale pour terminer la connexion.

## <a name="mfa-support-in-microsoft-365"></a>Prise en charge de l’authentification multifacteur dans Microsoft 365
Par défaut, Microsoft 365 et Office 365 prennent en charge l’authentification multifacteur pour les comptes d’utilisateur à l’aide des éléments suivants :

- Message texte envoyé à un téléphone et qui demande à l’utilisateur de taper un code de vérification.
- Un appel téléphonique.
- Application Smart Phone Microsoft authentificateur.

Dans les deux cas, la connexion MFA utilise la méthode « ce que vous avez avec vous qui n’est pas facilement dupliqué » pour la vérification supplémentaire.
Il existe plusieurs façons d’activer l’authentification multifacteur pour Microsoft 365 et Office 365 :

- Avec les paramètres de sécurité par défaut
- Avec des stratégies d’accès conditionnel
- Pour chaque compte d’utilisateur individuel (non recommandé)

Ces méthodes sont basées sur votre plan Microsoft 365.
    
|Planification  |Recommandation  | Type de client |
|---------|---------|----------|
| Tous les plans Microsoft 365 | Utilisez les paramètres de sécurité par défaut, qui nécessitent l’authentification multifacteur pour tous les comptes d’utilisateur. <br> Vous pouvez également exiger l’authentification MFA par compte d’utilisateur, mais cela n’est pas recommandé. | Petite entreprise |
| Microsoft 365 Business Premium <br><br> Microsoft 365 E3 <br><br> Licences Azure Active Directory (Azure AD) Premium P1 | Utilisez des stratégies d’accès conditionnel pour exiger l’authentification multifacteur pour les comptes d’utilisateur en fonction de l’appartenance à un groupe, des applications ou d’autres critères. | Petites et grandes entreprises |
| Microsoft 365 E5 <br><br> Licences Azure AD Premium P2 | Utilisez Azure AD Identity Protection pour exiger la MFA en fonction des critères de risque de connexion. |  Entreprise |
||||

### <a name="security-defaults"></a>Paramètres de sécurité par défaut

Les paramètres de sécurité par défaut sont une nouvelle fonctionnalité pour Microsoft 365 et les abonnements Office 365 payants ou en version d’évaluation créés après le 21 octobre 2019. Les paramètres de sécurité par défaut de ces abonnements sont activés :

- Tous vos utilisateurs doivent utiliser l’authentification multifacteur avec l’application Microsoft Authenticator.
- Bloque l’authentification héritée.

Les utilisateurs disposent de 14 jours pour s’inscrire à l’authentification multifacteur de l’application Microsoft Authenticator sur leur smartphone, un délai qui commence dès la première connexion suivant l’activation des paramètres de sécurité par défaut. Lorsque les 14 jours sont écoulés, l’utilisateur ne peut pas se connecter tant que son inscription à l’authentification multifacteur n’est pas terminée.

Les paramètres de sécurité par défaut garantissent que toutes les organisations ont un niveau de sécurité de base qui est activé par défaut pour la connexion des utilisateurs. Vous pouvez désactiver les paramètres de sécurité par défaut au profit de la fonction MFA avec des stratégies d’accès conditionnel.

Vous activez ou désactivez les paramètres de sécurité par défaut dans le volet des **Propriétés** pour Azure ad dans le portail Azure.

![](../../media/multi-factor-authentication-microsoft-365/security-defaults-mfa.png)

Vous pouvez utiliser les paramètres de sécurité par défaut avec n’importe quel plan Microsoft 365.

Pour plus d’informations, voir[Vue d’ensemble des paramètres de sécurité par défaut](https://docs.microsoft.com/azure/active-directory/fundamentals/concept-fundamentals-security-defaults). 

### <a name="conditional-access-policies"></a>Stratégies d’accès conditionnel

Les stratégies d’accès conditionnel sont un groupe de règles qui spécifient les conditions dans lesquelles les connexions sont évaluées et autorisées. Par exemple, vous pouvez créer une stratégie d’accès conditionnel qui indique :

- Si le nom du compte d’utilisateur concerne membre d’un groupe d’utilisateurs bénéficiant des rôles d’administrateur Exchange, utilisateur, mot de passe, sécurité, SharePoint ou global, exigez l’authentification multifacteur avant d’autoriser l’accès.

Cette stratégie vous permet de demander une authentification multifacteur basée sur l’appartenance au groupe, plutôt que d’essayer de configurer des comptes d’utilisateur individuels pour l’authentification multifacteur lorsqu’ils sont attribués ou non à des rôles d’administrateur.

Vous pouvez également utiliser des stratégies d’accès conditionnel pour des fonctionnalités plus avancées, telles que l’authentification MFA pour des applications spécifiques ou l’utilisation de la connexion à partir d’un appareil compatible, tel que votre ordinateur portable exécutant Windows 10.

Vous configurez les stratégies d’accès conditionnel à partir du volet de **sécurité** pour Azure ad dans le portail Azure.

![](../../media/multi-factor-authentication-microsoft-365/conditional-access-mfa.png)

Vous pouvez utiliser des stratégies d’accès conditionnel avec :

- Microsoft 365 Business Premium
- Microsoft 365 E3 et E5
- Licences Azure AD Premium P1 et Azure AD Premium P2 

Pour les petites entreprises avec Microsoft 365 Business Premium, vous pouvez facilement utiliser des stratégies d’accès conditionnel en procédant comme suit :

1. Créez un groupe pour contenir les comptes d’utilisateurs qui requièrent l’authentification multifacteur.
2. Activer la stratégie **exiger l’authentification multifacteur pour les administrateurs globaux** .
3. Créez une stratégie d’accès conditionnel basée sur un groupe avec ces paramètres :
    - Affectations > des utilisateurs et des groupes : nom de votre groupe de l’étape 1 ci-dessus.
    - Affectations > les applications ou les actions Cloud : toutes les applications Cloud.
    - Les contrôles d’accès > accorder > accorder l’accès > nécessitent une authentification multifacteur.
4. Activez la stratégie.
5. Ajoutez un compte d’utilisateur au groupe créé à l’étape 1 ci-dessus et testez.
6. Pour exiger l’authentification multifacteur pour les comptes d’utilisateur supplémentaires, ajoutez-les au groupe créé à l’étape 1.

Cette stratégie d’accès conditionnel vous permet de déployer la configuration MFA requise pour vos utilisateurs à votre rythme.

Les entreprises doivent utiliser des [stratégies d’accès conditionnel courantes](https://docs.microsoft.com/azure/active-directory/conditional-access/concept-conditional-access-policy-common) pour configurer les stratégies suivantes :

- [Exiger l’authentification multifacteur pour les administrateurs](https://docs.microsoft.com/azure/active-directory/conditional-access/howto-conditional-access-policy-admin-mfa)
- [Exiger l’authentification multifacteur pour tous les utilisateurs](https://docs.microsoft.com/azure/active-directory/conditional-access/howto-conditional-access-policy-all-users-mfa)
- [Bloquer l’authentification héritée](https://docs.microsoft.com/azure/active-directory/conditional-access/howto-conditional-access-policy-block-legacy)

Si vous souhaitez en savoir plus, consultez [Présentation de l’accès conditionnel](https://docs.microsoft.com/azure/active-directory/conditional-access/overview).

### <a name="azure-ad-identity-protection"></a>Azure AD Identity Protection

Avec Azure AD Identity Protection, vous pouvez créer une stratégie d’accès conditionnel supplémentaire pour [exiger l’authentification multifacteur lorsque le risque de connexion est moyen ou élevé](https://docs.microsoft.com/microsoft-365/enterprise/identity-access-policies#require-mfa-based-on-sign-in-risk).

Vous pouvez utiliser Azure AD identity protection et les stratégies d’accès conditionnel basées sur les risques avec :

- Microsoft 365 E5
- Licences Azure AD Premium P2

Si vous souhaitez en savoir plus, consultez la page [Présentation de Azure AD Identity Protection](https://docs.microsoft.com/azure/active-directory/identity-protection/overview-identity-protection).

### <a name="mfa-for-an-individual-user-account-not-recommended"></a>Authentification multifacteur pour un compte d’utilisateur individuel (non recommandé)

Vous devez utiliser des paramètres de sécurité par défaut ou des stratégies d’accès conditionnel pour exiger l’authentification multifacteur pour les connexions de vos comptes d’utilisateur. Toutefois, si l’une de ces méthodes n’est pas utilisable, Microsoft recommande vivement la fonction MFA pour les comptes d’utilisateur qui ont des rôles d’administrateur, en particulier le rôle d’administrateur général, pour n’importe quel abonnement de taille. 

Vous activez l’authentification multifacteur pour des comptes d’utilisateur individuels à partir du volet **utilisateur actif** du centre d’administration 365 de Microsoft.

![](../../media/multi-factor-authentication-microsoft-365/per-user-mfa.png)

Après avoir été activé, la prochaine fois que l’utilisateur se connecte, il est invité à s’inscrire pour l’authentification multifacteur (MFA) et à choisir et tester la méthode de vérification supplémentaire.

### <a name="using-these-methods-together"></a>Utilisation combinée des méthodes

Ce tableau présente les résultats de l’activation de l’authentification multifacteur avec les paramètres de sécurité par défaut, les stratégies d’accès conditionnel et les paramètres de compte par utilisateur.

|| Activé | Désactivé | Méthode d'authentification secondaire |
|:-------|:-----|:-------|:-------|
| **Paramètres de sécurité par défaut** | Ne peut pas utiliser les stratégies d’accès conditionnel |   Peut utiliser les stratégies d’accès conditionnel | Application Microsoft Authenticator |
| **Stratégies d’accès conditionnel** |Si l’une d’elles est activée, vous ne pouvez pas activer les paramètres de sécurité par défaut | Si tous ces éléments sont désactivés, vous pouvez activer les paramètres de sécurité par défaut | Utilisateur spécifié lors de l’inscription à l’authentification multifacteur |
| **Paramètre de compte par utilisateur (non recommandé)** | Remplace les paramètres de sécurité par défaut et les stratégies d’accès conditionnel exigeant une authentification multifacteur à chaque connexion | Remplacé par les paramètres de sécurité et les stratégies d’accès conditionnel | Utilisateur spécifié lors de l’inscription à l’authentification multifacteur|
||||

Si les paramètres de sécurité par défaut sont activés, tous les nouveaux utilisateurs sont invités à indiquer l’enregistrement MFA et l’utilisation de l’application Microsoft Authenticator lors de la prochaine connexion.

## <a name="ways-to-manage-mfa-settings"></a>Méthodes de gestion des paramètres MFA

Il existe deux façons de gérer les paramètres MFA.

Dans le portail Azure, vous pouvez :

- Activer et désactiver les paramètres de sécurité par défaut
- Configurer des stratégies d’accès conditionnel

Dans le centre d’administration 365 de Microsoft, vous pouvez configurer les paramètres par utilisateur et par authentification multifacteur de service.

## <a name="your-next-step"></a>Étape suivante

[Configurer MFA pour Microsoft 365](set-up-multi-factor-authentication.md)

