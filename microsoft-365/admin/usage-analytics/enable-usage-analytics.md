---
title: Activation de l'analyse de l'utilisation de Microsoft 365
f1.keywords:
- CSH
ms.author: sirkkuw
author: Sirkkuw
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
description: Découvrez comment commencer à collecter des données pour votre client à l’aide de l’application de modèle d’analyse de l’utilisation 365 de Microsoft dans Power BI.
ms.openlocfilehash: cda5931e81f7ea13208825afa658f1c672a2f326
ms.sourcegitcommit: 34ebec8e2bd54ba3d4ccfd9724797665c965c17f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2020
ms.locfileid: "49071454"
---
# <a name="enable-microsoft-365-usage-analytics"></a>Activation de l'analyse de l'utilisation de Microsoft 365

::: moniker range="o365-21vianet"

> [!NOTE]
> Le centre d’administration change. Si votre expérience ne correspond pas aux informations présentées ici, voir [À propos du nouveau centre d’administration Microsoft 365](https://docs.microsoft.com/microsoft-365/admin/microsoft-365-admin-center-preview?view=o365-21vianet).

::: moniker-end

L’analyse de l’utilisation de Microsoft 365 n’est pas encore disponible pour la communauté du gouvernement américain Microsoft 365.
  
## <a name="steps-to-enable-microsoft-365-usage-analytics"></a>Étapes d’activation de l’analyse de l’utilisation 365 Microsoft

Pour commencer à utiliser l’analyse de l’utilisation de Microsoft 365, vous devez d’abord mettre les données à disposition dans le centre d’administration 365 Microsoft, puis lancer l’application de modèle dans Power BI.
  
### <a name="get-power-bi"></a>Obtenir Power BI

Si vous ne disposez pas encore de Power BI, vous pouvez vous [inscrire à Power bi Pro](https://go.microsoft.com/fwlink/p/?linkid=845347). Sélectionnez **essayer gratuitement** pour vous inscrire pour une version d’évaluation ou **acheter maintenant** pour obtenir Power bi Pro.
  
  
Vous pouvez également développer **Produits** pour acheter une version de Power BI. 

> [!NOTE]
> Vous avez besoin d’une licence Power BI Pro pour installer, personnaliser et distribuer une application de modèle. Pour plus d’informations, reportez-vous à la rubrique [conditions préalables](https://docs.microsoft.com/power-bi/service-template-apps-install-distribute?source=docs#prerequisites).

Pour partager vos données, vous et les personnes avec lesquelles vous partagez des données, vous avez besoin d’une licence Power BI Pro ou le contenu doit se trouver dans un espace de travail dans un [service Power bi Premium](https://docs.microsoft.com/power-bi/service-premium-what-is). 
  
### <a name="enable-the-template-app"></a>Activer l’application de modèle

Pour activer l’application de modèle, vous devez être un **administrateur général**.
  
Pour plus d’informations, consultez la rubrique [à propos des rôles d’administrateur](../add-users/about-admin-roles.md) . 
  
1. Dans le centre d’administration, accédez à la page **Rapports** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Utilisation</a>. 
    
2. Sur la page **utilisation** , recherchez la carte d' **analyse d’utilisation Microsoft 365** , puis sélectionnez **prise en main**.
    
3. Dans le panneau rapports qui s’ouvre, définissez **mettre les données à la disposition de l’analyse de l’utilisation de Microsoft 365 pour Power bi à l'** **On** \> **enregistrement**. 
  
Le processus de collecte de données se terminera dans deux à 48 heures en fonction de la taille de votre client. Le bouton **go to Power bi** est activé (il n’est plus grisé) une fois la collecte de données terminée. 
    
### <a name="start-the-template-app"></a>Démarrer l’application de modèle

Pour démarrer l’application de modèle, vous devez être un **administrateur général** , un **lecteur de rapport** , un **administrateur Exchange** , un **administrateur Skype entreprise** ou un **administrateur SharePoint**. 
  
1. Copiez l’ID de client et sélectionnez **accéder à Power bi**.
    
2.  Lorsque vous accédez à Power BI, connectez-vous. **Sélectionnez ensuite applications** -> **obtenir des applications** dans le menu de navigation.    
  
3. Dans l’onglet **apps** , tapez Microsoft 365 dans la zone de recherche, puis sélectionnez **analyse de l’utilisation de Microsoft 365** \> **Get it now**.

    [![Sélectionnez obtenir maintenant](../../media/78102250-9874-4a32-8365-436f13560b52.png)](https://app.powerbi.com/groups/me/getapps/services/cia_microsoft365.microsoft-365-usage-analytics)
    
4.  Une fois que l’application est installée. Sélectionnez la mosaïque pour l’ouvrir.

5.  Sélectionnez **Explorer l’application** pour afficher l’application avec des exemples de données. Sélectionnez **connecter** pour connecter l’application aux données de votre organisation.

6.  Sélectionnez **connecter** , sur l’écran **se connecter à l’utilisation de Microsoft 365** , puis tapez l’ID de client (sans les tirets) que vous avez copié à l’étape (1), puis sélectionnez **suivant**.
    
7. Dans l’écran suivant, sélectionnez **OAuth2** comme **méthode d’authentification** \> **Sign in**. Si vous choisissez une autre méthode d’authentification, la connexion à l’application de modèle échouera.
    
    ![Choisir un compte Microsoft comme méthode d’authentification](../../media/ab6f0463-c3f7-4088-a605-67c699fa86adnew.png)
  
8. Une fois l’application de modèle instanciée, le tableau de bord d’analyse de l’utilisation de Microsoft 365 sera disponible dans Power BI sur le Web. Le chargement initial du tableau de bord prend entre 2 et 30 minutes.
  
Les agrégats de niveau client seront disponibles dans tous les rapports après avoir cliqué sur. Les **Détails au niveau de l’utilisateur ne seront disponibles que dans le cinquième mois du calendrier suivant**. Cela aura un impact sur tous les rapports sous activité de l’utilisateur (voir [naviguer et utiliser les rapports de l’analyse de l’utilisation de Microsoft 365](navigate-and-utilize-reports.md) pour obtenir des conseils sur l’affichage et l’utilisation de ces rapports).
    
## <a name="make-the-collected-data-anonymous"></a>Anonymiser les données collectées

Pour anonymiser les données collectées pour tous les rapports, vous devez être administrateur général. Cette opération masque les informations identifiables telles que les noms d’utilisateur, de groupe et de site dans les rapports et l’application de modèle.
  
1. Dans le centre d’administration, accédez à **Settings** paramètres d' \> **organisation** paramètres, puis, sous l’onglet **services** , choisissez **rapports**.
    
2. Sélectionnez **rapports** , puis choisissez d' **afficher les identificateurs anonymes**. Ce paramètre est appliqué à la fois aux rapports d’utilisation ainsi qu’à l’application de modèle.
  
3. Sélectionnez **Enregistrer les modifications**.
