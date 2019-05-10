---
title: Activer la gestion des appareils Windows 10 associés à un domaine par Microsoft 365 Business
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- M365-identity-device-management
ms.custom:
- Adm_O365
- Core_O365Admin_Migration
- MiniMaven
- MSB365
search.appverid:
- BCS160
- MET150
ms.assetid: 9b4de218-f1ad-41fa-a61b-e9e8ac0cf993
description: Découvrez comment activer Microsoft 365 pour protéger les appareils locaux Windows 10.
ms.openlocfilehash: 661e5bf8205a661eb4382b4bdd8fcf3a54ecc12f
ms.sourcegitcommit: db1dfb2df2c2f7beced3b57bc772d106c189e88a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2019
ms.locfileid: "33660306"
---
# <a name="enable-domain-joined-windows-10-devices-to-be-managed-by-microsoft-365-business"></a>Activer la gestion des appareils Windows 10 associés à un domaine par Microsoft 365 Business

Si votre organisation utilise Windows Server Active Directory en local, vous pouvez configurer Microsoft 365 entreprise pour protéger vos appareils Windows 10, tout en conservant l’accès aux ressources locales qui nécessitent une authentification locale. Vous pouvez configurer cette configuration en commençant par synchroniser Active Directory avec Azure Active Directory, puis en enregistrant les appareils Windows 10 avec Azure AD et en les inscrivant pour la gestion des appareils mobiles par Microsoft 365 entreprise.
  
## <a name="set-up-domain-joined-devices-to-be-managed-by-microsoft-365-business"></a>Configurer les appareils joints à un domaine pour qu’ils soient gérés par Microsoft 365 Business

Pour configurer les appareils joints à un domaine de votre organisation afin de tirer parti des fonctionnalités fournies par Azure Active Directory en plus d’Active Directory en local, vous pouvez implémenter des **appareils joints Azure ad hybrides**. Il s’agit des appareils qui sont joints à la fois à votre Active Directory local et à votre Azure Active Directory. Les appareils joints Azure AD hybrides peuvent être protégés et gérés par Microsoft 365 Business. 
  
Suivez les étapes ci-dessous pour faire en sorte que les appareils Windows 10 hybrides se joignent à Azure AD et soient gérés par Microsoft 365 Business.
  
1. Pour synchroniser vos utilisateurs, groupes et contacts à partir d’Active Directory local avec Azure Active Directory, exécutez l’Assistant synchronisation d’annuaires et Azure Active Directory Connect comme décrit dans [set up Directory Synchronization for Office 365](https://support.office.com/article/1b3b5318-6977-42ed-b5c7-96fa74b08846).
    
    > [!NOTE]
    > Les étapes sont exactement les mêmes pour Microsoft 365 Business. 
  
2. Avant d’effectuer l’étape 3 pour permettre aux appareils Windows 10 d’être associés à Azure AD hybride, vous devez vous assurer que vous remplissez les conditions préalables suivantes:

   - Vous exécutez la dernière version d’Azure AD Connect.

   - Azure AD Connect a synchronisé tous les objets ordinateur des appareils que vous souhaitez associer à Azure AD. Si les objets ordinateur appartiennent à des unités d’organisation (UO) spécifiques, assurez-vous également que ces unités d’organisation sont définies pour la synchronisation dans Azure AD Connect.
    
3. Enregistrez les appareils Windows 10 associés à un domaine pour qu’ils soient associés à Azure AD et inscrivez-les pour la gestion des appareils mobiles par Intune (Microsoft 365 Business):
    
4. Suivez les instructions pas à pas dans la [procédure de configuration des appareils joints Azure Active Directory hybrides](https://go.microsoft.com/fwlink/p/?linkid=872870). Cela permettra la synchronisation de votre annuaire Active Directory sur site avec des ordinateurs Windows 10 et rendez-les en nuage prêts.
    
5. Pour inscrire un appareil Windows 10 pour la gestion des appareils mobiles, reportez-vous à la rubrique [inscrire un appareil Windows 10 avec Intune à l’aide d’une stratégie de groupe](https://go.microsoft.com/fwlink/p/?linkid=872871) pour obtenir des instructions. Vous pouvez définir la stratégie de groupe au niveau d’un ordinateur local ou pour des opérations en bloc, vous pouvez créer ce paramètre de stratégie de groupe sur votre serveur de contrôleur de domaine.