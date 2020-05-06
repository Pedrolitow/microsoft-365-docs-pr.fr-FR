---
title: Déployer les applications sur les appareils
description: Informations pour ajouter et déployer des applications sur des appareils de bureau gérés Microsoft.
keywords: Microsoft Managed Desktop, Microsoft 365, service, documentation, applications, applications métiers, applications métier
ms.service: m365-md
author: jaimeo
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
ms.openlocfilehash: 9fd6efc56441cfbe8a05404319246c5e0bbe10ab
ms.sourcegitcommit: eb3c7f473e8fe62624f52c9bb38dcd6a96fa58a3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "44046327"
---
# <a name="deploy-apps-to-devices"></a>Déployer les applications sur les appareils
L’intégration à Microsoft Managed Desktop inclut l’ajout et le déploiement d’applications sur les appareils de vos utilisateurs. Une fois que vous utilisez le portail de bureau géré Microsoft, vous pouvez ajouter et déployer vos applications. 

Le processus global se présente comme suit :
1. [Ajouter des applications au portail de bureau géré Microsoft](#1) -il peut s’agir d’applications métier existantes ou d’applications de Microsoft Store pour les entreprises que vous avez synchronisées avec Intune. 
2. [Créer des groupes Azure Active Directory (AD) pour l’affectation d’application](#2) : vous utiliserez ces groupes pour gérer l’affectation d’application.
3. [Affecter des applications à vos utilisateurs](#3)

<span id="1" />

## <a name="step-1-add-apps-to-microsoft-managed-desktop-portal"></a>Étape 1 : ajouter des applications au portail de bureau géré Microsoft
Vous pouvez ajouter des [applications Win32 ou Windows MSI](#lob-apps), ou [des applications Microsoft Store pour les entreprises](#msfb-apps) à Microsoft Managed Desktop, puis les déployer sur des appareils de bureau gérés Microsoft.

<span id="lob-apps">

###  <a name="win32-or-windows-msi-based-apps-to-microsoft-managed-desktop"></a>Applications Win32 ou Windows MSI à Microsoft Managed Desktop

Vous pouvez ajouter vos applications métier à Microsoft Managed Desktop Portal. Pour plus d’informations sur les conditions requises pour les applications installées sur les appareils de bureau géré Microsoft, consultez la rubrique [conditions requises pour les applications de bureau géré Microsoft](https://docs.microsoft.com/microsoft-365/managed-desktop/service-description/mmd-app-requirements).

Dans cette procédure, vous allez sélectionner le type d’application que vous souhaitez ajouter, puis configurer et télécharger la source de l’application. 

**Pour ajouter votre application LOB ou votre application Windows au portail de bureau géré Microsoft**

Vous pouvez vous connecter à Microsoft Managed Desktop Portal ou vous connecter à Intune, puis rechercher le bureau géré Microsoft. Nous allons afficher la connexion à Microsoft Managed Desktop Portal. 

1.    Connectez-vous au [portail d’administration de bureau géré Microsoft](https://aka.ms/mmdportal). 
2.    Sous **inventaire**, sélectionnez **applications**.
3.    Dans la charge de travail applications, sélectionnez **Ajouter**.
4.    Dans **Ajouter une application**, sélectionnez **application métier** ou **application Windows (Win32)**.
    - Si vous avez sélectionné **application métier**, voir [Add a Windows Line of Business app to Microsoft Intune](https://docs.microsoft.com/intune/lob-apps-windows) pour obtenir des instructions sur l’ajout et la configuration d’applications métiers.
    - Si vous avez sélectionné **Windows App (Win32)**, voir [Win32 App Management](https://docs.microsoft.com/intune/apps-win32-app-management) pour obtenir des instructions sur l’ajout et la configuration d’applications Windows.

<span id="msfb-apps">

### <a name="microsoft-store-for-business-apps"></a>Applications Microsoft Store pour les entreprises
Si vous ne vous êtes pas inscrit auprès de Microsoft Store pour les entreprises, vous pouvez vous inscrire lorsque vous achetez des applications. Une fois que vous avez vos applications, vous pouvez les synchroniser avec le bureau géré Microsoft. 

**Pour acheter des applications à partir de Microsoft Store pour les entreprises**

1. Connectez-vous à [Microsoft Store pour entreprises](https://businessstore.microsoft.com) avec votre compte d’administrateur Microsoft Store pour les entreprises.
2. Sélectionnez **acheter pour mon groupe**.
3. Utilisez la recherche pour trouver l’application de votre choix, puis sélectionnez l’application.
4. Dans les détails du produit, sélectionnez **obtenir l’application**. Microsoft Store ajoute l’application à **vos produits** pour votre organisation.

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

## <a name="step-2-create-azure-ad-groups"></a>Étape 2 : créer des groupes Azure AD

Créez trois groupes Azure AD pour chaque application. Ce tableau décrit les groupes dont vous aurez besoin (disponible, requis et désinstallation). 

Type d’affectation d’application |    Utilisation de groupe    | Exemple de nom Azure AD
--- | --- | ---
Available |  L’application sera disponible à partir de l’application ou du site Web du portail d’entreprise. | MMD – *nom* de l’application – disponible
Obligatoire |  L’application est installée sur les appareils dans les groupes sélectionnés. | MMD – *nom* de l’application – obligatoire
Uninstall |  L’application est désinstallée des appareils dans les groupes sélectionnés. | MMD – *nom* de l’application – Uninstall

Ajoutez vos utilisateurs à ces groupes pour que l’application soit disponible, installez l’application ou supprimez l’application de son appareil de bureau géré Microsoft. 

<span id="3" />

## <a name="step-3-assign-apps-to-your-users"></a>Étape 3 : attribuer des applications à vos utilisateurs

**Pour affecter l’application à vos utilisateurs**

1. Connectez-vous au [portail d’administration de bureau géré Microsoft](https://aka.ms/mmdportal).
2. Dans le volet bureau géré, sélectionnez **applications**.
3. Dans la charge de travail applications, sélectionnez l’application à laquelle vous souhaitez attribuer des utilisateurs et sélectionnez **affecter des groupes d’utilisateurs**.
4. Pour l’application spécifique, sélectionnez un type d’affectation (disponible, obligatoire, désinstaller) et affectez le groupe approprié.
5. Dans le volet attribuer des applications, sélectionnez **OK**.


## <a name="steps-to-get-started-with-microsoft-managed-desktop"></a>Étapes de prise en main de Microsoft Managed Desktop

1. [Ajouter et vérifier des contacts d’administrateur dans le portail d’administration](add-admin-contacts.md)
2. [Ajuster l’accès conditionnel](conditional-access.md)
3. [Affecter des licences](assign-licenses.md)
4. [Déployer le portail d’entreprise Intune](company-portal.md)
5. [Activer Enterprise State Roaming](enterprise-state-roaming.md)
6. [Configurer les appareils](set-up-devices.md)
7. [Préparer vos utilisateurs à l’utilisation les appareils](get-started-devices.md)
8. Déployer des applications (cette rubrique)


<!--# Preparing apps for Microsoft Managed Desktop

This topic is the target for 2 "Learn more" links in the Admin Portal (aka.ms/app-overview;app-package); also target for link from Online resources (aka.ms/app-overviewmmd-app-prep) do not delete.

-->
