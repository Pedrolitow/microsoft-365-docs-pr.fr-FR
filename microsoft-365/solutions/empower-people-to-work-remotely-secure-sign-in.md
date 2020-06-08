---
title: Étape 1. Augmenter la sécurité de connexion pour les travailleurs à distance à l’aide d’une authentification multifacteur (MFA)
f1.keywords:
- NOCSH
author: JoeDavies-MSFT
ms.author: josephd
manager: laurawi
ms.date: 05/20/2020
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
localization_priority: Priority
ms.collection:
- M365-security-compliance
- Strat_O365_Enterprise
- remotework
- M365solutions
ms.custom: ''
description: Demander à vos employés à distance de se connecter à l’aide de l’authentification multifacteur (MFA).
ms.openlocfilehash: 142f4d42715ae53e411f045f4df09471b7ba63da
ms.sourcegitcommit: 9195c83c725a7e6ed395ce0253304da54e2195f0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "44560410"
---
# <a name="step-1-increase-sign-in-security-for-remote-workers-with-mfa"></a>Étape 1. Augmenter la sécurité de connexion pour les travailleurs à distance à l’aide d’une authentification multifacteur (MFA)

Pour renforcer la sécurité des connexions de vos employés à distance, utilisez l’authentification multifacteur (MFA). L’authentification multifacteur exige que les connexions des utilisateurs fassent l’objet d’une vérification supplémentaire, au-delà du mot de passe du compte d’utilisateur. Même si un utilisateur malveillant détermine un mot de passe de compte d’utilisateur, il doit également répondre à une vérification supplémentaire, par exemple, un message texte envoyé vers un smartphone, avant que l’accès ne lui soit accordé.

![Le mot de passe correct et une vérification supplémentaire génèrent une connexion réussie](../media/empower-people-to-work-remotely/remote-workers-mfa.png)

Pour tous les utilisateurs, y compris les employés à distance et les administrateurs en particulier, Microsoft recommande vivement l’authentification multifacteur.

Trois méthodes s’offrent à vous pour obliger vos utilisateurs à utiliser l’authentification multifacteur basée sur votre offre Microsoft 365.

|Planification  |Recommandation  |
|---------|---------|
|Toutes les offres Microsoft 365 (sans licence Azure AD Premium P1 ou P2)     |[Activer les paramètres de sécurité par défaut dans Azure AD](https://docs.microsoft.com/azure/active-directory/fundamentals/concept-fundamentals-security-defaults). La sécurité par défaut d’Azure AD inclut l’authentification multifacteur pour les utilisateurs et les administrateurs.   |
|Microsoft 365 E3 (inclut les licences Azure AD Premium P1)     | Utilisez les [Stratégies d’accès conditionnel courantes](https://docs.microsoft.com/azure/active-directory/conditional-access/concept-conditional-access-policy-common) pour configurer les stratégies suivantes : <br>- [Exiger l’authentification multifacteur pour les administrateurs](https://docs.microsoft.com/azure/active-directory/conditional-access/howto-conditional-access-policy-admin-mfa) <br>- [Exiger l’authentification multifacteur pour tous les utilisateurs](https://docs.microsoft.com/azure/active-directory/conditional-access/howto-conditional-access-policy-all-users-mfa) <br> - [Bloquer l’authentification héritée](https://docs.microsoft.com/azure/active-directory/conditional-access/howto-conditional-access-policy-block-legacy)       |
|Microsoft 365 E5 (inclut les licences Azure AD Premium P2)     | Pour tirer parti de la protection d’identité Azure AD Identity Protection, commencez à implémenter la [série recommandée concernant l’accès conditionnel et les stratégies associées](../enterprise/identity-access-policies.md) en créant les deux stratégies suivantes :<br> - [Exiger l’authentification multifacteur lorsque le risque de connexion est moyen ou élevé](../enterprise/identity-access-policies.md#require-mfa-based-on-sign-in-risk) <br>- [Bloquer les clients ne prenant pas en charge l’authentification moderne](../enterprise/identity-access-policies.md#block-clients-that-dont-support-modern-authentication)<br>- [Les utilisateurs à risque élevé doivent modifier leur mot de passe](../enterprise/identity-access-policies.md#high-risk-users-must-change-password)       |
| | |

## <a name="security-defaults"></a>Paramètres de sécurité par défaut

Les paramètres de sécurité par défaut sont une nouvelle fonctionnalité pour Microsoft 365 et les abonnements Office 365 payants ou en version d’évaluation créés après le 21 octobre 2019. Les paramètres de sécurité par défaut de ces abonnements sont activés, ce qui ***nécessite que tous vos utilisateurs utilisent l’authentification multifacteur à l’aide de l’application Microsoft Authenticator***.
 
Les utilisateurs disposent de 14 jours pour s’inscrire à l’authentification multifacteur de l’application Microsoft Authenticator sur leur smartphone, un délai qui commence dès la première connexion suivant l’activation des paramètres de sécurité par défaut. Lorsque les 14 jours sont écoulés, l’utilisateur ne peut pas se connecter tant que son inscription à l’authentification multifacteur n’est pas terminée.

Les paramètres de sécurité par défaut garantissent que toutes les organisations ont un niveau de sécurité de base qui est activé par défaut pour la connexion des utilisateurs. Vous pouvez désactiver les paramètres de sécurité par défaut en faveur de l’authentification multifacteur avec des stratégies d’accès conditionnel ou pour des comptes individuels.

Pour plus d’informations, voir[Vue d’ensemble des paramètres de sécurité par défaut](https://docs.microsoft.com/azure/active-directory/fundamentals/concept-fundamentals-security-defaults).

## <a name="conditional-access-policies"></a>Stratégies d’accès conditionnel

Les stratégies d’accès conditionnel sont un groupe de règles qui spécifient les conditions dans lesquelles les connexions sont évaluées et autorisées. Par exemple, vous pouvez créer une stratégie d’accès conditionnel qui indique :

- Si le nom du compte d’utilisateur concerne membre d’un groupe d’utilisateurs bénéficiant des rôles d’administrateur Exchange, utilisateur, mot de passe, sécurité, SharePoint ou global, exigez l’authentification multifacteur avant d’autoriser l’accès.

Cette stratégie vous permet de demander une authentification multifacteur basée sur l’appartenance au groupe, plutôt que d’essayer de configurer des comptes d’utilisateur individuels pour l’authentification multifacteur lorsqu’ils sont attribués ou non à des rôles d’administrateur.

Vous pouvez également utiliser les stratégies d’accès conditionnel pour des fonctionnalités plus avancées, telles que la nécessité de se connecter à partir d’un appareil compatible, tel que votre ordinateur portable fonctionnant sous Windows 10.

Les licences d’accès conditionnel exige Azure AD Premium P1, lesquelles sont incluses dans Microsoft 365 E3 et E5.

Si vous souhaitez en savoir plus, consultez [Présentation de l’accès conditionnel](https://docs.microsoft.com/azure/active-directory/conditional-access/overview).

## <a name="azure-ad-identity-protection-support"></a>Prise en charge d’Azure AD Identity Protection

Avec Azure AD Identity Protection, vous pouvez créer une stratégie d’accès conditionnel supplémentaire qui indique :

- Si une connexion est considéré comme présentant un risque moyen ou élevé, exigez l’authentification multifacteur.

Les licences Azure AD Identity Protection exige Azure AD Premium P2, lesquelles sont incluses dans Microsoft 365 E5.

Pour en savoir plus, consultez l'article [Accès conditionnel basé sur les risques](https://docs.microsoft.com/azure/active-directory/conditional-access/howto-conditional-access-policy-risk#require-mfa-medium-or-high-sign-in-risk-users).

## <a name="using-these-methods-together"></a>Utilisation combinée des méthodes

Gardez les éléments suivants à l’esprit :

- Vous ne pouvez pas activer les paramètres de sécurité par défaut si vous avez activé des stratégies d’accès conditionnel.
- Vous ne pouvez pas activer de stratégie d’accès conditionnel si les paramètres de sécurité par défaut sont activés.

Si les paramètres de sécurité par défaut sont activés, les nouveaux utilisateurs sont invités à s’inscrire pour l’authentification multifacteur et à utiliser l’application Microsoft Authenticator. 

Ce tableau présente les résultats de l’activation de l’authentification multifacteur avec les paramètres de sécurité par défaut et les stratégies d’accès conditionnel.

|| Activé | Désactivé | Méthode d'authentification supplémentaire |
|:-------|:-----|:-------|:-------|
| **Paramètres de sécurité par défaut**  | Ne peut pas utiliser les stratégies d’accès conditionnel | Peut utiliser les stratégies d’accès conditionnel | Application Microsoft Authenticator |
| **Stratégies d’accès conditionnel** | Si l’une d’elles est activée, vous ne pouvez pas activer les paramètres de sécurité par défaut | Si tous ces éléments sont désactivés, vous pouvez activer les paramètres de sécurité par défaut  | Utilisateur spécifié lors de l’inscription à l’authentification multifacteur  |
||||

## <a name="let-your-users-reset-their-own-passwords"></a>Autoriser vos utilisateurs à réinitialiser leur mot de passe

La Réinitialisation des mots de passe libre-service (SSPR) permet aux utilisateurs de réinitialiser leur mot de passe sans avoir de conséquence pour le personnel informatique. Les utilisateurs peuvent rapidement réinitialiser leur mot de passe à tout moment et n’importe où. Regardez [cette vidéo](https://go.microsoft.com/fwlink/?linkid=2128524) pour configurer la Réinitialisation des mots de passe libre-service.

## <a name="admin-technical-resources-for-mfa-and-identity"></a>Ressources techniques pour l’administrateur pour l’authentification multifacteur et l’identité

- [Authentification multifacteur pour Microsoft 365](https://docs.microsoft.com/microsoft-365/admin/security-and-compliance/multi-factor-authentication-microsoft-365)
- [Les 5 principales façons dont Azure AD peut vous aider pour activer le travail à distance](https://techcommunity.microsoft.com/t5/azure-active-directory-identity/top-5-ways-your-azure-ad-can-help-you-enable-remote-work/ba-p/1144691)
- [Planifier et déployer votre infrastructure d’identités de Microsoft 365](https://docs.microsoft.com/microsoft-365/enterprise/identity-infrastructure?view=o365-worldwide#plan-and-deploy-your-microsoft-365-enterprise-identity-infrastructure)
- [Vidéos de formation d’Azure Academy Azure AD](https://www.youtube.com/watch?v=pN8o0owHfI0&list=PL-V4YVm6AmwUFpC3rXr2i2piRQ708q_ia)
- [Configurer la stratégie d’inscription pour l'authentification multifacteur Azure](https://docs.microsoft.com/azure/active-directory/identity-protection/howto-identity-protection-configure-mfa-policy)
- [Planifier le déploiement de la réinitialisation de mot de passe en libre-service Azure AD](https://docs.microsoft.com/azure/active-directory/authentication/howto-sspr-deployment)

## <a name="results-of-step-1"></a>Résultats de l’étape 1

Après le déploiement de l'authentification multifacteur, vos utilisateurs :

- Ont l’obligation d’utiliser l’authentification multifacteur pour les connexions.
- Ont terminé le processus d’inscription à l’authentification multifacteur et utilisent l’authentification multifacteur pour toutes le connexions.
- Peuvent utiliser la Réinitialisation des mots de passe libre-service pour réinitialiser leur mot de passe.

## <a name="next-step"></a>Étape suivante

Passez à l’[Étape 2](empower-people-to-work-remotely-remote-access.md) pour fournir l’accès à distance aux applications et services locaux.
