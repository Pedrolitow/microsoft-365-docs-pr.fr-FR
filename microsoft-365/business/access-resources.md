---
title: Accéder aux ressources locales à partir d’un appareil joint à Azure AD dans Microsoft 365 Business
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.collection: M365-subscription-management
localization_priority: Normal
ms.custom:
- Core_O365Admin_Migration
- MiniMaven
- MSB365
- OKR_SMB_M365
search.appverid:
- BCS160
- MET150
ms.assetid: b0f4d010-9fd1-44d0-9d20-fabad2cdbab5
description: Découvrez comment accéder à des ressources locales telles que des applications métier, des partages de fichiers et des imprimantes à partir d’un appareil Azure Active Directory joint à Windows 10.
ms.openlocfilehash: 2af5d4b4f84f39f5b157313e5b38ef030da7263d
ms.sourcegitcommit: 70e920f76526f47fc849df615de4569e0ac2f4be
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "38030531"
---
# <a name="access-on-premises-resources-from-an-azure-ad-joined-device-in-microsoft-365-business"></a>Accéder aux ressources locales à partir d’un appareil joint à Azure AD dans Microsoft 365 Business

Tous les appareils Windows 10 qui sont joints à Azure Active Directory auront accès à toutes les ressources basées sur le Cloud, telles que vos applications Office 365, et peuvent être protégées par Microsoft 365 Business. Pour autoriser également l’accès aux ressources locales telles que les applications métier, les partages de fichiers et les imprimantes, vous devez synchroniser votre annuaire Active Directory local avec Azure Active Directory à l’aide d' [Azure ad Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect). 

Pour en savoir plus, consultez la rubrique [Présentation de la gestion des appareils dans Azure Active Directory](https://docs.microsoft.com/azure/active-directory/device-management-introduction) .
Les étapes sont également résumées dans les sections suivantes.

## <a name="run-azure-ad-connect"></a>Exécuter Azure AD Connect

Procédez comme suit pour activer les appareils Azure AD joints de votre organisation pour accéder aux ressources locales.
  
1. Pour synchroniser vos utilisateurs, groupes et contacts à partir d’Active Directory local avec Azure Active Directory, exécutez l’Assistant synchronisation d’annuaires et Azure AD Connect comme décrit dans [set up Directory Synchronization for Office 365](https://support.office.com/article/1b3b5318-6977-42ed-b5c7-96fa74b08846).
    
2. Une fois la synchronisation d’annuaires terminée, assurez-vous que les appareils Windows 10 de votre organisation sont joints à Azure AD. Cette étape est effectuée individuellement sur chaque appareil Windows 10. Pour plus d’informations, consultez la rubrique [configurer des appareils Windows pour les utilisateurs professionnels de Microsoft 365](set-up-windows-devices.md) . 
    
3. Une fois que les appareils Windows 10 sont joints à Azure AD, chaque utilisateur doit redémarrer ses appareils et se connecter avec leurs informations d’identification de l’entreprise Microsoft 365. Tous les périphériques auront également accès aux ressources locales.
    
Aucune étape supplémentaire n’est requise pour accéder aux ressources locales pour les appareils joints à Azure AD. Il s’agit d’une fonctionnalité intégrée disponible dans Windows 10. 
  
Si votre organisation n’est pas prête à être déployée dans la configuration d’appareil joint Azure AD décrite ci-dessus, envisagez de configurer la [configuration hybride Azure ad jointe](manage-windows-devices.md)de l’appareil.
  
### <a name="considerations-when-joining-your-windows-devices-to-azure-ad"></a>Éléments à prendre en compte lors de la participation à des appareils Windows sur Azure AD

Si vous joignez Azure AD à un appareil Windows qui a déjà été joint à un domaine ou dans un groupe de travail, vous devez tenir compte des limitations suivantes :
  
- Lorsqu’un appareil Azure AD rejoint une jointure, il crée un utilisateur sans référence à un profil existant. Pour résoudre ce problème, les profils doivent être migrés manuellement. Un profil utilisateur contient des informations comme les favoris, les fichiers locaux, les paramètres du navigateur, les paramètres du menu Démarrer, etc. Une meilleure approche consiste à trouver un outil tiers pour mapper des fichiers et des paramètres existants sur le nouveau profil.

- Si l’appareil utilise des objets de stratégie de groupe (GPO), certains objets de stratégie de groupe ne disposent pas nécessairement d’un [fournisseur de services de configuration](https://docs.microsoft.com/windows/configuration/provisioning-packages/how-it-pros-can-use-configuration-service-providers) (CSP) comparable dans Intune. Exécutez l' [outil mmat](https://www.microsoft.com/download/details.aspx?id=45520) pour rechercher des fournisseurs de services cryptographiques comparables pour les objets de stratégie de groupe existants.

- Les utilisateurs ne peuvent pas s’authentifier aux applications qui dépendent de l’authentification Active Directory. Pour traiter cette évaluation à l’aide d’une application héritée et envisager d’effectuer une mise à jour vers une application qui utilise l’authentification moderne dans la mesure du possible.

- La découverte des imprimantes Active Directory ne fonctionnera pas. Pour résoudre ce problème, fournissez des chemins d’accès directs aux imprimantes pour tous les utilisateurs ou utilisez l' [impression Cloud hybride](https://docs.microsoft.com/windows-server/administration/hybrid-cloud-print/hybrid-cloud-print-deploy).
