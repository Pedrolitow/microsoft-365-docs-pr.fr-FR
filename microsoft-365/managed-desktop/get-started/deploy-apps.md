---
title: Déployer des applications pour les périphériques de bureau Microsoft
description: Informations pour l’ajout et le déploiement d’applications sur les périphériques de bureau Microsoft.
keywords: Ordinateur de bureau Microsoft, Microsoft 365, service, documentation, applications, line-of-business applications, applications métier
ms.service: m365-md
author: trudyha
ms.localizationpriority: normal
ms.date: 01/17/2019
ms.openlocfilehash: 65d45be5ddb21d8f2cac876a1c8f93b2bbddf7b8
ms.sourcegitcommit: 0fc00286d7dc8cafddf9d17a98a375503b9551e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/18/2019
ms.locfileid: "29341603"
---
# <a name="deploy-apps-to-microsoft-managed-desktop-devices"></a>Déployer des applications sur les périphériques de bureau Microsoft
Composant d’intégration à Microsoft de bureau comprend l’ajout et déployer des applications sur les périphériques de l’utilisateur. Une fois que vous utilisez le portail Microsoft de bureau, vous pouvez ajouter et déployer vos applications. 

Le processus global ressemble à ceci :
1. [Ajouter les applications pour ordinateur de bureau Microsoft portal](#1) - cela peut être existant de métier (LOB) applications ou les applications de Microsoft Store for Business que vous avez synchronisé avec Intune. 
2. [Groupes créer Azure Active Directory (AD) pour l’affectation de l’application](#2) - vous allez utiliser ces groupes pour gérer l’affectation de l’application.
3. [Attribuer des applications à vos utilisateurs](#3)

<span id="1" />

## <a name="step-1-add-apps-to-microsoft-managed-desktop-portal"></a>Étape 1 : Ajouter des applications au portail Microsoft de bureau
Vous pouvez ajouter [Win32, applications basées sur Windows MSI](#lob-apps)ou [Magasin de Microsoft pour les applications métiers](#msfb-apps) à l’ordinateur de bureau Microsoft et puis déployez-les sur les périphériques de bureau Microsoft.

<span id="lob-apps">

###  <a name="win32-or-windows-msi-based-apps-to-microsoft-managed-desktop"></a>Applications basées sur MSI Win32 ou Windows à Microsoft géré du bureau

Vous pouvez ajouter vos applications de métier (LOB) au portail Microsoft de bureau. Pour plus d’informations sur la configuration requise pour les applications installées sur les périphériques de bureau Microsoft, voir [Configuration requise de bureau Microsoft](https://docs.microsoft.com/microsoft-365/managed-desktop/service-description/mmd-app-requirements).

Dans cette procédure, vous devez sélectionner le type d’application que vous souhaitez ajouter, puis configurer et télécharger la source de l’application. 

**Pour ajouter votre application métier ou une application Windows au portail Microsoft de bureau**

Vous pouvez connectez-vous au portail de l’ordinateur de bureau Microsoft, ou vous connecter à Intune et recherchez de bureau Microsoft. Nous allons connexion au portail Microsoft de bureau. 

1.  Connectez-vous au [portail d’administration de bureau géré Microsoft](http://aka.ms/mmdportal). 
2.  Dans le menu **inventaire**, sélectionnez **applications**.
3.  Dans la charge de travail des applications, sélectionnez **Ajouter**.
4.  Dans **Ajouter application**, sélectionnez **application métier** d’ou **Afficher un aperçu de l’application Windows (Win32)**.
    - Si vous avez sélectionné **métier d’application**, voir [Ajouter une application métier de Windows Intune Microsoft](https://docs.microsoft.com/intune/lob-apps-windows) pour obtenir des instructions sur l’ajout et la configuration des applications line-of-business.
    - Si vous avez sélectionné **Afficher un aperçu de l’application Windows (Win32) -**, voir [Gestion des applications Win32](https://docs.microsoft.com/intune/apps-win32-app-management) pour obtenir des instructions sur l’ajout et la configuration des applications Windows.

<span id="msfb-apps">

### <a name="microsoft-store-for-business-apps"></a>Magasin de Microsoft pour les applications métiers
Si vous n’avez pas encore inscrit auprès de Microsoft Store pour les entreprises, vous pouvez vous inscrire lorsque vous achetez des applications. Une fois que vous avez vos applications, vous pouvez les synchroniser avec l’ordinateur de bureau Microsoft. 

**Pour acheter des applications de le Store Microsoft pour les entreprises**

1. Connectez-vous à [Microsoft Store for Business](https://businessstore.microsoft.com) avec votre Store Microsoft pour le compte d’administrateur d’entreprise.
2. Sélectionnez **Mon groupe d’environnement de stockage centralisé**.
3. Utiliser la recherche pour trouver que l’application que vous souhaitez, puis sélectionnez l’application.
4. Dans les détails du produit, sélectionnez **obtenir l’application**. Microsoft Store ajoute l’application pour les **produits et services &** pour votre organisation.

**Pour forcer une synchronisation entre Intune et Microsoft Store pour les entreprises**
1. Connectez-vous au [Portail Azure](https://portal.azure.com/) Intune Admin ou administrateur Global pour votre client
2. Sélectionnez **tous les services > Intune**. Intune convient bien la surveillance + gestion section.
3. Dans le volet Intune, sélectionnez les **Applications clientes**, puis sélectionnez **Banque de Microsoft pour les entreprises**.
4. Sélectionnez **Activer** pour synchroniser votre Store Microsoft pour les applications métiers avec Intune.
    - Si vous n’avez pas déjà, sign up et associer votre Microsoft stocker pour un compte professionnel avec Intune
    - Sélectionnez la langue dans laquelle les applications de le Store Microsoft pour les entreprises seront affichera dans votre console Intune
    - Sélectionnez la **synchronisation** pour synchroniser votre Store Microsoft pour les applications métiers avec Intune.
    - Vérifiez que la synchronisation entre Microsoft Store for Business et Intune est active (étape suivante). 

**Pour vérifier qu’une synchronisation entre Intune et Microsoft Store for Business est active**
1. Connectez-vous à [Microsoft Store for Business](https://businessstore.microsoft.com) avec votre Store Microsoft pour le compte d’administrateur d’entreprise.
2. Sélectionnez **Gérer**.
3. Sélectionnez **paramètres** , puis **distribuer**.
4. Sous **Outils de gestion**, vérifiez que Intune est répertorié et que l’état est **actif**.  

<span id="2" />

## <a name="step-2-create-azure-ad-groups"></a>Étape 2 : Créer des groupes d’Azure AD

Créez trois groupes Azure AD pour chaque application. Ce tableau présente les groupes dont vous aurez besoin (disponible, nécessaire et désinstaller). 

Type d’application affectation |   Utilisation de groupe   | Nom de l’exemple Azure AD
--- | --- | ---
Disponible |  L’application sera disponible à partir d’application de portail d’entreprise ou un site Web. | MMD – *nom de l’application* – disponible
Obligatoire |  L’application est installée sur des appareils dans les groupes sélectionnés. | MMD – *nom de l’application* – requis
Désinstaller |  Application estimée est désinstallée à partir des périphériques dans les groupes sélectionnés. | MMD – *nom de l’application* – désinstaller

Ajouter des utilisateurs à ces groupes pour rendre l’application disponible, installer l’application ou supprimer l’application à partir de leur appareil de bureau Microsoft. 

<span id="3" />

## <a name="step-3-assign-apps-to-your-users"></a>Étape 3 : Attribuer des applications à vos utilisateurs

**Pour affecter l’application à vos utilisateurs**

1. Connectez-vous au [portail d’administration de bureau géré Microsoft](http://aka.ms/mmdportal).
2. Dans le volet de l’ordinateur de bureau, sélectionnez **applications**.
3. Dans la charge de travail des applications, sélectionnez l’application que vous souhaitez affecter des utilisateurs à et sélectionnez **affecter des groupes d’utilisateurs**.
4. Pour l’application spécifique, sélectionnez un type d’affectation (disponible, requis, Uninstall) et affecter le groupe approprié.
5. Dans le volet affecter des applications, sélectionnez **OK**.

<!--# Preparing apps for Microsoft Managed Desktop

This topic is the target for 2 "Learn more" links in the Admin Portal (aka.ms/app-overview;app-package); also target for link from Online resources (aka.ms/app-overviewmmd-app-prep) do not delete.

Applications: supported/onboard/deployment
 
Microsoft and Microsoft Managed Desktop customers have equally critical, yet different responsibilities around applications used with Microsoft Managed Desktop.

## Microsoft responsibilities
**Office 365 apps**
Microsoft will provide full service for the deployment, update, and support of specific Office 365 apps. All users will receive the base set of Office 365 click to run, 64 bit version of applications included in the device’s image so that a user can quickly become productive. The Project and Visio applications in of the Office 365 suite are licensed separately.  Microsoft Managed Desktop will provide deployment groups allowing the IT Administrator to manage licenses and deploy these applications appropriately for their organization. Microsoft will support end users of these applications through the Microsoft Managed Desktop Support channels.

**Line-of-business apps**
Microsoft provides tooling for IT Administrators to manage and deploy their line-of-business (LOB) applications to end users as a part of the Intune product. Microsoft will support application deployment issues as detailed in [Line-of-business applications](#line-of-business-applications) 

**Deploy with Intune**
Intune will be linked to the **Microsoft Store for Business** during Microsoft Managed Desktop onboarding allowing procured apps to be deployed through Intune. Microsoft will also deploy the web-based version of the Company Portal to end users so that IT Administrators can provide a self-service experience for end users.

**App management**
Microsoft may identify restricted applications which are not suitable for the modern workplace because of their system impact. When such an application is identified Microsoft will notify the customer and that application will need to be removed from the tenant. 

For more information on restricted app behaviors and app requirements, see [Microsoft Managed Desktop app requirements](../service-description/mmd-app-requirements.md)

## Customer responsibilities
The Office 365 Suite is core to Microsoft’s productivity offerings and is included in the Microsoft 365 License for all Microsoft Managed Desktop users. While Microsoft deploys, updates, and supports Office Applications to Microsoft Managed Desktop Devices there are still some areas for which the customer is responsible.
- **Assign licenses** - Customers are responsible for assigning the appropriate licenses to end users for Office 365. 
- **Add users to security groups** - For customers with users who need Project or Visio, the IT administrator must add those users to the appropriate deployment groups. IT administrators are also responsible for managing end of life for those users. 
- **Deploy Office 365 Add Ons** - Customers are responsible for deploying any plugins to the Office 365 suite which are deemed necessary. 

Since line-of-business (LOB) apps are unique for each customer, customers are responsible for managing all applications within their organization not deployed by Microsoft. This includes:
- Deciding which apps are needed and who needs them
- Assigning apps to those users
- Create and maintain Azure Active Directory (AD) groups for managing app assignments 

The customer must upload LOB apps to Intune. They are then responsible for deploying, updating, and decommissioning those applications over their respective lifecycles, as well as managing support for these apps for their users.

## Office applications
As part of the Microsoft 365 E5 license, Office 365 Standard Suite (64 Bit) is deployed by Microsoft. 

For details, see [Microsoft Managed Desktop technologies](../intro/technologies.md) <!--- and the other applications licensed under Office 365 E5 may be deployed by the customer using Intune’s deployment tools.

## Line-of-business applications
This table summarizes responsibilities across the different phases for line-of-business (LOB) applications. 

Application work items |    Customer    | Microsoft
--- | --- | ---
**Onboarding apps** |  |
Identify applications needed for targeted user groups   | ![yes](images/checkmark.png)  |
Create and manage Azure AD groups for app deployment | ![yes](images/checkmark.png) |   
**App Packaging** |  |
Package apps to meet Intune deployment standards |  ![yes](images/checkmark.png) |  
Upload apps to Intune | ![yes](images/checkmark.png)     |
Test apps in Microsoft Managed Desktop environment |    ![yes](images/checkmark.png) |  
Test apps with end users    | ![yes](images/checkmark.png) |    
**Deployment** | |
Manage and assign users to applications  | ![yes](images/checkmark.png)  |
Intune deployment tools delivers application to remote clients| |   ![yes](images/checkmark.png)
Identify and deploy application updates through Intune | ![yes](images/checkmark.png)    |
Unistall and remove applications when they have been retired    | ![yes](images/checkmark.png) |    
**Management** | |
Procure and assign licenses |   ![yes](images/checkmark.png)     |
Provide end-user support for line-of-business apps  | ![yes](images/checkmark.png) |
Manage app settings remotely    | ![yes](images/checkmark.png) |

For information on LOB application requirements, see [Microsoft Managed Desktop application requirements](../service-description/mmd-app-requirements.md)


## Intune application deployment
Application management can be handled through the Microsoft Managed Desktop Admin portal, or through the Intune portal. Intune’s app management portal shows applications deployed for Windows, Android, and iOS. Microsoft Managed Desktop Admin portal limits the view to Windows 10 applications. Both are available through the Azure Portal. 
* [Intune app management basics](https://docs.microsoft.com/intune/app-management)
* [Add apps to Intune](https://docs.microsoft.com/intune/app-management)
   * [Add a line-of-business App](https://docs.microsoft.com/intune/lob-apps-windows)
   * [Add Win32 apps to Intune](https://docs.microsoft.com/intune/apps-win32-app-management)
   * [Add web applications](https://docs.microsoft.com/intune/web-app)
* [Deploy apps](https://docs.microsoft.com/intune/apps-deploy)
   * [Deploy apps to Windows 10](https://docs.microsoft.com/intune/apps-windows-10-app-deploy)
* Company Portal
   * [Deploy the Company Portal](https://docs.microsoft.com/intune/store-apps-company-portal-app)
   * [Configure the Company Portal app](https://docs.microsoft.com/intune/company-portal-app)-->