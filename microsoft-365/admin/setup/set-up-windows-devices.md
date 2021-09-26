---
title: Configurer des Windows pour les utilisateurs Microsoft 365 Business Premium utilisateurs
f1.keywords:
- CSH
ms.author: sharik
author: skjerland
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- M365-identity-device-management
- Adm_TOC
ms.custom:
- Core_O365Admin_Migration
- MiniMaven
- MSB365
- OKR_SMB_M365
- TRN_M365B
- OKR_SMB_Videos
- seo-marvel-mar
- AdminSurgePortfolio
- okr_smb
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
ms.assetid: 2d7ff45e-0da0-4caa-89a9-48cabf41f193
description: Configurer des Windows en cours d Windows 10 Professionnel pour Microsoft 365 Business Premium utilisateurs, ce qui permet de centraliser la gestion et les contrôles de sécurité.
ms.openlocfilehash: 8fa14a7505e197c0e60f0ccceeb74c350a8b25b8
ms.sourcegitcommit: 24bff8a546491ff32ebf04d1f51abb3197035706
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2021
ms.locfileid: "59786274"
---
# <a name="set-up-windows-devices-for-microsoft-365-business-premium-users"></a>Configurer des Windows pour les utilisateurs Microsoft 365 Business Premium utilisateurs

## <a name="before-you-begin"></a>Avant de commencer

Avant de pouvoir configurer des Windows pour les utilisateurs Microsoft 365 Business Premium, assurez-vous que tous les appareils Windows exécutent Windows 10 Professionnel version 1703 (Creators Update). Windows 10 Professionnel est une condition préalable au déploiement de Windows 10 Business, qui est un ensemble de services cloud et de fonctionnalités de gestion des appareils qui complètent les Windows 10 Professionnel et permettent la gestion centralisée et les contrôles de sécurité de Microsoft 365 Business Premium.
  
Si vous avez des appareils Windows exécutant Windows 7 Pro, Windows 8 Professionnel ou Windows 8.1 Professionnel, votre abonnement Microsoft 365 Business Premium vous donne droit à une mise à niveau Windows 10 niveau.
  
Pour plus d'informations sur la mise à niveau des appareils Windows vers Windows 10 Professionnel Creators Update, suivez les étapes décrites dans cette rubrique : [Mettre à niveau des appareils Windows vers Windows Professionnel Creators Update](../../business-video/upgrade.md)
  
Vérifiez [que l’appareil est connecté à Azure AD](#verify-the-device-is-connected-to-azure-ad) pour vérifier que vous avez bien mis à niveau ou pour vous assurer que la mise à niveau a fonctionné.

## <a name="watch-connect-your-pc-to-microsoft-365-business"></a>Regardez : Connecter votre PC pour Microsoft 365 Entreprise

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE3yXh3] 

Si vous avez trouvé cette vidéo utile, consultez les [séries de formations complètes pour les petites entreprises et les nouveaux utilisateurs de Microsoft 365](../../business-video/index.yml).
  
## <a name="join-windows-10-devices-to-your-organizations-azure-ad"></a>Joindre des appareils Windows 10 au service Azure AD de votre organisation

Lorsque tous les appareils Windows de votre organisation ont été mis à niveau vers Windows 10 Professionnel Creators Update ou exécutent déjà Windows 10 Professionnel Creators Update, vous pouvez joindre ces appareils au Azure Active Directory de votre organisation. Une fois les appareils joints, ils sont automatiquement mis à niveau vers Windows 10 Business, qui fait partie de votre abonnement Microsoft 365 Business Premium abonnement.
  
### <a name="for-a-brand-new-or-newly-upgraded-windows-10-pro-device"></a>Pour un appareil Windows 10 Professionnel ou un appareil qui vient d'être mis à niveau

Suivez ces étapes pour un nouvel appareil exécutant Windows 10 Professionnel Creators Update, ou pour un appareil qui vient d'être mis à niveau vers Windows 10 Professionnel Creators Update sans passer par la configuration d'appareil Windows 10.
  
1. Suivez la configuration d'appareil Windows 10 jusqu'à ce que vous arriviez à la page **Comment souhaitez-vous configurer ?** 
    
    ![On the How would you like to set up page, choose Set up for an organization.](../../media/1b0b2dba-00bb-4a99-a729-441479220cb7.png)
  
2. Ici, **sélectionnez Configurer pour une** organisation, puis entrez votre nom d’utilisateur et votre mot de passe pour Microsoft 365 Business Premium. 
    
3. Terminez la configuration de l'appareil Windows 10.
    
   Une fois cette opération terminée, l'utilisateur est connecté au domaine Azure AD de votre organisation. Pour vous en assurer, voir [Vérifier qu'un appareil est connecté à Azure AD](#verify-the-device-is-connected-to-azure-ad). 
  
### <a name="for-a-device-already-set-up-and-running-windows-10-pro"></a>Pour un appareil qui a déjà été configuré et qui exécute Windows 10 Professionnel

 **Connecter des utilisateurs à Azure AD :**
  
1. Sur le PC Windows de l'utilisateur exécutant Windows 10 Professionnel, version 1703 (Creators Update) (voir [conditions préalables](../security-and-compliance/pre-requisites-for-data-protection.md)), cliquez sur le logo Windows, puis sur l'icône Paramètres.
  
   ![Dans la menu Démarrer, cliquez sur Windows Paramètres icône.](../../media/74e1ce9a-1554-4761-beb9-330b176e9b9d.png)
  
2. Dans **Paramètres**, accédez à **Comptes**.
  
   ![Dans Windows Paramètres, allez à Comptes.](../../media/472fd688-d111-4788-9fbb-56a00fbdc24d.png)
  
3. À la page **Vos informations**, cliquez sur **Accès Professionnel ou Scolaire** \> **Connexion**.
  
   ![Choisissez Connecter sous Accès Travail ou Scolaire.](../../media/af3a4e3f-f9b9-4969-b3e2-4ef99308090c.png)
  
4. Dans la boîte de dialogue **Configurer un compte professionnel ou scolaire**, sous **Autres actions**, sélectionnez **Joindre cet appareil à Azure Active Directory**.
  
   ![Cliquez sur Joindre cet appareil pour Azure Active Directory.](../../media/fb709a1b-05a9-4750-9cb9-e097f4412cba.png)
  
5. À la **page de connexion**, entrez votre adresse e-mail professionnelle ou scolaire \> **Suivant**.
  
   Dans la page **Saisie du mot de passe**, entrez votre mot de passe \> **Se connecter**.
  
   ![Entrez votre courrier électronique scolaire ou scolaire sur la page Vous aider à vous inscrire.](../../media/f70eb148-b1d2-4ba3-be38-7317eaf0321a.png)
  
6. Dans la page **Vérifier qu’il s’agit de votre** organisation, vérifiez que les informations sont correctes, puis sélectionnez **Rejoindre**.
  
   Sur le **you’re all set!** page, chosse **done**.
  
   ![Dans l’écran Assurez-vous qu’il s’agit de l’écran de votre organisation, sélectionnez Rejoindre.](../../media/c749c0a2-5191-4347-a451-c062682aa1fb.png)
  
Si vous avez chargé des fichiers vers OneDrive Entreprise, synchronisez-les vers votre ordinateur. Si vous avez utilisé un outil tiers pour migrer des profils et des fichiers, synchronisez-les également avec le nouveau profil.
  
## <a name="verify-the-device-is-connected-to-azure-ad"></a>Vérifiez que l’appareil est connecté à Azure AD

Pour vérifier votre état de synchronisation, sur la page **Access**  professionnel ou scolaire dans **Paramètres**, sélectionnez la zone Connecté à _ _ pour exposer les boutons Informations et \<organization name\> **Déconnexion.**  Choisissez **Info** pour obtenir votre état de synchronisation. 
  
Dans la page **État de la** synchronisation, sélectionnez **Synchroniser** pour obtenir les dernières stratégies de gestion des appareils mobiles sur le PC.
  
Pour commencer à utiliser le compte Microsoft 365 Business Premium, cliquez  avec le bouton Windows démarrer, cliquez avec le bouton droit sur l’image de votre compte actuel, puis changez **de compte.** Connectez-vous à l’aide de l’e-mail et du mot de passe de votre organisation.
  
![Cliquez sur le bouton Informations pour afficher l’état de synchronisation.](../../media/818f7043-adbf-402a-844a-59d50034911d.png)
  
## <a name="verify-the-pc-is-upgraded-to-windows-10-business"></a>Vérifiez que le PC est mis à niveau vers Windows 10 Business

Vérifiez que vos appareils joints à Azure AD Windows 10 sont mis à niveau vers Windows 10 Business dans le cadre de Microsoft 365 Business Premium abonnement.
  
1. Accédez à **Paramètres** \> **Système** \> **Informations système**.
    
2. Vérifiez que l' **édition** est bien **Windows 10 Business**.
    
    ![Verify that Windows edition is Windows 10 Business.](../../media/ff660fc8-d3ba-431b-89a5-f5abded96c4d.png)
  
## <a name="next-steps"></a>Étapes suivantes

Pour configurer vos appareils mobiles, voir Configurer des appareils mobiles pour les utilisateurs [Microsoft 365 Business Premium](set-up-mobile-devices.md), Pour définir des stratégies de protection des appareils ou des applications, voir Gérer Microsoft 365 [entreprise.](/admin/index.yml)
  
## <a name="related-content"></a>Contenu associé

[Vidéos de formation Microsoft 365 Entreprise](../../business-video/index.yml) (page de liens)
