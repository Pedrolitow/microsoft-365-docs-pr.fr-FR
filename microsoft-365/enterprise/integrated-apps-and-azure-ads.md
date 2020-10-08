---
title: Applications intégrées et Azure AD pour les administrateurs Microsoft 365
ms.author: josephd
author: JoeDavies-MSFT
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
description: Découvrez comment enregistrer et administrer des applications intégrées Office 365 dans Azure AD, en autorisant les autorisations d’application au niveau de l’administrateur général.
ms.openlocfilehash: 1e84b5e6f82848bf1d100004bcd2711ad2e9ed39
ms.sourcegitcommit: 11d1044c6600b1f568b6dc8a53db9b07f2f0ad1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/08/2020
ms.locfileid: "48384902"
---
# <a name="integrated-apps-and-azure-ad-for-microsoft-365-administrators"></a>Applications intégrées et Azure AD pour les administrateurs Microsoft 365

Il y a plus de gestion des applications intégrées que la simple [gestion du consentement de l’utilisateur pour les applications](https://docs.microsoft.com/microsoft-365/admin/misc/integrated-apps). Avec l’arrivée des API REST Microsoft 365, les utilisateurs peuvent accorder aux applications l’accès à leurs données Microsoft 365, telles que des courriers électroniques, des calendriers, des contacts, des utilisateurs, des groupes, des fichiers et des dossiers. Par défaut, les utilisateurs doivent accorder individuellement des autorisations à chaque application. 

Mais cela n’est pas adapté si vous souhaitez autoriser une application une seule fois au niveau de l’administrateur général et la déployer dans l’ensemble de votre organisation via le lanceur d’applications. Pour ce faire, vous devez enregistrer l’application dans Azure Active Directory (Azure AD). Vous devez effectuer certaines étapes avant de pouvoir enregistrer une application dans Azure AD, ainsi que des informations d’arrière-plan que vous devez savoir, qui peuvent vous aider à gérer les applications dans votre organisation Microsoft 365.
  
## <a name="azure-ad-resources-for-microsoft-365-admins"></a>Ressources Azure AD pour les administrateurs de Microsoft 365

Vous devez effectuer ces deux tâches pour pouvoir gérer vos applications Microsoft 365 dans Azure AD.
  
|Conditions préalables|Commentaires|
|:-----|:-----|
|[Utiliser votre abonnement Azure AD gratuit](https://docs.microsoft.com/microsoft-365/compliance/use-your-free-azure-ad-subscription-in-office-365) <br/> |Tous les abonnements payants à Microsoft 365 sont accompagnés d’un abonnement gratuit à Azure AD. Vous pouvez utiliser Azure AD pour gérer vos applications et pour créer et gérer des comptes d’utilisateur et de groupe. Pour utiliser Azure AD, accédez au portail Azure à l’adresse [https://portal.azure.com](https://portal.azure.com) et connectez-vous à l’aide de votre compte Microsoft 365.  <br/> |
|[Gérer le consentement de l’utilisateur pour les applications](https://docs.microsoft.com/microsoft-365/admin/misc/integrated-apps) <br/> |Vous devez gérer le consentement de l’utilisateur pour permettre aux applications tierces d’accéder aux informations Microsoft 365 de l’utilisateur et d’enregistrer des applications dans Azure AD. Une application tierce peut, par exemple, demander l'autorisation d'accéder au calendrier de l'utilisateur et de modifier les fichiers présents dans un dossier OneDrive.  <br/> |
   
La gestion des applications Microsoft 365 nécessite que vous connaissez les applications dans Azure AD. Utilisez ces articles pour vous fournir les informations d’arrière-plan dont vous avez besoin.
  
|Article|Commentaires|
|:-----|:-----|
|[Rencontrez le lanceur d’applications Microsoft 365](https://support.microsoft.com/office/meet-the-microsoft-365-app-launcher-79f12104-6fed-442f-96a0-eb089a3f476a) <br/> |Si vous débutez avec le lanceur d’applications, vous pouvez vous en demander en quoi il s’agit et comment l’utiliser. Le lanceur d’applications est conçu pour vous aider à accéder à vos applications de n’importe où dans Microsoft 365.  <br/> |
|[Vue d’ensemble des API de gestion d’Office 365](https://docs.microsoft.com/office/office-365-management-api/office-365-management-apis-overview) <br/> |Les API de gestion de Microsoft 365 vous permettent de fournir un accès à vos données Microsoft 365, notamment les éléments qui les intéressent le plus, leurs courriers, calendriers, contacts, utilisateurs et groupes, fichiers et dossiers. <br/> |
|[Intégration d’applications dans Azure AD](https://docs.microsoft.com/azure/active-directory/develop/quickstart-v1-add-azure-ad-app) <br/> | Découvrez les applications intégrées à Azure AD et comment enregistrer votre application, comprendre les concepts sous-jacents d’une application inscrite et en savoir plus sur les instructions de personnalisation pour les applications mutualisées.  <br/> |
|[Ajouter des vignettes personnalisées au lanceur d’applications](https://docs.microsoft.com/office365/admin/manage/customize-the-app-launcher)  <br/> |Le lanceur d’applications de Microsoft 365 permet aux utilisateurs de trouver plus facilement les applications et d’y accéder. Cet article décrit comment vous pouvez faire en sorte que vos applications apparaissent dans les lanceurs d’applications des utilisateurs et leur donner une expérience d’authentification unique (SSO) à l’aide de leurs informations d’identification Microsoft 365.  <br/> |
|[Didacticiels d’intégration Azure AD](https://docs.microsoft.com/azure/active-directory/saas-apps/tutorial-list) <br/> |L’objectif de ces didacticiels est de vous montrer comment configurer Azure AD SSO pour les applications SaaS tierces.  <br/> |
|[Scénarios d’authentification pour Azure AD](https://go.microsoft.com/fwlink/?LinkId=617145) <br/> |Azure AD simplifie l’authentification pour les développeurs en fournissant l’identité sous la forme d’un service, avec prise en charge des protocoles standard de l’industrie tels que OAuth 2,0 et OpenID Connect, ainsi que des bibliothèques Open source pour différentes plateformes pour vous aider à commencer à coder rapidement. Ce document vous aide à comprendre les différents scénarios pris en charge par Azure AD et vous montre comment commencer.  <br/> |
|[Accès aux applications](https://docs.microsoft.com/azure/active-directory/manage-apps/what-is-access-management) <br/> |Azure AD permet une intégration facile à de nombreux logiciels populaires actuels en tant qu’applications de service (SaaS). Il fournit la gestion des identités et des accès, et fournit un panneau d’accès pour les utilisateurs, où ils peuvent découvrir l’accès aux applications dont ils disposent et où ils peuvent utiliser l’authentification unique pour accéder à leurs applications. Cet article fournit des liens vers les ressources associées qui vous permettent d’en savoir plus sur les améliorations de l’accès aux applications pour Azure AD et sur la façon de les aider.  <br/> |
|[Personnaliser votre expérience Office 365](https://support.microsoft.com/office/personalize-your-office-365-experience-eb34a21b-52fa-4fbf-a8d5-146132242985) <br/> |Vous pouvez accéder rapidement aux applications que vous utilisez quotidiennement en ajoutant ou en supprimant des applications dans le lanceur d’applications Microsoft 365.  <br/> |

