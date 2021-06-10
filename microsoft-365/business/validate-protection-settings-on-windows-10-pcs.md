---
title: Valider les paramètres de protection des applications sur les PC Windows 10
f1.keywords:
- NOCSH
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
description: Validez Microsoft 365 Business Premium paramètres de protection des applications sur Windows 10 et vérifiez que les utilisateurs ne peuvent pas copier les données de l’entreprise dans des fichiers personnels ou des applications non gérées.
ms.openlocfilehash: e319ffa5149f055b5de45078facc8899acffc223
ms.sourcegitcommit: 53acc851abf68e2272e75df0856c0e16b0c7e48d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2021
ms.locfileid: "51579859"
---
# <a name="validate-app-protection-settings-on-windows-10-pcs"></a>Valider les paramètres de protection des applications sur les PC Windows 10

## <a name="verify-that-users-cannot-copy-company-data-to-personal-files-on-corporate-devices"></a>Vérifiez que les utilisateurs ne peuvent pas copier des données professionnelles dans des fichiers personnels sur les appareils de l'entreprise

Une fois les [stratégies de protection des applications configurées](protection-settings-for-windows-10-devices.md), quelques heures peuvent être nécessaires avant que celles-ci prennent effet sur les appareils des utilisateurs. Si vous  avez désactivé le paramètre Empêcher les utilisateurs de copier des données d’entreprise dans des fichiers personnels et les forcer à enregistrer des fichiers professionnels dans le paramètre **OneDrive Entreprise** pour les appareils de l’entreprise, vous pouvez le vérifier sur l’appareil de l’utilisateur une fois connecté à Azure AD et connecté. 
  
 **Vérifiez les paramètres de connexion**
  
1. Après vous être connecté avec les informations d’identification Microsoft 365 Business Premium et vous êtes connecté à Azure AD comme décrit dans Configurer des appareils Windows pour les utilisateurs [Microsoft 365 Business Premium,](set-up-windows-devices.md)accédez à **Windows Paramètres** Compte d’accès scolaire ou \>  \> scolaire. Choose **Connected to Azure \<tenant name\> AD,** and then choose **Info**.
    
    ![Click or tap Info on the Connected to Azure AD dialog.](../media/a36ede2b-d1a0-4d4e-8ea7-af39b4b63890.png)
  
2. Dans la page **Géré par,** vous pouvez voir les informations de connexion qui incluent une adresse de serveur de gestion comme celle présentée \<tenant name\> dans la figure suivante.   
    
    ![Managed by page shows connection info of the device manager URL.](../media/47515a8e-2d0c-4bea-99f0-6b2545b88a11.png)
  
 **Vérifier que vous ne pouvez pas coller des données d’entreprise dans une application non gérée**
  
1. Ouvrez Outlook 2016 qui a été installé par Microsoft 365 Business Premium.
    
2. Ouvrez un e-mail et copiez du contenu à partir de celui-ci.
    
    Ouvrez le Bloc-notes et essayez de coller le contenu.
    
    Vous recevrez une erreur qui indique que l’application ne peut pas accéder au contenu.
    
    ![A dialog that states app can't access content when you paste into an unmanaged app.](../media/5e82b154-cf2f-43c8-ae80-b45d8ad80e56.png)
  
    En revanche, vous pouvez coller ce contenu dans Word 2016.
    
## <a name="verify-that-users-cannot-copy-company-data-to-personal-files-on-personal-devices"></a>Vérifiez que les utilisateurs ne peuvent pas copier des données professionnelles dans des fichiers personnels sur des appareils personnels

 **Vérifiez les paramètres de connexion**
  
1. Sur votre appareil Windows 10 personnel sur lequel vous êtes connecté en tant qu’utilisateur local,  accédez à **Windows Paramètres,** puis cliquez ou appuyez sur Accès compte travail ou \> **scolaire.**
    
2. Sous **Accès Professionnel ou Scolaire**, choisissez **Connexion**.
    
3. Entrez vos informations d Microsoft 365 Business Premium dans la boîte de dialogue Configurer un compte scolaire ou **scolaire,** \> **connectez-vous.**
    
4. Sur la page **Accès Professionnel ou Scolaire**, choisissez **Compte professionnel ou scolaire**, puis **Informations**.
    
    ![Cliquez ou appuyez sur Info dans la boîte de dialogue Compte scolaire ou travail.](../media/63bd8b32-cb32-4afa-8ce0-6070ac403abc.png)
  
5. Dans la page **Accès** travail ou  scolaire, vous  pouvez voir les informations de connexion qui incluent une adresse de serveur de gestion comme celle présentée dans la figure suivante, et inclut les mots *wip* et *mam* dans. 
    
    ![Managed by page shows connection info URL that includes the words mam and wpi.](../media/abd4eaf4-44fa-4538-a3e8-1e0d331dfe1e.png)
  
 **Vérifier que vous ne pouvez pas coller des données d’entreprise dans une application non gérée**
  
1. Ouvrez Outlook 2016 et ajoutez votre compte Microsoft 365 Business Premium si nécessaire et connectez-vous à l’Microsoft 365 Business Premium informations d’identification.
    
2. Ouvrez un e-mail et copiez du contenu à partir de celui-ci.
    
    Ouvrez le Bloc-notes et essayez de coller le contenu.
    
    Vous recevrez une erreur qui indique que l’application ne peut pas accéder au contenu.
    
    ![A dialog that states app can't access content when you paste into an unmanaged app.](../media/5e82b154-cf2f-43c8-ae80-b45d8ad80e56.png)
  
    En revanche, vous pouvez coller ce contenu dans Word 2016.
    

