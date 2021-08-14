---
title: Mise en place Microsoft 365 entreprise
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
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
description: Découvrez comment Microsoft 365 pour les entreprises, comment le configurer et comment préparer les appareils et pc de vos utilisateurs afin qu’ils sont protégés par Microsoft 365 entreprise.
ms.openlocfilehash: 3ac8ec3c831d14cfa6d0018340458b2b494b2dd746a7f2bd61d2eba0b4eaf0a1
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53837888"
---
# <a name="get-started-with-microsoft-365-for-business"></a>Mise en place Microsoft 365 entreprise

## <a name="what-is-microsoft-365-for-business"></a>Qu’est-ce Microsoft 365 entreprise ?

Microsoft 365 entreprise est un ensemble complet d’outils de productivité et de collaboration, tels que Outlook, Word, Excel et d’autres produits Office, qui sont toujours à jour. Vous pouvez protéger vos fichiers de travail sur tous vos appareils iOS, Android et Windows 10 avec une sécurité de niveau entreprise facile à gérer.

## <a name="watch-what-is-microsoft-365-business-premium"></a>Regarder : Qu’est-ce que Microsoft 365 Business Premium ?

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE2mhaA] 
  
Microsoft 365 entreprise est destiné à 300 licences au plus. Si vous avez besoin de licences supplémentaires, consultez la documentation de [Microsoft 365 Entreprise](../enterprise/index.yml) pour obtenir plus d’informations. 
  
## <a name="get-microsoft-365-for-business"></a>Obtenir Microsoft 365 entreprise

- Si vous avez un partenaire, il Microsoft 365 pour les entreprises : obtenir Microsoft 365 pour les entreprises à partir de [l’Partner Center Microsoft](get-microsoft-365-business.md).
    
- Si vous n’avez pas de partenaire et que vous souhaitez Microsoft 365 entreprise, vous pouvez [l’acheter ici.](https://www.microsoft.com/microsoft-365/business)
    
## <a name="set-up-microsoft-365-for-business"></a>Configurer Microsoft 365 Entreprises

 **Vue d’ensemble Microsoft 365 la suite pour les entreprises**
  
Le diagramme suivant décrit la façon dont les administrateurs Microsoft 365 pour les entreprises. Il décrit également les étapes à suivre pour préparer Windows PC pour Microsoft 365 entreprise. Vous pouvez également ajouter de nouveaux appareils dans le Centre d’administration Microsoft 365 avec [Windows AutoPilot](add-autopilot-devices-and-profile.md). Vous pouvez utiliser AutoPilot pour configurer et pré-configurer de nouveaux appareils afin qu’ils sont prêts à être utilisés de façon productive dès qu’un utilisateur se connecté avec ses informations d’identification Microsoft 365 entreprise.
  
![A diagram that shows the setup and management flow for admins, and also for a user](../media/249f81fc-7e79-44c7-8425-3a0b7b651c3b.png)

## <a name="watch-set-up-microsoft-365-business"></a>Regardez : Configurer Microsoft 365 Business

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE1FYSM] 

Si vous avez trouvé cette vidéo utile, consultez les [séries de formations complètes pour les petites entreprises et les nouveaux utilisateurs de Microsoft 365](../business-video/index.yml).

  
### <a name="1-set-up-microsoft-365-for-business-admin"></a>1 : configurer Microsoft 365 entreprise (administrateur)

Connectez-vous [Centre d’administration Microsoft 365](https://admin.microsoft.com/adminportal/home) avec vos informations d’identification d’administrateur global et effectuer les étapes suivantes pour configurer Microsoft 365 entreprise. 
  
1. [Conditions préalables à la protection des données sur les appareils avec Microsoft 365 entreprise](pre-requisites-for-data-protection.md)
    
    Lisez d’abord les conditions préalables pour vous assurer que vos appareils sont prêts Microsoft 365 entreprise.
    
2. [Utiliser l’Assistant Installation pour configurer Microsoft 365 entreprise](set-up.md)
    
    Si vous êtes en train de passer définitivement d’un annuaire **Active Directory local** au cloud, vous pouvez passer à l’Centre d’administration Microsoft 365 et utiliser l’Assistant Installation pour ajouter manuellement vos utilisateurs, ou vous pouvez synchroniser vos utilisateurs à une seule fois avec Azure AD Connecter. Il existe deux méthodes pour y parvenir : 
    
    - Si vous avez également un serveur Exchange 2010, Exchange 2013 ou Exchange 2016, vous pouvez utiliser un serveur hybride minimal pour migrer rapidement des boîtes aux lettres Exchange vers [Microsoft 365](/Exchange/mailbox-migration/use-minimal-hybrid-to-quickly-migrate). Les étapes hybrides minimales incluent une synchronisation à temps seul des utilisateurs avec Azure AD et la migration du courrier électronique de l’local vers le cloud. Une fois la migration de messagerie terminée, la synchronisation d’annuaires est automatiquement désactivée lorsque vous utilisez cette méthode.
    
    - Utilisez l’Assistant Synchronisation d’annuaires pour synchroniser vos utilisateurs avec le cloud. Suivez les étapes de la procédure Configurer la synchronisation [d’annuaires Microsoft 365](../enterprise/set-up-directory-synchronization.md) pour effectuer ce processus. Après avoir synchronisé vos utilisateurs avec le cloud, vous devez désactiver la synchronisation d’annuaires [pour Microsoft 365](../enterprise/turn-off-directory-synchronization.md).
    
    Vous devez également donner à chaque utilisateur qui a été ajouté de cette façon une licence pour Microsoft 365 entreprise. Vous pouvez le faire dans [l’Assistant Installation](set-up.md) ou attribuer [des licences aux utilisateurs.](../admin/manage/assign-licenses-to-users.md)
    
### <a name="2-prepare-mobile-devices"></a>2 : préparer les appareils mobiles

Suivez les étapes de la procédure De configurer des appareils mobiles pour [Microsoft 365](set-up-mobile-devices.md) pour que les utilisateurs professionnels installent des applications Office sur les appareils et assurez-vous qu’ils sont protégés par Microsoft 365 pour les entreprises. 
  
### <a name="3-prepare-pcs"></a>3 : Préparer les PC

Les administrateurs peuvent pré-sélectionner les paramètres des nouveaux PC Windows 10 à l’aide Windows [AutoPilot](add-autopilot-devices-and-profile.md). Les utilisateurs peuvent configurer leurs appareils Windows 10 existants ou nouveaux en suivant les étapes de cette rubrique : Configurer des PC Windows pour Microsoft 365 pour les utilisateurs [professionnels.](set-up-windows-devices.md) Pour les appareils existants, les utilisateurs peuvent **éventuellement** [déplacer des fichiers vers OneDrive Entreprise](move-files-to-onedrive.md). Ils peuvent également utiliser des outils tiers pour déplacer des fichiers associés Windows profil vers OneDrive.
  
Si votre organisation utilise Windows Server Active Directory localement, vous pouvez configurer Microsoft 365 entreprise pour protéger vos appareils Windows 10, tout en conservant l’accès aux ressources locales qui nécessitent une authentification locale. Suivez les étapes de [l’étape](manage-windows-devices.md) Activer les appareils joints Windows 10 domaine à gérer par Microsoft 365 entreprise pour configurer cette procédure. Cette méthode est préférée et les appareils dans cet état sont appelés appareils joints **à Azure AD hybride.** 
  
Si vous conservez un Active Directory local qui contient certaines ressources locales (telles que des partages de fichiers et des imprimantes), vous pouvez donner à vos appareils joints à Azure AD l’accès à ces ressources en suivant les étapes **ci-après** : Accéder aux ressources locales à partir d’un appareil joint à [Azure AD](access-resources.md)dans Microsoft 365 pour les entreprises.
  
  
## <a name="contact-support"></a>Contacter le support

 **Si vous devez contacter le support technique :**
  
- Contactez votre partenaire.
    
- En tant qu Microsoft 365 pour les entreprises, vous avez accès à notre équipe de support client : Contacter le support technique pour les produits d’entreprise - Aide **[de l’administrateur](../business-video/get-help-support.md)**
    
## <a name="related-content"></a>Contenu connexe

[Microsoft 365 documentation et ressources pour les](./index.yml) entreprises (page de liens)\
[Gérer Microsoft 365 entreprise](manage.md) (article)\
[Migrer vers Microsoft 365 entreprise](migrate-to-microsoft-365-business.md) (article)\
[Vidéos de formation Microsoft 365 Entreprise](../business-video/index.yml) (page de liens)