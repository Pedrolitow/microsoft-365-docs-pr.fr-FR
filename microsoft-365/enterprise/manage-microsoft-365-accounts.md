---
title: Gérer les comptes d’utilisateur Microsoft 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: overview
ms.prod: office-online-server
localization_priority: Normal
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-mar2020
ms.collection:
- Ent_O365
- M365-subscription-management
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: 98ca5b3f-f720-4d8e-91be-fe656548a25a
description: Découvrez comment gérer les comptes d’utilisateurs Microsoft 365.
ms.openlocfilehash: a7b6d89a0f66605dde168b85d74fcd8e513afc15
ms.sourcegitcommit: 04c4252457d9b976d31f53e0ba404e8f5b80d527
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2020
ms.locfileid: "48327758"
---
# <a name="manage-microsoft-365-user-accounts"></a>Gérer les comptes d’utilisateur Microsoft 365

Vous pouvez gérer les comptes d’utilisateurs Microsoft 365 de différentes manières, selon votre configuration. Vous pouvez gérer les comptes d’utilisateurs dans le Centre d’administration [Microsoft 365,](https://docs.microsoft.com/microsoft-365/admin/add-users/) [PowerShell,](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)dans les services de domaine Active Directory (AD DS) ou dans le portail d’administration Azure Active Directory (Azure AD). 

Dès que vous achetez Microsoft 365, le Centre d’administration Microsoft 365 et PowerShell peuvent être utilisés pour gérer les comptes. Lors de la gestion des identités cloud, chaque personne de votre organisation dispose d’un nom de compte d’utilisateur et d’un mot de passe distincts. Si vous souhaitez intégrer votre infrastructure locale et synchroniser des comptes d’utilisateurs avec Microsoft 365, vous pouvez utiliser Azure AD Connect pour fournir la synchronisation des identités et des mots de passe pour la fonctionnalité d’personnalisation unique (SSO).
  
## <a name="plan-for-where-and-how-you-will-manage-your-user-accounts"></a>Planifier l’endroit et la façon dont vous allez gérer vos comptes d’utilisateur

L’endroit où et comment vous pouvez gérer vos comptes d’utilisateur dépend du modèle d’identité que vous souhaitez utiliser pour votre Microsoft 365. Les deux modèles globaux sont uniquement cloud et hybrides.
  
### <a name="cloud-only"></a>Cloud uniquement

Vous créez et gérez des utilisateurs dans le Centre d’administration Microsoft 365. Vous pouvez également utiliser PowerShell ou le Centre d’administration Azure AD. 
    
### <a name="hybrid"></a>Hybride

Les comptes d’utilisateur sont synchronisés avec Microsoft 365 à partir d’AD DS. Vous devez donc utiliser les outils AD DS locaux pour gérer les comptes d’utilisateurs. 
    
## <a name="managing-accounts"></a>Gestion des comptes

Lorsque vous décidez de la façon dont votre organisation crée et gère les comptes, prenons en compte les exigences suivantes :
  
- Le logiciel de synchronisation d’annuaires doit être installé sur les serveurs de votre environnement local pour connecter les identités entre Microsoft 365 et vos services AD DS.
    
- Toute option de synchronisation d’annuaires, y compris les options DSO, nécessite que vos attributs AD DS respectent les normes. Les spécificités des attributs utilisés dans votre répertoire et le nettoyage (le cas nécessaire) sont décrites dans Préparer la synchronisation d’annuaires avec [Microsoft 365.](prepare-for-directory-synchronization.md) 
    
- Planifiez la façon dont vous allez créer des comptes Microsoft 365.
    
Le tableau suivant répertorie les différents outils de gestion des comptes.
    
|Outil|Notes|
|:-----|:-----|
|Centre d’administration Microsoft 365  <br/> |[Ajouter des utilisateurs individuellement ou en bloc](https://docs.microsoft.com/microsoft-365/admin/add-users/add-users) <br/>  Fournit une interface web simple pour ajouter et modifier des comptes d’utilisateurs.  <br/>  Ne peut pas être utilisé pour modifier les utilisateurs si la synchronisation d’annuaires est activée (l’emplacement et l’attribution de licence peuvent être définies).  <br/>  Ne peut pas être utilisé avec les options DSO.  <br/> |
|Windows PowerShell  <br/> |[Gérer Microsoft 365 avec Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=698471) <br/>  Permet d’ajouter des utilisateurs en bloc à l’aide d’Windows PowerShell script.  <br/>  Peut être utilisé pour attribuer un emplacement et des licences à des comptes, quelle que soit la façon dont les comptes sont créés.  <br/> |
|Importation en bloc  <br/> |[Ajouter plusieurs utilisateurs simultanément](add-several-users-at-the-same-time.md) <br/>  Permet d’importer un fichier CSV pour ajouter un groupe d’utilisateurs à Microsoft 365.  <br/>  Ne peut pas être utilisé avec les options DSO.  <br/> |
|Azure AD  <br/> |Vous obtenez une édition gratuite d’Azure AD avec votre abonnement Microsoft 365. Vous pouvez effectuer des fonctions telles que la réinitialisation du mot de passe en libre-service pour les utilisateurs du cloud et la personnalisation des pages de la page de signature et du Panneau d’accès à l’aide de l’édition gratuite. Pour obtenir des fonctionnalités améliorées, vous pouvez mettre à niveau vers l’édition de base, Azure AD Premium P1 ou Azure AD Premium P2. Consultez [les éditions Azure AD](https://go.microsoft.com/fwlink/p/?LinkId=698465) pour obtenir la liste des fonctionnalités pris en charge.  <br/> |
|Synchronisation d’annuaires  <br/> |[Intégration de vos identités locales à Azure AD](https://go.microsoft.com/fwlink/p/?LinkID=624168) <br/>  Pour la synchronisation d’annuaires avec ou sans synchronisation de mot de passe, utilisez [Azure AD Connect avec les paramètres express.](https://go.microsoft.com/fwlink/p/?LinkID=698537)  <br/>  Pour plusieurs forêts et options DSO, utilisez [l’installation personnalisée d’Azure AD Connect.](https://go.microsoft.com/fwlink/p/?LinkId=698430)  <br/>  Fournit l’infrastructure nécessaire pour activer l' cesso.  <br/>  Requis pour de nombreux scénarios hybrides tels que la migration par étapes et Exchange hybride  <br/>  Synchronise la sécurité et les groupes à messagerie à partir de vos services AD DS.  <br/> |
|||
   
- Quelle que soit la façon dont vous envisagez d’ajouter les comptes d’utilisateur à Microsoft 365, vous devez gérer plusieurs fonctionnalités de compte, telles que l’attribution de licences, la spécification de l’emplacement, etc. Ces fonctionnalités peuvent être gérées à long terme à partir du Centre d’administration Microsoft 365 ou vous pouvez également créer des comptes d’utilisateurs [avec PowerShell.](https://go.microsoft.com/fwlink/p/?LinkId=717083)
    
    Si vous choisissez d’ajouter et de gérer tous vos utilisateurs via le Centre d’administration, vous spécifiez l’emplacement et attribuez des licences en même temps que la création du compte Microsoft 365. Par conséquent, peu de planification est requise.
    
    > [!IMPORTANT]
    > La création de comptes dans Microsoft 365 sans attribuer de licence (à SharePoint Online, par exemple) signifie que le propriétaire du compte peut afficher le Centre Microsoft 365, mais qu’il ne peut accéder à aucun des services au sein de l’abonnement de votre entreprise. Une fois que vous avez affecté un emplacement et la licence, le compte est répliqué sur le ou les services que vous avez affectés. L’utilisateur peut se connecter à son compte et utiliser les services que vous lui avez affectés. 
  
## <a name="see-also"></a>Voir aussi

[Centre d’administration Microsoft 365](https://docs.microsoft.com/microsoft-365/admin/add-users)

[PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)  
