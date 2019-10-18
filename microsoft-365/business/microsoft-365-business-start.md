---
title: Prise en main de Microsoft 365 Entreprise
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
ms.custom:
- Adm_O365
- Core_O365Admin_Migration
- MiniMaven
- MSB365
- OKR_SMB_M365
search.appverid:
- BCS160
- MET150
ms.assetid: 496e690b-b75d-4ff5-bf34-cc32905d0364
description: Découvrez comment configurer Microsoft 365 Business.
ms.openlocfilehash: ed302a79d125ffc9c6203d902f437749a5b0f8d4
ms.sourcegitcommit: bd52f7b662887f552f90c46f69d6a2a42fb66914
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2019
ms.locfileid: "37575895"
---
# <a name="get-started-with-microsoft-365-business"></a>Prise en main de Microsoft 365 Entreprise

## <a name="what-is-microsoft-365-business"></a>Qu’est-ce que Microsoft 365 entreprise

Microsoft 365 Business est un ensemble complet d'outils professionnels de productivité et de collaboration, tels que Outlook, Word, Excel et d'autres produits Office toujours à jour. Vous pouvez protéger vos fichiers professionnels sur tous vos appareils iOS, Android et Windows 10 grâce à une sécurité de qualité professionnelle facile à gérer.
  
Microsoft 365 Business est destiné à 300 licences, si vous avez besoin de plus de licences, reportez-vous à la documentation de [microsoft 365 Enterprise](https://go.microsoft.com/fwlink/p/?linkid=860986) pour plus d’informations. 
  
## <a name="get-microsoft-365-business"></a>Obtenir Microsoft 365 Business

- Si vous faites appel à un partenaire, il recevra Microsoft 365 Entreprise : [Obtenir Microsoft 365 Business auprès de l'Espace partenaires Microsoft](get-microsoft-365-business.md).
    
- Si vous ne disposez pas d’un partenaire et que vous souhaitez obtenir Microsoft 365 entreprise, vous pouvez l' [acheter ici](https://www.microsoft.com/en-us/microsoft-365/business).
    
## <a name="set-up-microsoft-365-business"></a>Configurer Microsoft 365 Business

 **Vue d’ensemble de la configuration de Microsoft 365 Business Suite**
  
Le diagramme suivant décrit comment les administrateurs configurent Microsoft 365 Business. Il décrit également la procédure pour préparer les PC Windows pour Microsoft 365 Entreprise. Vous pouvez également ajouter de nouveaux appareils dans le Centre d'administration Microsoft 365 Entreprise avec [Windows AutoPilot](add-autopilot-devices-and-profile.md). Vous pouvez utiliser AutoPilot pour installer et préconfigurer de nouveaux appareils, afin qu'ils soient prêts à être utilisés dès qu'un utilisateur se connecte avec ses informations d'identification Microsoft 365 Entreprise.
  
![A diagram that shows the setup and management flow for admins, and also for a user](media/249f81fc-7e79-44c7-8425-3a0b7b651c3b.png)
  
### <a name="1-set-up-microsoft-365-business-admin"></a>1 : configurer Microsoft 365 entreprise (administrateur)

Connectez-vous au [Centre d'administration Microsoft 365 Business](https://portal.office.com/adminportal/home) avec vos informations d'identification d'administrateur général et suivez les étapes ci-dessous pour configurer Microsoft 365 Entreprise. 
  
1. [Conditions préalables à la protection des données sur les appareils avec Microsoft 365 Business](pre-requisites-for-data-protection.md)
    
    Commencez par lire les conditions préalables pour vous assurer que vos appareils sont prêts pour Microsoft 365 Entreprise.
    
2. [Installer Microsoft 365 Business à l'aide de l'Assistant Installation](set-up.md)
    
    Si vous effectuez un **transfert permanent d’un annuaire Active Directory local vers le Cloud**, vous pouvez ajouter vos utilisateurs manuellement dans le centre d’administration de Microsoft 365 Business à l’aide de l’Assistant Installation ou effectuer une synchronisation unique avec Azure ad Connect. Vous pouvez procéder de deux manières : 
    
  - Si vous disposez également d’un serveur Exchange 2010, Exchange 2013 ou Exchange 2016, vous pouvez [utiliser un environnement hybride minimal pour migrer rapidement des boîtes aux lettres Exchange vers Office 365](https://support.office.com/article/fdecceed-0702-4af3-85be-f2a0013937ef). La procédure de configuration hybride minimale inclut une synchronisation unique des utilisateurs avec Azure AD, ainsi que la migration de la messagerie électronique de l'environnement local vers le cloud. Après la migration de la messagerie électronique, la synchronisation d'annuaires est automatiquement désactivée lorsque vous utilisez cette méthode.
    
  - Utilisez l'Assistant Synchronisation d'annuaires Office 365 pour synchroniser vos utilisateurs avec le cloud. Suivez les étapes de [Configurer la synchronisation d'annuaires pour Office 365](https://support.office.com/article/1b3b5318-6977-42ed-b5c7-96fa74b08846) pour effectuer cette procédure. Une fois vos utilisateurs synchronisés avec le cloud, vous devrez [Désactiver la synchronisation d'annuaires](https://support.office.com/article/ee5f861e-bd48-4267-83d1-a4ead4b4a00d).
    
    Vous devrez également donner à chaque utilisateur ajouté de cette manière une licence Microsoft 365 Business. Vous pouvez effectuer cette opération dans l' [Assistant Installation](set-up.md)ou dans le [site attribuer des licences aux utilisateurs dans Office 365 pour les entreprises](https://support.office.com/article/997596B5-4173-4627-B915-36ABAC6786DC).
    
### <a name="2-prepare-mobile-devices"></a>2 : préparer les appareils mobiles

Suivez les étapes de la procédure[configurer des appareils mobiles pour les utilisateurs professionnels de microsoft 365](set-up-mobile-devices.md) pour installer des applications Office sur des appareils et vous assurer qu’elles sont protégées par Microsoft 365 Business. 
  
### <a name="3-prepare-pcs"></a>3 : préparer des PC

Les administrateurs peuvent présélectionner des paramètres pour les nouveaux appareils Windows 10 PC à l’aide de [Windows AutoPilot](add-autopilot-devices-and-profile.md). Les utilisateurs peuvent configurer leurs appareils Windows 10 existants ou nouveaux en suivant les étapes décrites dans cette rubrique : [configurer des ordinateurs Windows pour les utilisateurs professionnels de Microsoft 365](set-up-windows-devices.md). Pour les appareils existants, les utilisateurs **peuvent également**[déplacer des fichiers vers OneDrive entreprise](move-files-to-onedrive.md). Ils peuvent également utiliser des outils tiers pour déplacer des fichiers associés à un profil Windows vers OneDrive.
  
Si votre organisation utilise Windows Server Active Directory en local, vous pouvez configurer Microsoft 365 entreprise pour protéger vos appareils Windows 10, tout en conservant l’accès aux ressources locales qui nécessitent une authentification locale. Suivez les étapes de la procédure [activer les appareils Windows 10 appartenant à un domaine pour qu’ils soient gérés par Microsoft 365 Business](manage-windows-devices.md) pour le configurer. Il s’agit de la méthode préférée et les appareils dans cet État sont appelés **appareils hybrides Azure ad**. 
  
Si vous conservez un annuaire Active Directory local contenant certaines ressources locales (telles que des partages de fichiers et des imprimantes), vous pouvez donner à vos **appareils joints à Azure ad** l’accès à ces ressources en suivant les étapes ci-dessous : [accéder aux ressources locales à partir d’un Appareil rejoint Azure AD dans Microsoft 365 Business](access-resources.md).
  
Une fois que vous avez configuré les PC Windows 10, vous pouvez [installer automatiquement Office](auto-install-or-uninstall-office.md) sur les appareils. 
  
## <a name="contact-support"></a>Contacter l’assistance

 **Si vous devez contacter le support technique :**
  
- Contactez votre partenaire.
    
- En tant qu’administrateur commercial Microsoft 365, vous avez accès à notre équipe de support client, ** [contacter le support pour les entreprises-aide de l’administrateur](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b)**
    
## <a name="related-topics"></a>Rubriques connexes
[Documentation et ressources pour Microsoft 365 Business](https://go.microsoft.com/fwlink/p/?linkid=853701)
  
[Gérer microsoft 365 Business](manage.md)[migrer vers Microsoft 365 Business](migrate-to-microsoft-365-business.md)
  

