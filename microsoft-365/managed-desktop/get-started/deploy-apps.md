---
title: Déployer les applications sur les appareils
description: Informations pour l’ajout et le déploiement d’applications sur Microsoft Manged Desktop appareils.
keywords: Microsoft Manged Desktop, Microsoft 365, service, documentation, applications, applications métier, applications métier
ms.service: m365-md
author: jaimeo
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: jaimeo
manager: laurawi
ms.topic: article
ms.openlocfilehash: a84f6e13a7c189ce4cd33f308e765e5c59dae374
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60195232"
---
# <a name="deploy-apps-to-devices"></a>Déployer les applications sur les appareils
Une partie de l’intégration à Microsoft Manged Desktop inclut l’ajout et le déploiement d’applications sur les appareils de vos utilisateurs. Une fois que vous utilisez le portail Microsoft Manged Desktop, vous pouvez ajouter et déployer vos applications. 

Le processus global ressemble à ceci :
1. [Ajoutez](#1) des applications au portail Microsoft Manged Desktop : il peut s’y trouver des applications métier existantes ou des applications de Microsoft Store pour Entreprises que vous avez synchronisées avec Intune. 
2. [Créez Azure Active Directory groupes (AD)](#2) pour l’affectation d’application : vous utiliserez ces groupes pour gérer l’affectation d’application.
3. [Affecter des applications à vos utilisateurs](#3)

<span id="1" />

## <a name="step-1-add-apps-to-microsoft-managed-desktop-portal"></a>Étape 1 : Ajouter des applications à Microsoft Manged Desktop portail
Vous pouvez ajouter [Win32 ou Windows applications MSI,](#lob-apps)ou [Microsoft Store pour Entreprises des](#msfb-apps) applications à Microsoft Manged Desktop, puis les déployer sur Microsoft Manged Desktop appareils.

<span id="lob-apps">

###  <a name="win32-or-windows-msi-based-apps-to-microsoft-managed-desktop"></a>Win32 ou Windows applications basées sur MSI pour Microsoft Manged Desktop

Vous pouvez ajouter vos applications métier à Microsoft Manged Desktop portail. Pour plus d’informations sur les conditions requises pour les applications installées sur Microsoft Manged Desktop, voir [Microsoft Manged Desktop’application requise.](../service-description/mmd-app-requirements.md)

Dans cette procédure, vous allez sélectionner le type d’application que vous souhaitez ajouter, puis configurer et télécharger la source de l’application. 

**Pour ajouter votre application LOB ou votre Windows à Microsoft Manged Desktop portail**

Vous pouvez vous Microsoft Manged Desktop portail, ou vous connectez à Intune, puis rechercher des Microsoft Manged Desktop. Nous allons vous montrer la Microsoft Manged Desktop portail. 

1.    Connectez-vous [Microsoft Manged Desktop portail d’administration.](https://aka.ms/mmdportal) 
2.    Sous **Inventaire,** sélectionnez **Applications.**
3.    Dans la charge de travail applications, sélectionnez **Ajouter.**
4.    Dans **Ajouter une application,** sélectionnez **application** métier ou Windows **application (Win32).**
    - Si vous avez sélectionné une application **métier,** voir Ajouter une application métier Windows à [Microsoft Intune](/intune/lob-apps-windows) pour obtenir des instructions sur l’ajout et la configuration d’applications métier.
    - Si vous avez sélectionné **Windows application (Win32),** voir Gestion des applications [Win32](/intune/apps-win32-app-management) pour obtenir des instructions sur l’ajout et la configuration Windows applications.

<span id="msfb-apps">

### <a name="microsoft-store-for-business-apps"></a>Applications Microsoft Store pour Entreprises.
Si vous ne vous êtes pas inscrit à Microsoft Store pour Entreprises, vous pouvez vous inscrire lorsque vous achetez des applications. Une fois que vous avez vos applications, vous pouvez les synchroniser avec Microsoft Manged Desktop. 

**Pour acheter des applications à partir du Microsoft Store pour Entreprises**

1. Connectez-vous [Microsoft Store pour Entreprises](https://businessstore.microsoft.com) avec votre compte Microsoft Store pour Entreprises administrateur.
2. Sélectionnez **Acheter pour mon groupe.**
3. Utilisez la recherche pour rechercher l’application de votre choix, puis sélectionnez l’application.
4. Dans les détails du produit, **sélectionnez Obtenir l’application.** Microsoft Store ajoute l’application **à vos produits** pour votre organisation.

**Pour forcer une synchronisation entre Intune et Microsoft Store pour Entreprises**
1. Connectez-vous au [centre Microsoft Endpoint Manager’administration.](https://go.microsoft.com/fwlink/?linkid=2109431)
2. Sélectionnez **les**  >  **connecteurs et jetons d’administration**  >  **des Microsoft Store pour Entreprises**.
3. Sélectionnez **Synchroniser** pour obtenir les applications que vous avez achetées auprès du Microsoft Store dans Intune.

**Pour vérifier qu’une synchronisation entre Intune et Microsoft Store pour Entreprises est active**
1. Connectez-vous [Microsoft Store pour Entreprises](https://businessstore.microsoft.com) avec votre compte Microsoft Store pour Entreprises administrateur.
2. Sélectionnez **Gérer**.
3. Sélectionnez **Paramètres** puis **distribuer.**
4. Sous **Outils de** gestion, vérifiez qu’Intune est répertorié et que l’état est **Actif**.  

<span id="2" />

## <a name="step-2-create-azure-ad-groups"></a>Étape 2 : Créer des groupes Azure AD

Créez trois groupes Azure AD pour chaque application. Ce tableau présente les groupes dont vous aurez besoin (disponible, obligatoire et désinstallé). 

Type d’affectation d’application |    Utilisation de groupe    | Exemple de nom Azure AD
--- | --- | ---
Disponible |  L’application sera disponible à partir Portail d'entreprise application ou site web. | MMD – *nom de l’application* – Disponible
Obligatoire |  L’application est installée sur les appareils des groupes sélectionnés. | MMD – *nom de l’application* – Obligatoire
Désinstaller |  L’application est désinstallée des appareils des groupes sélectionnés. | MMD – *nom de l’application* – Désinstaller

Ajoutez vos utilisateurs à ces groupes pour rendre l’application disponible, installer l’application ou supprimer l’application de Microsoft Manged Desktop appareil. 

<span id="3" />

## <a name="step-3-assign-apps-to-your-users"></a>Étape 3 : Attribuer des applications à vos utilisateurs

**Pour affecter l’application à vos utilisateurs**

1. Connectez-vous [Microsoft Manged Desktop portail d’administration.](https://aka.ms/mmdportal)
2. Dans le volet Bureau géré, sélectionnez **Applications.**
3. Dans la charge de travail applications, sélectionnez l’application à qui vous souhaitez affecter des utilisateurs et **sélectionnez Affecter des groupes d’utilisateurs.**
4. Pour l’application spécifique, sélectionnez un type d’affectation (Disponible, Obligatoire, Désinstaller) et affectez le groupe approprié.
5. Dans le volet Attribuer des applications, sélectionnez **OK.**


## <a name="steps-to-get-started-with-microsoft-managed-desktop"></a>Étapes de mise en Microsoft Manged Desktop

1. Accéder au[Portail d’administration](access-admin-portal.md).
1. [Ajouter et vérifier des contacts d’administrateur dans le portail d’administration](add-admin-contacts.md).
1. [Ajuster les paramètres après l’inscription](conditional-access.md).
1. Déployez et affectez le[Portail d’entreprise Intune](company-portal.md).
1. [Attribuer des licences](assign-licenses.md).
1. Déployer des applications (cet article).
1. [Configurer les appareils](set-up-devices.md).
1. Configurez l’[Expérience de première exécution avec Autopilot et la page d’état d’inscription](esp-first-run.md).
1. [Activer les fonctionnalités de support utilisateur](enable-support.md).
1. [Préparez vos utilisateurs à utiliser des appareils](get-started-devices.md).
1. [Démarrage avec le contrôle d’application](get-started-app-control.md).


<!--# Preparing apps for Microsoft Managed Desktop

This topic is the target for 2 "Learn more" links in the Admin Portal (aka.ms/app-overview;app-package); also target for link from Online resources (aka.ms/app-overviewmmd-app-prep) do not delete.

-->