---
title: Applications intégrées et Administrateurs Azure AD pour Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
audience: Admin
ms.topic: landing-page
ms.service: microsoft-365-enterprise
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
ms.collection:
- scotvorg
- M365-subscription-management
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: cb2250e3-451e-416f-bf4e-363549652c2a
description: Découvrez comment inscrire et administrer Office 365 applications intégrées dans Azure AD, en autorisant les autorisations d’application au niveau **de l’administrateur azure AD DC** ou **de l’administrateur général**.
ms.openlocfilehash: fac21bb980623c0456727593840628aa2753027e
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68208895"
---
# <a name="integrated-apps-and-azure-ad-for-microsoft-365-administrators"></a>Applications intégrées et Administrateurs Azure AD pour Microsoft 365

La gestion des applications intégrées ne se contente pas de [gérer le consentement de l’utilisateur aux applications](../admin/misc/user-consent.md). Avec l’avènement des API REST Microsoft 365, les utilisateurs peuvent accorder aux applications l’accès à leurs données Microsoft 365, telles que la messagerie, les calendriers, les contacts, les utilisateurs, les groupes, les fichiers et les dossiers. Par défaut, les utilisateurs doivent accorder individuellement des autorisations à chaque application. 

Toutefois, cette mise à l’échelle ne fonctionne pas correctement si vous souhaitez autoriser une application une seule fois au niveau **de l’administrateur Azure AD DC** ou **de l’administrateur général** et la déployer dans toute votre organisation via le lanceur d’applications. Pour ce faire, vous devez inscrire l’application dans Azure Active Directory (Azure AD). Vous devez effectuer certaines étapes avant de pouvoir inscrire une application dans Azure AD et des informations générales qui peuvent vous aider à gérer les applications de votre organisation Microsoft 365.
  
## <a name="azure-ad-resources-for-microsoft-365-admins"></a>Ressources Azure AD pour les administrateurs Microsoft 365

Vous devez effectuer ces deux tâches avant de pouvoir gérer vos applications Microsoft 365 dans Azure AD.
  
|Configuration requise|Comments|
|:-----|:-----|
|[Utiliser votre abonnement Azure AD gratuit](../compliance/use-your-free-azure-ad-subscription-in-office-365.md) <br/> |Chaque abonnement payant à Microsoft 365 est fourni avec un abonnement gratuit à Azure AD. Vous pouvez utiliser Azure AD pour gérer vos applications et créer et gérer des comptes d’utilisateurs et de groupes. Pour utiliser Azure AD, accédez simplement à la Portail Azure [https://portal.azure.com](https://portal.azure.com) et connectez-vous à l’aide de votre compte Microsoft 365.  <br/> |
|[Gérer le consentement de l’utilisateur aux applications](../admin/misc/user-consent.md) <br/> |Vous devez gérer le consentement de l’utilisateur aux applications pour permettre aux applications tierces d’accéder aux informations microsoft 365 utilisateur et pour vous permettre d’inscrire des applications dans Azure AD. Une application tierce peut, par exemple, demander l'autorisation d'accéder au calendrier de l'utilisateur et de modifier les fichiers présents dans un dossier OneDrive.  <br/> |
   
Pour gérer les applications Microsoft 365, vous devez connaître les applications dans Azure AD. Utilisez ces articles pour vous donner l’arrière-plan dont vous avez besoin.
  
|Article|Comments|
|:-----|:-----|
|[Rencontrez le lanceur d’applications Microsoft 365](https://support.microsoft.com/office/meet-the-microsoft-365-app-launcher-79f12104-6fed-442f-96a0-eb089a3f476a) <br/> |Si vous débutez avec le lanceur d’applications, vous vous demandez peut-être ce qu’il est et comment l’utiliser. Le lanceur d’applications est conçu pour vous aider à accéder à vos applications n’importe où dans Microsoft 365.  <br/> |
|[Vue d’ensemble des API de gestion Office 365](/office/office-365-management-api/office-365-management-apis-overview) <br/> |Les API de gestion Microsoft 365 vous permettent de fournir l’accès à vos données Microsoft 365, y compris les éléments qui les intéressent le plus ( courrier, calendriers, contacts, utilisateurs et groupes, fichiers et dossiers). <br/> |
|[Intégration d’applications dans Azure AD](/azure/active-directory/develop/quickstart-v1-add-azure-ad-app) <br/> | Découvrez les applications intégrées à Azure AD et comment inscrire votre application, comprendre les concepts d’une application inscrite et en savoir plus sur les recommandations de personnalisation pour les applications mutualisées.  <br/> |
|[Ajouter des vignettes personnalisées au lanceur d’applications](/office365/admin/manage/customize-the-app-launcher)  <br/> |Le lanceur d’applications dans Microsoft 365 permet aux utilisateurs de trouver et d’accéder plus facilement à leurs applications. Cet article décrit comment vous, en tant que développeur, pouvez faire apparaître vos applications dans les lanceurs d’applications des utilisateurs et leur offrir une expérience d’authentification unique (SSO) à l’aide de leurs informations d’identification Microsoft 365.  <br/> |
|[Didacticiels sur l’intégration d’Azure AD](/azure/active-directory/saas-apps/tutorial-list) <br/> |L’objectif de ces didacticiels est de vous montrer comment configurer l’authentification unique Azure AD pour des applications SaaS tierces.  <br/> |
|[Scénarios d’authentification pour Azure AD](/azure/active-directory/develop/authentication-vs-authorization) <br/> |Azure AD simplifie l’authentification pour les développeurs en fournissant une identité en tant que service, avec la prise en charge de protocoles standard comme OAuth 2.0 et OpenID Connect, ainsi que des bibliothèques open source pour différentes plateformes afin de vous aider à commencer rapidement le codage. Ce document vous aide à comprendre les différents scénarios pris en charge par Azure AD et vous montre comment commencer.  <br/> |
|[Accès à l’application](/azure/active-directory/manage-apps/what-is-access-management) <br/> |Azure AD permet une intégration facile à de nombreuses applications SaaS (Software as a Service) les plus populaires d’aujourd’hui. Il fournit la gestion des identités et des accès, et fournit une volet d'accès pour les utilisateurs où ils peuvent découvrir l’accès aux applications dont ils disposent et où ils peuvent utiliser l’authentification unique pour accéder à leurs applications. Cet article vous fournit des liens vers les ressources associées qui vous permettent d’en savoir plus sur les améliorations apportées à l’accès aux applications pour Azure AD et sur la façon dont vous pouvez y contribuer.  <br/> |
|[Personnaliser votre expérience Office 365](https://support.microsoft.com/office/personalize-your-office-365-experience-eb34a21b-52fa-4fbf-a8d5-146132242985) <br/> |Vous pouvez accéder rapidement aux applications que vous utilisez chaque jour en ajoutant ou en supprimant des applications dans le lanceur d’applications Microsoft 365.  <br/> |
