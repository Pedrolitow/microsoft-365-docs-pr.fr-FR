---
title: Microsoft 365'intégration aux environnements locaux
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
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
description: Dans cet article, découvrez comment intégrer des Microsoft 365 à vos services d’annuaire et environnements locaux existants.
ms.openlocfilehash: 06e6ff598d064f14ffb89bcf88e78932cc621225
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60198432"
---
# <a name="microsoft-365-integration-with-on-premises-environments"></a>Microsoft 365'intégration aux environnements locaux

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Vous pouvez intégrer Microsoft 365 à vos services de domaine Active Directory (AD DS) locaux existants et aux installations sur site de Exchange Server, Skype Entreprise Server 2015 ou SharePoint Server.
  
 - Lorsque vous intégrez AD DS, vous pouvez synchroniser et gérer les comptes d’utilisateur pour les deux environnements. Vous pouvez également ajouter une synchronisation de hachage de mot de passe (PHS) ou une personnalisation unique (SSO) pour que les utilisateurs se connectent aux deux environnements avec leurs informations d’identification sur site.
 - Lorsque vous intégrez des produits serveur locaux, vous créez un environnement hybride. Un environnement hybride peut vous aider lors de la migration d’utilisateurs ou d’informations vers Microsoft 365, ou vous pouvez continuer à avoir des utilisateurs ou des informations sur site et d’autres dans le cloud. Pour plus d’informations sur les environnements hybrides, voir [le cloud hybride.](../solutions/cloud-architecture-models.md#hybrid)

Vous pouvez également utiliser les conseillers Azure Active Directory (Azure AD) pour obtenir des instructions de configuration personnalisées dans le Centre d'administration Microsoft 365 (vous devez être Microsoft 365) :

- [Guide de configuration d’Azure AD](https://aka.ms/aadpguidance)
- [Synchroniser les utilisateurs à partir de l’annuaire de votre organisation](https://aka.ms/aadconnectpwsync)
- [Conseiller en déploiement des services AD FS (Active Directory Federation Services)](https://aka.ms/adfsguidance)
   
## <a name="before-you-begin"></a>Avant de commencer

Avant d’intégrer Microsoft 365 et un environnement local, vous devez également planifier le réseau et régler [les performances.](network-planning-and-performance.md) Vous souhaitez également comprendre les modèles [d’identité disponibles.](about-microsoft-365-identity.md) 

Consultez gérer Microsoft 365 pour obtenir la liste des [outils](manage-microsoft-365-accounts.md) que vous pouvez utiliser pour gérer Microsoft 365 comptes d’utilisateurs. 
  
## <a name="integrate-microsoft-365-with-ad-ds"></a>Intégrer Microsoft 365 avec AD DS

Si vous avez des comptes d’utilisateurs dans AD DS, vous ne souhaitez pas re-créer tous ces comptes dans Microsoft 365 et risquez d’introduire des différences ou des erreurs entre les environnements. La synchronisation d’annuaires vous permet de refléter ces comptes entre vos environnements locaux et en ligne. Avec la synchronisation d’annuaires, vos utilisateurs n’ont pas besoin de mémoriser de nouvelles informations pour chaque environnement, et vous n’avez pas besoin de créer ou de mettre à jour des comptes deux fois. Vous devrez préparer [votre annuaire local pour](prepare-for-directory-synchronization.md) la synchronisation d’annuaires.
  
![Utilisez la synchronisation d’annuaires pour synchroniser les informations de compte d’utilisateur local et en ligne.](../media/microsoft-365-integration/directory-synchronization.png)
  
Si vous souhaitez que les utilisateurs puissent se connecter à Microsoft 365 avec leurs informations d’identification sur site, vous pouvez également configurer l' utilisateur sso. Avec l’authentification Microsoft 365 est configuré pour faire confiance à l’environnement local pour l’authentification des utilisateurs.
  
![Avec l' sign-on unique, le même compte est disponible dans les environnements locaux et en ligne.](../media/microsoft-365-integration/single-sign-on.png)

### <a name="directory-synchronization-with-or-without-password-hash-synchronization-or-pass-through-authentication-pta"></a>Synchronisation d’annuaires avec ou sans synchronisation de hachage de mot de passe ou authentification directe (PTA)

Un utilisateur se connecte à son environnement local avec son compte d’utilisateur (domaine \nom d’utilisateur). Lorsqu’ils Microsoft 365, ils doivent se connecter à nouveau avec leur compte scolaire ou scolaire (user@domain.com). Le nom d’utilisateur est le même dans les deux environnements. Lorsque vous ajoutez phs ou PTA, l’utilisateur a le même mot de passe pour les deux environnements, mais devra fournir à nouveau ces informations d’identification lors de la connexion à Microsoft 365. La synchronisation d’annuaires avec PHS est la synchronisation d’annuaires la plus couramment utilisée.

Pour configurer la synchronisation d’annuaires, utilisez Azure AD Connecter. Pour obtenir des instructions, voir Configurer la synchronisation d’annuaires [pour Microsoft 365](set-up-directory-synchronization.md) et [Azure AD Connecter avec des paramètres express.](/azure/active-directory/hybrid/how-to-connect-install-express)

En savoir plus [sur la préparation de la synchronisation d’annuaires Microsoft 365](prepare-for-directory-synchronization.md).

### <a name="directory-synchronization-with-sso"></a>Synchronisation d’annuaires avec sso

Un utilisateur se connecte à son environnement local avec son compte d’utilisateur. Lorsqu’ils se connectent à Microsoft 365, ils sont connectés automatiquement ou ils se connectent à l’aide des mêmes informations d’identification qu’ils utilisent pour leur environnement local (domaine \nom d’utilisateur).

Pour configurer l' sso, vous utilisez également Azure AD Connecter. Pour obtenir des instructions, voir [Installation personnalisée d’Azure AD Connecter](/azure/active-directory/hybrid/how-to-connect-install-custom).

Pour plus d’informations, [voir l' sign-on unique.](/azure/active-directory/manage-apps/what-is-single-sign-on)

## <a name="azure-ad-connect"></a>Azure AD Connect

Azure AD Connecter versions antérieures des outils d’intégration d’identité tels que DirSync et Azure AD Sync. Si vous souhaitez mettre à jour Azure Active Directory synchronisation avec Azure AD Connecter, consultez les instructions de mise [à niveau.](/azure/active-directory/hybrid/how-to-dirsync-upgrade-get-started) 

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de Microsoft 365 Entreprise](microsoft-365-overview.md)