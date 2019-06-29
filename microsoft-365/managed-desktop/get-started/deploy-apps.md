---
title: Déployer des applications pour les appareils de bureau gérés Microsoft
description: Informations pour ajouter et déployer des applications sur des appareils de bureau gérés Microsoft.
keywords: Microsoft Managed Desktop, Microsoft 365, service, documentation, applications, applications métiers, applications métier
ms.service: m365-md
author: jaimeo
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
ms.openlocfilehash: 5eac2e8c3023015bd034c51ad7e16a669a484772
ms.sourcegitcommit: 427c6459614d58f6ef7c74354ae1816423e22323
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/28/2019
ms.locfileid: "35390421"
---
# <a name="deploy-apps-to-microsoft-managed-desktop-devices"></a>Déployer des applications sur des appareils de bureau gérés Microsoft
L’intégration à Microsoft Managed Desktop inclut l’ajout et le déploiement d’applications sur les appareils de vos utilisateurs. Une fois que vous utilisez le portail de bureau géré Microsoft, vous pouvez ajouter et déployer vos applications. 

Le processus global se présente comme suit:
1. [Ajouter des applications au portail de bureau géré Microsoft](#1) -il peut s’agir d’applications métier existantes ou d’applications de Microsoft Store pour les entreprises que vous avez synchronisées avec Intune. 
2. [Créer des groupes Azure Active Directory (AD) pour l’affectation d’application](#2) : vous utiliserez ces groupes pour gérer l’affectation d’application.
3. [Affecter des applications à vos utilisateurs](#3)

<span id="1" />

## <a name="step-1-add-apps-to-microsoft-managed-desktop-portal"></a>Étape 1: ajouter des applications au portail de bureau géré Microsoft
Vous pouvez ajouter des [applications Win32 ou Windows MSI](#lob-apps), ou [des applications Microsoft Store pour les entreprises](#msfb-apps) à Microsoft Managed Desktop, puis les déployer sur des appareils de bureau gérés Microsoft.

<span id="lob-apps">

###  <a name="win32-or-windows-msi-based-apps-to-microsoft-managed-desktop"></a>Applications Win32 ou Windows MSI à Microsoft Managed Desktop

Vous pouvez ajouter vos applications métier à Microsoft Managed Desktop Portal. Pour plus d’informations sur les conditions requises pour les applications installées sur les appareils de bureau géré Microsoft, consultez la rubrique [conditions requises pour les applications de bureau géré Microsoft](https://docs.microsoft.com/microsoft-365/managed-desktop/service-description/mmd-app-requirements).

Dans cette procédure, vous allez sélectionner le type d’application que vous souhaitez ajouter, puis configurer et télécharger la source de l’application. 

**Pour ajouter votre application LOB ou votre application Windows au portail de bureau géré Microsoft**

Vous pouvez vous connecter à Microsoft Managed Desktop Portal ou vous connecter à Intune, puis rechercher le bureau géré Microsoft. Nous allons afficher la connexion à Microsoft Managed Desktop Portal. 

1.  Connectez-vous au [portail d’administration de bureau géré Microsoft](http://aka.ms/mmdportal). 
2.  Sous **inventaire**, sélectionnez **applications**.
3.  Dans la charge de travail applications, sélectionnez **Ajouter**.
4.  Dans **Ajouter une application**, sélectionnez **application métier** ou **application Windows (Win32)-Aperçu**.
    - Si vous avez sélectionné **application métier**, voir [Add a Windows Line of Business app to Microsoft Intune](https://docs.microsoft.com/intune/lob-apps-windows) pour obtenir des instructions sur l’ajout et la configuration d’applications métiers.
    - Si vous avez sélectionné **Windows App (Win32)-Preview**, voir [Win32 App Management](https://docs.microsoft.com/intune/apps-win32-app-management) pour obtenir des instructions sur l’ajout et la configuration d’applications Windows.

<span id="msfb-apps">

### <a name="microsoft-store-for-business-apps"></a>Applications Microsoft Store pour les entreprises
Si vous ne vous êtes pas inscrit auprès de Microsoft Store pour les entreprises, vous pouvez vous inscrire lorsque vous achetez des applications. Une fois que vous avez vos applications, vous pouvez les synchroniser avec le bureau géré Microsoft. 

**Pour acheter des applications à partir de Microsoft Store pour les entreprises**

1. Connectez-vous à [Microsoft Store pour entreprises](https://businessstore.microsoft.com) avec votre compte d’administrateur Microsoft Store pour les entreprises.
2. Sélectionnez **acheter pour mon groupe**.
3. Utilisez la recherche pour trouver l’application de votre choix, puis sélectionnez l’application.
4. Dans les détails du produit, sélectionnez **obtenir l’application**. Le Microsoft Store ajoute l’application aux **produits & services** de votre organisation.

**Pour forcer une synchronisation entre Intune et Microsoft Store pour les entreprises**
1. Se connecter au [portail Azure](https://portal.azure.com/) en tant qu’administrateur Intune ou administrateur global pour votre client
2. Sélectionnez **tous les services > Intune**. Intune se trouve dans la section surveillance + Management.
3. Dans le volet Intune, sélectionnez **applications clientes**, puis sélectionnez **Microsoft Store pour les entreprises**.
4. Sélectionnez **activer** pour synchroniser vos applications Microsoft Store pour les entreprises avec Intune.
    - Si vous ne l’avez pas encore fait, inscrivez-vous et associez votre compte Microsoft Store pour les entreprises avec Intune
    - Sélectionnez la langue dans laquelle les applications de Microsoft Store pour les entreprises seront affichées dans votre console Intune.
    - Sélectionnez **synchroniser** pour synchroniser vos applications Microsoft Store pour les entreprises avec Intune.
    - Vérifiez que la synchronisation entre Microsoft Store pour les entreprises et Intune est active (étape suivante). 

**Pour vérifier qu’une synchronisation entre Intune et Microsoft Store pour les entreprises est active**
1. Connectez-vous à [Microsoft Store pour entreprises](https://businessstore.microsoft.com) avec votre compte d’administrateur Microsoft Store pour les entreprises.
2. Sélectionnez **gérer**.
3. Sélectionnez **paramètres** , puis **distribuer**.
4. Sous **outils de gestion**, vérifiez que Intune est affiché et que l’État est **actif**.  

<span id="2" />

## <a name="step-2-create-azure-ad-groups"></a>Étape 2: créer des groupes Azure AD

Créez trois groupes Azure AD pour chaque application. Ce tableau décrit les groupes dont vous aurez besoin (disponible, requis et désinstallation). 

Type d’affectation d’application |   Utilisation de groupe   | Exemple de nom Azure AD
--- | --- | ---
Available |  L’application sera disponible à partir de l’application ou du site Web du portail d’entreprise. | MMD – *nom* de l’application – disponible
Obligatoire |  L’application est installée sur les appareils dans les groupes sélectionnés. | MMD – *nom* de l’application – obligatoire
Uninstall |  L’application est désinstallée des appareils dans les groupes sélectionnés. | MMD – *nom* de l’application – Uninstall

Ajoutez vos utilisateurs à ces groupes pour que l’application soit disponible, installez l’application ou supprimez l’application de son appareil de bureau géré Microsoft. 

<span id="3" />

## <a name="step-3-assign-apps-to-your-users"></a>Étape 3: attribuer des applications à vos utilisateurs

**Pour affecter l’application à vos utilisateurs**

1. Connectez-vous au [portail d’administration de bureau géré Microsoft](http://aka.ms/mmdportal).
2. Dans le volet bureau géré, sélectionnez **applications**.
3. Dans la charge de travail applications, sélectionnez l’application à laquelle vous souhaitez attribuer des utilisateurs et sélectionnez **affecter des groupes d’utilisateurs**.
4. Pour l’application spécifique, sélectionnez un type d’affectation (disponible, obligatoire, désinstaller) et affectez le groupe approprié.
5. Dans le volet attribuer des applications, sélectionnez **OK**.

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
