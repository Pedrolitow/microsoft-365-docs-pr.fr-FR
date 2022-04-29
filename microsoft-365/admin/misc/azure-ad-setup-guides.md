---
title: guides d’installation Azure Active Directory
ms.author: Kwekua
author: Kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
description: Découvrez les guides d’installation pour Azure Active Directory.
ms.openlocfilehash: 58f7ed9a20580db742a773cb8a7874137f0cfc4c
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/29/2022
ms.locfileid: "65128409"
---
# <a name="azure-active-directory-setup-guides"></a>guides d’installation Azure Active Directory

Azure Active Directory fonctionnalités (Azure AD) vous aident à gérer et à sécuriser votre organisation. Ces guides d’installation vous aideront à intégrer ces fonctionnalités de manière simple. Dans les sections suivantes, nous allons décrire brièvement les guides d’installation et partager des liens vers les guides.

## <a name="who-are-these-setup-guides-for"></a>Qui ces guides d’installation sont-ils adaptés ?

Ces guides d’installation sont conçus pour les petites et moyennes organisations qui ne disposent généralement pas d’une équipe d’identité dédiée. Vous n’avez pas besoin d’être expert en identité pour les utiliser.

## <a name="what-to-expect-and-what-youll-need"></a>À quoi vous attendre et ce dont vous aurez besoin

Les guides d’installation vous aident à configurer les fonctionnalités principales de Azure AD. Si vous devez configurer une configuration plus avancée, le guide d’installation vous dirige vers l’emplacement approprié dans le portail Azure AD.

### <a name="required-permissions"></a>Autorisations requises

Vous devez être membre des rôles d’administration suivants :

- Administrateur général : vous permet d’utiliser des outils intégrés dans les guides d’installation pour apporter des modifications à votre organisation Microsoft 365.

- Lecteur global : vous permet d’afficher les guides d’installation, mais pas d’apporter des modifications à votre locataire.

## <a name="identity-security-for-teams"></a>Sécurité des identités pour Teams

Azure Active Directory (Azure AD) est notre service de gestion des identités et des accès basé sur le cloud, qui permet à vos employés de se connecter et d’accéder aux applications et services.
Ce catalogue contient certaines fonctionnalités de sécurité de base que vous pouvez utiliser pour garantir la sécurité de vos utilisateurs et avoir le temps le plus productif à l’aide de Teams.

### <a name="licensing"></a>Licences

Une licence Azure Active Directory P2 est nécessaire pour utiliser les fonctionnalités de sécurité de ce catalogue.

[Ouvrir la sécurité d’identité pour Teams catalogue](https://aka.ms/teamsidentity)

## <a name="identity-governance"></a>Gouvernance des identités

Ce catalogue d’Assistants est conçu pour aider les clients à utiliser Azure Active Directory fonctionnalités P2, notamment les révisions d’accès (AR), les Privileged Identity Management (PIM) et la gestion des droits d’utilisation (ELM). Pour PIM et ELM, nous proposons une liste organisée de documents et un pointeur vers le centre d’administration Azure Active Directory, où l’administrateur peut configurer cette fonctionnalité. Pour AR, nous offrons une expérience entièrement automatisée qui permet aux administrateurs de choisir parmi deux modèles. Ces modèles incluent un modèle qui permet aux propriétaires de groupes d’approuver l’utilisation des invités dans tous les groupes Microsoft 365. Il s’agit d’une stratégie de haut niveau que les clients utilisent aujourd’hui.  

Ensuite, nous proposons un modèle de test, où l’administrateur est le réviseur d’invités pour un groupe spécifique qu’il choisit. Si le locataire dispose déjà d’une révision qui couvre tous les utilisateurs invités Microsoft 365 groupes, l’administrateur est pointé vers le centre d’administration Azure Active Directory pour gérer la révision existante et il n’y aura aucune expérience automatisée.

[Ouvrir le guide d’installation de la gouvernance des identités](https://go.microsoft.com/fwlink/p/?linkid=386330)

> [!NOTE]
> Azure Active Directory licence P2 est nécessaire pour utiliser les fonctionnalités de sécurité de ce catalogue.

## <a name="azure-active-directory-deployment"></a>déploiement Azure Active Directory  

Le guide d’installation Azure Active Directory vous aidera à configurer les fonctionnalités de Azure AD les plus courantes dans un ordre recommandé. Le guide d’installation est divisé en trois sections : **Initial**, **Core** et **Advanced**. Chaque section recommande un ensemble de fonctionnalités que vous devez activer.

Les guides d’installation contiennent une liste de vérification des tâches que vous devez effectuer et vous pouvez suivre votre progression à mesure que vous parcourez les guides. Les guides sont également liés aux autres guides d’installation si nécessaire.

[Ouvrez le guide d’installation Azure Active Directory](https://go.microsoft.com/fwlink/p/?linkid=2183427).

## <a name="add-or-sync-users-to-your-microsoft-account"></a>Ajouter ou synchroniser des utilisateurs à votre compte Microsoft  

Ce guide vous aide à configurer la configuration des comptes d’utilisateur dans Azure et Microsoft 365. En fonction de votre environnement et de vos besoins, vous pouvez choisir d’ajouter des utilisateurs individuellement, de migrer votre répertoire local avec Azure AD synchronisation cloud ou Azure AD Connecter, ou de résoudre les problèmes de synchronisation existants.

### <a name="licensing"></a>Licences

L’utilisation des outils de synchronisation Azure Active Directory est gratuite et incluse dans tous les abonnements Microsoft 365.

[Ouvrez le guide d’installation d’Ajouter ou de synchroniser des utilisateurs](https://go.microsoft.com/fwlink/?linkid=2183349).

## <a name="secure-your-cloud-apps-with-single-sign-on-sso"></a>Sécuriser vos applications cloud avec l’authentification unique (SSO)

Ce guide est conçu pour vous aider à ajouter des applications cloud à Microsoft 365. Dans notre guide, vous pouvez ajouter une application à votre locataire, ajouter des utilisateurs à l’application, attribuer des rôles, etc.  Si l’application prend en charge l'Sign-On authentification unique (SSO), nous allons également vous guider dans cette configuration.

### <a name="licensing"></a>Licences

Chaque abonnement payant à Microsoft 365 est fourni avec un abonnement gratuit à Azure AD. Vous pouvez utiliser Azure AD pour gérer vos applications et créer et gérer des comptes d’utilisateurs et de groupes.

[Ouvrir le guide d’installation d’Ajouter une application cloud à Microsoft 365](https://aka.ms/AzureAppSetup)

## <a name="azure-self-service-password-reset-sspr-guide"></a>Guide de réinitialisation de mot de passe Azure Self-Service (SSPR)

Ce guide d’installation est conçu pour vous aider à activer et à configurer la réinitialisation de mot de passe en libre-service. Le guide d’installation vous guide dans les options recommandées, notamment la réécriture du mot de passe et les notifications d’administration.

### <a name="licensing"></a>Licences

SSPR nécessite l’une des licences suivantes :

- Azure Active Directory P1 ou P2

- Microsoft 365 Business Premium

- Microsoft 365 Entreprise E3 ou E5  

- Enterprise Mobilité et sécurité E3 ou E5

[Ouvrez le guide d’installation de la réinitialisation de mot de passe en libre-service](https://go.microsoft.com/fwlink/p/?linkid=2183284).

## <a name="multi-factor-authentication-mfa"></a>Authentification multifacteur (MFA)

Ce guide fournit l’état actuel de l’authentification multifacteur et aide les administrateurs informatiques à sélectionner la meilleure option MFA qui répond aux exigences de leur organisation. Ensuite, nous aidons à configurer et à appliquer la méthode MFA sélectionnée pour l’organisation.

### <a name="licensing"></a>Licences

L’accès conditionnel nécessite une licence P1 ou P2 Azure Active Directory, les paramètres de sécurité par défaut et l’authentification multifacteur par utilisateur sont gratuits et inclus dans tous les abonnements Microsoft 365.

[Ouvrir le guide d’authentification multifacteur (MFA)](https://go.microsoft.com/fwlink/?linkid=2183506)

## <a name="the-passwordless-setup-guide"></a>Guide d’installation sans mot de passe

Le guide d’installation sans mot de passe est conçu pour vous aider à déterminer la meilleure méthode sans mot de passe pour votre environnement. Les méthodes incluent les clés de sécurité, les Windows Hello Entreprise et l’application Microsoft Authenticator. Si la recommandation est Windows Hello Entreprise, une section vous guide dans les différentes options. Le guide vous pose des questions pour vous aider à élaborer un plan pas à pas.

### <a name="licensing"></a>Licences

Chaque abonnement payant à Microsoft 365 est fourni avec un abonnement gratuit à Azure AD. Vous pouvez utiliser Azure AD pour gérer vos applications et créer et gérer des comptes d’utilisateurs et de groupes.

[Ouvrez le guide d’installation sans mot de passe](https://go.microsoft.com/fwlink/?linkid=2183427).
