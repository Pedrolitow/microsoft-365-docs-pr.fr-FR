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
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 9db96e9f-a622-4d5d-b134-09dcace55b6a
description: Découvrez comment commencer à collecter des données pour votre client à l'aide de l'application modèle Analyse de l'utilisation de Microsoft 365 dans Power BI.
ms.openlocfilehash: d9cadcc8258478fd1d5dbc0d9ae6bf4e814a8435
ms.sourcegitcommit: b6763a8ab240fbdd56078a7c9452445d0c4b9545
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2021
ms.locfileid: "51957514"
---
# <a name="enable-microsoft-365-usage-analytics"></a>Activation de l'analyse de l'utilisation de Microsoft 365

L'analyse de l'utilisation de Microsoft 365 n'est pas encore disponible pour la communauté Microsoft 365 pour le gouvernement américain.
  
## <a name="steps-to-enable-microsoft-365-usage-analytics"></a>Procédure d’analyse de l’utilisation de Microsoft 365

Pour commencer à utiliser l'analyse de l'utilisation de Microsoft 365, vous devez d'abord rendre les données disponibles dans le Centre d'administration Microsoft 365, puis lancer l'application modèle dans Power BI.
  
### <a name="get-power-bi"></a>Obtenir Power BI

Si vous n'avez pas encore Power BI, vous pouvez vous [inscrire à Power BI Pro.](https://go.microsoft.com/fwlink/p/?linkid=845347) Sélectionnez **Essayer gratuitement** de vous inscrire à une version d'essai ou **achetez** maintenant pour obtenir Power BI Pro.
  
  
Vous pouvez également développer **Produits** pour acheter une version de Power BI. 

> [!NOTE]
> Vous avez besoin d'une licence Power BI Pro pour installer, personnaliser et distribuer une application de modèle. Pour plus d'informations, voir [Conditions préalables.](/power-bi/service-template-apps-install-distribute?source=docs#prerequisites)

Pour partager vos données, vous et les personnes avec qui vous partagez les données, vous avez besoin d'une licence Power BI Pro ou le contenu doit se trouver dans un espace de travail dans un [service Premium Power BI.](/power-bi/service-premium-what-is) 
  
### <a name="enable-the-template-app"></a>Activer l'application de modèle

Pour activer l'application de modèle, vous devez être administrateur **général.**
  
Pour plus [d'informations, voir](../add-users/about-admin-roles.md) les rôles d'administrateur. 
  
1. Dans le centre d'administration, allez dans **l'onglet** \> **Paramètres Org settings** \> **Services.** 
    
2. Sous **l'onglet Services,** sélectionnez **Rapports.**
    
3. Dans le panneau Rapports qui s'ouvre, définissez Rendre les données de rapport disponibles pour l'analyse de l'utilisation de **Microsoft 365** pour Power BI sur **Sur** \> **Enregistrer.** 
  
Le processus de collecte de données se terminera dans deux à 48 heures en fonction de la taille de votre client. Le **bouton Aller à Power BI** est activé (plus gris) lorsque la collecte de données est terminée. 
    
### <a name="start-the-template-app"></a>Démarrer l'application de modèle

Pour démarrer l'application de modèle, vous devez être administrateur **général,** lecteur de **rapports,** administrateur **Exchange,** administrateur **Skype** Entreprise ou **administrateur SharePoint.** 
  
1. Copiez l'ID de client et **sélectionnez Go to Power BI**.
    
2.  Lorsque vous accédez à Power BI, connectez-vous. Sélectionnez **ensuite Applications** -> **Obtenir des applications** dans le menu de navigation.    
  
3. Dans **l'onglet** Applications, tapez Microsoft 365 dans la zone de recherche, puis sélectionnez Analyse de l'utilisation **de Microsoft 365** \> **Obtenez-le maintenant.**

    [![Sélectionnez Obtenir maintenant](../../media/78102250-9874-4a32-8365-436f13560b52.png)](https://app.powerbi.com/groups/me/getapps/services/cia_microsoft365.microsoft-365-usage-analytics)
    
4.  Une fois l'application installée. Sélectionnez la vignette pour l'ouvrir.

5.  Sélectionnez **Explorer l'application** pour afficher l'application avec des exemples de données. Choisissez **Se** connecter pour connecter l'application aux données de votre organisation.

6.  Choose **Connect**, on the **Connect to Microsoft 365 usage analytics** screen, then type in the tenant ID (without dashes) you copied in step (1), and select **Next**.
    
7. Dans l'écran suivant, sélectionnez **OAuth2 en** tant que méthode **d'authentification,** \> **connectez-vous.** Si vous choisissez une autre méthode d'authentification, la connexion à l'application de modèle échoue.
    
    ![Choisir un compte Microsoft comme méthode d'authentification](../../media/ab6f0463-c3f7-4088-a605-67c699fa86adnew.png)
  
8. Une fois l'application de modèle ins instantiée, le tableau de bord d'analyse de l'utilisation de Microsoft 365 sera disponible dans Power BI sur le web. Le chargement initial du tableau de bord prendra entre 2 et 30 minutes.
  
Les agrégats au niveau du client seront disponibles dans tous les rapports après l'avoir choisi. Les détails au niveau de l'utilisateur ne seront disponibles qu'autour du 5 du mois calendaire suivant **après l'avoir choisi.** Cela aura un impact sur tous les rapports sous Activité de l'utilisateur (voir Parcourir et utiliser les rapports dans l'analyse de l'utilisation de [Microsoft 365](navigate-and-utilize-reports.md) pour obtenir des conseils sur la façon d'afficher et d'utiliser ces rapports).
    
## <a name="make-the-collected-data-anonymous"></a>Anonymiser les données collectées

Pour anonymiser les données collectées pour tous les rapports, vous devez être administrateur général. Cela masquera les informations identifiables telles que les noms d'utilisateur, de groupe et de site dans les rapports et dans l'application de modèle.
  
1. Dans le Centre d'administration, sélectionnez **Paramètres** de l'organisation \> **paramètres,** puis sous **l'onglet Services,** choisissez **Rapports.**
    
2. Sélectionnez **Rapports,** puis choisissez **d'afficher les identificateurs anonymes.** Ce paramètre est appliqué à la fois aux rapports d'utilisation et à l'application de modèle.
  
3. Sélectionnez **Enregistrer les modifications**.
