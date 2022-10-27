---
title: Activer l’analytique de l’utilisation de Microsoft 365
f1.keywords:
- CSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: microsoft-365-business
ms.localizationpriority: medium
ms.collection:
- Tier2
- scotvorg
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
- admindeeplinkMAC
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 9db96e9f-a622-4d5d-b134-09dcace55b6a
description: Découvrez comment commencer à collecter des données pour votre locataire à l’aide de l’application modèle Analyse de l’utilisation Microsoft 365 dans Power BI.
ms.openlocfilehash: 16168afaf9a5ac232f2d238a4a33f87af32f15a8
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68736560"
---
# <a name="enable-microsoft-365-usage-analytics"></a>Activer l’analytique de l’utilisation de Microsoft 365

Pour activer l’analytique de l’utilisation de Microsoft 365 dans un locataire Microsoft 365 US Government Community Cloud (GCC), consultez [Se connecter à des données Microsoft 365 Government Community Cloud (GCC) avec Usage Analytics](connect-to-gcc-data-with-usage-analytics.md).

## <a name="before-you-begin"></a>Avant de commencer

Pour commencer à utiliser l’analytique de l’utilisation de Microsoft 365, vous devez d’abord rendre les données disponibles dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centre d'administration Microsoft 365</a>, puis sélectionner **Rapports** > **d’utilisation** et lancer l’application modèle dans Power BI.

## <a name="get-power-bi"></a>Obtenir Power BI

Si vous n’avez pas encore Power BI, vous pouvez vous [inscrire à Power BI Pro](https://go.microsoft.com/fwlink/p/?linkid=845347). Sélectionnez **Essayer gratuitement** pour vous inscrire à un essai, ou **Acheter maintenant** pour obtenir Power BI Pro.


Vous pouvez également développer **Produits** pour acheter une version de Power BI.

> [!NOTE]
> Vous avez besoin d’une licence Power BI Pro pour installer, personnaliser et distribuer une application modèle. Pour plus d’informations, consultez [Prérequis](/power-bi/service-template-apps-install-distribute?source=docs#prerequisites).

Pour partager vos données, vous et les personnes avec lesquelles vous partagez les données, avez besoin d’une licence Power BI Pro ou le contenu doit se trouver dans un espace de travail dans un [service Power BI Premium](/power-bi/service-premium-what-is).

## <a name="enable-the-template-app"></a>Activer l’application modèle

Pour activer l’application modèle, vous devez être **un Administrateur général**.

Pour plus [d’informations, consultez les rôles d’administrateur](../add-users/about-admin-roles.md) .

1. Dans le Centre d’administration, accédez à l’onglet **Paramètres** \> **De l’organisation Services**\>.

2. Sous l’onglet **Services** , sélectionnez  **Rapports**.

3. Dans le panneau Rapports qui s’ouvre, **définissez Rendre les données de rapport disponibles sur Analyse de l’utilisation de Microsoft 365 pour Power BI** **sur Enregistrer**\>.

Le processus de collecte de données se terminera dans deux à 48 heures en fonction de la taille de votre locataire. Le bouton **Accéder à Power BI** est activé (plus gris) une fois la collecte de données terminée. Une fois l’opération terminée, l’application fournit des données d’historique d’utilisation au niveau de votre organisation. 

> [!NOTE]
> Les données de l’onglet **« Activité de l’utilisateur »** sont actualisées uniquement après le quinzième jour du mois en cours et le premier jour du mois suivant, de sorte qu’elles restent vides initialement jusqu’à ce que la première actualisation soit terminée.

## <a name="start-the-template-app"></a>Démarrer l’application modèle

Pour démarrer l’application modèle, vous devez être **administrateur général**, lecteur de **rapport**, **administrateur Exchange**, **administrateur Skype Entreprise** ou **administrateur SharePoint**.

1. Copiez l’ID de locataire et sélectionnez **Accéder à Power BI**.

2. Lorsque vous accédez à Power BI, connectez-vous. Sélectionnez ensuite **Applications**->**Obtenir des applications** dans le menu de navigation.

3. Sous l’onglet **Applications**, tapez Microsoft 365 dans la zone de recherche, puis sélectionnez **Analyse de l’utilisation de Microsoft 365** **Obtenir maintenant**.\>

    [![Sélectionnez Obtenir maintenant.](../../media/78102250-9874-4a32-8365-436f13560b52.png)](https://app.powerbi.com/groups/me/getapps/services/cia_microsoft365.microsoft-365-usage-analytics)

4. Une fois l’application installée. Sélectionnez la vignette pour l’ouvrir.

5. Sélectionnez **Explorer l’application** pour afficher l’application avec des exemples de données. Choisissez **Se connecter** pour connecter l’application aux données de votre organisation.

6. Choisissez **Se connecter**, dans l’écran **Se connecter à Microsoft 365 Usage Analytics** , tapez l’ID de locataire (sans tirets) que vous avez copié à l’étape (1), puis sélectionnez **Suivant**.

7. Dans l’écran suivant, sélectionnez **OAuth2** comme **méthode** \> d’authentification **Se connecter**. Si vous choisissez une autre méthode d’authentification, la connexion à l’application modèle échoue.

    ![Choisissez compte Microsoft comme méthode d’authentification.](../../media/ab6f0463-c3f7-4088-a605-67c699fa86adnew.png)

8. Une fois l’application modèle instanciée, le tableau de bord d’analyse de l’utilisation de Microsoft 365 est disponible dans Power BI sur le web. Le chargement initial du tableau de bord prend entre 2 et 30 minutes.

Les agrégats au niveau du locataire seront disponibles dans tous les rapports après l’inscription. **Les détails au niveau de l’utilisateur ne seront disponibles que vers le 5 du prochain mois calendaire après l’inscription**. Cela aura un impact sur tous les rapports sous Activité utilisateur (voir [Naviguer et utiliser les rapports dans l’analytique de l’utilisation de Microsoft 365](navigate-and-utilize-reports.md) pour obtenir des conseils sur la façon d’afficher et d’utiliser ces rapports).

## <a name="make-the-collected-data-anonymous"></a>Anonymiser les données collectées

Les rapports fournissent des informations sur les données d’utilisation de votre organisation. Par défaut, les rapports affichent des informations avec des noms identifiables pour les utilisateurs, les groupes et les sites. À compter du 1er septembre 2021, nous masquons les informations utilisateur par défaut pour tous les rapports dans le cadre de notre engagement continu à aider les entreprises à prendre en charge leurs lois locales sur la confidentialité.
  
Les administrateurs globaux peuvent inverser cette modification pour leur client et afficher des informations d’utilisateur identifiables si les pratiques de confidentialité de leur organisation le permettent. Vous pouvez le faire dans le Centre d'administration Microsoft 365 en suivant les étapes suivantes :
  
1. Dans le Centre d’administration, allez à la page **Paramètres** \> **Paramètres de l’organisation** \> **Services**.

2. Sélectionnez **Rapports**. 
  
3. Décochez l’instruction **Dans tous les rapports, affichez les noms anonymisés des utilisateurs, des groupes et des sites**, puis enregistrez vos modifications.  
  
L’application de ces modifications prendra quelques minutes. L’affichage des informations utilisateur identifiables est un événement enregistré dans le journal d’audit du Centre de conformité Microsoft Purview.   

## <a name="related-content"></a>Contenu associé

[À propos de l’analytique de l’utilisation](usage-analytics.md) (article)\
[Obtenir la dernière version de l’analyse de l’utilisation](get-the-latest-version-of-usage-analytics.md) (article)\
[Naviguer et utiliser les rapports dans l’analytique de l’utilisation de Microsoft 365](navigate-and-utilize-reports.md) (article)
