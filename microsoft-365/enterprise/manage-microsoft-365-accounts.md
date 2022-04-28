---
title: Gérer Microsoft 365 comptes d’utilisateur
ms.author: kvice
author: kelleyvice-msft
manager: scotv
audience: Admin
ms.topic: overview
ms.prod: office-online-server
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-mar2020
- admindeeplinkMAC
ms.collection:
- Ent_O365
- M365-subscription-management
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: 98ca5b3f-f720-4d8e-91be-fe656548a25a
description: Découvrez comment gérer Microsoft 365 comptes d’utilisateur.
ms.openlocfilehash: dbd1c0a3c1c6fdb10d157299552e83a77f495e3c
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65098337"
---
# <a name="manage-microsoft-365-user-accounts"></a>Gérer Microsoft 365 comptes d’utilisateur

Vous pouvez gérer Microsoft 365 comptes d’utilisateur de plusieurs manières différentes, en fonction de votre configuration. Vous pouvez gérer des comptes d’utilisateur dans le [Centre d'administration Microsoft 365](/admin), [PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md), dans services de domaine Active Directory (AD DS) ou dans le portail d’administration Azure Active Directory (Azure AD) . 

Dès que vous achetez Microsoft 365, les <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centre d'administration Microsoft 365</a> et PowerShell peuvent être utilisés pour gérer les comptes. Lors de la gestion des identités cloud, chaque personne de votre organisation dispose d’un nom de compte d’utilisateur et d’un mot de passe distincts. Si vous souhaitez intégrer votre infrastructure locale et que des comptes d’utilisateurs sont synchronisés avec Microsoft 365, vous pouvez utiliser Azure AD Connecter pour fournir la synchronisation des identités et des mots de passe pour les fonctionnalités d’authentification unique (SSO).
  
## <a name="plan-for-where-and-how-you-will-manage-your-user-accounts"></a>Planifier l’emplacement et la façon dont vous allez gérer vos comptes d’utilisateur

L’emplacement et la façon dont vous pouvez gérer vos comptes d’utilisateur dépendent du modèle d’identité que vous souhaitez utiliser pour votre Microsoft 365. Les deux modèles globaux sont cloud uniquement et hybrides.
  
### <a name="cloud-only"></a>Cloud uniquement

Vous créez et gérez des utilisateurs dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centre d'administration Microsoft 365</a>. Vous pouvez également utiliser PowerShell ou le centre d’administration Azure AD. 
    
### <a name="hybrid"></a>Hybride

Les comptes d’utilisateur sont synchronisés avec Microsoft 365 d’AD DS. Vous devez donc utiliser les outils AD DS locaux pour gérer les comptes d’utilisateur. 
    
## <a name="managing-accounts"></a>Gestion des comptes

Lorsque vous décidez de la façon dont votre organisation créera et gérera des comptes, tenez compte des exigences suivantes :
  
- Le logiciel de synchronisation d’annuaires doit être installé sur les serveurs de votre environnement local pour connecter les identités entre Microsoft 365 et votre AD DS.
    
- Toute option de synchronisation d’annuaires, y compris les options d’authentification unique, nécessite que vos attributs AD DS répondent aux normes. Les spécificités des attributs utilisés dans votre répertoire et du nettoyage (le cas échéant) sont décrites dans [Préparer la synchronisation d’annuaires à Microsoft 365](prepare-for-directory-synchronization.md). 
    
- Planifiez la façon dont vous allez créer des comptes Microsoft 365.
    
Le tableau suivant répertorie les différents outils de gestion de compte.
    
|Outil|Remarques|
|:-----|:-----|
|Centre d’administration Microsoft 365  <br/> |[Ajouter des utilisateurs individuellement ou en bloc](../admin/add-users/add-users.md) <br/>  Fournit une interface web simple pour ajouter et modifier des comptes d’utilisateur.  <br/>  Ne peut pas être utilisé pour modifier les utilisateurs si la synchronisation d’annuaires est activée (l’emplacement et l’attribution de licence peuvent être définis).  <br/>  Impossible d’utiliser les options d’authentification unique.  <br/> |
|Windows PowerShell  <br/> |[Gérer Microsoft 365 avec Windows PowerShell](./manage-microsoft-365-with-microsoft-365-powershell.md) <br/>  Vous permet d’ajouter des utilisateurs dans des utilisateurs en bloc à l’aide d’un script Windows PowerShell.  <br/>  Peut être utilisé pour attribuer des emplacements et des licences à des comptes, quelle que soit la façon dont les comptes sont créés.  <br/> |
|Importation en bloc  <br/> |[Ajouter plusieurs utilisateurs simultanément](add-several-users-at-the-same-time.md) <br/>  Vous permet d’importer un fichier CSV pour ajouter un groupe d’utilisateurs à Microsoft 365.  <br/>  Impossible d’utiliser les options d’authentification unique.  <br/> |
|Azure AD  <br/> |Vous bénéficiez d’une édition gratuite de Azure AD avec votre abonnement Microsoft 365. Vous pouvez effectuer des fonctions telles que la réinitialisation de mot de passe en libre-service pour les utilisateurs du cloud et la personnalisation des pages de connexion et de volet d'accès à l’aide de l’édition gratuite. Pour bénéficier de fonctionnalités améliorées, vous pouvez effectuer une mise à niveau vers l’édition de base, la Azure AD Premium P1 ou la Azure AD Premium P2. Consultez [Azure AD éditions](/azure/active-directory/fundamentals/active-directory-whatis) pour obtenir la liste des fonctionnalités prises en charge.  <br/> |
|Synchronisation d’annuaires  <br/> |[Intégration de vos identités locales à Azure AD](/azure/active-directory/hybrid/whatis-hybrid-identity) <br/>  Pour la synchronisation d’annuaires avec ou sans synchronisation de mot de passe, utilisez [Azure AD Connecter avec des paramètres express](/azure/active-directory/hybrid/how-to-connect-install-express).  <br/>  Pour plusieurs forêts et options d’authentification unique, utilisez [l’installation personnalisée de Azure AD Connecter](/azure/active-directory/hybrid/how-to-connect-install-custom).  <br/>  Fournit l’infrastructure nécessaire pour activer l’authentification unique.  <br/>  Requis pour de nombreux scénarios hybrides tels que la migration intermédiaire et les Exchange hybrides  <br/>  Synchronise les groupes de sécurité et de messagerie à partir de votre service AD DS.  <br/> |
|||
   
- Quelle que soit la façon dont vous envisagez d’ajouter les comptes d’utilisateur à Microsoft 365, vous devez gérer plusieurs fonctionnalités de compte, telles que l’attribution de licences, la spécification de l’emplacement, etc. Ces fonctionnalités peuvent être gérées à long terme à partir du <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centre d'administration Microsoft 365</a> ou vous pouvez également [créer des comptes d’utilisateur avec PowerShell](./create-user-accounts-with-microsoft-365-powershell.md).
    
    Si vous choisissez d’ajouter et de gérer tous vos utilisateurs via le Centre d’administration, vous spécifiez l’emplacement et attribuez des licences en même temps que la création du compte Microsoft 365. Par conséquent, peu de planification est nécessaire.
    
    > [!IMPORTANT]
    > La création de comptes dans Microsoft 365 sans attribuer de licence (à SharePoint Online, par exemple) signifie que le propriétaire du compte peut afficher le centre de Microsoft 365, mais ne peut accéder à aucun des services de l’abonnement de votre entreprise. Une fois que vous avez attribué un emplacement et la licence, le compte est répliqué vers le service ou les services que vous avez affectés. L’utilisateur peut se connecter à son compte et utiliser les services que vous lui avez affectés. 
  
## <a name="see-also"></a>Voir aussi

[Centre d’administration Microsoft 365](/admin)

[PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)