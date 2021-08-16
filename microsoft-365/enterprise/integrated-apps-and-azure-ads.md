---
title: Applications intégrées et Azure AD pour Microsoft 365 administrateurs
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
ms.collection: M365-subscription-management
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: cb2250e3-451e-416f-bf4e-363549652c2a
description: Découvrez comment inscrire et administrer Office 365 applications intégrées dans Azure AD, en permettant des autorisations d’application au niveau de l’administrateur général.
ms.openlocfilehash: f604260646aa4e6793540003346c9e83d7a6b269
ms.sourcegitcommit: e269371de759a1a747c9f292775463aa11415f25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/16/2021
ms.locfileid: "58354223"
---
# <a name="integrated-apps-and-azure-ad-for-microsoft-365-administrators"></a>Applications intégrées et Azure AD pour Microsoft 365 administrateurs

La gestion des applications intégrées n’est pas seulement la gestion [du consentement de l’utilisateur pour les applications.](../admin/misc/user-consent.md) Avec l’avènement des API REST Microsoft 365, les utilisateurs peuvent accorder aux applications l’accès à leurs données Microsoft 365, telles que la messagerie, les calendriers, les contacts, les utilisateurs, les groupes, les fichiers et les dossiers. Par défaut, les utilisateurs doivent accorder individuellement des autorisations à chaque application. 

Toutefois, cette mise à l’échelle n’est pas bonne si vous souhaitez autoriser une application une fois au niveau de l’administrateur général et la déployer dans l’ensemble de votre organisation via le lanceur d’applications. Pour ce faire, vous devez inscrire l’application dans Azure Active Directory (Azure AD). Vous devez suivre certaines étapes avant de pouvoir inscrire une application dans Azure AD, ainsi que des informations d’arrière-plan qui peuvent vous aider à gérer les applications de votre organisation Microsoft 365.
  
## <a name="azure-ad-resources-for-microsoft-365-admins"></a>Ressources Azure AD pour Microsoft 365 administrateurs

Vous devez effectuer ces deux tâches avant de pouvoir gérer vos applications Microsoft 365 dans Azure AD.
  
|Conditions préalables|Commentaires|
|:-----|:-----|
|[Utiliser votre abonnement Azure AD gratuit](../compliance/use-your-free-azure-ad-subscription-in-office-365.md) <br/> |Chaque abonnement payant à Microsoft 365 est fourni avec un abonnement gratuit à Azure AD. Vous pouvez utiliser Azure AD pour gérer vos applications et pour créer et gérer des comptes d’utilisateur et de groupe. Pour utiliser Azure AD, il vous suffit d’aller sur le portail Azure et de vous y Microsoft 365 [https://portal.azure.com](https://portal.azure.com) compte.  <br/> |
|[Gérer le consentement des utilisateurs aux applications](../admin/misc/user-consent.md) <br/> |Vous devez gérer le consentement des utilisateurs aux applications pour autoriser les applications tierces à accéder aux informations d’Microsoft 365 utilisateur et pour vous permettre d’inscrire des applications dans Azure AD. Une application tierce peut, par exemple, demander l'autorisation d'accéder au calendrier de l'utilisateur et de modifier les fichiers présents dans un dossier OneDrive.  <br/> |
   
Pour gérer Microsoft 365 applications, vous devez connaître les applications dans Azure AD. Utilisez ces articles pour vous donner l’arrière-plan dont vous avez besoin.
  
|Article|Commentaires|
|:-----|:-----|
|[Meet the Microsoft 365 app launcher](https://support.microsoft.com/office/meet-the-microsoft-365-app-launcher-79f12104-6fed-442f-96a0-eb089a3f476a) <br/> |Si vous débutez dans le lanceur d’applications, vous vous demandez peut-être ce qu’il est et comment l’utiliser. Le lanceur d’applications est conçu pour vous aider à vous rendre à vos applications n’importe où dans Microsoft 365.  <br/> |
|[présentation Office 365 API de gestion des Office 365](/office/office-365-management-api/office-365-management-apis-overview) <br/> |Les API de gestion Microsoft 365 vous permettent d’accéder à vos données Microsoft 365, y compris les éléments qui les intéressent le plus :courrier, calendriers, contacts, utilisateurs et groupes, fichiers et dossiers. <br/> |
|[Intégration d’applications dans Azure AD](/azure/active-directory/develop/quickstart-v1-add-azure-ad-app) <br/> | Découvrez les applications qui sont intégrées à Azure AD, et comment inscrire votre application, comprendre les concepts sous-tels qu’une application inscrite et en savoir plus sur les instructions de branding pour les applications multi-locataires.  <br/> |
|[Ajouter des vignettes personnalisées au lanceur d’applications](/office365/admin/manage/customize-the-app-launcher)  <br/> |Le lanceur d’applications dans Microsoft 365 permet aux utilisateurs de trouver et d’accéder plus facilement à leurs applications. Cet article décrit comment, en tant que développeur, vous pouvez faire apparaître vos applications dans les lanceurs d’applications des utilisateurs et leur offrir une expérience d' sign-on unique (SSO) à l’aide de leurs informations d’identification Microsoft 365.  <br/> |
|[Didacticiels d’intégration Azure AD](/azure/active-directory/saas-apps/tutorial-list) <br/> |L’objectif de ces didacticiels est de vous montrer comment configurer Azure AD SSO pour des applications SaaS tierces.  <br/> |
|[Scénarios d’authentification pour Azure AD](/azure/active-directory/develop/authentication-vs-authorization) <br/> |Azure AD simplifie l’authentification pour les développeurs en fournissant l’identité en tant que service, avec la prise en charge des protocoles standard tels que OAuth 2.0 et OpenID Connecter, ainsi que des bibliothèques open source pour différentes plateformes pour vous aider à démarrer rapidement le codage. Ce document vous aide à comprendre les différents scénarios pris en charge par Azure AD et vous montre comment commencer.  <br/> |
|[Accès aux applications](/azure/active-directory/manage-apps/what-is-access-management) <br/> |Azure AD permet une intégration facile à de nombreuses applications SaaS (Software as a Service) les plus populaires d’aujourd’hui. Il fournit la gestion des identités et des accès, et fournit un panneau d’accès aux utilisateurs qui leur permet de découvrir l’accès aux applications dont ils disposent et où ils peuvent utiliser l' utilisateur unique pour accéder à leurs applications. Cet article vous fournit des liens vers les ressources associées qui vous permettent d’en savoir plus sur les améliorations apportées à l’accès aux applications pour Azure AD et sur la façon dont vous pouvez y contribuer.  <br/> |
|[Personnaliser votre expérience Office 365 personnalisée](https://support.microsoft.com/office/personalize-your-office-365-experience-eb34a21b-52fa-4fbf-a8d5-146132242985) <br/> |Vous pouvez accéder rapidement aux applications que vous utilisez quotidiennement en ajoutant ou en supprimant des applications dans le lanceur d Microsoft 365 applateur.  <br/> |