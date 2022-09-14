---
title: Afficher l’état de synchronisation d’annuaires dans Microsoft 365
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
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED150
ms.assetid: 18be3b98-34ae-47be-9337-ab6c3fb372ac
description: Dans cet article, découvrez comment vérifier l’état de votre synchronisation d’annuaires dans Office 365.
ms.openlocfilehash: 050c4f4abfb8e4d925af3d65117d6c9ae8cb26e7
ms.sourcegitcommit: 437461fa1d38ff9bb95dd8a1c5f0b94e8111ada2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2022
ms.locfileid: "67670474"
---
# <a name="view-directory-synchronization-status-in-microsoft-365"></a>Afficher l’état de synchronisation d’annuaires dans Microsoft 365

Si vous avez intégré votre Active Directory local Domain Services (AD DS) à Azure Active Directory (Azure AD) en synchronisant votre environnement local avec Microsoft 365, vous pouvez également vérifier l’état de votre synchronisation.
  
## <a name="view-directory-synchronization-status"></a>Consulter l’état de synchronisation des annuaires

- Connectez-vous au [Centre d'administration Microsoft 365](https://admin.microsoft.com) et choisissez **État DirSync** sur la page d’accueil.
- Vous pouvez également accéder aux **utilisateurs utilisateurs** \> **actifs** et, dans la page **Utilisateurs actifs** , sélectionner la synchronisation **Elipse** \> **Directory**. Dans le volet **Synchronisation d’annuaires** , **choisissez Accéder à la gestion DirSync**.

## <a name="information-on-the-manage-directory-synchronization-page"></a>Informations sur la page Gérer la synchronisation d’annuaires

Le tableau suivant répertorie les fonctionnalités sur laquelle vous pouvez obtenir des informations sur la page.
  
En cas de problème avec votre synchronisation d’annuaires, les erreurs sont également répertoriées sur cette page. Pour plus d’informations sur les différentes erreurs que vous pouvez rencontrer, consultez [Identifier les erreurs de synchronisation d’annuaires dans Microsoft 365](identify-directory-synchronization-errors.md).
  
|Élément|Objet|
|:-----|:-----|
|**Domaines vérifiés** | Nombre de domaines dans votre locataire Microsoft 365 que vous avez vérifiés vous possédez. |
|**Domaines non vérifiés** | Domaines que vous avez ajoutés, mais non vérifiés. |
|**Synchronisation d’annuaires activée** |True ou False. Spécifie si vous avez activé la synchronisation d’annuaires. |
|**Synchronisation d’annuaires la plus récente** | Dernière exécution de la synchronisation d’annuaires. Affiche un avertissement et un lien vers un outil de résolution des problèmes si la dernière synchronisation remonte à plus de trois jours. |
|**Synchronisation de mot de passe activée** | True ou False. Spécifie si vous avez une synchronisation de hachage de mot de passe entre notre environnement local et votre locataire Microsoft 365. |
|**Dernière synchronisation de mot de passe** | Dernière exécution de la synchronisation de hachage de mot de passe. Affiche un avertissement et un lien vers un outil de résolution des problèmes si la dernière synchronisation remonte à plus de trois jours. |
|**Version du client de synchronisation d’annuaires** | Contient un lien de téléchargement si une nouvelle version d’Azure AD Connect a été publiée. |
|**Compte de service de synchronisation d’annuaires** | Affiche le nom de votre compte de service de synchronisation d’annuaires Microsoft 365. |
|||

## <a name="monitor-synchronization-health"></a>Surveiller l’état de la synchronisation

Dans cette section, vous allez installer un agent d’intégrité Azure AD Connect sur chacun de vos contrôleurs de domaine AD DS pour surveiller votre infrastructure d’identité et les services de synchronisation fournis par Azure AD Connect. Les informations de surveillance sont disponibles sur un portail Azure AD Connect Health, où vous pouvez afficher les alertes, surveiller les performances, analyser les utilisations, etc.

La décision de conception clé concernant l’utilisation d’Azure AD Connect Health est basée sur la manière dont vous utilisez Azure AD Connect :

- Si vous utilisez de nouveau l’option d’**authentification gérée**, commencez avec la rubrique relative à l’[utilisation d’Azure AD Connect Health avec la synchronisation](/azure/active-directory/connect-health/active-directory-aadconnect-health-sync) pour comprendre et configurer Azure AD Connect Health.
- Si vous synchronisez uniquement les noms des comptes et des groupes à l’aide de l’**authentification fédérée** avec Active Directory Federation Services (AD FS), commencez avec la rubrique [Utilisation d’Azure AD Connect Health avec AD FS](/azure/active-directory/connect-health/active-directory-aadconnect-health-adfs) pour comprendre et configurer Azure AD Connect Health.

Une fois l’opération terminée, vous disposerez des opérations suivantes :

- l’agent Azure AD Connect Health installé sur vos serveurs de fournisseur d’identité local ;
- le portail Azure AD Connect Health qui affiche l’état actuel de vos activités d’infrastructure et de synchronisation locales avec le client Azure AD pour votre abonnement Microsoft 365.
