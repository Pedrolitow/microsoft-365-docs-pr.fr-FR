---
title: Activation de l'analyse de l'utilisation de Microsoft 365
f1.keywords:
- CSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
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
description: Découvrez comment commencer à collecter des données pour votre client à l’aide de l’application Microsoft 365 d’analyse de l’utilisation dans Power BI.
ms.openlocfilehash: b547acc5adf312458e82108a36bbd9c0cbf60f10
ms.sourcegitcommit: 57211e8082a3429017ad33fe0e6bd9af203bb7ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2022
ms.locfileid: "62487310"
---
# <a name="enable-microsoft-365-usage-analytics"></a>Activation de l'analyse de l'utilisation de Microsoft 365

Pour activer Microsoft 365'analyse de l’utilisation dans Microsoft 365 client Cloud de la communauté du secteur public (Cloud de la communauté du secteur public) américain, voir Connecter [ Microsoft 365 Cloud de la communauté du secteur public (Cloud de la communauté du secteur public) avec l’analyse de l’utilisation](connect-to-gcc-data-with-usage-analytics.md).

## <a name="before-you-begin"></a>Avant de commencer

Pour commencer à utiliser Microsoft 365 l’analyse de l’utilisation, vous devez d’abord rendre les données disponibles dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centre d'administration Microsoft 365</a>, puis lancer l’application de modèle dans Power BI.

## <a name="get-power-bi"></a>Obtenir Power BI

Si vous n’avez pas encore Power BI, vous pouvez vous inscrire [à Power BI Pro](https://go.microsoft.com/fwlink/p/?linkid=845347). **Sélectionnez Essayer de** vous inscrire gratuitement à une version d’essai ou **achetez** maintenant pour obtenir Power BI Pro.


Vous pouvez également développer **Produits** pour acheter une version de Power BI.

> [!NOTE]
> Vous avez besoin d Power BI Pro licence pour installer, personnaliser et distribuer une application de modèle. Pour plus d’informations, voir [Conditions préalables](/power-bi/service-template-apps-install-distribute?source=docs#prerequisites).

Pour partager vos données, vous et les personnes avec qui vous partagez les données, vous avez besoin d’une licence Power BI Pro ou le contenu doit se trouver dans un espace de travail dans un [service Power BI premium](/power-bi/service-premium-what-is).

## <a name="enable-the-template-app"></a>Activer l’application de modèle

Pour activer l’application de modèle, vous devez être administrateur **général**.

Pour plus [d’informations, voir les rôles](../add-users/about-admin-roles.md) d’administrateur.

1. Dans le Centre d’administration, allez dans **l’onglet Paramètres** \> **Services des paramètres** **de l’organisation**\>.

2. Sous **l’onglet Services** , sélectionnez  **Rapports**.

3. Dans le panneau Rapports qui s’ouvre, définissez Rendre les données de rapport disponibles Microsoft 365 **l’analyse de l’utilisation Power BI** sur **Sur** \> **enregistrer**.

Le processus de collecte de données se terminera en 2 à 48 heures en fonction de la taille de votre client. Le **bouton Go to Power BI** est activé (plus gris) lorsque la collecte de données est terminée. Une fois l’application effectuée, elle fournit des données d’utilisation historiques au niveau de votre organisation. 

> [!NOTE]
> Les données de l’onglet « Activité de l’utilisateur » sont actualisées uniquement après le quinzième jour du mois en cours et le premier jour du mois suivant. Elles restent donc vides initialement jusqu’à ce que la première actualisation soit terminée.

## <a name="start-the-template-app"></a>Démarrer l’application de modèle

Pour démarrer l’application de modèle, vous devez être un administrateur **général****, un** lecteur de rapports, un administrateur **Exchange****, un** administrateur Skype Entreprise ou **un administrateur SharePoint de rapports**.

1. Copiez l’ID de client et **sélectionnez Power BI**.

2. Lorsque vous accédez à Power BI, connectez-vous. **Sélectionnez ensuite applications AppsGet**-> **dans** le menu de navigation.

3. Dans **l’onglet** Applications, tapez Microsoft 365 dans la zone de recherche, puis sélectionnez Microsoft 365 **l’analyse de l’utilisation** \> **.**

    [![Sélectionnez Obtenir maintenant.](../../media/78102250-9874-4a32-8365-436f13560b52.png)](https://app.powerbi.com/groups/me/getapps/services/cia_microsoft365.microsoft-365-usage-analytics)

4. Une fois l’application installée. Sélectionnez la vignette pour l’ouvrir.

5. **Sélectionnez Explorer l’application** pour afficher l’application avec des exemples de données. Choisissez **Connecter** pour connecter l’application aux données de votre organisation.

6. Choisissez **Connecter**, sur **l’écran d’analyse** de l’utilisation Connecter à Microsoft 365, tapez l’ID de locataire (sans tirets) que vous avez copié à l’étape (1), puis sélectionnez **Suivant.**

7. Dans l’écran suivant, sélectionnez **OAuth2** comme méthode **d’authentification se** \> **connectant**. Si vous choisissez une autre méthode d’authentification, la connexion au modèle d’application échoue.

    ![Choisissez un compte Microsoft comme méthode d’authentification.](../../media/ab6f0463-c3f7-4088-a605-67c699fa86adnew.png)

8. Une fois l’application de modèle ins Microsoft 365 le tableau de bord d’analyse de l’utilisation sera disponible Power BI sur le web. Le chargement initial du tableau de bord prend entre 2 et 30 minutes.

Les agrégats au niveau du client seront disponibles dans tous les rapports après l’avoir choisi. **Les détails au niveau de l’utilisateur ne seront disponibles que le 5 du mois calendaire suivant après l’avoir choisi**. Cela aura un impact sur tous les rapports sous Activité [](navigate-and-utilize-reports.md) de l’utilisateur (voir Parcourir et utiliser les rapports dans Microsoft 365'analyse de l’utilisation pour obtenir des conseils sur la façon d’afficher et d’utiliser ces rapports).

## <a name="make-the-collected-data-anonymous"></a>Anonymiser les données collectées

Les rapports fournissent des informations sur les données d’utilisation de votre organisation. Par défaut, les rapports affichent des informations avec des noms identifiables pour les utilisateurs, les groupes et les sites. À compter du 1er septembre 2021, nous masquons les informations utilisateur par défaut pour tous les rapports dans le cadre de notre engagement continu à aider les entreprises à prendre en charge leurs lois locales sur la confidentialité.
  
Les administrateurs globaux peuvent inverser cette modification pour leur client et afficher des informations d’utilisateur identifiables si les pratiques de confidentialité de leur organisation le permettent. Vous pouvez le faire dans le Centre d'administration Microsoft 365 en suivant les étapes suivantes :
  
1. Dans le Centre d’administration, allez à la page **Paramètres** \> **Paramètres de l’organisation** \> **Services**.

2. Sélectionnez **Rapports**. 
  
3. Décochez l’instruction **Dans tous les rapports, affichez les noms anonymisés des utilisateurs, des groupes et des sites**, puis enregistrez vos modifications.  
  
L’application de ces modifications prendra quelques minutes. L’affichage des informations utilisateur identifiables est un événement enregistré dans le journal d’audit du Centre de conformité Microsoft 365.   

## <a name="related-content"></a>Contenu associé

[À propos de l’analyse de l’utilisation](usage-analytics.md) (article)\
[Obtenir la dernière version de l’analyse de l’utilisation](get-the-latest-version-of-usage-analytics.md) (article)\
[Naviguer et utiliser les rapports dans l’analyse Microsoft 365'utilisation (](navigate-and-utilize-reports.md)article)
