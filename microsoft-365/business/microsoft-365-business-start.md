---
title: Mise en place de Microsoft 365 pour les entreprises
f1.keywords:
- NOCSH
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Adm_O365
- M365-subscription-management
- TRN_SMB
ms.custom:
- Adm_O365
- Core_O365Admin_Migration
- MiniMaven
- MSB365
- OKR_SMB_M365
- TRN_M365B
- OKR_SMB_Videos
- seo-marvel-mar
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
ms.assetid: 496e690b-b75d-4ff5-bf34-cc32905d0364
description: Découvrez Microsoft 365 pour les entreprises, comment le configurer et comment préparer les appareils et PC de vos utilisateurs afin de s’assurer qu’ils sont protégés par Microsoft 365 pour les entreprises.
ms.openlocfilehash: ec50036f589cfd8497b0e7e9af6519b30d25dcd3
ms.sourcegitcommit: 555d756c69ac9031d1fb928f2e1f9750beede066
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2020
ms.locfileid: "47306486"
---
# <a name="get-started-with-microsoft-365-for-business"></a>Mise en place de Microsoft 365 pour les entreprises

## <a name="what-is-microsoft-365-for-business"></a>Qu’est-ce que Microsoft 365 pour les entreprises ?

Microsoft 365 pour les entreprises est un ensemble complet d’outils de productivité et de collaboration d’entreprise, tels qu’Outlook, Word, Excel et d’autres produits Office, qui sont toujours à jour. Vous pouvez protéger vos fichiers de travail sur tous vos appareils iOS, Android et Windows 10 avec une sécurité de niveau entreprise facile à gérer.

Regardez cette vidéo pour obtenir une vue d’ensemble rapide de Microsoft 365 pour les entreprises.<br><br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE2mhaA] 
  
Microsoft 365 pour les entreprises est destiné à 300 licences au plus. Si vous avez besoin de licences supplémentaires, consultez la documentation de [Microsoft 365 Entreprise](https://go.microsoft.com/fwlink/p/?linkid=860986) pour obtenir plus d’informations. 
  
## <a name="get-microsoft-365-for-business"></a>Obtenir Microsoft 365 pour les entreprises

- Si vous avez un partenaire, il reçoit Microsoft 365 pour les entreprises : obtenez Microsoft 365 pour les entreprises à partir de [l’Partner Center Microsoft.](get-microsoft-365-business.md)
    
- Si vous n’avez pas de partenaire et que vous souhaitez obtenir Microsoft 365 pour les entreprises, vous pouvez [l’acheter ici.](https://www.microsoft.com/microsoft-365/business)
    
## <a name="set-up-microsoft-365-for-business"></a>Configurer Microsoft 365 Entreprises

 **Vue d’ensemble de la mise en place de Microsoft 365 for business Suite**
  
Le diagramme suivant décrit comment les administrateurs configurer Microsoft 365 pour les entreprises. Il décrit également les étapes de préparation des PC Windows pour Microsoft 365 pour les entreprises. Vous pouvez également ajouter de nouveaux appareils dans le Centre d’administration Microsoft 365 avec [Windows AutoPilot](add-autopilot-devices-and-profile.md). Vous pouvez utiliser AutoPilot pour configurer et pré-configurer de nouveaux appareils afin qu’ils sont prêts à être utilisés de façon productive dès qu’un utilisateur se connecté avec ses informations d’identification Microsoft 365 pour l’entreprise.
  
![A diagram that shows the setup and management flow for admins, and also for a user](../media/249f81fc-7e79-44c7-8425-3a0b7b651c3b.png)

Regardez cette vidéo pour obtenir une vue d’ensemble de la configuration de Microsoft 365 pour les entreprises.<br><br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE1FYSM] 

Si vous avez trouvé cette vidéo utile, consultez les [séries de formations complètes pour les petites entreprises et les nouveaux utilisateurs de Microsoft 365](https://support.microsoft.com/office/6ab4bbcd-79cf-4000-a0bd-d42ce4d12816).

  
### <a name="1-set-up-microsoft-365-for-business-admin"></a>1 : configurer Microsoft 365 pour les entreprises (administrateur)

Connectez-vous au Centre d’administration [Microsoft 365](https://portal.office.com/adminportal/home) avec vos informations d’identification d’administrateur global et complétez les étapes suivantes pour configurer Microsoft 365 pour les entreprises. 
  
1. [Conditions préalables à la protection des données sur les appareils avec Microsoft 365 pour les entreprises](pre-requisites-for-data-protection.md)
    
    Lisez d’abord les conditions préalables pour vous assurer que vos appareils sont prêts pour Microsoft 365 pour les entreprises.
    
2. [Utiliser l’Assistant Configuration pour configurer Microsoft 365 pour les entreprises](set-up.md)
    
    Si vous êtes en train de passer définitivement d’un annuaire **Active Directory local** au cloud, vous pouvez vous rendre dans le Centre d’administration Microsoft 365 et utiliser l’Assistant Configuration pour ajouter manuellement vos utilisateurs, ou vous pouvez faire une synchronisation à usage définitif avec Azure AD Connect. Vous pouvez procéder de deux manières : 
    
    - Si vous avez également un serveur Exchange 2010, Exchange 2013 ou Exchange 2016, vous pouvez utiliser l’hybride minimal pour migrer rapidement des boîtes aux lettres Exchange vers [Microsoft 365.](https://docs.microsoft.com/Exchange/mailbox-migration/use-minimal-hybrid-to-quickly-migrate) Les étapes hybrides minimales incluent une synchronisation à temps seul des utilisateurs avec Azure AD et la migration du courrier électronique de l’local vers le cloud. Une fois la migration de messagerie terminée, la synchronisation d’annuaires est automatiquement désactivée lorsque vous utilisez cette méthode.
    
    - Utilisez l’Assistant Synchronisation d’annuaires pour synchroniser vos utilisateurs avec le cloud. Suivez les étapes de la procédure De mise en place de la synchronisation d’annuaires [pour Microsoft 365](https://docs.microsoft.com/microsoft-365/enterprise/set-up-directory-synchronization) pour effectuer ce processus. Après avoir synchronisé vos utilisateurs avec le cloud, vous devez désactiver la synchronisation d’annuaires [pour Microsoft 365.](https://docs.microsoft.com/microsoft-365/enterprise/turn-off-directory-synchronization)
    
    Vous devez également donner à chaque utilisateur qui a été ajouté de cette façon une licence à Microsoft 365 pour les entreprises. Vous pouvez le faire dans [l’Assistant Installation](set-up.md) ou attribuer [des licences aux utilisateurs.](../admin/manage/assign-licenses-to-users.md)
    
### <a name="2-prepare-mobile-devices"></a>2 : préparer les appareils mobiles

Suivez les étapes de l’étape Configurer les appareils mobiles pour que les utilisateurs [de Microsoft 365](set-up-mobile-devices.md) pour les entreprises installent les applications Office sur les appareils et assurez-vous qu’ils sont protégés par Microsoft 365 pour les entreprises. 
  
### <a name="3-prepare-pcs"></a>3 : Préparer les PC

Les administrateurs peuvent pré-sélectionner les paramètres des nouveaux PC Windows 10 à l’aide [de Windows AutoPilot](add-autopilot-devices-and-profile.md). Les utilisateurs peuvent configurer leurs appareils Windows 10 existants ou nouveaux en suivant les étapes de cette rubrique : Configurer des PC Windows pour les utilisateurs [de Microsoft 365 pour les entreprises.](set-up-windows-devices.md) Pour les appareils existants, les utilisateurs peuvent **éventuellement** déplacer des fichiers [vers OneDrive Entreprise.](move-files-to-onedrive.md) Ils peuvent également utiliser des outils tiers pour déplacer des fichiers associés au profil Windows vers OneDrive.
  
Si votre organisation utilise Windows Server Active Directory en local, vous pouvez configurer Microsoft 365 pour les entreprises pour protéger vos appareils Windows 10, tout en conservant l’accès aux ressources locales qui nécessitent une authentification locale. Suivez les étapes de l’étape Activer les appareils Windows 10 joints à un domaine à gérer par [Microsoft 365](manage-windows-devices.md) pour les entreprises pour configurer cette procédure. Cette méthode est préférée et les appareils dans cet état sont appelés appareils joints **à Azure AD hybride.** 
  
Si vous conservez un Active Directory local qui contient certaines ressources locales (telles que des partages de fichiers et des imprimantes), vous pouvez donner à vos appareils joints à Azure AD l’accès à ces ressources en suivant les étapes **ci-après** : Accéder aux ressources locales à partir d’un appareil joint à Azure AD dans [Microsoft 365](access-resources.md)pour les entreprises.
  
  
## <a name="contact-support"></a>Contacter l’assistance

 **Si vous devez contacter le support technique :**
  
- Contactez votre partenaire.
    
- En tant qu’administrateur Microsoft 365 pour les entreprises, vous avez accès à notre équipe de support client : Contacter le support technique pour les produits d’entreprise - Aide **[de l’administrateur](https://docs.microsoft.com/microsoft-365/admin/contact-support-for-business-products)**
    
## <a name="see-also"></a>Voir aussi

[Documentation et ressources microsoft 365 pour les entreprises](https://go.microsoft.com/fwlink/p/?linkid=853701)
  
[Gérer Microsoft 365 pour les entreprises](manage.md)[Migrer vers Microsoft 365 pour les entreprises](migrate-to-microsoft-365-business.md)

[Vidéos de formation Microsoft 365 Entreprise](https://support.microsoft.com/office/6ab4bbcd-79cf-4000-a0bd-d42ce4d12816) 
