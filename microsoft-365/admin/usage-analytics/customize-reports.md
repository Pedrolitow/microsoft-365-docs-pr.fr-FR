---
title: Personnaliser les rapports dans l’analyse de l’utilisation de Microsoft 365
f1.keywords:
- NOCSH
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
ms.assetid: 9b76065f-29b9-4b89-8059-c5f9db9ddbf6
description: Découvrez comment personnaliser des rapports dans le navigateur et Power BI Desktop.
ms.openlocfilehash: 121a9be4a83570b7fcf358c48bf558d3bc7c1131
ms.sourcegitcommit: 2d59b24b877487f3b84aefdc7b1e200a21009999
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "44402929"
---
# <a name="customize-the-reports-in-microsoft-365-usage-analytics"></a>Personnaliser les rapports dans l’analyse de l’utilisation de Microsoft 365

::: moniker range="o365-21vianet"

> [!NOTE]
> Le centre d’administration change. Si votre expérience ne correspond pas aux informations présentées ici, voir [À propos du nouveau centre d’administration Microsoft 365](https://docs.microsoft.com/microsoft-365/admin/microsoft-365-admin-center-preview?view=o365-21vianet).

::: moniker-end

L’analyse de l’utilisation de Microsoft 365 fournit un tableau de bord dans Power BI qui offre des informations sur la façon dont les utilisateurs adoptent et utilisent Microsoft 365. Le tableau de bord n'est qu'un point de départ pour interagir avec les données d'utilisation. Les rapports peuvent être personnalisés pour fournir des informations plus pertinentes.
  
Vous pouvez également utiliser Power BI Desktop pour approfondir la personnalisation de vos rapports en les connectant à d'autres sources de données afin d'obtenir des informations plus pertinentes sur votre activité.
  
## <a name="customizing-reports-in-the-browser"></a>Personnaliser les rapports dans le navigateur

Les deux exemples suivants montrent comment modifier un élément visuel existant et comment créer un élément visuel.
  
### <a name="modify-an-existing-visual"></a>Modifier un élément visuel existant

Cet exemple montre comment modifier l’onglet **activation** dans le rapport d' **activation/** de gestion des licences. 
  
1. Dans le rapport **activation/** gestion des licences, cliquez sur l’onglet **activation** .
    
2. Entrez le mode d’édition en cliquant sur le bouton **modifier** dans la partie supérieure via le bouton ![ autres pages du ](../../media/d8da3c19-3f2d-4bf6-811e-faa804f74770.png) bouton Power bi. 
    
    ![Click Edit report on the top right navigation](../../media/e2c16663-1fbd-4d7f-887c-0cbb891d3b3d.png)
  
3. En haut à droite, cliquez sur **dupliquer cette page**.
    
    ![Choose Duplicate this page](../../media/b2d18dcd-6b82-4ce7-ab79-1b24e3721309.png)
  
4. En bas à droite, cliquez sur l’un des graphiques représentant le nombre d’utilisateurs activés en fonction du système d’exploitation, comme Android, iOS, Mac, etc.
    
5. Dans la zone **visualisations** vers la droite, pour supprimer nombre de **Mac** de l’affichage, cliquez sur **X** en regard de l’icône.

    ![Supprimer le nombre de Mac](../../media/ce3d8358-df57-4f64-bd25-ac5be7fc8713.png)    
    
### <a name="create-a-new-visual"></a>Créer un élément visuel

L'exemple suivant montre comment créer un élément visuel pour assurer le suivi mensuel des nouveaux utilisateurs de Yammer.
  
1. Accédez au rapport d' **utilisation du produit** à l’aide du point de navigation gauche, puis cliquez sur l’onglet **Yammer** .
    
2. Passez en mode édition en cliquant sur ![ le bouton autres pages de Power bi ](../../media/d8da3c19-3f2d-4bf6-811e-faa804f74770.png) et **Modifiez**. 
    
3. Au bas de la page, cliquez sur ![Bouton Ajouter une page dans Power BI](../../media/d3b8c117-17d4-4f53-b078-8fefc2155b24.png) pour créer une page.
  
4. Dans la zone **visualisations** à droite, cliquez sur le **graphique à barres empilées** (ligne du haut, d’abord à partir de la gauche).

    ![Sélectionner un graphique à barres](../../media/214c3fed-6eae-43e6-83fb-708a2d74406e.png)
    
5. Cliquez sur l'angle inférieur droit de cette visualisation et faites-la glisser pour l'agrandir.

6. Dans la zone **champs** à droite, développez la table **calendrier** .

7. Faites glisser **MonthName** vers la zone Champs, juste en-dessous du titre **Axe** de la zone **Visualisations**.
 
    ![Faire glisser le nom du mois](../../media/bff99987-8c4b-4618-89fd-47df557b0ed7.png)
    
8. Dans la zone **Champs** de droite, développez la table **TenantProductUsage**.

9. Faites glisser **FirstTimeUsers** vers la zone Champs, juste en-dessous du titre **Valeur**.

10. Faites glisser **Produit** vers la zone **Filtres**, juste en-dessous du titre **Filtres au niveau de l'élément visuel**.

11. Dans la zone **Type de filtre** qui s'affiche, cochez la case **Yammer**.

    ![Case à cocher Sélectionner Yammer](../../media/82e99730-0de9-42da-928a-76aab0c3e609.png)
  
12. Juste en dessous de la liste des visualisations, cliquez **sur l'** icône format de l’icône ![ dans Power bi Visualizaions ](../../media/ee0602f3-3df5-4930-b862-db1d90ae4ae2.png) .

13. Développez Titre et remplacez la valeur **Texte du titre** par **Nouveaux utilisateurs de Yammer par mois**.
    
14. Remplacez la valeur **Taille du texte** par **12**.
    
15. Modifiez le titre de la nouvelle page en modifiant le nom de la page en bas à droite.

16.  Enregistrez le rapport en cliquant sur **mode lecture** en haut, puis sur **Enregistrer**.
    
## <a name="customizing-the-reports-in-power-bi-desktop"></a>Personnaliser les rapports dans Power BI Desktop

Pour la plupart des clients, la version web de Power BI suffit pour modifier les éléments visuels des rapports et des graphiques. Pour d'autres, en revanche, il peut être nécessaire de joindre ces données à d'autres sources de données afin d'obtenir des informations contextuelles plus pertinentes sur leur entreprise. Dans ce cas, ils peuvent utiliser Power BI Desktop pour personnaliser et créer des rapports supplémentaires. Vous pouvez télécharger [Power BI Desktop](https://go.microsoft.com/fwlink/p/?linkid=849797) gratuitement. 
  
### <a name="use-the-reporting-apis"></a>Utiliser les API de création de rapports

Vous pouvez commencer par vous connecter directement aux API de création de rapports ODATA à partir de Microsoft 365 pour alimenter ces rapports.
  
1. Accédez à **Obtenir des données** \> **Autres** \> **Flux ODATA** \> **Connexion**.
    
2. Dans la fenêtre URL, entrez « https:// <i></i> reports.Office.com/PBI/v1.0/ \<tenantid\> ».
    
    **Remarque :** Les API de création de rapports sont en aperçu et sont susceptibles d’être modifiées jusqu’à ce qu’elles soient en production. 
  
    ![OData feed URL for Power BI desktop](../../media/c0ef967e-a454-4eba-bc8e-61e113170053.png)
  
3. Entrez vos informations d’identification d’administrateur Microsoft 365 (organisation ou école) pour vous authentifier auprès de Microsoft 365 lorsque vous y êtes invité.
    
    Pour plus d’informations sur les personnes autorisées à accéder aux rapports d’application de modèle Microsoft 365 adoption, consultez le [Forum aux questions](usage-analytics.md#faq) . 
    
4. Une fois la connexion autorisée, la fenêtre du Navigateur affichera les jeux de données auxquels vous pouvez vous connecter.
    
    Sélectionnez tout, puis cliquez sur **Charger**.
    
    Les données sont téléchargées dans votre instance de Power BI Desktop. Enregistrez ce fichier pour pouvoir commencer à créer les rapports dont vous avez besoin.
    
    ![Valeurs ODATA disponibles dans l’API de création de rapports](../../media/545b4d17-dbbd-4cfc-b75a-a8b27283d438.png)
  
### <a name="use-the-microsoft-365-usage-analytics-template"></a>Utiliser le modèle d’analyse de l’utilisation de Microsoft 365

Vous pouvez également utiliser le fichier de modèle Power BI qui correspond aux rapports d’analyse de l’utilisation 365 de Microsoft comme point de départ pour la connexion aux données. L'avantage du fichier pbit est qu'il contient une chaîne de connexion déjà établie. Vous pouvez également tirer parti de toutes les mesures personnalisées créées, en plus des données renvoyées par le schéma de base.
  
Vous pouvez télécharger le fichier de modèle Power BI à partir du centre de téléchargement Microsoft à partir du [Centre de téléchargement](https://download.microsoft.com/download/7/8/2/782ba8a7-8d89-4958-a315-dab04c3b620c/Microsoft%20365%20Usage%20Analytics.pbit). Après avoir téléchargé le modèle de fichier Power BI, procédez comme suit pour commencer :
  
1. Ouvrez le fichier pbit.
    
2. Entrez votre ID de locataire dans la boîte de dialogue.
    
    ![Enter your tenant ID to open the pbit file](../../media/071ed0bf-8b9d-49c6-81fc-fd4c6cc85bd3.png)
  
3. Entrez vos informations d’identification d’administrateur pour vous authentifier auprès de Microsoft 365 lorsque vous y êtes invité.
    
     Pour plus d’informations sur les personnes autorisées à accéder aux rapports d’analyse de l’utilisation de Microsoft 365. 
    
    Une fois autorisées, les données seront actualisées dans le fichier Power BI.
    
    Le chargement des données peut prendre un certain temps. Au terme de celui-ci, vous pouvez enregistrer le fichier au format .pbix et continuer à personnaliser les rapports ou associer une source de données supplémentaire à ce rapport.
    
4. Suivez la documentation [Prise en main de Power BI](https://go.microsoft.com/fwlink/?linkid=849802) pour créer des rapports, les publier sur le service Power BI et les partager au sein de votre organisation. Pour poursuivre la personnalisation et le partage, des licences Power BI supplémentaires peuvent être nécessaires. Voir les [Conseils relatifs aux licences](https://go.microsoft.com/fwlink/p/?linkid=849803) Power BI pour plus d'informations. 
    

