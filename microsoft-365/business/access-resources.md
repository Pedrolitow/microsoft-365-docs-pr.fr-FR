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
ms.openlocfilehash: 4a2ff28107c6e2ec4473859c75bf720df7662747
ms.sourcegitcommit: 58a7bd70a4bcf52530baf5f82507fd5dc4455fd9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "39668785"
---
# <a name="access-on-premises-resources-from-an-azure-ad-joined-device-in-microsoft-365-business"></a>Accéder aux ressources locales à partir d’un appareil joint à Azure AD dans Microsoft 365 Business

Tout appareil Windows 10 qui est joint à Azure Active Directory a accès à toutes les ressources en nuage, telles que vos applications Office 365, et peut être protégé par Microsoft 365 Business. Vous pouvez également autoriser l’accès à des ressources locales telles que des applications métier, des partages de fichiers et des imprimantes. Pour autoriser l’accès, utilisez [Azure ad Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect) pour synchroniser votre annuaire Active Directory local avec Azure Active Directory. 

Pour en savoir plus, consultez la rubrique [Présentation de la gestion des appareils dans Azure Active Directory](https://docs.microsoft.com/azure/active-directory/device-management-introduction).
Les étapes sont également résumées dans les sections suivantes.

> [!IMPORTANT]
> Cette procédure s’applique uniquement à OAuth et NTLM. Kerberos n’est pas pris en charge.
 
## <a name="run-azure-ad-connect"></a>Exécuter Azure AD Connect

Procédez comme suit pour activer les appareils Azure AD joints de votre organisation pour accéder aux ressources locales.
  
1. Pour synchroniser vos utilisateurs, groupes et contacts à partir d’Active Directory local avec Azure Active Directory, exécutez l’Assistant synchronisation d’annuaires et Azure AD Connect comme décrit dans [set up Directory Synchronization for Office 365](https://support.office.com/article/1b3b5318-6977-42ed-b5c7-96fa74b08846).
    
2. Une fois la synchronisation d’annuaires terminée, assurez-vous que les appareils Windows 10 de votre organisation sont joints à Azure AD. Cette étape est effectuée individuellement sur chaque appareil Windows 10. Pour plus d’informations, consultez la rubrique [configurer des appareils Windows pour les utilisateurs professionnels de Microsoft 365](set-up-windows-devices.md) . 
    
3. Une fois que les appareils Windows 10 sont joints à Azure AD, chaque utilisateur doit redémarrer ses appareils et se connecter avec leurs informations d’identification d’entreprise Microsoft 365. Tous les périphériques ont désormais accès aux ressources locales également.
    
Aucune étape supplémentaire n’est requise pour accéder aux ressources locales pour les appareils joints à Azure AD. Cette fonctionnalité est intégrée dans Windows 10. 

Si vous avez l’intention de vous connecter à l’appareil AADJ autre que la méthode de mot de passe comme code confidentiel/bio-métrique via WHFB de connexion d’informations d’identification et d’accéder aux ressources locales (partages, imprimantes.. etc.), suivezhttps://docs.microsoft.com/en-us/windows/security/identity-protection/hello-for-business/hello-hybrid-aadj-sso-base
  
Si votre organisation n’est pas prête à être déployée dans la configuration d’appareil joint Azure AD décrite ci-dessus, envisagez de configurer la [configuration hybride Azure ad jointe](manage-windows-devices.md)de l’appareil.
  
### <a name="considerations-when-you-join-windows-devices-to-azure-ad"></a>Éléments à prendre en compte lorsque vous associez des appareils Windows à Azure AD

Si le périphérique Windows auquel vous participez à Azure-AD a été précédemment joint à un domaine ou dans un groupe de travail, tenez compte des limitations suivantes :
  
- Lorsqu’un appareil Azure AD rejoint une jointure, il crée un utilisateur sans référence à un profil existant. Les profils doivent être migrés manuellement. Un profil utilisateur contient des informations comme les favoris, les fichiers locaux, les paramètres de navigateur et les paramètres du menu Démarrer. Une meilleure approche consiste à trouver un outil tiers pour mapper les fichiers et les paramètres existants sur le nouveau profil.

- Si l’appareil utilise des objets de stratégie de groupe (GPO), certains objets de stratégie de groupe ne disposent pas nécessairement d’un [fournisseur de services de configuration](https://docs.microsoft.com/windows/configuration/provisioning-packages/how-it-pros-can-use-configuration-service-providers) (CSP) comparable dans Intune. Exécutez l' [outil mmat](https://www.microsoft.com/download/details.aspx?id=45520) pour rechercher des fournisseurs de services cryptographiques comparables pour les objets de stratégie de groupe existants.

- Les utilisateurs ne peuvent pas s’authentifier aux applications qui dépendent de l’authentification Active Directory. Évaluez l’application héritée et envisagez d’effectuer une mise à jour vers une application qui utilise l’authentification moderne, si possible.

- La découverte des imprimantes Active Directory ne fonctionne pas. Vous pouvez fournir des chemins d’accès directs aux imprimantes pour tous les utilisateurs ou utiliser l’impression sur le [Cloud hybride](https://docs.microsoft.com/windows-server/administration/hybrid-cloud-print/hybrid-cloud-print-deploy).
