---
title: Intégration de Microsoft 365 à des environnements locaux
ms.author: kvice
author: kelleyvice-msft
manager: scotv
audience: Admin
ms.topic: article
ms.service: microsoft-365-enterprise
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
description: Dans cet article, découvrez comment intégrer Microsoft 365 à vos services d’annuaire existants et à vos environnements locaux.
ms.openlocfilehash: 69d21a5da22db7ae51ab28df548f832b58ca95f6
ms.sourcegitcommit: e9323a90a1156c10b037abca3e16d7367ef92dd7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2022
ms.locfileid: "67570158"
---
# <a name="microsoft-365-integration-with-on-premises-environments"></a>Intégration de Microsoft 365 à des environnements locaux

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Vous pouvez intégrer Microsoft 365 à vos services de domaine Active Directory local existants (AD DS) et à des installations locales de Exchange Server, Skype Entreprise Server 2015 ou SharePoint Server.
  
 - Quand vous intégrez AD DS, vous pouvez synchroniser et gérer des comptes d’utilisateur pour les deux environnements. Vous pouvez également ajouter la synchronisation de hachage de mot de passe (PHS) ou l’authentification unique (SSO) afin que les utilisateurs puissent se connecter aux deux environnements avec leurs informations d’identification locales.
 - Lorsque vous intégrez des produits serveur locaux, vous créez un environnement hybride. Un environnement hybride peut vous aider à migrer des utilisateurs ou des informations vers Microsoft 365, ou vous pouvez continuer à avoir des utilisateurs ou des informations locales et d’autres dans le cloud. Pour plus d’informations sur les environnements hybrides, consultez [cloud hybride](../solutions/cloud-architecture-models.md#hybrid).

Vous pouvez également utiliser les conseillers Azure Active Directory (Azure AD) pour obtenir des conseils d’installation personnalisés dans le Centre d'administration Microsoft 365 (vous devez être connecté à Microsoft 365) :

- [Guide d’installation d’Azure AD](https://aka.ms/aadpguidance)
- [Synchroniser les utilisateurs à partir du répertoire de votre organisation](https://aka.ms/aadconnectpwsync)
- [conseiller de déploiement Services ADFS (AD FS)](https://aka.ms/adfsguidance)
   
## <a name="before-you-begin"></a>Avant de commencer

Avant d’intégrer Microsoft 365 et un environnement local, vous devez également effectuer une [planification réseau et un réglage des performances](network-planning-and-performance.md). Vous souhaiterez également comprendre les [modèles d’identité](deploy-identity-solution-identity-model.md) disponibles. 

Consultez [gérer les comptes Microsoft 365](manage-microsoft-365-accounts.md) pour obtenir la liste des outils que vous pouvez utiliser pour gérer les comptes d’utilisateurs Microsoft 365. 
  
## <a name="integrate-microsoft-365-with-ad-ds"></a>Intégrer Microsoft 365 à AD DS

Si vous avez des comptes d’utilisateurs existants dans AD DS, vous ne souhaitez pas recréer tous ces comptes dans Microsoft 365 et risquez d’introduire des différences ou des erreurs entre les environnements. La synchronisation d’annuaires vous permet de mettre en miroir ces comptes entre vos environnements locaux et en ligne. Avec la synchronisation d’annuaires, vos utilisateurs n’ont pas besoin de mémoriser de nouvelles informations pour chaque environnement, et vous n’avez pas besoin de créer ou de mettre à jour des comptes deux fois. Vous devez [préparer votre répertoire local](prepare-for-directory-synchronization.md) pour la synchronisation d’annuaires.
  
![Utilisez la synchronisation d’annuaires pour synchroniser les informations de compte d’utilisateur locales et en ligne.](../media/microsoft-365-integration/directory-synchronization.png)
  
Si vous souhaitez que les utilisateurs puissent se connecter à Microsoft 365 avec leurs informations d’identification locales, vous pouvez également configurer l’authentification unique. Avec l’authentification unique, Microsoft 365 est configuré pour approuver l’environnement local pour l’authentification utilisateur.
  
![Avec l’authentification unique, le même compte est disponible dans les environnements locaux et en ligne.](../media/microsoft-365-integration/single-sign-on.png)

### <a name="directory-synchronization-with-or-without-password-hash-synchronization-or-pass-through-authentication-pta"></a>Synchronisation d’annuaires avec ou sans synchronisation de hachage de mot de passe ou authentification directe (PTA)

Un utilisateur se connecte à son environnement local avec son compte d’utilisateur (domaine\nom d’utilisateur). Lorsqu’ils se connectent à Microsoft 365, ils doivent se reconnecter avec leur compte professionnel ou scolaire (user@domain.com). Le nom d’utilisateur est le même dans les deux environnements. Lorsque vous ajoutez PHS ou PTA, l’utilisateur a le même mot de passe pour les deux environnements, mais devra fournir à nouveau ces informations d’identification lors de la connexion à Microsoft 365. La synchronisation d’annuaires avec PHS est la synchronisation d’annuaires la plus couramment utilisée.

Pour configurer la synchronisation d’annuaires, utilisez Azure AD Connect. Pour obtenir des instructions, consultez [Configurer la synchronisation d’annuaires pour Microsoft 365](set-up-directory-synchronization.md) et [Azure AD Connect avec des paramètres express](/azure/active-directory/hybrid/how-to-connect-install-express).

En savoir plus sur [la préparation de la synchronisation d’annuaires avec Microsoft 365](prepare-for-directory-synchronization.md).

### <a name="directory-synchronization-with-sso"></a>Synchronisation d’annuaires avec l’authentification unique

Un utilisateur se connecte à son environnement local avec son compte d’utilisateur. Lorsqu’ils accédent à Microsoft 365, ils sont connectés automatiquement ou ils se connectent à l’aide des mêmes informations d’identification qu’ils utilisent pour leur environnement local (domaine\nom d’utilisateur).

Pour configurer l’authentification unique, vous utilisez également Azure AD Connect. Pour obtenir des instructions, consultez [Installation personnalisée d’Azure AD Connect](/azure/active-directory/hybrid/how-to-connect-install-custom).

Pour plus d’informations, consultez [l’authentification unique](/azure/active-directory/manage-apps/what-is-single-sign-on).

## <a name="azure-ad-connect"></a>Azure AD Connect

Azure AD Connect remplace les versions antérieures des outils d’intégration d’identité tels que DirSync et Azure AD Sync. Si vous souhaitez effectuer une mise à jour d’Azure Active Directory Sync vers Azure AD Connect, consultez [les instructions de mise à niveau](/azure/active-directory/hybrid/how-to-dirsync-upgrade-get-started). 

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de Microsoft 365 Entreprise](microsoft-365-overview.md)