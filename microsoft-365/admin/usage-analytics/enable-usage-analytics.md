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
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 9db96e9f-a622-4d5d-b134-09dcace55b6a
description: Découvrez comment commencer à collecter des données pour votre client à l’aide de l’application de modèle d’analyse de l’utilisation 365 de Microsoft dans Power BI.
ms.openlocfilehash: 249fadce15ca2e4c979d6e1930ff0d14ccd9bc08
ms.sourcegitcommit: 812aab5f58eed4bf359faf0e99f7f876af5b1023
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/02/2020
ms.locfileid: "42355005"
---
# <a name="enable-microsoft-365-usage-analytics"></a>Activation de l'analyse de l'utilisation de Microsoft 365

Microsoft 365 l’analyse de l’utilisation est également disponible pour la communauté du gouvernement américain Microsoft 365.
  
## <a name="steps-to-enable-microsoft-365-usage-analytics"></a>Étapes d’activation de l’analyse de l’utilisation 365 Microsoft

Pour commencer à utiliser l’analyse de l’utilisation de Microsoft 365, vous devez d’abord mettre les données à disposition dans le centre d’administration 365 Microsoft, puis lancer l’application de modèle dans Power BI.
  
### <a name="get-power-bi"></a>Obtenir Power BI

Si vous ne disposez pas encore de Power BI, vous pouvez vous [inscrire à Power bi Pro](https://go.microsoft.com/fwlink/p/?linkid=845347). Sélectionnez **essayer gratuitement** pour vous inscrire pour une version d’évaluation ou **acheter maintenant** pour obtenir Power bi Pro.
  
  
Vous pouvez également développer **Produits** pour acheter une version de Power BI. 

> [!NOTE]
> Vous avez besoin d’une licence Power BI Pro pour installer, personnaliser et distribuer une application de modèle. Pour plus d’informations, reportez-vous à la rubrique [conditions préalables](https://docs.microsoft.com/power-bi/service-template-apps-install-distribute?source=docs#prerequisites).

Vous avez besoin d’une licence Power BI Pro pour partager votre contenu, et les personnes avec lesquelles vous le partagez également, ou le contenu doit se trouver dans un espace de travail d’une [capacité étendue](https://docs.microsoft.com/power-bi/service-premium-what-is). 
  
### <a name="enable-the-template-app"></a>Activer l’application de modèle

Pour activer l’application de modèle, vous devez être un **administrateur général**, un **lecteur de rapport**, un **administrateur Exchange**, un **administrateur Skype entreprise**ou un **administrateur SharePoint**. 
  
Pour plus d’informations, consultez la rubrique [à propos des rôles d’administrateur](../add-users/about-admin-roles.md) . 
  
1. Dans le centre d’administration, accédez à la page **Rapports** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Utilisation</a>. 
    
2. Sur la page **utilisation** , recherchez la carte d' **analyse d’utilisation Microsoft 365** , puis sélectionnez **prise en main**.
    
3. Dans le panneau rapports qui s’ouvre, définissez **mettre les données à la disposition de l’analyse de l’utilisation de Microsoft 365 pour Power bi** **à** \> l' **enregistrement**. 
  
Cette opération lance le processus de collecte de données et se termine dans les 2 à 48 heures suivant la taille de votre client. Le bouton **go to Power bi** est activé (il n’est plus grisé) une fois la collecte de données terminée. 
    
### <a name="initiate-the-template-app"></a>Lancer l’application de modèle

Pour lancer l’application de modèle, vous devez être un **administrateur général**, un **lecteur de rapports**, un **administrateur Exchange**, un **administrateur Skype entreprise**ou un **administrateur SharePoint**. 
  
1. Copiez l’ID de client et sélectionnez **accéder à Power bi**.
    
2.  Lorsque vous accédez à Power BI, connectez-vous. Sélectionnez applications->obtenir des applications à partir du menu de navigation.    
  
3. Dans l’onglet **apps** , tapez Microsoft 365 dans la zone de recherche, puis sélectionnez analyse \> **** de **l’utilisation de Microsoft 365** .

    [![Sélectionnez obtenir maintenant](../../media/78102250-9874-4a32-8365-436f13560b52.png)](https://app.powerbi.com/groups/me/getapps/services/cia_microsoft365.microsoft-365-usage-analytics)
    
4.  Une fois que l’application est installée. Cliquez sur la mosaïque pour l’ouvrir.

5.  Cliquez sur **Explorer l’application** pour afficher l’application avec des exemples de données. Cliquez sur **se connecter** pour connecter l’application aux données de votre organisation.

6.  Une fois que vous avez cliqué sur **connexion**, dans l’écran **se connecter à l’utilisation de Microsoft 365** , tapez l’ID client que \> vous avez copié à l’étape (1) **suivant**.
    
7. Dans l’écran suivant, sélectionnez **oAuth2** comme \> **** **méthode d’authentification** . Si vous choisissez une autre méthode d’authentification, la connexion à l’application de modèle échouera.
    
    ![Choose oAuth2 as authentication method](../../media/ac85a360-c278-4c60-8aa3-68f4828f1d96.png)
  
8. Une fois l’application de modèle instanciée, le tableau de bord d’analyse de l’utilisation de Microsoft 365 sera disponible dans Power BI sur le Web. Le chargement initial du tableau de bord prend entre 2 et 30 minutes.
  
Les agrégats de niveau client seront disponibles dans tous les rapports. **Les détails au niveau de l’utilisateur ne seront disponibles qu’après le 1er ou le 15 jour du mois civil après avoir**pris l’opt. Cela aura un impact sur tous les rapports sous activité de l’utilisateur (voir [naviguer et utiliser les rapports de l’analyse de l’utilisation de Microsoft 365](navigate-and-utilize-reports.md) pour obtenir des conseils sur l’affichage et l’utilisation de ces rapports).
    
## <a name="make-the-collected-data-anonymous"></a>Anonymiser les données collectées

Pour anonymiser les données collectées pour tous les rapports, vous devez être administrateur général. Cette opération masque les informations identifiables telles que les noms d’utilisateur, de groupe et de site dans les rapports et l’application de modèle.
  
1. Dans le centre d’administration, accédez aux **** \> **paramètres**paramètres, puis sous l’onglet **services** , choisissez **rapports**.
    
2. Sélectionnez **rapports**, puis choisissez d' **afficher les identificateurs anonymes**. Ce paramètre est appliqué à la fois aux rapports d’utilisation ainsi qu’à l’application de modèle.
  
3. Sélectionnez **Enregistrer les modifications**.
