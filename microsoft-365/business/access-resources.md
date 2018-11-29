---
title: Accès aux ressources à partir d’un périphérique joint à AD Azure dans Microsoft 365 Business sur site
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom:
- Core_O365Admin_Migration
- MiniMaven
- MSB365
search.appverid:
- BCS160
- MET150
ms.assetid: b0f4d010-9fd1-44d0-9d20-fabad2cdbab5
description: Découvrez comment accéder aux ressources locales telles que les applications métier, des partages de fichiers et des imprimantes à partir d’Azure Active Directory joint périphérique Windows 10.
ms.openlocfilehash: 0a5d4b0828888fcb99676223000c446479f84ddc
ms.sourcegitcommit: eb1a77e4cc4e8f564a1c78d2ef53d7245fe4517a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2018
ms.locfileid: "26866866"
---
# <a name="access-on-premises-resources-from-an-azure-ad-joined-device-in-microsoft-365-business"></a>Accès aux ressources à partir d’un périphérique joint à AD Azure dans Microsoft 365 Business sur site

Tout périphérique 10 Windows Azure Active Directory joint auront accès à toutes les ressources en nuage tels que vos applications Office 365 et peut être protégé par Microsoft 365 Business. Pour également autoriser l’accès aux ressources locales telles que des applications, des partages de fichiers et des imprimantes ligne de métier (LOB), vous devez synchroniser Active Directory local avec Azure Active Directory à l’aide [d’Azure AD se connecter](https://docs.microsoft.com/en-us/azure/active-directory/connect/active-directory-aadconnect). Voir [Introduction à la gestion des périphériques dans Azure Active Directory](https://docs.microsoft.com/en-us/azure/active-directory/device-management-introduction) pour en savoir plus. 
  
## <a name="run-azure-ad-connect"></a>Exécuter Azure AD

Effectuez les étapes suivantes pour permettre aux appareils Azure AD joint de votre organisation d’accéder aux ressources locales.
  
1. Pour synchroniser vos utilisateurs, groupes et des contacts à partir d’Active Directory local dans Azure Active Directory, exécutez l’Assistant synchronisation d’annuaires et Azure AD se connecter en tant que décrit dans [configurer la synchronisation d’annuaires pour Office 365](https://support.office.com/article/1b3b5318-6977-42ed-b5c7-96fa74b08846).
    
2. À l’issue de la synchronisation d’annuaires, assurez-vous que les périphériques Windows 10 de votre organisation sont Azure AD lié. Cette étape est effectuée individuellement sur chaque périphérique Windows 10. Pour plus d’informations, voir [configurer les périphériques de Windows pour les utilisateurs professionnels 365 de Microsoft](set-up-windows-devices.md) . 
    
3. Une fois les périphériques 10 Windows Azure AD lié, chaque utilisateur doit redémarrer leurs périphériques et la connexion avec leurs informations d’identification Microsoft 365 Business. Tous les périphériques maintenant auront accès à ainsi que les ressources locales.
    
Des étapes supplémentaires sont nécessaires pour accéder aux ressources pour Azure AD joint périphériques sur site. Il s’agit des fonctionnalités intégrées dans Windows 10. 
  
Si votre organisation n’est pas prête à déployer dans la Azure AD joints périphérique Configuration décrite ci-dessus, pensez à configurer [configuration hybride Azure AD joint du périphérique](manage-windows-devices.md).
  
### <a name="considerations-when-joining-your-windows-devices-to-azure-ad"></a>Considérations relatives à la participation à vos périphériques Windows pour Azure AD

Si vous êtes Azure AD joindre un appareil Windows qui a été précédemment à un domaine ou un groupe de travail, vous devez prendre en compte les limitations suivantes :
  
- Lorsqu’un périphérique Azure AD joint, il crée un nouvel utilisateur sans faire référence à un profil existant. Pour résoudre ce problème, les profils doivent être migrées manuellement. Un profil utilisateur contient des informations telles que des Favoris, les fichiers locaux, les paramètres du navigateur, les paramètres du menu Démarrer, etc.. Une meilleure approche consiste à trouver un outil tiers pour mapper les fichiers et paramètres existants dans le nouveau profil
    
- Si le périphérique est à l’aide des objets de stratégie de groupe (GPO), certains objets de stratégie de groupe peut-être pas un comparables de [Fournisseur de services de Configuration](https://docs.microsoft.com/windows/configuration/provisioning-packages/how-it-pros-can-use-configuration-service-providers) Intune. Exécutez l' [outil MMAT](https://www.microsoft.com/download/details.aspx?id=45520) pour rechercher les fournisseurs comparables pour les objets GPO existants. 
    
- Les utilisateurs ne pourront pas s’authentifier sur les applications qui dépendent de l’authentification Active Directory. Pour traiter cette évaluation de l’utilisation d’une application héritée et prendre en compte la mise à jour vers une application qui utilise une authentification moderne si possible.
    
- Recherche d’imprimante Active Directory ne fonctionne pas. Pour résoudre ce problème, fournir des chemins d’accès de l’imprimante directe pour tous les utilisateurs ou tirer parti [d’Impression de nuage hybride](https://docs.microsoft.com/windows-server/administration/hybrid-cloud-print/hybrid-cloud-print-deploy).
    

