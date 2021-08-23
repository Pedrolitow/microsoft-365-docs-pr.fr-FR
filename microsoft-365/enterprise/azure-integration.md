---
title: Intégration d’Azure avec Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection:
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
description: Intégrez Microsoft 365 Azure AD si vous souhaitez synchroniser le mot de passe ou l' sign-on unique avec votre environnement local.
ms.openlocfilehash: eaf2b42910c2d0b3a7f672262b2397f8010793ba
ms.sourcegitcommit: 9469d16c6bbd29442a6787beaf7d84fb7699c5e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/19/2021
ms.locfileid: "58400318"
---
# <a name="azure-integration-with-microsoft-365"></a>Intégration d’Azure avec Microsoft 365

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Microsoft 365 utilise Azure Active Directory (Azure AD) pour gérer les identités des utilisateurs en arrière-plan. Votre abonnement Microsoft 365 inclut un abonnement Azure AD gratuit qui vous permet d’intégrer vos services de domaine Active Directory (AD DS) locaux pour synchroniser les comptes d’utilisateur et les mots de passe ou configurer l' sign-on unique. Vous pouvez également acheter des fonctionnalités avancées pour mieux gérer vos comptes.
  
Azure AD offre également d’autres fonctionnalités, telles que la gestion des applications intégrées, que vous pouvez utiliser pour étendre et personnaliser Microsoft 365 abonnements.
  
Vous pouvez utiliser les conseillers de déploiement Azure AD pour une configuration guidée dans le Centre d’administration Microsoft 365 (vous devez être Microsoft 365) :

 - [Azure AD Connecter advisor](https://aka.ms/aadconnectpwsync)
 - [Conseiller de déploiement AD FS](https://aka.ms/adfsguidance)
 - [Guide de configuration d’Azure AD](https://aka.ms/aadpguidance)
  
## <a name="azure-ad-editions-and-microsoft-365-identity-management"></a>Éditions Azure AD et gestion Microsoft 365 identités

Si vous avez un abonnement payant Microsoft 365, vous avez également un abonnement Azure AD gratuit. Vous pouvez utiliser Azure AD pour créer et gérer des comptes d’utilisateur et de groupe. Pour activer cet abonnement, vous devez effectuer une inscription à une seule fois. Ensuite, vous pouvez accéder à Azure AD à partir de votre Centre d’administration Microsoft 365. 

Pour obtenir des instructions pour inscrire votre abonnement Azure AD gratuit, consultez votre abonnement [Azure AD gratuit.](../compliance/use-your-free-azure-ad-subscription-in-office-365.md) N’allez pas directement à azure.microsoft.com pour vous inscrire ou vous vous retrouverez avec un abonnement d’essai ou payant à Microsoft Azure distinct de votre abonnement Azure AD gratuit avec Microsoft 365. 
  
Avec l’abonnement gratuit, vous pouvez synchroniser avec les annuaires locaux, configurer l' sign-on unique et synchroniser avec de nombreux logiciels en tant qu’applications de service, tels que Salesforce, DropBox et bien plus encore.
  
Si vous souhaitez améliorer les fonctionnalités AD DS, la synchronisation bi-directionnelle et d’autres fonctionnalités de gestion, vous pouvez mettre à niveau votre abonnement gratuit vers un abonnement premium payant. Pour plus d’informations, [voir Azure Active Directory éditions.](https://azure.microsoft.com/pricing/details/active-directory/)
  
Pour plus d’informations sur Microsoft 365 et Azure AD, voir [Microsoft 365 modèles d’identité.](about-microsoft-365-identity.md)
  
## <a name="extend-the-capabilities-of-your-microsoft-365-tenant"></a>Étendre les fonctionnalités de votre client Microsoft 365 client

|**Fonctionnalité**|**Description**|
|:-----|:-----|
|Applications intégrées  <br/> |Vous pouvez accorder à des applications individuelles l’accès à Microsoft 365 données de messagerie, de calendriers, de contacts, d’utilisateurs, de groupes, de fichiers et de dossiers. Vous pouvez également autoriser ces applications au niveau de l’administrateur global et les mettre à la disposition de l’ensemble de votre entreprise en les enregistrant dans Azure AD. Pour plus d’informations, voir [Applications intégrées et Azure AD pour Microsoft 365 administrateurs.](integrated-apps-and-azure-ads.md)  <br/> Voir aussi [1 000 000 000](/azure/active-directory/manage-apps/what-is-single-sign-on).  <br/> |
|Power Apps  <br/> | Power Apps sont des applications axées sur les appareils mobiles qui peuvent se connecter à vos sources de données existantes, telles que SharePoint listes et autres applications de données. Pour [plus d’informations,](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab) voir Créer une application Power App pour une liste SharePoint Online [et Power Apps page.](https://powerapps.microsoft.com/)  <br/> |
   
## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de Microsoft 365 Entreprise](microsoft-365-overview.md)
