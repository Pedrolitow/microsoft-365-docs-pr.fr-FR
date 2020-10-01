---
title: Afficher l’état de la synchronisation d’annuaires dans Microsoft 365
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
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED150
ms.assetid: 18be3b98-34ae-47be-9337-ab6c3fb372ac
description: Dans cet article, Découvrez comment vérifier l’état de votre synchronisation d’annuaires dans Office 365.
ms.openlocfilehash: 7577ed358a262d5b0ef2932bc73cf61941bec31b
ms.sourcegitcommit: 04c4252457d9b976d31f53e0ba404e8f5b80d527
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2020
ms.locfileid: "48326948"
---
# <a name="view-directory-synchronization-status-in-microsoft-365"></a>Afficher l’état de la synchronisation d’annuaires dans Microsoft 365

Si vous avez intégré vos services de domaine Active Directory (AD DS) sur site à Azure Active Directory (Azure AD) en synchronisant votre environnement local avec Microsoft 365, vous pouvez également vérifier l’état de votre synchronisation.
  
## <a name="view-directory-synchronization-status"></a>Consulter l’état de synchronisation des annuaires

- Connectez-vous au [Centre d’administration Microsoft 365](https://admin.microsoft.com) et choisissez **DirSync Status** sur la page d’accueil.
- Vous pouvez également **accéder à utilisateurs** \> **actifs**, puis, sur la page **utilisateurs actifs** , sélectionner plus de **More** \> **synchronisation d’annuaires**. Dans le volet **synchronisation d’annuaires** , sélectionnez **accéder à la gestion DirSync**.

## <a name="information-on-the-manage-directory-synchronization-page"></a>Informations sur la page gérer la synchronisation d’annuaires

Le tableau suivant répertorie les fonctionnalités sur lesquelles vous pouvez obtenir des informations sur la page.
  
En cas de problème avec la synchronisation d’annuaires, les erreurs sont également répertoriées sur cette page. Pour plus d’informations sur les différentes erreurs que vous pouvez rencontrer, consultez la rubrique [identifier les erreurs de synchronisation d’annuaires dans Microsoft 365](identify-directory-synchronization-errors.md).
  
|Item|Objet|
|:-----|:-----|
|**Domaines vérifiés** | Nombre de domaines de votre client Microsoft 365 que vous avez vérifié. |
|**Domaines non vérifiés** | Les domaines que vous avez ajoutés, mais qui n’ont pas été vérifiés. |
|**Synchronisation d’annuaires activée** |True ou false. Indique si la synchronisation d’annuaires est activée. |
|**Dernière synchronisation d’annuaires** | Dernière exécution de la synchronisation d’annuaires. Affichera un avertissement et un lien vers un outil de dépannage Si la dernière synchronisation remonte à plus de trois jours. |
|**Synchronisation de mot de passe activée** | True ou false. Indique si la synchronisation de hachage de mot de passe s’est déplacée entre notre client local et votre client Microsoft 365. |
|**Dernière synchronisation de mot de passe** | Dernière exécution de la synchronisation de hachage de mot de passe. Affichera un avertissement et un lien vers un outil de dépannage Si la dernière synchronisation remonte à plus de trois jours. |
|**Version du client de synchronisation d’annuaires** | Contient un lien de téléchargement si une nouvelle version d’Azure AD Connect a été publiée. |
|**Compte de service de synchronisation d’annuaires** | Affiche le nom de votre compte de service de synchronisation d’annuaires Microsoft 365. |
|||

## <a name="monitor-synchronization-health"></a>Surveiller l’état de la synchronisation

Dans cette section, vous allez installer un agent d’intégrité Azure AD Connect sur chacun de vos contrôleurs de domaine AD DS pour surveiller votre infrastructure d’identité et les services de synchronisation fournis par Azure AD Connect. Les informations de surveillance sont disponibles sur un portail Azure AD Connect Health, où vous pouvez afficher les alertes, surveiller les performances, analyser les utilisations, etc.

La décision de conception clé concernant l’utilisation d’Azure AD Connect Health est basée sur la manière dont vous utilisez Azure AD Connect :

- Si vous utilisez de nouveau l’option d’**authentification gérée**, commencez avec la rubrique relative à l’[utilisation d’Azure AD Connect Health avec la synchronisation](https://docs.microsoft.com/azure/active-directory/connect-health/active-directory-aadconnect-health-sync) pour comprendre et configurer Azure AD Connect Health.
- Si vous synchronisez uniquement les noms des comptes et des groupes à l’aide de l’**authentification fédérée** avec Active Directory Federation Services (AD FS), commencez avec la rubrique [Utilisation d’Azure AD Connect Health avec AD FS](https://docs.microsoft.com/azure/active-directory/connect-health/active-directory-aadconnect-health-adfs) pour comprendre et configurer Azure AD Connect Health.

Lorsque vous avez terminé, vous disposez des éléments suivants :

- l’agent Azure AD Connect Health installé sur vos serveurs de fournisseur d’identité local ;
- le portail Azure AD Connect Health qui affiche l’état actuel de vos activités d’infrastructure et de synchronisation locales avec le client Azure AD pour votre abonnement Microsoft 365.

