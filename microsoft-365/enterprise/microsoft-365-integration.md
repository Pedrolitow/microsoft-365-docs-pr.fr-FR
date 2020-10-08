---
title: Intégration de Microsoft 365 aux environnements locaux
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
ms.collection:
- Ent_O365
search.appverid:
- MET150
- LYN150
- SPS150
- MOE150
- MED150
ms.assetid: 263faf8d-aa21-428b-aed3-2021837a4b65
description: Dans cet article, Découvrez comment intégrer Microsoft 365 avec vos services d’annuaire et environnements locaux existants.
ms.openlocfilehash: 9c5e287ed4a440d1f62081a4c94e39f0f162b4dc
ms.sourcegitcommit: 11d1044c6600b1f568b6dc8a53db9b07f2f0ad1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/08/2020
ms.locfileid: "48384867"
---
# <a name="microsoft-365-integration-with-on-premises-environments"></a>Intégration de Microsoft 365 aux environnements locaux

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Vous pouvez intégrer Microsoft 365 à vos services de domaine Active Directory (AD DS) locaux existants et aux installations locales d’Exchange Server, Skype entreprise Server 2015 ou SharePoint Server.
  
 - Lorsque vous intégrez les services AD DS, vous pouvez synchroniser et gérer les comptes d’utilisateur pour les deux environnements. Vous pouvez également ajouter la synchronisation de hachage de mot de passe (hachage) ou l’authentification unique (SSO) de sorte que les utilisateurs puissent se connecter aux deux environnements à l’aide de leurs informations d’identification locales.
 - Lorsque vous intégrez des produits serveur sur site, vous créez un environnement hybride. Un environnement hybride peut vous aider lors de la migration des utilisateurs ou des informations vers Microsoft 365, ou vous pouvez continuer à avoir des utilisateurs ou des informations sur site et d’autres dans le Cloud. Pour plus d’informations sur les environnements hybrides, consultez la rubrique [Cloud hybride](../solutions/cloud-architecture-models.md#hybrid).

Vous pouvez également utiliser les conseillers Azure Active Directory (Azure AD) pour obtenir des instructions de configuration personnalisées dans le centre d’administration 365 de Microsoft (vous devez être connecté à Microsoft 365) :

- [Guide de configuration d’Azure AD](https://aka.ms/aadpguidance)
- [Synchroniser les utilisateurs du répertoire de votre organisation](https://aka.ms/aadconnectpwsync)
- [Gestionnaire de déploiement des services ADFS (Active Directory Federation Services)](https://aka.ms/adfsguidance)
   
## <a name="before-you-begin"></a>Avant de commencer

Avant d’intégrer Microsoft 365 et un environnement local, vous devez également effectuer une planification du [réseau et un réglage des performances](network-planning-and-performance.md). Vous voudrez également comprendre les modèles d' [identité](about-microsoft-365-identity.md)disponibles. 

Consultez la rubrique [Manage microsoft 365 Accounts](manage-microsoft-365-accounts.md) pour obtenir la liste des outils que vous pouvez utiliser pour gérer les comptes d’utilisateur Microsoft 365. 
  
## <a name="integrate-microsoft-365-with-ad-ds"></a>Intégration de Microsoft 365 à AD DS

Si vous avez des comptes d’utilisateur existants dans AD DS, vous ne souhaitez pas recréer tous ces comptes dans Microsoft 365 et risquez d’introduire des différences ou des erreurs entre les environnements. La synchronisation d’annuaires vous permet de mettre en miroir ces comptes entre vos environnements locaux et en ligne. Avec la synchronisation d’annuaires, vos utilisateurs n’ont pas à se souvenir des nouvelles informations pour chaque environnement, et vous n’avez pas à créer ou mettre à jour les comptes deux fois. Vous devrez [préparer votre annuaire local pour la](prepare-for-directory-synchronization.md) synchronisation d’annuaires.
  
![Utiliser la synchronisation d’annuaires pour maintenir la synchronisation des informations sur les comptes d’utilisateur en ligne et en ligne](../media/microsoft-365-integration/directory-synchronization.png)
  
Si vous souhaitez que les utilisateurs puissent se connecter à Microsoft 365 avec leurs informations d’identification locales, vous pouvez également configurer l’authentification unique. Avec l’authentification unique, Microsoft 365 est configuré pour approuver l’environnement local pour l’authentification des utilisateurs.
  
![Avec l’authentification unique, le même compte est disponible dans les environnements locaux et en ligne.](../media/microsoft-365-integration/single-sign-on.png)

### <a name="directory-synchronization-with-or-without-password-hash-synchronization-or-pass-through-authentication-pta"></a>Synchronisation d’annuaires avec ou sans synchronisation de hachage de mot de passe ou authentification directe (directe)

Un utilisateur se connecte à son environnement local à l’aide de son compte d’utilisateur (DOMAINE\nom d’utilisateur). Lorsque les utilisateurs accèdent à Microsoft 365, ils doivent se reconnecter avec leur compte professionnel ou scolaire (user@domain.com). Le nom d’utilisateur est le même dans les deux environnements. Lorsque vous ajoutez hachage ou directe, l’utilisateur a le même mot de passe pour les deux environnements, mais il devra de nouveau fournir ces informations d’identification lors de la connexion à Microsoft 365. La synchronisation d’annuaires avec hachage est la synchronisation d’annuaires la plus couramment utilisée.

Pour configurer la synchronisation d’annuaires, utilisez Azure AD Connect. Pour obtenir des instructions, consultez la rubrique [configurer la synchronisation d’annuaires pour Microsoft 365](set-up-directory-synchronization.md) et [Azure ad Connect with Express Settings](https://go.microsoft.com/fwlink/p/?LinkId=698537).

Pour en savoir plus, consultez la rubrique relative [à la préparation de la synchronisation d’annuaires avec Microsoft 365](prepare-for-directory-synchronization.md).

### <a name="directory-synchronization-with-sso"></a>Synchronisation d’annuaires avec SSO

Un utilisateur se connecte à son environnement local à l’aide de son compte d’utilisateur. Lorsque les utilisateurs accèdent à Microsoft 365, ils se connectent automatiquement ou se connectent à l’aide des mêmes informations d’identification qu’ils utilisent pour leur environnement local (DOMAINE\nom d’utilisateur).

Pour configurer l’authentification unique, vous devez également utiliser Azure AD Connect. Pour obtenir des instructions, voir [installation personnalisée d’Azure ad Connect](https://go.microsoft.com/fwlink/p/?LinkID=698430).

Pour plus d’informations, consultez la rubrique [authentification unique](https://go.microsoft.com/fwlink/p/?LinkId=698604).

## <a name="azure-ad-connect"></a>Azure AD Connect

Azure AD Connect remplace les anciennes versions des outils d’intégration des identités telles que DirSync et Azure AD Sync. Si vous souhaitez effectuer une mise à jour à partir d’Azure Active Directory Sync vers Azure AD Connect, consultez [les instructions de mise à niveau](https://go.microsoft.com/fwlink/p/?LinkId=733240). 

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de Microsoft 365 Entreprise](microsoft-365-overview.md)
