---
title: Azure Active Directory guides d’installation
ms.author: Kwekua
author: Kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
description: Découvrez les guides de configuration pour Azure Active Directory.
ms.openlocfilehash: 059890bd6a79ced1f7121e973b070790dffd8db9
ms.sourcegitcommit: 601ab9ad2b624e3b5e04eed927a08884c885c72a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2022
ms.locfileid: "64403608"
---
# <a name="azure-active-directory-setup-guides"></a>Azure Active Directory guides d’installation

Azure Active Directory (Azure AD) vous aident à gérer et à sécuriser votre organisation. Ces guides de configuration vous aideront à intégrer ces fonctionnalités de manière simple. Dans les sections suivantes, nous allons brièvement décrire les guides d’installation et partager des liens vers les guides.

## <a name="who-are-these-setup-guides-for"></a>Qui ces guides d’installation sont-ils là pour ?

Ces guides de configuration sont conçus pour les petites et moyennes organisations qui n’ont généralement pas d’équipe d’identité dédiée. Vous n’avez pas besoin d’être un expert en identité pour les utiliser.

## <a name="what-to-expect-and-what-youll-need"></a>Ce à quoi vous devez vous attendre et ce dont vous aurez besoin

Les guides d’installation vous aident à configurer les fonctionnalités de base de Azure AD. Si vous devez configurer une configuration plus avancée, le guide d’installation vous pointe vers l’emplacement approprié dans Azure AD portail.

### <a name="required-permissions"></a>Autorisations requises

Vous devez être membre des rôles d’administration suivants :

- Administrateur général : vous permet d’utiliser des outils intégrés dans les guides d’installation pour apporter des modifications dans Microsoft 365 organisation.

- Lecteur global : vous permet d’afficher les guides d’installation sans apporter de modifications à votre client.

## <a name="identity-security-for-teams"></a>Sécurité des identités pour Teams

Azure Active Directory (Azure AD) est notre service de gestion des identités et des accès basé sur le cloud, qui permet à vos employés de se connecter et d’accéder aux applications et services.
Ce catalogue contient certaines fonctionnalités de sécurité de base que vous pouvez utiliser pour vous assurer que vos utilisateurs sont en sécurité et qu’ils ont le temps le plus productif d’utiliser Teams.

### <a name="licensing"></a>Licences

Une Azure Active Directory P2 est nécessaire pour utiliser les fonctionnalités de sécurité de ce catalogue.

[Ouvrir la sécurité d’identité pour Teams catalogue](https://aka.ms/teamsidentity)

## <a name="azure-active-directory-deployment"></a>Azure Active Directory déploiement  

Le Azure Active Directory de configuration vous aidera à configurer les fonctionnalités de Azure AD les plus courantes dans l’ordre recommandé. Le guide d’installation est divisé en trois sections : **Initial**, **Core** et **Advanced**. Chaque section recommande un ensemble de fonctionnalités que vous devez activer.

Les guides d’installation contiennent une liste de contrôle des tâches que vous devez effectuer et vous pouvez suivre votre progression au fil des guides. Les guides sont également des liens vers les autres guides d’installation si nécessaire.

[Ouvrez le guide Azure Active Directory configuration.](https://go.microsoft.com/fwlink/p/?linkid=2183427)

## <a name="add-or-sync-users-to-your-microsoft-account"></a>Ajouter ou synchroniser des utilisateurs à votre compte Microsoft  

Ce guide vous aide à configurer la configuration des comptes d’utilisateurs dans Azure et Microsoft 365. En fonction de votre environnement et de vos besoins, vous pouvez choisir d’ajouter des utilisateurs individuellement, de migrer votre annuaire local avec Azure AD synchronisation ou Azure AD Connecter cloud, ou de résoudre les problèmes de synchronisation existants.

### <a name="licensing"></a>Licences

L Azure Active Directory outils de synchronisation est gratuit et inclus dans tous les abonnements Microsoft 365 de synchronisation.

[Ouvrez le guide de configuration Ajouter ou synchroniser des utilisateurs](https://go.microsoft.com/fwlink/?linkid=2183349).

## <a name="add-a-cloud-app-to-microsoft-365"></a>Ajouter une application cloud à Microsoft 365 

Ce guide est conçu pour vous aider à ajouter des applications cloud à Microsoft 365. Dans notre guide, vous pouvez ajouter une application à votre client, ajouter des utilisateurs à l’application, attribuer des rôles, etc.  Si l’application prend en charge Sign-On (SSO), nous vous aiderons également dans cette configuration.

### <a name="licensing"></a>Licences

Chaque abonnement payant à Microsoft 365 est livré avec un abonnement gratuit à Azure AD. Vous pouvez utiliser Azure AD pour gérer vos applications et créer et gérer des comptes d’utilisateurs et de groupes.

[Ouvrir le guide d’installation Ajouter une application cloud Microsoft 365 de configuration](https://aka.ms/AzureAppSetup)

## <a name="azure-self-service-password-reset-sspr-guide"></a>Guide de réinitialisation du mot de passe Azure Self-Service (SSPR)

Ce guide de configuration est conçu pour vous aider à activer et configurer la réinitialisation du mot de passe en libre-service. Le guide de configuration vous guide à travers les options recommandées, y compris les notifications d’écriture et d’administration de mot de passe.

### <a name="licensing"></a>Licences

SSPR nécessite l’une des licences suivantes :

- Azure Active Directory P1 ou P2

- Microsoft 365 Business Premium

- Microsoft 365 Entreprise E3 ou E5  

- Enterprise Mobility and Security E3 ou E5

[Ouvrez le guide de configuration de la réinitialisation du mot de passe en libre-service](https://go.microsoft.com/fwlink/p/?linkid=2183284).

## <a name="multi-factor-authentication-mfa"></a>Authentification multifacteur (MFA)

Ce guide fournit l’état actuel de l’mf et aide les administrateurs informatiques à sélectionner la meilleure option mfa qui répond aux besoins de leur organisation. Nous vous aidons ensuite à configurer et à appliquer la méthode MFA sélectionnée pour l’organisation.

### <a name="licensing"></a>Licences

L’accès conditionnel nécessite une licence Azure Active Directory P1 ou P2, les paramètres de sécurité par défaut et l’mf par utilisateur sont gratuits et inclus dans tous Microsoft 365 abonnements.

[Ouvrir le guide d’authentification multifacteur (MFA)](https://go.microsoft.com/fwlink/?linkid=2183506)

## <a name="the-passwordless-setup-guide"></a>Guide de configuration sans mot de passe

Le guide de configuration sans mot de passe est conçu pour vous aider à déterminer la meilleure méthode sans mot de passe pour votre environnement. Les méthodes incluent les clés de sécurité, Windows Hello entreprise et l’Microsoft Authenticator app. Si la recommandation est Windows Hello entreprise, une section vous guide à travers les différentes options. Le guide vous pose des questions pour vous aider à élaborer un plan pas à pas.

### <a name="licensing"></a>Licences

Chaque abonnement payant à Microsoft 365 est livré avec un abonnement gratuit à Azure AD. Vous pouvez utiliser Azure AD pour gérer vos applications et créer et gérer des comptes d’utilisateurs et de groupes.

[Ouvrez le guide de configuration sans mot de passe](https://go.microsoft.com/fwlink/?linkid=2183427).
