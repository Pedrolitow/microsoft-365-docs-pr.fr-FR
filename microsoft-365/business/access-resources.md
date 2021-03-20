---
title: Accéder aux ressources sur site à partir d’un appareil joint à Azure AD dans Microsoft 365 Business
f1.keywords:
- NOCSH
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
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
ms.assetid: b0f4d010-9fd1-44d0-9d20-fabad2cdbab5
description: Découvrez comment accéder aux ressources locales telles que les applications métier, les partages de fichiers et les imprimantes à partir d’un appareil Windows 10 joint à Azure Active Directory.
ms.openlocfilehash: b78509d72cbd9b3c121039c4965625bf5c21c7e0
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50913519"
---
# <a name="access-on-premises-resources-from-an-azure-ad-joined-device-in-microsoft-365-business-premium"></a>Accéder aux ressources sur site à partir d’un appareil joint à Azure AD dans Microsoft 365 Business Premium

Cet article s’applique à Microsoft 365 Business Premium.

Tout appareil Windows 10 joint à Azure Active Directory a accès à toutes les ressources basées sur le cloud, telles que vos applications Microsoft 365, et peut être protégé par Microsoft 365 Business Premium. Vous pouvez également autoriser l’accès à des ressources locales telles que des applications métier, des partages de fichiers et des imprimantes. Pour autoriser l’accès, utilisez [Azure AD Connect](/azure/active-directory/connect/active-directory-aadconnect) pour synchroniser votre annuaire Active Directory local avec Azure Active Directory. 

Pour en savoir plus, [consultez l’introduction à la gestion des appareils dans Azure Active Directory.](/azure/active-directory/device-management-introduction)
Les étapes sont également résumées dans les sections suivantes.
 
## <a name="run-azure-ad-connect"></a>Exécuter Azure AD Connect

Pour permettre aux appareils joints à Azure AD de votre organisation d’accéder aux ressources sur site, complétez les étapes suivantes.
  
1. Pour synchroniser vos utilisateurs, groupes et contacts d’Active Directory local dans Azure Active Directory, exécutez l’Assistant Synchronisation d’annuaires et Azure AD Connect comme décrit dans Configurer la synchronisation d’annuaires pour [Office 365.](../enterprise/set-up-directory-synchronization.md)
    
2. Une fois la synchronisation d’annuaires terminée, assurez-vous que les appareils Windows 10 de votre organisation sont joints à Azure AD. Cette étape est effectuée individuellement sur chaque appareil Windows 10. Pour plus d’informations, voir Configurer des appareils Windows pour les utilisateurs de [Microsoft 365 Business Premium.](set-up-windows-devices.md) 
    
3. Une fois que les appareils Windows 10 sont joints à Azure AD, chaque utilisateur doit redémarrer ses appareils et se connecter avec ses informations d’identification Microsoft 365 Business Premium. Tous les appareils ont désormais également accès aux ressources sur site.
    
Aucune étape supplémentaire n’est requise pour accéder aux ressources sur site pour les appareils joints à Azure AD. Cette fonctionnalité est intégrée à Windows 10. 

Si vous avez l’intention de vous connecter à l’appareil AADJ autre que la méthode de mot de passe comme le code confidentiel/la mesure Bio via la connexion d’informations d’identification WHFB, puis accéder aux ressources locales (partages, imprimantes). etc.), veuillez suivre https://docs.microsoft.com/windows/security/identity-protection/hello-for-business/hello-hybrid-aadj-sso-base
  
Si votre organisation n’est pas prête à déployer dans la configuration d’appareil joint à Azure AD décrite ci-dessus, envisagez de définir la configuration de l’appareil joint à [Azure AD hybride.](manage-windows-devices.md)
  
### <a name="considerations-when-you-join-windows-devices-to-azure-ad"></a>Considérations lorsque vous joignez des appareils Windows à Azure AD

Si l’appareil Windows que vous avez joint à Azure-AD était précédemment joint au domaine ou dans un groupe de travail, prenons en compte les limitations suivantes :
  
- Lorsqu’un appareil Joint Azure AD, il crée un utilisateur sans référencer un profil existant. Les profils doivent être migrés manuellement. Un profil utilisateur contient des informations telles que les favoris, les fichiers locaux, les paramètres du navigateur et les paramètres du menu Démarrer. Une meilleure approche consiste à trouver un outil tiers pour ma map les fichiers et paramètres existants au nouveau profil.

- Si l’appareil utilise des objets de stratégie de groupe (GPO), certains objets de stratégie de groupe peuvent ne pas avoir de fournisseur de services de [configuration](/windows/configuration/provisioning-packages/how-it-pros-can-use-configuration-service-providers) (CSP) comparable dans Intune. Exécutez [l’outil MMAT](https://www.microsoft.com/download/details.aspx?id=45520) pour rechercher des CSP comparables pour les GME existants.

- Les utilisateurs peuvent ne pas être en mesure de s’authentifier aux applications qui dépendent de l’authentification Active Directory. Évaluez l’application héritée et envisagez la mise à jour vers une application qui utilise l’th moderne, si possible.

- La découverte d’imprimantes Active Directory ne fonctionne pas. Vous pouvez fournir des chemins d’impression directs pour tous les utilisateurs ou utiliser [l’impression universelle.](/universal-print/)