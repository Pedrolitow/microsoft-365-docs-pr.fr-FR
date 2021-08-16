---
title: Afficher l’état de synchronisation d’annuaires dans Microsoft 365
ms.author: kvice
author: kelleyvice-msft
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
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED150
ms.assetid: 18be3b98-34ae-47be-9337-ab6c3fb372ac
description: Dans cet article, découvrez comment vérifier l’état de la synchronisation d’annuaires dans Office 365.
ms.openlocfilehash: 0fddffc667e4fc23b2c7663e70fb5e60c49814a2
ms.sourcegitcommit: e269371de759a1a747c9f292775463aa11415f25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/16/2021
ms.locfileid: "58355843"
---
# <a name="view-directory-synchronization-status-in-microsoft-365"></a>Afficher l’état de synchronisation d’annuaires dans Microsoft 365

Si vous avez intégré vos services de domaine Active Directory (AD DS) locaux à Azure Active Directory (Azure AD) en synchronisant votre environnement local avec Microsoft 365, vous pouvez également vérifier l’état de votre synchronisation.
  
## <a name="view-directory-synchronization-status"></a>Consulter l’état de synchronisation des annuaires

- Connectez-vous [au Centre d’administration Microsoft 365](https://admin.microsoft.com) puis choisissez État de la **DirSync** sur la page d’accueil.
- Vous pouvez également vous  rendre sur Utilisateurs actifs et, sur la page Utilisateurs actifs, choisir Plus de synchronisation \>    \> **d’annuaires.** Dans le volet Synchronisation d’annuaires, choisissez **Go to DirSync management**. 

## <a name="information-on-the-manage-directory-synchronization-page"></a>Informations sur la page Gérer la synchronisation d’annuaires

Le tableau suivant répertorie les fonctionnalités dont vous pouvez obtenir des informations sur la page.
  
En cas de problème avec votre synchronisation d’annuaires, les erreurs sont également répertoriées sur cette page. Pour plus d’informations sur les différentes erreurs que vous pouvez rencontrer, voir Identifier les erreurs de synchronisation d’annuaires [dans Microsoft 365](identify-directory-synchronization-errors.md).
  
|Item|Objet|
|:-----|:-----|
|**Domaines vérifiés** | Nombre de domaines dans votre client Microsoft 365 que vous avez vérifié que vous possédez. |
|**Domaines non vérifiés** | Domaines que vous avez ajoutés, mais pas vérifiés. |
|**Synchronisation d’annuaires activée** |True ou False. Spécifie si vous avez activé la synchronisation d’annuaires. |
|**Dernière synchronisation d’annuaires** | Dernière synchronisation d’annuaires. Affiche un avertissement et un lien vers un outil de dépannage si la dernière synchronisation a eu lieu il y a plus de trois jours. |
|**Synchronisation de mot de passe activée** | True ou False. Spécifie si vous disposez d’une synchronisation de hachage de mot de passe entre notre site local et votre Microsoft 365 client. |
|**Dernière synchronisation de mot de passe** | Dernière synchronisation de hachage du mot de passe. Affiche un avertissement et un lien vers un outil de dépannage si la dernière synchronisation a eu lieu il y a plus de trois jours. |
|**Version du client de synchronisation d’annuaires** | Contient un lien de téléchargement si une nouvelle version d’Azure AD Connecter a été publiée. |
|**Compte de service de synchronisation d’annuaires** | Affiche le nom de votre compte Microsoft 365 service de synchronisation d’annuaires. |
|||

## <a name="monitor-synchronization-health"></a>Surveiller l’état de la synchronisation

Dans cette section, vous allez installer un agent d’intégrité Azure AD Connect sur chacun de vos contrôleurs de domaine AD DS pour surveiller votre infrastructure d’identité et les services de synchronisation fournis par Azure AD Connect. Les informations de surveillance sont disponibles sur un portail Azure AD Connect Health, où vous pouvez afficher les alertes, surveiller les performances, analyser les utilisations, etc.

La décision de conception clé concernant l’utilisation d’Azure AD Connect Health est basée sur la manière dont vous utilisez Azure AD Connect :

- Si vous utilisez de nouveau l’option d’**authentification gérée**, commencez avec la rubrique relative à l’[utilisation d’Azure AD Connect Health avec la synchronisation](/azure/active-directory/connect-health/active-directory-aadconnect-health-sync) pour comprendre et configurer Azure AD Connect Health.
- Si vous synchronisez uniquement les noms des comptes et des groupes à l’aide de l’**authentification fédérée** avec Active Directory Federation Services (AD FS), commencez avec la rubrique [Utilisation d’Azure AD Connect Health avec AD FS](/azure/active-directory/connect-health/active-directory-aadconnect-health-adfs) pour comprendre et configurer Azure AD Connect Health.

Lorsque vous avez terminé, vous aurez :

- l’agent Azure AD Connect Health installé sur vos serveurs de fournisseur d’identité local ;
- le portail Azure AD Connect Health qui affiche l’état actuel de vos activités d’infrastructure et de synchronisation locales avec le client Azure AD pour votre abonnement Microsoft 365.