---
title: Authentification multifacteur pour Microsoft 365
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: conceptual
ms.service: microsoft-365-business
ms.localizationpriority: medium
ms.collection:
- Tier1
- scotvorg
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- okr_smb
- AdminTemplateSet
- admindeeplinkMAC
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 043807b2-21db-4d5c-b430-c8a6dee0e6ba
ROBOTS: NOINDEX, NOFOLLOW
description: L’authentification multifacteur (MFA) utilise à la fois un mot de passe, qui doit être fort, et une méthode de vérification supplémentaire.
ms.openlocfilehash: f63c97019bab485b2922a61ef2c101a75cc3d1c9
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68735944"
---
# <a name="multifactor-authentication-for-microsoft-365"></a>Authentification multifacteur pour Microsoft 365

Les mots de passe sont la méthode la plus courante pour authentifier une connexion à un ordinateur ou à un service en ligne, mais ils sont également les plus vulnérables. Les utilisateurs peuvent choisir des mots de passe faciles à utiliser et utiliser les mêmes mots de passe pour plusieurs connexions sur différents ordinateurs et services.

Pour fournir un niveau de sécurité supplémentaire pour les connexions, vous devez utiliser l’authentification multifacteur (MFA), qui utilise à la fois un mot de passe, qui doit être fort, et une méthode de vérification supplémentaire basée sur :

- Quelque chose que vous avez avec vous qui n’est pas facile à dupliquer, tel qu’un smartphone.
- Quelque chose que vous possédez de manière unique et biologique, comme vos empreintes digitales, votre visage ou un autre attribut biométrique.

La méthode de vérification supplémentaire n’est pas utilisée tant que le mot de passe de l’utilisateur n’a pas été vérifié. Avec l’authentification multifacteur, même si un mot de passe fort est volé, l’usurpateur ne dispose pas de votre smartphone ou de votre empreinte digitale pour terminer la connexion.

## <a name="mfa-support-in-microsoft-365"></a>Prise en charge de l’authentification multifacteur dans Microsoft 365

Par défaut, Microsoft 365 et Office 365 prennent en charge l’authentification multifacteur pour les comptes d’utilisateur à l’aide de :

- Un SMS envoyé à un téléphone qui demande à l'utilisateur de taper un code de vérification.
- Un appel téléphonique.
- L'application pour smartphone Microsoft Authenticator.

Dans les deux cas, la connexion MFA utilise la méthode « quelque chose que vous avez avec vous qui n’est pas facilement dupliqué » pour la vérification supplémentaire. Il existe plusieurs façons d’activer l’authentification multifacteur pour Microsoft 365 et Office 365 :

- Avec les paramètres de sécurité par défaut
- Avec les stratégies d’accès conditionnel
- Pour chaque compte d’utilisateur individuel (non recommandé)

Ces méthodes sont basées sur votre plan Microsoft 365.

|Planification|Recommandation|Type de client|
|---|---|---|
|Tous les plans Microsoft 365|Utilisez les paramètres de sécurité par défaut, qui requièrent l’authentification multifacteur pour tous les comptes d’utilisateur. <p> Vous pouvez également configurer l’authentification multifacteur par utilisateur sur des comptes d’utilisateur individuels, mais cela n’est pas recommandé.|Petite entreprise|
|Microsoft 365 Business Premium <p> Microsoft 365 E3 <p> Licences Azure Active Directory (Azure AD) Premium P1|Utilisez [des stratégies de sécurité par défaut ou d’accès conditionnel](/microsoft-365/business-premium/m365bp-conditional-access) pour exiger l’authentification multifacteur pour les comptes d’utilisateur en fonction de l’appartenance au groupe, des applications ou d’autres critères.|Petites entreprises à entreprise|
|Microsoft 365 E5 <p> licences Azure AD Premium P2|Utilisez Azure AD Identity Protection pour exiger l’authentification multifacteur sur la base des critères de risque de connexion.|Entreprise|
||||

### <a name="security-defaults"></a>Paramètres de sécurité par défaut

Les paramètres de sécurité par défaut sont une nouvelle fonctionnalité pour Microsoft 365 et les abonnements Office 365 payants ou en version d’évaluation créés après le 21 octobre 2019. Les paramètres de sécurité par défaut de ces abonnements étant activés :

- Exige que tous vos utilisateurs utilisent l’authentification multifacteur avec l’application Microsoft Authenticator.
- L’authentification héritée est bloquée.

Les utilisateurs disposent de 14 jours pour s’inscrire à l’authentification multifacteur de l’application Microsoft Authenticator sur leur smartphone, un délai qui commence dès la première connexion suivant l’activation des paramètres de sécurité par défaut. Lorsque les 14 jours sont écoulés, l’utilisateur ne peut pas se connecter tant que son inscription à l’authentification multifacteur n’est pas terminée.

Les paramètres de sécurité par défaut garantissent que toutes les organisations ont un niveau de sécurité de base qui est activé par défaut pour la connexion des utilisateurs. Vous pouvez désactiver les paramètres de sécurité par défaut en faveur de l’authentification multifacteur avec des stratégies d’accès conditionnel.

Vous activez ou désactivez les paramètres de sécurité par défaut dans le volet **Propriétés** d’Azure AD dans le Portail Azure.

![Image de la page propriétés du répertoire.](../../media/multi-factor-authentication-microsoft-365/security-defaults-mfa.png)

Vous pouvez utiliser les paramètres de sécurité par défaut avec n’importe quel plan Microsoft 365.

Pour plus d’informations, voir[Vue d’ensemble des paramètres de sécurité par défaut](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults).

### <a name="conditional-access-policies"></a>Stratégies d’accès conditionnel

Les stratégies d’accès conditionnel sont un groupe de règles qui spécifient les conditions dans lesquelles les connexions sont évaluées et autorisées. Par exemple, vous pouvez créer une stratégie d’accès conditionnel qui indique :

- Si le nom du compte d’utilisateur concerne membre d’un groupe d’utilisateurs bénéficiant des rôles d’administrateur Exchange, utilisateur, mot de passe, sécurité, SharePoint ou global, exigez l’authentification multifacteur avant d’autoriser l’accès.

Cette stratégie vous permet de demander une authentification multifacteur basée sur l’appartenance au groupe, plutôt que d’essayer de configurer des comptes d’utilisateur individuels pour l’authentification multifacteur lorsqu’ils sont attribués ou non à des rôles d’administrateur.

Vous pouvez également utiliser des stratégies d’accès conditionnel pour des fonctionnalités plus avancées, telles que l’exigence de l’authentification multifacteur pour des applications spécifiques ou le fait que la connexion s’effectue à partir d’un appareil conforme, tel que votre ordinateur portable exécutant Windows 10.

Vous configurez des stratégies d’accès conditionnel à partir du volet **Sécurité** pour Azure AD dans le Portail Azure.

![Image de l’option de menu pour l’accès conditionnel.](../../media/multi-factor-authentication-microsoft-365/conditional-access-mfa.png)

Vous pouvez utiliser les stratégies d’accès conditionnel avec :

- Microsoft 365 Business Premium
- Microsoft 365 E3 et E5
- Licences Azure AD Premium P1 et Azure AD Premium P2

Pour les petites entreprises avec Microsoft 365 Business Premium, vous pouvez facilement utiliser les stratégies d’accès conditionnel en procédant comme suit :

1. Créez un groupe pour contenir les comptes d’utilisateurs qui requièrent une authentification multifacteur.
2. Activez la stratégie **Exiger l’authentification multifacteur pour les administrateurs généraux**.
3. Créez une stratégie d’accès conditionnel basée sur un groupe avec ces paramètres :
    - Affectations > Utilisateurs et groupes : nom de votre groupe de l’étape 1 ci-dessus.
    - Affectations > applications ou actions cloud : toutes les applications cloud.
    - Contrôles d’accès > Accorder > Accorder l’accès > Exiger l’authentification multifacteur.
4. Activez la stratégie.
5. Ajoutez un compte d’utilisateur au groupe créé à l’étape 1 ci-dessus et testez-le.
6. Pour exiger l’authentification multifacteur pour d’autres comptes d’utilisateur, ajoutez-les au groupe créé à l’étape 1.

Cette stratégie d’accès conditionnel vous permet de déployer la configuration MFA pour vos utilisateurs à votre rythme.

Les entreprises doivent utiliser [Stratégies d’accès conditionnel courantes](/azure/active-directory/conditional-access/concept-conditional-access-policy-common) pour configurer les stratégies suivantes :

- [Exiger l’authentification multifacteur pour les administrateurs](/azure/active-directory/conditional-access/howto-conditional-access-policy-admin-mfa)
- [Exiger l’authentification multifacteur pour tous les utilisateurs](/azure/active-directory/conditional-access/howto-conditional-access-policy-all-users-mfa)
- [Bloquer l’authentification héritée](/azure/active-directory/conditional-access/howto-conditional-access-policy-block-legacy)

Si vous souhaitez en savoir plus, consultez [Présentation de l’accès conditionnel](/azure/active-directory/conditional-access/overview).

### <a name="azure-ad-identity-protection"></a>Azure AD Identity Protection

Avec Azure AD Identity Protection, vous pouvez créer une stratégie d’accès conditionnel supplémentaire pour [exiger l’authentification multifacteur lorsque le risque de connexion est moyen ou élevé](../../security/office-365-security/identity-access-policies.md#require-mfa-based-on-sign-in-risk).

Vous pouvez utiliser Azure AD Identity Protection et des stratégies d’accès conditionnel basées sur les risques avec :

- Microsoft 365 E5
- licences Azure AD Premium P2

Si vous souhaitez en savoir plus, consultez la page [Présentation de Azure AD Identity Protection](/azure/active-directory/identity-protection/overview-identity-protection).

### <a name="legacy-per-user-mfa-not-recommended"></a>Authentification multifacteur héritée par utilisateur (non recommandé)

Vous devez utiliser des stratégies de sécurité par défaut ou d’accès conditionnel pour exiger l’authentification multifacteur pour les connexions de votre compte d’utilisateur. Toutefois, si l’un de ces éléments ne peut pas être utilisé, Microsoft recommande vivement l’authentification multifacteur pour les comptes d’utilisateur qui ont des rôles d’administrateur, en particulier le rôle d’administrateur général, pour n’importe quelle taille d’abonnement.

Vous activez l’authentification multifacteur pour les comptes d’utilisateur individuels à partir du volet <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">**Utilisateurs actifs**</a> du Centre d'administration Microsoft 365.

![Image de l’option d’authentification multifacteur dans la page Utilisateurs actifs.](../../media/multi-factor-authentication-microsoft-365/per-user-mfa.png)

Une fois activé, la prochaine fois que l’utilisateur se connecte, il est invité à s’inscrire à l’authentification multifacteur et à choisir et tester la méthode de vérification supplémentaire.

### <a name="using-these-methods-together"></a>Utilisation combinée des méthodes

Ce tableau présente les résultats de l’activation de l’authentification multifacteur avec les paramètres de sécurité par défaut, les stratégies d’accès conditionnel et les paramètres de compte par utilisateur.

|*Élément*|Activé|Désactivé|Méthode d'authentification secondaire|
|---|---|---|---|
|**Paramètres de sécurité par défaut**|Impossible d’utiliser les stratégies d’accès conditionnel|Peut utiliser les stratégies d’accès conditionnel|Application Microsoft Authenticator|
|**Stratégies d’accès conditionnel**|Si elles sont activées, vous ne pouvez pas activer les paramètres de sécurité par défaut|Si tous ces éléments sont désactivés, vous pouvez activer les paramètres de sécurité par défaut|Utilisateur spécifié lors de l’inscription à l’authentification multifacteur|
|**Authentification multifacteur héritée par utilisateur (non recommandé)**|Remplace les paramètres de sécurité par défaut et les stratégies d’accès conditionnel nécessitant l’authentification multifacteur à chaque connexion|Remplacé par les paramètres de sécurité par défaut et les stratégies d’accès conditionnel|Utilisateur spécifié lors de l’inscription à l’authentification multifacteur|
||||

Si les paramètres de sécurité par défaut sont activés, les nouveaux utilisateurs sont invités à s’inscrire pour l’authentification multifacteur et à utiliser l’application Microsoft Authenticator à leur prochaine connexion.

## <a name="ways-to-manage-mfa-settings"></a>Méthodes de gestion des paramètres MFA

Il existe deux façons de gérer les paramètres de l’authentification multifacteur.

Dans le Portail Azure, vous pouvez :

- Activer et désactiver les paramètres de sécurité par défaut
- Configurer des stratégies d’accès conditionnel

Dans le Centre d'administration Microsoft 365, vous pouvez configurer <a href="https://go.microsoft.com/fwlink/?LinkId=279980" target="_blank">les paramètres MFA</a> par utilisateur et par service.

## <a name="next-steps"></a>Prochaines étapes

[Configurer l’authentification multifacteur pour Microsoft 365](set-up-multi-factor-authentication.md)

## <a name="related-content"></a>Contenu connexe

[Activer l’authentification multi-facteurs](set-up-multi-factor-authentication.md) (vidéo)\
[Activer l’authentification multi-facteurs sur votre téléphone](https://support.microsoft.com/office/ace1d096-61e5-449b-a875-58eb3d74de14) (vidéo)
