---
title: Intégration Azure avec Microsoft 365
ms.author: josephd
author: JoeDavies-MSFT
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
description: Intégrez Microsoft 365 à Azure AD si vous voulez une synchronisation de mot de passe ou une authentification unique avec votre environnement local.
ms.openlocfilehash: b1f20ebc692421ed6df0d6f7c31a4d80347133e3
ms.sourcegitcommit: 11d1044c6600b1f568b6dc8a53db9b07f2f0ad1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/08/2020
ms.locfileid: "48384739"
---
# <a name="azure-integration-with-microsoft-365"></a>Intégration Azure avec Microsoft 365

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Microsoft 365 utilise Azure Active Directory (Azure AD) pour gérer les identités des utilisateurs en arrière-plan. Votre abonnement Microsoft 365 inclut un abonnement Azure AD gratuit afin que vous puissiez intégrer vos services de domaine Active Directory (AD DS) locaux pour synchroniser les comptes d’utilisateurs et les mots de passe ou configurer l’authentification unique. Vous pouvez également acheter des fonctionnalités avancées pour mieux gérer vos comptes.
  
Azure AD offre également d’autres fonctionnalités, telles que la gestion des applications intégrées, que vous pouvez utiliser pour étendre et personnaliser vos abonnements Microsoft 365.
  
Vous pouvez utiliser les conseillers au déploiement Azure AD pour une expérience de configuration et d’installation guidée dans le centre d’administration 365 de Microsoft (vous devez être connecté à Microsoft 365) :

 - [Conseiller Azure AD Connect](https://aka.ms/aadconnectpwsync)
 - [Conseiller de déploiement AD FS](https://aka.ms/adfsguidance)
 - [Guide de configuration d’Azure AD](https://aka.ms/aadpguidance)
  
## <a name="azure-ad-editions-and-microsoft-365-identity-management"></a>La gestion des identités Azure AD Edition et Microsoft 365

Si vous disposez d’un abonnement payant à Microsoft 365, vous disposez également d’un abonnement Azure AD gratuit. Vous pouvez utiliser Azure AD pour créer et gérer des comptes d’utilisateurs et de groupes. Pour activer cet abonnement, vous devez effectuer une inscription unique. Par la suite, vous pouvez accéder à Azure AD à partir de votre centre d’administration Microsoft 365. 

Pour obtenir des instructions sur l’enregistrement de votre abonnement Azure AD gratuit, consultez [la rubrique utiliser votre abonnement Azure ad gratuit](../compliance/use-your-free-azure-ad-subscription-in-office-365.md). N’accédez pas directement à azure.microsoft.com pour vous inscrire ou vous obtiendrez une version d’évaluation ou un abonnement payant à Microsoft Azure qui est distinct de votre abonnement Azure AD gratuit avec Microsoft 365. 
  
Avec l’abonnement gratuit, vous pouvez synchroniser avec des annuaires locaux, configurer l’authentification unique et effectuer une synchronisation avec de nombreux logiciels en tant qu’applications de service, telles que Salesforce, DropBox et bien d’autres encore.
  
Si vous souhaitez améliorer les fonctionnalités AD DS, la synchronisation bidirectionnelle et les autres fonctionnalités de gestion, vous pouvez mettre à niveau votre abonnement gratuit vers un abonnement payant payant. Pour plus d’informations, reportez-vous à la rubrique [Azure Active Directory Editions](https://azure.microsoft.com/pricing/details/active-directory/).
  
Pour plus d’informations sur Microsoft 365 et Azure AD, voir [microsoft 365 Identity Models](about-microsoft-365-identity.md).
  
## <a name="extend-the-capabilities-of-your-microsoft-365-tenant"></a>Étendez les capacités de votre client Microsoft 365

|**Fonctionnalité**|**Description**|
|:-----|:-----|
|Applications intégrées  <br/> |Vous pouvez accorder à des applications individuelles l’accès à vos données Microsoft 365, telles que des courriers électroniques, des calendriers, des contacts, des utilisateurs, des groupes, des fichiers et des dossiers. Vous pouvez également autoriser ces applications au niveau de l’administrateur général et les rendre accessibles à votre entreprise entière en enregistrant les applications dans Azure AD. Formore informations, consultez la rubrique [applications intégrées et Azure AD pour les administrateurs de Microsoft 365](integrated-apps-and-azure-ads.md).  <br/> Voir aussi [authentification unique](https://go.microsoft.com/fwlink/p/?LinkId=698604).  <br/> |
|PowerApps  <br/> | Les applications Power sont des applications ciblées pour les appareils mobiles qui peuvent se connecter à vos sources de données existantes, telles que les listes SharePoint et les autres applications de données. Pour plus d’informations, reportez-vous à la rubrique [créer un PowerApp pour une liste dans SharePoint Online](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab) et la [page des PowerApp](https://powerapps.microsoft.com/) .  <br/> |
   
## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de Microsoft 365 Entreprise](microsoft-365-overview.md)
