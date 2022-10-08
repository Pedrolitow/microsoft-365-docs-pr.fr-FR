---
title: Intégration d’Azure à Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
audience: Admin
ms.topic: overview
ms.service: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- scotvorg
- Ent_O365
- M365-identity-device-management
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: a5efce5d-9c9c-4190-b61b-fd273c1d425f
description: Intégrez Microsoft 365 à Azure AD si vous souhaitez synchroniser le mot de passe ou l’authentification unique avec votre environnement local.
ms.openlocfilehash: 9369437e556e3faf1691c2af513ace846e0ad944
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68209291"
---
# <a name="azure-integration-with-microsoft-365"></a>Intégration d’Azure à Microsoft 365

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Microsoft 365 utilise Azure Active Directory (Azure AD) pour gérer les identités des utilisateurs en arrière-plan. Votre abonnement Microsoft 365 inclut un abonnement Azure AD gratuit afin que vous puissiez intégrer vos services de domaine Active Directory local (AD DS) pour synchroniser les comptes d’utilisateur et les mots de passe, ou configurer l’authentification unique. Vous pouvez également acheter des fonctionnalités avancées pour mieux gérer vos comptes.
  
Azure AD offre également d’autres fonctionnalités, telles que la gestion des applications intégrées, que vous pouvez utiliser pour étendre et personnaliser vos abonnements Microsoft 365.
  
Vous pouvez utiliser les conseillers de déploiement Azure AD pour une installation guidée et une expérience de configuration dans le Centre d'administration Microsoft 365 (vous devez être connecté à Microsoft 365) :

 - [Conseiller Azure AD Connect](https://aka.ms/aadconnectpwsync)
 - [Conseiller de déploiement AD FS](https://aka.ms/adfsguidance)
 - [Guide d’installation d’Azure AD](https://aka.ms/aadpguidance)
  
## <a name="azure-ad-editions-and-microsoft-365-identity-management"></a>Éditions Azure AD et gestion des identités Microsoft 365

Si vous avez un abonnement payant à Microsoft 365, vous disposez également d’un abonnement Azure AD gratuit. Vous pouvez utiliser Azure AD pour créer et gérer des comptes d’utilisateurs et de groupes. Pour activer cet abonnement, vous devez effectuer une inscription unique. Ensuite, vous pouvez accéder à Azure AD à partir de votre Centre d'administration Microsoft 365. 

Pour obtenir des instructions pour inscrire votre abonnement Azure AD gratuit, consultez [utiliser votre abonnement Azure AD gratuit](../compliance/use-your-free-azure-ad-subscription-in-office-365.md). N’accédez pas directement à azure.microsoft.com pour vous inscrire ou vous vous retrouverez avec un abonnement d’évaluation ou payant à Microsoft Azure distinct de votre abonnement Azure AD gratuit avec Microsoft 365. 
  
Avec l’abonnement gratuit, vous pouvez vous synchroniser avec des répertoires locaux, configurer l’authentification unique et synchroniser avec de nombreux logiciels comme des applications de service, telles que Salesforce, DropBox et bien plus encore.
  
Si vous souhaitez améliorer les fonctionnalités AD DS, la synchronisation bidirectionnelle et d’autres fonctionnalités de gestion, vous pouvez mettre à niveau votre abonnement gratuit vers un abonnement Premium payant. Pour plus d’informations, consultez [les éditions d’Azure Active Directory](https://azure.microsoft.com/pricing/details/active-directory/).
  
Pour plus d’informations sur Microsoft 365 et Azure AD, consultez [les modèles d’identité Microsoft 365](deploy-identity-solution-identity-model.md).
  
## <a name="extend-the-capabilities-of-your-microsoft-365-tenant"></a>Étendre les fonctionnalités de votre locataire Microsoft 365

|**Fonctionnalité**|**Description**|
|:-----|:-----|
|Applications intégrées  <br/> |Vous pouvez accorder à des applications individuelles l’accès à vos données Microsoft 365, telles que la messagerie, les calendriers, les contacts, les utilisateurs, les groupes, les fichiers et les dossiers. Vous pouvez également autoriser ces applications au niveau **de l’administrateur Azure AD DC** ou **de l’administrateur général** et les mettre à la disposition de l’ensemble de votre entreprise en les inscrivant dans Azure AD. Pour plus d’informations, consultez [Applications intégrées et Azure AD pour les administrateurs Microsoft 365](integrated-apps-and-azure-ads.md).<br/> Pour plus d’informations, consultez la rubrique [À propos des rôles d’administrateur](/microsoft-365/admin/add-users/about-admin-roles?). <br/> Voir également [Authentification unique](/azure/active-directory/manage-apps/what-is-single-sign-on).  <br/> |
|Power Apps  <br/> | Power Apps sont des applications axées sur les appareils mobiles qui peuvent se connecter à vos sources de données existantes, telles que les listes SharePoint et d’autres applications de données. Pour plus d’informations, consultez [Créer une application Power pour une liste dans SharePoint Online](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab) et la [page Power Apps](https://powerapps.microsoft.com/) .  <br/> |
   
## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de Microsoft 365 Entreprise](microsoft-365-overview.md)
