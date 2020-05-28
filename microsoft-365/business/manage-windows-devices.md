---
title: Activer la gestion des appareils Windows 10 associés à un domaine par Microsoft 365 pour les entreprises
f1.keywords:
- NOCSH
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
audience: Admin
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
- OKR_SMB_M365
- seo-marvel-mar
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
ms.assetid: 9b4de218-f1ad-41fa-a61b-e9e8ac0cf993
description: Découvrez comment permettre à Microsoft 365 de protéger les appareils Windows 10 à annuaire Active Directory joints en quelques étapes seulement.
ms.openlocfilehash: e7f83e620fbb43a478dba98f78d5f471a541aea7
ms.sourcegitcommit: 2d59b24b877487f3b84aefdc7b1e200a21009999
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "44403055"
---
# <a name="enable-domain-joined-windows-10-devices-to-be-managed-by-microsoft-365-for-business"></a>Activer la gestion des appareils Windows 10 associés à un domaine par Microsoft 365 pour les entreprises

Si votre organisation utilise Windows Server Active Directory en local, vous pouvez configurer Microsoft 365 pour les entreprises afin de protéger vos appareils Windows 10, tout en conservant l’accès aux ressources locales qui nécessitent une authentification locale.
Pour configurer cette protection, vous pouvez implémenter des **appareils joints Azure ad hybrides**. Ces appareils sont joints à votre annuaire Active Directory local et à votre Azure Active Directory.

Cette vidéo décrit la procédure à suivre pour le scénario le plus courant, qui est également détaillée dans les étapes suivantes.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE3C9hO]
  

## <a name="1-prepare-for-directory-synchronization"></a>1. préparer la synchronisation d’annuaires 

Avant de synchroniser vos utilisateurs et ordinateurs à partir du domaine Active Directory local, consultez la [préparation de la synchronisation d’annuaires vers Office 365](https://docs.microsoft.com/office365/enterprise/prepare-for-directory-synchronization). En particulier :

   - Assurez-vous qu’il n’existe pas de doublons dans votre répertoire pour les attributs suivants : **mail**, **proxyAddresses**et **userPrincipalName**. Ces valeurs doivent être uniques et les doublons doivent être supprimés.
   
   - Nous vous recommandons de configurer l’attribut **userPrincipalName** (UPN) de chaque compte d’utilisateur local de sorte qu’il corresponde à l’adresse de messagerie principale correspondant à l’utilisateur Microsoft 365 sous licence. Par exemple : *Mary.Shelley@contoso.com* plutôt que *Mary@contoso. local*
   
   - Si le domaine Active Directory se termine par un suffixe non routable comme *. local* ou *. LAN*, au lieu d’un suffixe routable Internet tel que *. com* ou *. org*, ajustez d’abord le suffixe UPN des comptes d’utilisateurs locaux comme décrit dans [Prepare a non routable domain for Directory Synchronization](https://docs.microsoft.com/office365/enterprise/prepare-a-non-routable-domain-for-directory-synchronization). 

## <a name="2-install-and-configure-azure-ad-connect"></a>2. installer et configurer Azure AD Connect

Pour synchroniser vos utilisateurs, groupes et contacts à partir de l’Active Directory local avec Azure Active Directory, installez Azure Active Directory Connect et configurez la synchronisation d’annuaires. Pour plus d’informations, consultez la rubrique [configurer la synchronisation d’annuaires pour Office 365](https://docs.microsoft.com/office365/enterprise/set-up-directory-synchronization) .

> [!NOTE]
> Les étapes sont exactement les mêmes pour Microsoft 365 pour les entreprises. 

Lorsque vous configurez vos options pour Azure AD Connect, nous vous recommandons d’activer la **synchronisation de mot de passe**, l' **authentification unique transparente**et la fonctionnalité d' **écriture différée de mot de passe** , qui est également prise en charge dans Microsoft 365 pour les entreprises.

> [!NOTE]
> Il existe quelques étapes supplémentaires pour l’écriture différée de mot de passe au-delà de la case à cocher dans Azure AD Connect. Pour plus d’informations, voir [procédure : configurer l’écriture différée de mot de passe](https://docs.microsoft.com/azure/active-directory/authentication/howto-sspr-writeback). 

## <a name="3-configure-hybrid-azure-ad-join"></a>3. configurer une jointure Azure AD hybride

Avant d’autoriser les appareils Windows 10 à être associés à Azure AD hybride, veillez à respecter les conditions préalables suivantes :

   - Vous utilisez la dernière version d’Azure AD Connect.

   - Azure AD Connect a synchronisé tous les objets ordinateur des appareils que vous souhaitez associer à Azure AD. Si les objets ordinateur appartiennent à des unités d’organisation (UO) spécifiques, assurez-vous également que ces unités d’organisation sont définies pour la synchronisation dans Azure AD Connect.

Pour enregistrer les appareils Windows 10 joints à un domaine en tant que membres Azure AD hybrides, suivez les étapes décrites dans le [Didacticiel : configure Hybrid Azure Active Directory Join for Managed Domains](https://docs.microsoft.com/azure/active-directory/devices/hybrid-azuread-join-managed-domains#configure-hybrid-azure-ad-join). Cette fonction hybride permet d’activer votre environnement Active Directory existant sur des ordinateurs Windows 10 et de les rendre prêts pour le Cloud.
    
## <a name="4-enable-automatic-enrollment-for-windows-10"></a>4. activer l’enregistrement automatique pour Windows 10

 Pour inscrire automatiquement des appareils Windows 10 pour la gestion des appareils mobiles dans Intune, reportez-vous à [la rubrique inscrire un appareil Windows 10 automatiquement à l’aide](https://docs.microsoft.com/windows/client-management/mdm/enroll-a-windows-10-device-automatically-using-group-policy)de la stratégie de groupe. Vous pouvez définir la stratégie de groupe au niveau d’un ordinateur local ou pour les opérations en bloc, vous pouvez utiliser la console de gestion des stratégies de groupe et les modèles ADMX pour créer ce paramètre de stratégie de groupe sur votre contrôleur de domaine.

## <a name="5-configure-seamless-single-sign-on"></a>5. configurer l’authentification unique transparente

  La fonction SSO transparente signe automatiquement les utilisateurs dans leurs ressources Cloud Microsoft 365 lorsqu’elles utilisent des ordinateurs d’entreprise. Déployez simplement l’une des deux options de stratégie de groupe décrites dans [Azure Active Directory transparent Single Sign-On : Quick Start](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-sso-quick-start#step-2-enable-the-feature). L’option de **stratégie de groupe** ne permet pas aux utilisateurs de modifier leurs paramètres, tandis que l’option de **préférence stratégie de groupe** définit les valeurs mais les laisse également modifiables par l’utilisateur.

## <a name="6-set-up-windows-hello-for-business"></a>6. configurer Windows Hello entreprise

 Windows Hello entreprise remplace les mots de passe par une authentification forte à deux facteurs (2FA) pour la connexion à un ordinateur local. Un facteur est une paire de clés asymétriques et l’autre est un code confidentiel ou un autre mouvement local, tel que l’empreinte digitale ou la reconnaissance faciale si votre appareil le prend en charge. Nous vous recommandons de remplacer les mots de passe par 2FA et Windows Hello entreprise dans la mesure du possible.

Pour configurer Windows Hello entreprise hybride, passez en revue les [conditions préalables à la configuration requise pour l’approbation de la clé hybride Windows Hello entreprise](https://docs.microsoft.com/windows/security/identity-protection/hello-for-business/hello-hybrid-key-trust-prereqs). Ensuite, suivez les instructions de la [section configurer les paramètres d’approbation de clé Windows Hello entreprise hybride](https://docs.microsoft.com/windows/security/identity-protection/hello-for-business/hello-hybrid-key-whfb-settings). 
