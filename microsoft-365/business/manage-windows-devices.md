---
title: Permettre à un domaine aux périphériques Windows 10 devant être gérés par Microsoft 365 entreprise
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom:
- Adm_O365
- Core_O365Admin_Migration
- MiniMaven
- MSB365
search.appverid:
- BCS160
- MET150
ms.assetid: 9b4de218-f1ad-41fa-a61b-e9e8ac0cf993
description: Découvrez comment activer Microsoft 365 protéger AD local joints périphériques Windows 10.
ms.openlocfilehash: 6e66a2c5417c9037232c1ada654d4cac3c520607
ms.sourcegitcommit: e491c4713115610cbe13d2fbd0d65e1a41c34d62
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "26866988"
---
# <a name="enable-domain-joined-windows-10-devices-to-be-managed-by-microsoft-365-business"></a>Permettre à un domaine aux périphériques Windows 10 devant être gérés par Microsoft 365 entreprise

Si votre organisation utilise Windows Server Active Directory sur site, vous pouvez configurer Microsoft 365 Business pour protéger vos périphériques Windows 10, tout en conservant l’accès aux ressources locales qui nécessitent une authentification locale. Vous pouvez configurer ce paramètre en première synchronisation Active Directory avec Azure Active Directory, suivi d’inscription les périphériques Windows 10 avec Azure AD et leur inscription pour la gestion des appareils mobiles par Microsoft 365 Business.
  
## <a name="set-up-domain-joined-devices-to-be-managed-by-microsoft-365-business"></a>Configurer les périphériques liés à un domaine devant être gérés par Microsoft 365 entreprise

Pour configurer les périphériques liés à un domaine de votre organisation afin de bénéficier des fonctionnalités fournies par Azure Active Directory en plus des locaux Active Directory, vous pouvez implémenter **hybride Azure AD participé à des périphériques**. Il s’agit de périphériques qui sont joints à la fois sur site Active Directory et Azure Active Directory. Hybride Azure AD joint périphériques peuvent être protégés et gérées par Microsoft 365 Business... 
  
Effectuez les étapes ci-dessous pour rendre vos périphériques Windows 10 hybride Azure AD joint et gérées par Microsoft 365 Business.
  
1. Pour synchroniser vos utilisateurs, groupes et des contacts à partir d’Active Directory local dans Azure Active Directory, exécutez l’Assistant synchronisation d’annuaires et Azure Active Directory se connecter comme décrit dans [configurer la synchronisation d’annuaires pour Office 365](https://support.office.com/article/1b3b5318-6977-42ed-b5c7-96fa74b08846).
    
    > [!NOTE]
    > Les étapes sont exactement les mêmes pour Microsoft 365 Business. 
  
2. Avant d’effectuer l’étape 3 pour permettre aux périphériques Windows 10 être hybride Azure AD lié, vous devez respecter les conditions préalables suivantes :
    
   - Vous exécutez la dernière version d’Azure AD se connecter.
    
   - Se connecter Azure AD a synchronisé tous les objets ordinateur des périphériques devant être hybride joints Azure AD. Se connecter également si les objets ordinateur appartenant à des unités d’organisation (UO), assurez-vous que ces unités d’organisation sont définies pour la synchronisation dans Azure AD.
    
3. Inscrivez à un domaine Windows 10 les périphériques existants pour être hybride Azure AD joint et les inscrire pour la gestion des appareils mobiles par Intune (365 Microsoft Business) :
    
4. Suivez les instructions étape par étape comment [configurer les périphériques d’Azure Active Directory joint hybride](https://go.microsoft.com/fwlink/p/?linkid=872870). Cela permettra la synchronisation d’Active Directory local joint des ordinateurs Windows 10 et rendre prêt en nuage.
    
5. Pour inscrire un appareil Windows 10 pour la gestion des appareils mobiles, voir [inscrire un appareil Windows 10 avec Intune à l’aide d’une stratégie de groupe](https://go.microsoft.com/fwlink/p/?linkid=872871) pour obtenir des instructions. Vous pouvez définir la stratégie de groupe sur un ordinateur local au niveau ou pour les opérations en bloc, vous pouvez créer ce paramètre de stratégie de groupe sur votre serveur de contrôleur de domaine. 
    

