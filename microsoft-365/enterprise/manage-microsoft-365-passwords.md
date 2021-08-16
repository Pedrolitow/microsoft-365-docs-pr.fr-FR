---
title: Gérer les Microsoft 365 de compte d’utilisateur
ms.author: kvice
author: kelleyvice-msft
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
description: Découvrez comment gérer les mots de passe Microsoft 365 compte d’utilisateur.
ms.openlocfilehash: 85d3c42a7aca977472e44fce63af3968fc8e9705
ms.sourcegitcommit: e269371de759a1a747c9f292775463aa11415f25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/16/2021
ms.locfileid: "58356659"
---
# <a name="manage-microsoft-365-user-account-passwords"></a>Gérer les Microsoft 365 de compte d’utilisateur

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Vous pouvez gérer Microsoft 365 mots de passe de compte d’utilisateur de différentes manières, en fonction de la configuration de votre identité. Vous pouvez gérer les comptes d’utilisateurs dans [Centre d’administration Microsoft 365,](../admin/add-users/index.yml)dans les services de domaine Active Directory (AD DS) ou dans le Centre d’administration Azure Active Directory (Azure AD).

## <a name="plan-for-where-and-how-you-will-manage-your-user-account-passwords"></a>Planifier l’endroit et la façon dont vous allez gérer les mots de passe de votre compte d’utilisateur

L’endroit où et comment vous pouvez gérer vos comptes d’utilisateur dépend du modèle d’identité que vous souhaitez utiliser pour votre Microsoft 365. Les deux modèles sont uniquement cloud et hybrides.
  
### <a name="cloud-only"></a>Cloud uniquement

Vous gérez les mots de passe de compte d’utilisateur dans :

- [Le Centre d’administration Microsoft 365](../admin/add-users/index.yml)
- Centre d’administration Azure AD
    
### <a name="hybrid"></a>Hybride

Avec l’identité hybride, les mots de passe sont stockés dans AD DS. Vous devez donc utiliser les outils AD DS locaux pour gérer les mots de passe de compte d’utilisateur. Même lors de l’utilisation de la synchronisation de hachage de mot de passe (PHS), dans laquelle Azure AD stocke une version hachée de la version déjà hachée dans AD DS, vous et les utilisateurs devez gérer leurs mots de passe dans AD DS.

Avec [l’écriture écriture par](#pw_writeback)mot de passe, vos utilisateurs peuvent modifier leurs mots de passe AD DS via Azure AD.

## <a name="prevent-bad-passwords"></a>Éviter les mots de passe incorrects

Tous vos utilisateurs doivent utiliser le [guide des mots de passe Microsoft](https://www.microsoft.com/research/publication/password-guidance) pour créer leurs mots de passe de compte d'utilisateur.

Pour empêcher les utilisateurs de créer un mot de passe facile à déterminer, optez pour la protection par mot de passe Azure AD qui utilise une liste globale de mots de passe interdits et une liste personnalisée facultative de mots de passe interdits que vous spécifiez. Par exemple, vous pouvez spécifier des termes propres à votre organisation, tels que :

- Noms de marques
- Noms de produits
- Emplacements (par exemple, le siège social de l’entreprise)
- Termes internes spécifiques à l’entreprise
- Abréviations dotées d’une signification spécifique à l’entreprise.

Vous pouvez interdire les mots de passe incorrects dans [le cloud](/azure/active-directory/authentication/concept-password-ban-bad) et pour vos [services AD DS locaux.](/azure/active-directory/authentication/concept-password-ban-bad-on-premises)

## <a name="simplify-user-sign-in"></a>Simplifiez la connexion utilisateur

Azure AD Seamless Single Sign-On (Azure AD Seamless SSO) fonctionne avec PHS et l’authentification Pass-Through (PTA), pour permettre à vos utilisateurs de se connecter à des services qui utilisent des comptes d’utilisateur Azure AD sans avoir à taper leur mot de passe et, dans de nombreux cas, leur nom d’utilisateur. Cela donne à vos utilisateurs un accès facile aux applications basées sur le cloud, telles qu’Office 365, sans nécessiter des composants supplémentaires en local, tels que des serveurs de fédération d’identité.

Vous configurez l’authentification unique transparente Azure AD avec l’outil Azure AD Connect. Reportez-vous aux [instructions pour configurer l’authentification unique transparente d’Azure AD](/azure/active-directory/connect/active-directory-aadconnect-sso-quick-start).

<a name="pw_writeback"></a>
## <a name="simplify-password-updates-to-ad-ds"></a>Simplifier les mises à jour de mot de passe pour AD DS

Avec la réinitialisation du mot de passe, vous pouvez autoriser les utilisateurs à réinitialiser leur mot de passe via Azure AD, qui est ensuite répliqué dans AD DS. Les utilisateurs n’ont pas besoin d’accéder à leurs services AD DS locaux pour mettre à jour leurs mots de passe. C’est utile pour les utilisateurs itinérants ou distants qui ne possèdent pas de connexion d’accès à distance au réseau local.

L’écriture différée de mot de passe est requise pour exploiter pleinement les fonctionnalités Azure AD Identity Protection, comme obliger les utilisateurs à modifier leur mot de passe en local lorsqu’un risque élevé de compromission de compte a été détecté.

Pour obtenir plus d’informations et les instructions de configuration, consultez l’article [Azure AD SSPR avec l’écriture différée de mot de passe](/azure/active-directory/active-directory-passwords-writeback).

>[!Note]
>Procédez à la mise à niveau vers la dernière version d’Azure AD Connect pour vous assurer la meilleure expérience possible et les nouvelles fonctionnalités dès leur diffusion. Pour obtenir plus d’informations, consultez l’article [Installation personnalisée d’Azure AD Connect](/azure/active-directory/connect/active-directory-aadconnect-get-started-custom).
>

## <a name="simplify-password-resets"></a>Simplifiez les réinitialisations du mot de passe

La réinitialisation du mot de passe en libre-service (SSPR) permet aux utilisateurs de réinitialiser ou de déverrouiller leur mot de passe ou leur compte. Le système inclut des rapports détaillés de suivi d’accès au système, ainsi que des notifications pour vous prévenir de toute utilisation malveillante ou de tout abus. Vous devez activer [l’écriture écriture par mot de](#pw_writeback) passe avant de pouvoir déployer les réinitialisations de mot de passe.

Reportez-vous aux [Instructions pour activer la réinitialisation de mot de passe](/azure/active-directory/authentication/howto-sspr-deployment).