---
title: Valider les paramètres de protection des applications sur les PC Windows 10
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom:
- Adm_O365
- Core_O365Admin_Migration
- MSB365
search.appverid:
- BCS160
- MET150
ms.assetid: fae8819d-7235-495f-9f07-d016f545887f
description: Découvrez comment valider les paramètres de protection Microsoft 365 Business application pour les appareils Windows 10.
ms.openlocfilehash: f00dd380103ad9498d77b0e8814bace3de168df4
ms.sourcegitcommit: e491c4713115610cbe13d2fbd0d65e1a41c34d62
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "26867246"
---
# <a name="validate-app-protection-settings-on-windows-10-pcs"></a>Valider les paramètres de protection des applications sur les PC Windows 10

## <a name="verify-that-users-cannot-copy-company-data-to-personal-files-on-corporate-devices"></a>Vérifiez que les utilisateurs ne peuvent pas copier des données professionnelles dans des fichiers personnels sur les appareils de l'entreprise

Une fois les [stratégies de protection des applications configurées](protection-settings-for-windows-10-devices.md), quelques heures peuvent être nécessaires avant que celles-ci prennent effet sur les appareils des utilisateurs. Si vous avez **activé** le paramètre **Empêcher les utilisateurs de copier des données professionnelles dans des fichiers personnels et les obliger à enregistrer les fichiers professionnels dans OneDrive Entreprise** pour les appareils appartenant à l'entreprise, vous pouvez vérifier qu'il est appliqué sur l'appareil de l'utilisateur une fois celui-ci connecté à Azure AD et authentifié. 
  
 **Vérifier les paramètres de connexion**
  
1. Une fois authentifié avec vos informations d'identification Microsoft 365 Entreprise et connecté à Azure AD, comme décrit dans [Configurer des appareils Windows pour les utilisateurs de Microsoft 365 Business](set-up-windows-devices.md), accédez à **Paramètres Windows** \> **Comptes** \> **Accès Professionnel ou Scolaire**. Choisissez **Connecté à \<nom du client\> Azure AD**, puis **Informations**.
    
    ![Click or tap Info on the Connected to Azure AD dialog.](media/a36ede2b-d1a0-4d4e-8ea7-af39b4b63890.png)
  
2. La page **Gérés par** \<nom du client\> affiche les **Informations de connexion**, avec une **Adresse de serveur de gestion** semblable à celle illustrée sur la figure suivante. 
    
    ![Managed by page shows connection info of the device manager URL.](media/47515a8e-2d0c-4bea-99f0-6b2545b88a11.png)
  
 **Vérifiez que vous ne pouvez pas coller de données professionnelles dans une application non gérée**
  
1. Ouvrez l'instance d'Outlook 2016 qui a été installée par Microsoft 365 Entreprise.
    
2. Ouvrez un e-mail et copiez du contenu à partir de celui-ci.
    
    Ouvrez le Bloc-notes et essayez de coller le contenu.
    
    Vous recevrez un message d'erreur indiquant que l'application n'a pas accès au contenu.
    
    ![A dialog that states app can't access content when you paste into an unmanaged app.](media/5e82b154-cf2f-43c8-ae80-b45d8ad80e56.png)
  
    En revanche, vous pouvez coller ce contenu dans Word 2016.
    
## <a name="verify-that-users-cannot-copy-company-data-to-personal-files-on-personal-devices"></a>Vérifiez que les utilisateurs ne peuvent pas copier des données professionnelles dans des fichiers personnels sur des appareils personnels

 **Vérifiez les paramètres de connexion**
  
1. Sur l'appareil Windows 10 personnel auquel vous êtes connecté en tant qu'un utilisateur local, accédez à **Paramètres Windows** et cliquez ou appuyez sur **Comptes** \> **Accès Professionnel ou Scolaire**.
    
2. Sous **Accès Professionnel ou Scolaire**, choisissez **Connexion**.
    
3. Entrez vos informations d'identification Microsoft 365 Entreprise dans la boîte de dialogue **Configurer un compte professionnel ou scolaire** \> **Se connecter**.
    
4. Sur la page **Accès Professionnel ou Scolaire**, choisissez **Compte professionnel ou scolaire**, puis **Informations**.
    
    ![Click or tap Info on the Work or school account dalog.](media/63bd8b32-cb32-4afa-8ce0-6070ac403abc.png)
  
5. La page **Accès Professionnel ou Scolaire** affiche les **Informations de connexion** avec une **Adresse de serveur de gestion** semblable à celle illustrée sur la figure suivante ainsi que les mots  *wip*  et  *mam*  . 
    
    ![Managed by page shows connection info URL that includes the words mam and wpi.](media/abd4eaf4-44fa-4538-a3e8-1e0d331dfe1e.png)
  
 **Vérifiez que vous ne pouvez pas coller de données professionnelles dans une application non gérée**
  
1. Ouvrez Outlook 2016 et, si nécessaire, ajoutez votre compte Microsoft 365 Entreprise, puis connectez-vous avec vos informations d'identification Microsoft 365 Entreprise.
    
2. Ouvrez un e-mail et copiez du contenu à partir de celui-ci.
    
    Ouvrez le Bloc-notes et essayez de coller le contenu.
    
    Vous recevrez un message d'erreur indiquant que l'application n'a pas accès au contenu.
    
    ![A dialog that states app can't access content when you paste into an unmanaged app.](media/5e82b154-cf2f-43c8-ae80-b45d8ad80e56.png)
  
    En revanche, vous pouvez coller ce contenu dans Word 2016.
    

