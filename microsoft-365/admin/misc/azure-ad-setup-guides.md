---
title: Guides d’installation d’Azure Active Directory
ms.author: Kwekua
author: Kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: microsoft-365-business
ms.localizationpriority: medium
ms.collection:
- Tier3
- scotvorg
description: Découvrez les guides d’installation pour Azure Active Directory.
ms.openlocfilehash: df54d2218e40fa6b184399c33b8e53f614b843e6
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68734250"
---
# <a name="azure-active-directory-setup-guides"></a>Guides d’installation d’Azure Active Directory

Les fonctionnalités Azure Active Directory (Azure AD) vous aident à gérer et à sécuriser votre organisation. Ces guides de configuration vous aideront à intégrer ces fonctionnalités de manière simple. Dans les sections suivantes, nous allons décrire brièvement les guides d’installation et partager des liens vers les guides.

## <a name="who-are-these-setup-guides-for"></a>À qui sont destinés ces guides d’installation ?

Ces guides de configuration sont conçus pour les petites et moyennes organisations qui n’ont généralement pas d’équipe d’identité dédiée. Vous n’avez pas besoin d’être un expert en identité pour les utiliser.

## <a name="what-to-expect-and-what-youll-need"></a>Ce à quoi vous devez vous attendre et ce dont vous aurez besoin

Les guides d’installation vous aident à configurer les fonctionnalités de base d’Azure AD. Si vous devez configurer une configuration plus avancée, le guide d’installation vous dirigera vers l’emplacement approprié dans le portail Azure AD.

### <a name="required-permissions"></a>Autorisations requises

Vous devez être membre des rôles d’administration suivants :

- Administrateur général : vous permet d’utiliser des outils intégrés dans les guides d’installation pour apporter des modifications à votre organisation Microsoft 365.

- Lecteur global : vous permet d’afficher les guides d’installation, mais pas d’apporter de modifications dans votre locataire.

## <a name="identity-security-for-teams"></a>Sécurité des identités pour Teams

Azure Active Directory (Azure AD) est notre service cloud de gestion des identités et des accès, qui permet à vos employés de se connecter et d’accéder aux applications et services.
Ce catalogue contient certaines fonctionnalités de sécurité de base que vous pouvez utiliser pour garantir que vos utilisateurs sont en sécurité et disposent du temps le plus productif à l’aide de Teams.

### <a name="licensing"></a>Licences

Une licence Azure Active Directory P2 est nécessaire pour utiliser les fonctionnalités de sécurité de ce catalogue.

[Ouvrir le catalogue Identity Security for Teams](https://portal.office.com/AdminPortal/home?Q=azuredocs#/teamsidentity)

## <a name="identity-governance"></a>Gouvernance des identités

Ce catalogue de l’Assistant est conçu pour aider les clients à utiliser les fonctionnalités Azure Active Directory P2, notamment les révisions d’accès (AR), les Privileged Identity Management (PIM) et la gestion des droits d’utilisation (ELM). Pour PIM et ELM, nous proposons une liste organisée de documents et un pointeur vers le centre d’administration Azure Active Directory, où l’administrateur peut configurer cette fonctionnalité. Pour la réalité augmentée, nous offrons une expérience entièrement automatisée qui permet aux administrateurs de choisir parmi deux modèles. Ces modèles incluent un qui permet aux propriétaires de groupes d’approuver l’utilisation des invités dans tous les groupes Microsoft 365. Il s’agit d’une stratégie principale que les clients utilisent aujourd’hui.  

Ensuite, nous proposons un modèle de test, dans lequel l’administrateur est le réviseur des invités pour un groupe spécifique qu’il choisit. Si le locataire dispose déjà d’une révision qui couvre tous les utilisateurs invités des groupes Microsoft 365, l’administrateur est dirigé vers le Centre d’administration Azure Active Directory pour gérer la révision existante et il n’y aura aucune expérience automatisée.

[Ouvrir le guide de configuration de la gouvernance des identités](https://admin.microsoft.com/adminportal/home?Q=azuredocs#/modernonboarding/identitygovernance)

> [!NOTE]
> Une licence Azure Active Directory P2 est nécessaire pour utiliser les fonctionnalités de sécurité de ce catalogue.

## <a name="azure-active-directory-deployment"></a>Déploiement Azure Active Directory  

Le guide de configuration d’Azure Active Directory vous aidera à configurer les fonctionnalités Azure AD les plus courantes dans un ordre recommandé. Le guide de configuration est divisé en trois sections : **Initial**, **Core** et **Avancé**. Chaque section recommande un ensemble de fonctionnalités que vous devez activer.

Les guides d’installation contiennent une liste de contrôle des tâches que vous devez effectuer et vous pouvez suivre votre progression à mesure que vous parcourez les guides. Les guides sont également liés aux autres repères d’installation si nécessaire.

[Ouvrez le guide d’installation d’Azure Active Directory](https://admin.microsoft.com/adminportal/home?Q=azuredocs#/modernonboarding/azureadsetup).

## <a name="add-or-sync-users-to-your-microsoft-account"></a>Ajouter ou synchroniser des utilisateurs à votre compte Microsoft  

Ce guide vous aide à configurer la configuration des comptes d’utilisateur dans Azure et Microsoft 365. En fonction de votre environnement et de vos besoins, vous pouvez choisir d’ajouter des utilisateurs individuellement, de migrer votre annuaire local avec Azure AD Cloud Sync ou Azure AD Connect, ou de résoudre les problèmes de synchronisation existants.

### <a name="licensing"></a>Licences

L’utilisation des outils de synchronisation Azure Active Directory est gratuite et incluse dans tous les abonnements Microsoft 365.

[Ouvrez le guide de configuration Ajouter ou synchroniser des utilisateurs](https://admin.microsoft.com/adminportal/home?Q=azuredocs#/modernonboarding/identitywizard).

## <a name="secure-your-cloud-apps-with-single-sign-on-sso"></a>Sécuriser vos applications cloud avec l’authentification unique (SSO)

Ce guide est conçu pour vous aider à ajouter des applications cloud à Microsoft 365. Dans notre guide, vous pouvez ajouter une application à votre locataire, ajouter des utilisateurs à l’application, attribuer des rôles, etc.  Si l’application prend en charge l'Sign-On authentification unique (SSO), nous allons également vous guider tout au long de cette configuration.

### <a name="licensing"></a>Licences

Chaque abonnement payant à Microsoft 365 est fourni avec un abonnement gratuit à Azure AD. Vous pouvez utiliser Azure AD pour gérer vos applications et créer et gérer des comptes d’utilisateur et de groupe.

[Ouvrez le guide de configuration Ajouter une application cloud à Microsoft 365](https://portal.office.com/AdminPortal/home?Q=azuredocs#/azureadappintegration)

## <a name="azure-self-service-password-reset-sspr-guide"></a>Guide de réinitialisation de mot de passe Azure Self-Service (SSPR)

Ce guide d’installation est conçu pour vous aider à activer et configurer la réinitialisation de mot de passe en libre-service. Le guide d’installation vous guidera dans les options recommandées, notamment la réécriture du mot de passe et les notifications d’administrateur.

### <a name="licensing"></a>Licences

SSPR nécessite l’une des licences suivantes :

- Azure Active Directory P1 ou P2

- Microsoft 365 Business Premium

- Microsoft 365 Entreprise E3 ou E5  

- Enterprise Mobility and Security E3 ou E5

[Ouvrez le guide de configuration de la réinitialisation de mot de passe en libre-service](https://admin.microsoft.com/adminportal/home?Q=azuredocs#/modernonboarding/ssprsetup).

## <a name="multi-factor-authentication-mfa"></a>Authentification multifacteur (MFA)

Ce guide fournit l’état actuel de l’authentification multifacteur et aide les administrateurs informatiques à sélectionner la meilleure option MFA qui répond aux exigences de leur organisation. Ensuite, nous vous aidons à configurer et à appliquer la méthode MFA sélectionnée pour l’organisation.

### <a name="licensing"></a>Licences

L’accès conditionnel nécessite une licence Azure Active Directory P1 ou P2, les paramètres de sécurité par défaut et l’authentification multifacteur par utilisateur sont gratuits et inclus dans tous les abonnements Microsoft 365.

[Ouvrir le guide de l’authentification multifacteur (MFA)](https://admin.microsoft.com/adminportal/home?Q=azuredocs#/modernonboarding/mfasetupguide)

## <a name="the-passwordless-setup-guide"></a>Guide de configuration sans mot de passe

Le guide de configuration sans mot de passe est conçu pour vous aider à déterminer la meilleure méthode sans mot de passe pour votre environnement. Les méthodes incluent les clés de sécurité, les Windows Hello Entreprise et l’application Microsoft Authenticator. Si la recommandation est Windows Hello Entreprise, il existe une section pour vous guider dans les différentes options. Le guide vous pose des questions pour vous aider à élaborer un plan pas à pas.

### <a name="licensing"></a>Licences

Chaque abonnement payant à Microsoft 365 est fourni avec un abonnement gratuit à Azure AD. Vous pouvez utiliser Azure AD pour gérer vos applications et créer et gérer des comptes d’utilisateur et de groupe.

[Ouvrez le guide d’installation sans mot de passe](https://admin.microsoft.com/adminportal/home?Q=azuredocs#/modernonboarding/passwordlesssetup).
