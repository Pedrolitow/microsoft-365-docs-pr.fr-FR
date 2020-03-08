---
title: Prise en main de Microsoft 365 Entreprise
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
search.appverid:
- BCS160
- MET150
ms.assetid: 496e690b-b75d-4ff5-bf34-cc32905d0364
description: Découvrez Microsoft 365 Business, comment le configurer et comment préparer les appareils et les ordinateurs de vos utilisateurs pour vous assurer qu’ils sont protégés par Microsoft 365 Business.
ms.openlocfilehash: 220fb747e2bc501f3f6d46d967b30d2e5fd79a4a
ms.sourcegitcommit: 217de0fc54cbeaea32d253f175eaf338cd85f5af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/07/2020
ms.locfileid: "42561437"
---
# <a name="get-started-with-microsoft-365-business"></a>Prise en main de Microsoft 365 Entreprise

## <a name="what-is-microsoft-365-business"></a>Qu’est-ce que Microsoft 365 entreprise

Microsoft 365 Business est un ensemble complet d’outils de productivité et de collaboration d’entreprise, tels que Outlook, Word, Excel et d’autres produits Office, qui sont toujours à jour. Vous pouvez protéger vos fichiers professionnels sur tous vos appareils iOS, Android et Windows 10 avec une sécurité de niveau entreprise facile à gérer.

Regardez cette vidéo pour une présentation rapide de Microsoft 365 Business.<br><br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE2mhaA] 
  
Microsoft 365 Business est destiné à 300 licences. Si vous avez besoin de plus de licences, consultez la documentation de [Microsoft 365 Enterprise](https://go.microsoft.com/fwlink/p/?linkid=860986) pour plus d’informations. 
  
## <a name="get-microsoft-365-business"></a>Obtenir Microsoft 365 Business

- Si vous avez un partenaire, il obtiendra Microsoft 365 entreprise : [obtenir microsoft 365 entreprise à partir du centre de partenaires Microsoft](get-microsoft-365-business.md).
    
- Si vous ne disposez pas d’un partenaire et que vous souhaitez obtenir Microsoft 365 entreprise, vous pouvez l' [acheter ici](https://www.microsoft.com/microsoft-365/business).
    
## <a name="set-up-microsoft-365-business"></a>Configurer Microsoft 365 Business

 **Vue d’ensemble de la configuration de Microsoft 365 Business Suite**
  
Le diagramme suivant décrit comment les administrateurs configurent Microsoft 365 Business. Il décrit également la procédure pour préparer les PC Windows pour Microsoft 365 Entreprise. Vous pouvez également ajouter de nouveaux appareils dans le centre d’administration de Microsoft 365 Business avec [Windows AutoPilot](add-autopilot-devices-and-profile.md). Vous pouvez utiliser AutoPilot pour configurer et pré-configurer de nouveaux appareils afin qu’ils soient prêts à être utilisés dès qu’un utilisateur se connecte à l’aide de leurs informations d’identification Microsoft 365 entreprise.
  
![A diagram that shows the setup and management flow for admins, and also for a user](../media/249f81fc-7e79-44c7-8425-3a0b7b651c3b.png)

Regardez cette vidéo pour obtenir une vue d’ensemble de l’installation de Microsoft 365 Business.<br><br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE1FYSM] 

Si vous avez trouvé cette vidéo utile, consultez les [séries de formations complètes pour les petites entreprises et les nouveaux utilisateurs de Microsoft 365](https://support.office.com/article/6ab4bbcd-79cf-4000-a0bd-d42ce4d12816).

  
### <a name="1-set-up-microsoft-365-business-admin"></a>1 : configurer Microsoft 365 entreprise (administrateur)

Connectez-vous au [Centre d’administration de microsoft 365](https://portal.office.com/adminportal/home) avec vos informations d’identification d’administrateur général et effectuez les étapes suivantes pour configurer Microsoft 365 Business. 
  
1. [Conditions préalables à la protection des données sur les appareils avec Microsoft 365 Business](pre-requisites-for-data-protection.md)
    
    Commencez par lire les conditions préalables pour vous assurer que vos appareils sont prêts pour Microsoft 365 Business.
    
2. [Utiliser l’Assistant Installation pour configurer Microsoft 365 Business](set-up.md)
    
    Si vous êtes en **déplacement permanent d’un annuaire Active Directory local vers le Cloud**, vous pouvez accéder au centre d’administration de Microsoft 365 Business et utiliser l’Assistant Installation pour ajouter vos utilisateurs manuellement ou effectuer une synchronisation unique avec Azure ad Connect. Vous pouvez procéder de deux manières : 
    
    - Si vous disposez également d’un serveur Exchange 2010, Exchange 2013 ou Exchange 2016, vous pouvez [utiliser un environnement hybride minimal pour migrer rapidement des boîtes aux lettres Exchange vers Office 365](https://support.office.com/article/fdecceed-0702-4af3-85be-f2a0013937ef). Les étapes hybrides minimales incluent une synchronisation unique des utilisateurs vers Azure AD et la migration de la messagerie électronique sur site vers le Cloud. Une fois la migration de la messagerie terminée, la synchronisation d’annuaires est automatiquement désactivée lorsque vous utilisez cette méthode.
    
    - Utilisez l’Assistant synchronisation d’annuaires Office 365 pour synchroniser vos utilisateurs avec le Cloud. Suivez les étapes de [Configurer la synchronisation d'annuaires pour Office 365](https://support.office.com/article/1b3b5318-6977-42ed-b5c7-96fa74b08846) pour effectuer cette procédure. Après avoir synchronisé vos utilisateurs sur le Cloud, vous devez désactiver la [synchronisation d’annuaires pour Office 365](https://support.office.com/article/ee5f861e-bd48-4267-83d1-a4ead4b4a00d).
    
    Vous devrez également donner à chaque utilisateur qui a été ajouté de cette manière une licence Microsoft 365 Business. Vous pouvez effectuer cette opération dans l' [Assistant Installation](set-up.md) ou vous pouvez [attribuer des licences aux utilisateurs dans Office 365 pour les entreprises](https://support.office.com/article/997596B5-4173-4627-B915-36ABAC6786DC).
    
### <a name="2-prepare-mobile-devices"></a>2 : préparer les appareils mobiles

Suivez les étapes de la procédure [configurer des appareils mobiles pour les utilisateurs professionnels de microsoft 365](set-up-mobile-devices.md) pour installer les applications Office sur des appareils et vous assurer qu’ils sont protégés par Microsoft 365 Business. 
  
### <a name="3-prepare-pcs"></a>3 : préparer des PC

Les administrateurs peuvent présélectionner des paramètres pour les nouveaux PC Windows 10 à l’aide de [Windows AutoPilot](add-autopilot-devices-and-profile.md). Les utilisateurs peuvent configurer leurs appareils Windows 10 existants ou nouveaux en suivant les étapes décrites dans cette rubrique : [configurer des ordinateurs Windows pour les utilisateurs professionnels de Microsoft 365](set-up-windows-devices.md). Pour les périphériques existants, les utilisateurs peuvent **éventuellement** [déplacer des fichiers vers OneDrive entreprise](move-files-to-onedrive.md). Ils peuvent également utiliser des outils tiers pour déplacer des fichiers associés à un profil Windows vers OneDrive.
  
Si votre organisation utilise Windows Server Active Directory en local, vous pouvez configurer Microsoft 365 entreprise pour protéger vos appareils Windows 10, tout en conservant l’accès aux ressources locales qui nécessitent une authentification locale. Suivez les étapes de la procédure [activer les appareils Windows 10 appartenant à un domaine pour qu’ils soient gérés par Microsoft 365 Business](manage-windows-devices.md) pour le configurer. Cette méthode est préférée et les appareils dans cet État sont appelés **périphériques hybrides Azure ad**. 
  
Si vous conservez un annuaire Active Directory local contenant certaines ressources locales (telles que des partages de fichiers et des imprimantes), vous pouvez donner à vos **appareils joints à Azure ad** l’accès à ces ressources en suivant les étapes ci-dessous : [accéder aux ressources locales à partir d’un appareil joint à Azure ad dans Microsoft 365 Business](access-resources.md).
  
  
## <a name="contact-support"></a>Contacter l’assistance

 **Si vous devez contacter le support technique :**
  
- Contactez votre partenaire.
    
- En tant qu’administrateur commercial Microsoft 365, vous avez accès à notre équipe de support technique : ** [contacter le support pour les entreprises-aide de l’administrateur](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b)**
    
## <a name="see-also"></a>Voir aussi

[Documentation et ressources pour Microsoft 365 Business](https://go.microsoft.com/fwlink/p/?linkid=853701)
  
[Gérer microsoft 365 Business](manage.md)[migrer vers Microsoft 365 Business](migrate-to-microsoft-365-business.md)

[Vidéos de formation Microsoft 365 Entreprise](https://support.office.com/article/6ab4bbcd-79cf-4000-a0bd-d42ce4d12816) 
