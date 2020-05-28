---
title: Valider les paramètres de protection des applications sur les PC Windows 10
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
- MSB365
- seo-marvel-mar
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
ms.assetid: fae8819d-7235-495f-9f07-d016f545887f
description: Valider les paramètres de protection des applications Premium de Microsoft 365 sur les appareils Windows 10 et vérifier que les utilisateurs ne peuvent pas copier les données d’entreprise dans des fichiers personnels ou des applications non gérées.
ms.openlocfilehash: 589d2fc25cc1425a775523595881660cc03e152e
ms.sourcegitcommit: 2d59b24b877487f3b84aefdc7b1e200a21009999
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "44403387"
---
# <a name="validate-app-protection-settings-on-windows-10-pcs"></a>Valider les paramètres de protection des applications sur les PC Windows 10

## <a name="verify-that-users-cannot-copy-company-data-to-personal-files-on-corporate-devices"></a>Vérifiez que les utilisateurs ne peuvent pas copier des données professionnelles dans des fichiers personnels sur les appareils de l'entreprise

Une fois les [stratégies de protection des applications configurées](protection-settings-for-windows-10-devices.md), quelques heures peuvent être nécessaires avant que celles-ci prennent effet sur les appareils des utilisateurs. Si vous avez **activé la** case à cocher **empêcher les utilisateurs de copier les données d’entreprise dans des fichiers personnels et les forcer à enregistrer les fichiers de travail dans OneDrive entreprise** pour les appareils appartenant à une entreprise, vous pouvez vérifier cela sur l’appareil de l’utilisateur après s’être connecté à Azure ad et s’être connecté. 
  
 **Vérifiez les paramètres de connexion**
  
1. Une fois que vous vous êtes connecté à l’aide des informations d’identification de Microsoft 365 Business Premium et que vous vous connectez à Azure AD comme décrit dans la rubrique [configurer des appareils Windows pour les utilisateurs de Microsoft 365 Business Premium](set-up-windows-devices.md), accédez à **Paramètres Windows** \> **Accounts** \> **accès aux comptes d’accès professionnel ou scolaire**. Choisissez **connecté à \<tenant name\> Azure ad**, puis sélectionnez **informations**.
    
    ![Click or tap Info on the Connected to Azure AD dialog.](../media/a36ede2b-d1a0-4d4e-8ea7-af39b4b63890.png)
  
2. Sur la page **géré par** \<tenant name\> , vous pouvez voir les **informations de connexion** qui incluent une **adresse de serveur de gestion** telle que celle illustrée dans la figure suivante. 
    
    ![Managed by page shows connection info of the device manager URL.](../media/47515a8e-2d0c-4bea-99f0-6b2545b88a11.png)
  
 **Vérifier que vous ne pouvez pas coller les données d’entreprise dans une application non gérée**
  
1. Ouvrez Outlook 2016 qui a été installé par Microsoft 365 Business Premium.
    
2. Ouvrez un e-mail et copiez du contenu à partir de celui-ci.
    
    Ouvrez le Bloc-notes et essayez de coller le contenu.
    
    Vous recevrez un message d’erreur indiquant que l’application ne peut pas accéder au contenu.
    
    ![A dialog that states app can't access content when you paste into an unmanaged app.](../media/5e82b154-cf2f-43c8-ae80-b45d8ad80e56.png)
  
    En revanche, vous pouvez coller ce contenu dans Word 2016.
    
## <a name="verify-that-users-cannot-copy-company-data-to-personal-files-on-personal-devices"></a>Vérifiez que les utilisateurs ne peuvent pas copier des données professionnelles dans des fichiers personnels sur des appareils personnels

 **Vérifiez les paramètres de connexion**
  
1. Sur votre appareil personnel Windows 10 où vous êtes connecté en tant qu’utilisateur local, accédez à **Paramètres Windows**, puis cliquez ou appuyez **Accounts** sur \> **l’accès aux comptes professionnel ou scolaire**.
    
2. Sous **Accès Professionnel ou Scolaire**, choisissez **Connexion**.
    
3. Entrez vos informations d’identification Microsoft 365 Business Premium dans la **boîte de dialogue Configurer un compte professionnel ou scolaire** \> **Sign in**.
    
4. Sur la page **Accès Professionnel ou Scolaire**, choisissez **Compte professionnel ou scolaire**, puis **Informations**.
    
    ![Cliquez ou appuyez sur informations dans la boîte de dialogue compte scolaire ou professionnel.](../media/63bd8b32-cb32-4afa-8ce0-6070ac403abc.png)
  
5. Sur la **page accès professionnel ou scolaire** , vous pouvez voir les **informations de connexion** qui incluent une **adresse de serveur de gestion** telle que celle illustrée dans la figure suivante, et inclut les mots travail en *cours* et *Mam* au sein de. 
    
    ![Managed by page shows connection info URL that includes the words mam and wpi.](../media/abd4eaf4-44fa-4538-a3e8-1e0d331dfe1e.png)
  
 **Vérifier que vous ne pouvez pas coller les données d’entreprise dans une application non gérée**
  
1. Si nécessaire, ouvrez Outlook 2016 et ajoutez votre compte Microsoft 365 Business Premium, puis connectez-vous à l’aide de vos informations d’identification Microsoft 365 Business Premium.
    
2. Ouvrez un e-mail et copiez du contenu à partir de celui-ci.
    
    Ouvrez le Bloc-notes et essayez de coller le contenu.
    
    Vous recevrez un message d’erreur indiquant que l’application ne peut pas accéder au contenu.
    
    ![A dialog that states app can't access content when you paste into an unmanaged app.](../media/5e82b154-cf2f-43c8-ae80-b45d8ad80e56.png)
  
    En revanche, vous pouvez coller ce contenu dans Word 2016.
    

