---
title: Prise en main de Microsoft 365 Entreprise
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Adm_O365
ms.custom:
- Adm_O365
- Core_O365Admin_Migration
- MiniMaven
- MSB365
search.appverid:
- BCS160
- MET150
ms.assetid: 496e690b-b75d-4ff5-bf34-cc32905d0364
description: Découvrez comment configurer Microsoft 365 Business.
ms.openlocfilehash: 1c4adc64f62f7d4ae5038603804aa10e48d8a6e1
ms.sourcegitcommit: e491c4713115610cbe13d2fbd0d65e1a41c34d62
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "26867481"
---
# <a name="get-started-with-microsoft-365-business"></a>Prise en main de Microsoft 365 Entreprise

## <a name="what-is-microsoft-365-business"></a>Microsoft 365 Business, de quoi s'agit-il ?

Microsoft 365 Business est un ensemble complet d'outils professionnels de productivité et de collaboration, tels que Outlook, Word, Excel et d'autres produits Office toujours à jour. Vous pouvez protéger vos fichiers professionnels sur tous vos appareils iOS, Android et Windows 10 grâce à une sécurité de qualité professionnelle facile à gérer.
  
Microsoft 365 entreprise est destiné aux licences jusqu'à 300, si vous avez besoin de davantage de licences, voir la documentation [Microsoft 365 pour entreprises](https://go.microsoft.com/fwlink/p/?linkid=860986) pour plus d’informations. 
  
## <a name="get-microsoft-365-business"></a>Obtenir Microsoft 365 Business

- Si vous faites appel à un partenaire, il recevra Microsoft 365 Entreprise : [Obtenir Microsoft 365 Business auprès de l'Espace partenaires Microsoft](get-microsoft-365-business.md).
    
- Si vous ne disposez un partenaire et souhaitez obtenir Microsoft 365 Business, vous pouvez [acheter ici](https://www.microsoft.com/en-us/microsoft-365/business).
    
## <a name="set-up-microsoft-365-business"></a>Configurer Microsoft 365 Business

 **Vue d’ensemble de Microsoft 365 Business Suite configurer**
  
Le diagramme suivant décrit comment définir des administrateurs Microsoft 365 entreprise. Il décrit également les étapes pour préparer les ordinateurs Windows pour Microsoft 365 Business. Vous pouvez également ajouter de nouveaux périphériques à dans le centre d’administration Microsoft 365 Business avec [Pilote de Windows](add-autopilot-devices-and-profile.md). Vous pouvez utiliser le pilote au préalable configurer de nouveaux périphériques, obtenir prêts à être utilisés productifs dès qu’un utilisateur se connecte avec leurs informations d’identification Microsoft 365 Business.
  
![A diagram that shows the setup and management flow for admins, and also for a user](media/249f81fc-7e79-44c7-8425-3a0b7b651c3b.png)
  
### <a name="1-set-up-microsoft-365-business-admin"></a>1 : configurer Microsoft 365 Business (Admin)

Connectez-vous au [Centre d'administration Microsoft 365 Business](https://portal.office.com/adminportal/home) avec vos informations d'identification d'administrateur général et suivez les étapes ci-dessous pour configurer Microsoft 365 Entreprise. 
  
1. [Conditions préalables à la protection des données sur les appareils avec Microsoft 365 Business](pre-requisites-for-data-protection.md)
    
    Commencez par lire les conditions préalables pour vous assurer que vos appareils sont prêts pour Microsoft 365 Entreprise.
    
2. [Installer Microsoft 365 Business à l'aide de l'Assistant Installation](set-up.md)
    
    Si vous êtes **définitivement passage d’un site Active Directory local vers le nuage**, vous pouvez ajouter vos utilisateurs manuellement dans le centre d’administration Microsoft 365 à l’aide de l’Assistant installation, ou vous pouvez effectuer une synchronisation avec Azure AD connexion unique. Il existe deux façons de procéder : 
    
  - Si vous avez également un Exchange 2010, Exchange 2013 ou 2016 Exchange server, vous pouvez [Hybride Minimal utilisé pour migrer des boîtes aux lettres Exchange à Office 365 rapidement](https://support.office.com/article/fdecceed-0702-4af3-85be-f2a0013937ef). Les étapes hybride minimal incluent une synchronisation unique des utilisateurs à Azure AD ainsient migration sur site vers le nuage de messagerie. Une fois la migration terminée, la synchronisation d’annuaires est automatiquement désactivée lors de l’utilisation de cette méthode.
    
  - Utilisez l'Assistant Synchronisation d'annuaires Office 365 pour synchroniser vos utilisateurs avec le cloud. Suivez les étapes de [Configurer la synchronisation d'annuaires pour Office 365](https://support.office.com/article/1b3b5318-6977-42ed-b5c7-96fa74b08846) pour effectuer cette procédure. Une fois vos utilisateurs synchronisés avec le cloud, vous devrez [Désactiver la synchronisation d'annuaires](https://support.office.com/article/ee5f861e-bd48-4267-83d1-a4ead4b4a00d).
    
    Vous devrez également donner à chaque utilisateur qui a été ajouté de cette manière une licence pour Microsoft 365 Business. Vous pouvez le faire dans l' [Assistant Installation](set-up.md)ou dans l' [attribution de licences aux utilisateurs dans Office 365 pour entreprises](https://support.office.com/article/997596B5-4173-4627-B915-36ABAC6786DC).
    
### <a name="2-prepare-mobile-devices"></a>2 : préparer les appareils mobiles

Suivez les étapes de[Configuration des appareils mobiles pour les utilisateurs professionnels 365 de Microsoft](set-up-mobile-devices.md) pour installer les applications Office sur les périphériques et s’assurer qu’ils sont protégés par Microsoft 365 Business. 
  
### <a name="3-prepare-pcs"></a>3 : préparer PC

Administrateurs peuvent sélectionnez préalable des paramètres nouveaux périphériques Windows 10 PC à l’aide de [Pilote Windows](add-autopilot-devices-and-profile.md). Les utilisateurs peuvent définir leurs périphériques Windows 10 nouvelles ou existantes en suivant les étapes décrites dans cette rubrique : [configurer des ordinateurs Windows pour les utilisateurs professionnels 365 de Microsoft](set-up-windows-devices.md). Pour les périphériques existants les utilisateurs peuvent également **éventuellement**[déplacer les fichiers vers OneDrive entreprise](move-files-to-onedrive.md). Ils pouvant également utiliser des outils tiers pour déplacer les fichiers associés au profil Windows vers OneDrive.
  
Si votre organisation utilise Windows Server Active Directory sur site, vous pouvez configurer Microsoft 365 Business pour protéger vos périphériques Windows 10, tout en conservant l’accès aux ressources locales qui nécessitent une authentification locale. Suivez les étapes [permettre à un domaine aux périphériques Windows 10 devant être gérés par Microsoft 365 Business](manage-windows-devices.md) sur cette configuration. Il s’agit de la méthode recommandée et périphériques dans cet état sont appelés **hybride Azure AD participé à des périphériques**. 
  
Si vous conservez un local Active Directory contenant les ressources (telles que des partages de fichiers et d’imprimantes) sur site, vous pouvez donner votre accès **Azure périphériques AD-lié** à ces ressources en suivant les étapes décrites ici : [accès local ressources d’un Azure appareil AD-lié dans Microsoft 365 Business](access-resources.md).
  
Une fois que vous avez configuré Windows 10 PC, vous pouvez [installer automatiquement Office](auto-install-or-uninstall-office.md) sur les périphériques. 
  
## <a name="contact-support"></a>Contacter l’assistance

 **Si vous devez contacter le support technique :**
  
- Contactez votre partenaire.
    
- En tant qu’un administrateur de Microsoft 365 Business, vous avez accès à notre équipe de support client, ** [contacter le support technique pour les produits métiers : aide d’administration](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b)**
    
## <a name="related-topics"></a>Rubriques connexes
[Documentation et ressources pour Microsoft 365 Business](https://go.microsoft.com/fwlink/p/?linkid=853701)
  
[Gérer Microsoft 365 Business](manage.md) [Effectuer la migration vers Microsoft 365 Business](migrate-to-microsoft-365-business.md)
  

