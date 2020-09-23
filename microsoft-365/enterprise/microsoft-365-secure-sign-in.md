---
title: Connexion sécurisée des utilisateurs à votre client Microsoft 365
f1.keywords:
- NOCSH
author: JoeDavies-MSFT
ms.author: josephd
manager: laurawi
ms.date: 09/16/2020
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
localization_priority: Priority
ms.collection:
- M365-security-compliance
- Strat_O365_Enterprise
ms.custom: ''
description: Renforcez la sécurité des connexions de vos utilisateurs à l’aide de l’authentification multifacteur (MFA) et d’autres fonctionnalités.
ms.openlocfilehash: 6c8f58e54ae21b4a5e1566dc72673e1d69152863
ms.sourcegitcommit: fdb5f9d865037c0ae23aae34a5c0f06b625b2f69
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2020
ms.locfileid: "48132240"
---
# <a name="secure-user-sign-ins-to-your-microsoft-365-tenant"></a>Connexion sécurisée des utilisateurs à votre client Microsoft 365

Pour renforcer la sécurité des connexions des utilisateurs :

- Utilisez la protection par mot de passe Azure Active Directory (Azure AD).
- Utilisez l’authentification multifacteur (MFA)
- Déployez des stratégies communes pour d’identité et d’accès aux appareils

## <a name="azure-ad-password-protection"></a>Protection par mot de passe Azure AD.

La protection par mot de passe Azure AD détecte et bloque les mots de passe faibles connus et leurs variantes, et peut également bloquer d’autres termes faibles définis par votre organisation. Les listes générales par défaut de mots de passe interdits sont automatiquement appliquées à tous les utilisateurs d’un client Azure AD. Vous pouvez définir d’autres entrées dans une liste personnalisée de mots de passe interdits. Lorsque les utilisateurs modifient ou réinitialisent leurs mots de passe, ces listes sont vérifiées de façon à garantir l’utilisation de mots de passe forts.

Pour plus d’informations, voir [Configurer la protection par mot de passe Azure AD](https://docs.microsoft.com/azure/active-directory/authentication/concept-password-ban-bad).

## <a name="mfa"></a>Authentification multifacteur

L’authentification multifacteur exige que les connexions des utilisateurs fassent l’objet d’une vérification supplémentaire, au-delà du mot de passe du compte d’utilisateur. Même si un utilisateur malveillant détermine un mot de passe de compte d’utilisateur, il doit également répondre à une vérification supplémentaire, par exemple, un message texte envoyé vers un smartphone, avant que l’accès ne lui soit accordé.

![Le mot de passe correct et une vérification supplémentaire génèrent une connexion réussie](../media/empower-people-to-work-remotely/remote-workers-mfa.png)

La première étape de l’utilisation de l’authentification multifacteur est de ***l’imposer à tous les comptes d’administrateurs***, également appelés comptes privilégiés.

Une fois cette première étape effectuée, Microsoft recommande vivement l’authentification multifacteur pour tous les utilisateurs.

En fonction de votre plan Microsoft 365, trois méthodes sont possibles pour imposer l’utilisation de l’authentification multifacteur.

| Planification | Recommandation |
|---------|---------|
|Toutes les offres Microsoft 365 (sans licence Azure AD Premium P1 ou P2)     |[Activer les paramètres de sécurité par défaut dans Azure AD](https://docs.microsoft.com/azure/active-directory/fundamentals/concept-fundamentals-security-defaults). La sécurité par défaut d’Azure AD inclut l’authentification multifacteur pour les utilisateurs et les administrateurs.   |
|Microsoft 365 E3 (inclut les licences Azure AD Premium P1)     | Utilisez les [Stratégies d’accès conditionnel courantes](https://docs.microsoft.com/azure/active-directory/conditional-access/concept-conditional-access-policy-common) pour configurer les stratégies suivantes : <br>- [Exiger l’authentification multifacteur pour les administrateurs](https://docs.microsoft.com/azure/active-directory/conditional-access/howto-conditional-access-policy-admin-mfa) <br>- [Exiger l’authentification multifacteur pour tous les utilisateurs](https://docs.microsoft.com/azure/active-directory/conditional-access/howto-conditional-access-policy-all-users-mfa) <br> - [Bloquer l’authentification héritée](https://docs.microsoft.com/azure/active-directory/conditional-access/howto-conditional-access-policy-block-legacy)       |
|Microsoft 365 E5 (inclut les licences Azure AD Premium P2)     | Pour tirer parti de la protection d’identité Azure AD Identity Protection, commencez à implémenter la [série recommandée concernant l’accès conditionnel et les stratégies associées](../enterprise/identity-access-policies.md) en créant les deux stratégies suivantes :<br> - [Exiger l’authentification multifacteur lorsque le risque de connexion est moyen ou élevé](../enterprise/identity-access-policies.md#require-mfa-based-on-sign-in-risk) <br>- [Les utilisateurs à risque élevé doivent modifier leur mot de passe](../enterprise/identity-access-policies.md#high-risk-users-must-change-password)       |
| | |

### <a name="security-defaults"></a>Paramètres de sécurité par défaut

Les paramètres de sécurité par défaut sont une nouvelle fonctionnalité pour Microsoft 365 et les abonnements Office 365 payants ou en version d’évaluation créés après le 21 octobre 2019. Les paramètres de sécurité par défaut de ces abonnements sont activés, ce qui ***nécessite que tous vos utilisateurs utilisent l’authentification multifacteur à l’aide de l’application Microsoft Authenticator***.
 
Les utilisateurs disposent de 14 jours pour s’inscrire à l’authentification multifacteur de l’application Microsoft Authenticator sur leur smartphone, un délai qui commence dès la première connexion suivant l’activation des paramètres de sécurité par défaut. Lorsque les 14 jours sont écoulés, l’utilisateur ne peut pas se connecter tant que son inscription à l’authentification multifacteur n’est pas terminée.

Les paramètres de sécurité par défaut garantissent que toutes les organisations ont un niveau de sécurité de base qui est activé par défaut pour la connexion des utilisateurs. Vous pouvez désactiver les paramètres de sécurité par défaut en faveur de l’authentification multifacteur avec des stratégies d’accès conditionnel ou pour des comptes individuels.

Pour plus d’informations, voir[Vue d’ensemble des paramètres de sécurité par défaut](https://docs.microsoft.com/azure/active-directory/fundamentals/concept-fundamentals-security-defaults).

### <a name="conditional-access-policies"></a>Stratégies d’accès conditionnel

Les stratégies d’accès conditionnel sont un groupe de règles qui spécifient les conditions dans lesquelles les connexions sont évaluées et l’accès autorisé. Par exemple, vous pouvez créer une stratégie d’accès conditionnel qui indique :

- Si le nom du compte d’utilisateur concerne membre d’un groupe d’utilisateurs bénéficiant des rôles d’administrateur Exchange, utilisateur, mot de passe, sécurité, SharePoint ou global, exigez l’authentification multifacteur avant d’autoriser l’accès.

Cette stratégie vous permet de demander une authentification multifacteur basée sur l’appartenance au groupe, plutôt que d’essayer de configurer des comptes d’utilisateur individuels pour l’authentification multifacteur lorsqu’ils sont attribués ou non à des rôles d’administrateur.

Vous pouvez également utiliser les stratégies d’accès conditionnel pour des fonctionnalités plus avancées, telles que la nécessité de se connecter à partir d’un appareil compatible, tel que votre ordinateur portable fonctionnant sous Windows 10.

Les licences d’accès conditionnel exige Azure AD Premium P1, lesquelles sont incluses dans Microsoft 365 E3 et E5.

Si vous souhaitez en savoir plus, consultez [Présentation de l’accès conditionnel](https://docs.microsoft.com/azure/active-directory/conditional-access/overview).

### <a name="using-these-methods-together"></a>Utilisation combinée des méthodes

Gardez les éléments suivants à l’esprit :

- Vous ne pouvez pas activer les paramètres de sécurité par défaut si vous avez activé des stratégies d’accès conditionnel.
- Vous ne pouvez pas activer de stratégie d’accès conditionnel si les paramètres de sécurité par défaut sont activés.

Si les paramètres de sécurité par défaut sont activés, les nouveaux utilisateurs sont invités à s’inscrire pour l’authentification multifacteur et à utiliser l’application Microsoft Authenticator. 

Ce tableau présente les résultats de l’activation de l’authentification multifacteur avec les paramètres de sécurité par défaut et les stratégies d’accès conditionnel.

| Méthode | Activé | Désactivé | Méthode d'authentification supplémentaire |
|:-------|:-----|:-------|:-------|
| **Paramètres de sécurité par défaut**  | Ne peut pas utiliser les stratégies d’accès conditionnel | Peut utiliser les stratégies d’accès conditionnel | Application Microsoft Authenticator |
| **Stratégies d’accès conditionnel** | Si l’une d’elles est activée, vous ne pouvez pas activer les paramètres de sécurité par défaut | Si tous ces éléments sont désactivés, vous pouvez activer les paramètres de sécurité par défaut  | Utilisateur spécifié lors de l’inscription à l’authentification multifacteur  |
||||

## <a name="identity-and-device-access-policies"></a>Stratégies d’identité et d’accès aux appareils

Les paramètres et stratégies d’identité et d’accès aux appareils sont des fonctionnalités préalables recommandées et leurs paramètres, associés à un accès conditionnel, à Intune et à des stratégies de protection d’identité Azure AD, qui déterminent si une demande d’accès doit être accordée et dans quelles conditions. La décision se fonde sur le compte d’utilisateur utilisé pour la connexion, l’appareil utilisé, l’application utilisée par l’utilisateur pour l’accès, l’emplacement depuis lequel la demande d’accès est émise et l’évaluation du risque lié à la demande. Cela permet de s’assurer que seuls les utilisateurs et les appareils approuvés ont accès aux ressources critiques de l’entreprise.

>[!Note]
>Azure AD Identity Protection requiert des licences Azure AD Premium P2, incluses dans Microsoft 365 E5.
>

Les stratégies d’identité et d’accès aux appareils sont définies pour une utilisation à trois niveaux : 

- La protection de base constitue un niveau de sécurité minimal pour les identités et appareils qui accèdent à vos applications et données.
- La protection sensible propose une sécurité supplémentaire pour les données spécifiques. Les identités et les appareils doivent démontrer des niveaux de sécurité et d’intégrité des appareils plus élevés.
- La protection des environnements comportant des données hautement réglementées ou classifiées est généralement limitée à de petites quantités de données hautement classifiées, comportant des secrets commerciaux ou soumises à des réglementations sur les données. Les identités et les appareils doivent démontrer des niveaux de sécurité et d’intégrité des appareils bien plus élevés. 

Ces niveaux de protection et les configurations correspondantes apportent des niveaux de protection cohérents selon les données, les identités et les appareils.

Microsoft recommande vivement de configurer et de déployer les stratégies d’identité et d’accès aux appareils dans votre organisation, notamment des paramètres spécifiques pour Microsoft Teams, Exchange Online et SharePoint. Pour plus d’informations, voir [Configurations des identités et de l’accès aux appareils](microsoft-365-policies-configurations.md).

<!--

## Let your users reset their own passwords

Self-Service Password Reset (SSPR) enables users to reset their own passwords without impacting IT staff. Users can quickly reset their passwords at any time and from any place. Watch [this video](https://go.microsoft.com/fwlink/?linkid=2128524) to set up SSPR.

## Sign in to SaaS apps with Azure AD

In addition to providing cloud authentication for users, Azure AD can also be your central way to secure all your apps, whether they’re on-premises, in Microsoft’s cloud, or in another cloud. By [integrating your apps into Azure AD](https://docs.microsoft.com/azure/active-directory/manage-apps/plan-an-application-integration), you can make it easy for your users to discover the applications they need and sign into them securely.

## Results of deployment of secure sign-ins

After deployment of MFA, your users:

- Are required to use MFA for sign-ins.
- Have completed the MFA registration process and are using MFA for all sign-ins.
- Can use SSPR to reset their own passwords.

- [Plan an Azure AD self-service password reset deployment](https://docs.microsoft.com/azure/active-directory/authentication/howto-sspr-deployment)

--> 

## <a name="admin-technical-resources-for-mfa-and-secure-sign-ins"></a>Ressources techniques pour l’administrateur pour l’authentification multifacteur et la connexion sécurisée

- [Authentification multifacteur pour Microsoft 365](../admin/security-and-compliance/multi-factor-authentication-microsoft-365.md)
- [Feuille de route relative à l’identité pour Microsoft 365](identity-roadmap-microsoft-365.md)
- [Vidéos de formation d’Azure Academy Azure AD](https://www.youtube.com/watch?v=pN8o0owHfI0&list=PL-V4YVm6AmwUFpC3rXr2i2piRQ708q_ia)
- [Configurer la stratégie d’inscription pour l'authentification multifacteur Azure](https://docs.microsoft.com/azure/active-directory/identity-protection/howto-identity-protection-configure-mfa-policy)
- [Configurations des identités et de l’accès aux appareils](microsoft-365-policies-configurations.md)

