---
title: Personnaliser les rapports dans l’analyse Microsoft 365'utilisation
f1.keywords:
- NOCSH
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
ms.assetid: 9b76065f-29b9-4b89-8059-c5f9db9ddbf6
description: Apprenez à personnaliser les rapports dans le navigateur et les Power BI Desktop.
ms.openlocfilehash: 0ef2364c82318dfea93e8df4e64d53a66caa8d74
ms.sourcegitcommit: 53acc851abf68e2272e75df0856c0e16b0c7e48d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2021
ms.locfileid: "51580773"
---
# <a name="customize-the-reports-in-microsoft-365-usage-analytics"></a>Personnaliser les rapports dans l’analyse Microsoft 365'utilisation

Microsoft 365'analyse de l’utilisation fournit un tableau de bord Power BI qui fournit des informations sur la façon dont les utilisateurs adoptent et utilisent Microsoft 365. Le tableau de bord n'est qu'un point de départ pour interagir avec les données d'utilisation. Les rapports peuvent être personnalisés pour fournir des informations plus pertinentes.
  
Vous pouvez également utiliser Power BI Desktop pour approfondir la personnalisation de vos rapports en les connectant à d'autres sources de données afin d'obtenir des informations plus pertinentes sur votre activité.
  
## <a name="customizing-reports-in-the-browser"></a>Personnaliser les rapports dans le navigateur

Les deux exemples suivants montrent comment modifier un élément visuel existant et comment créer un élément visuel.
  
### <a name="modify-an-existing-visual"></a>Modifier un élément visuel existant

Cet exemple montre comment modifier l’onglet **Activation** dans le rapport **Activation/Licences.** 
  
1. Dans le rapport **Activation/Licences,** sélectionnez **l’onglet Activation.**
    
2. Entrez le mode d’édition en cliquant sur le bouton Modifier en haut à travers le bouton Plus de page dans Power BI  ![ ](../../media/d8da3c19-3f2d-4bf6-811e-faa804f74770.png) bouton. 
    
    ![Click Edit report on the top right navigation](../../media/e2c16663-1fbd-4d7f-887c-0cbb891d3b3d.png)
  
3. Dans la partie supérieure droite, sélectionnez **Dupliquer cette page.**
    
    ![Choose Duplicate this page](../../media/b2d18dcd-6b82-4ce7-ab79-1b24e3721309.png)
  
4. En bas à droite, choisissez l’un des graphiques à barres affichant le nombre d’utilisateurs qui s’activent en fonction du système d’exploitation tel qu’Android, iOS, Mac, etc.
    
5. Dans la **zone Visualisations** à droite, afin de supprimer **Mac Count** de l’visuel, sélectionnez **le X** à côté de celui-ci.

    ![Supprimer le nombre de Mac](../../media/ce3d8358-df57-4f64-bd25-ac5be7fc8713.png)    
    
### <a name="create-a-new-visual"></a>Créer un élément visuel

L'exemple suivant montre comment créer un élément visuel pour assurer le suivi mensuel des nouveaux utilisateurs de Yammer.
  
1. Go to the **Product Usage** report using the left nav and select the **Yammer** tab.
    
2. Basculez en mode Édition en choisissant Le bouton plus ![ de page dans Power BI et ](../../media/d8da3c19-3f2d-4bf6-811e-faa804f74770.png) **Modifier**. 
    
3. En bas de la page, sélectionnez le ![Bouton Ajouter une page dans Power BI](../../media/d3b8c117-17d4-4f53-b078-8fefc2155b24.png) pour créer une page.
  
4. Dans la **zone Visualisations** à droite, choisissez le graphique **à** barres empilées (ligne supérieure, en premier à partir de la gauche).

    ![Sélectionner un graphique à barres](../../media/214c3fed-6eae-43e6-83fb-708a2d74406e.png)
    
5. Sélectionnez le bas à droite de cette visualisation et faites glisser pour l’agrandir.

6. Dans la **zone Champs** à droite, développez **la** table Calendrier.

7. Faites glisser **MonthName** vers la zone Champs, juste en-dessous du titre **Axe** de la zone **Visualisations**.
 
    ![Drag Month Name](../../media/bff99987-8c4b-4618-89fd-47df557b0ed7.png)
    
8. Dans la zone **Champs** de droite, développez la table **TenantProductUsage**.

9. Faites glisser **FirstTimeUsers** vers la zone Champs, juste en-dessous du titre **Valeur**.

10. Faites glisser **Produit** vers la zone **Filtres**, juste en-dessous du titre **Filtres au niveau de l'élément visuel**.

11. Dans la zone **Type de filtre** qui s'affiche, cochez la case **Yammer**.

    ![Cochez Yammer cocher](../../media/82e99730-0de9-42da-928a-76aab0c3e609.png)
  
12. Juste en dessous de la liste des visualisations, choisissez l’icône **Format** de l’icône ![ Format Power BI Visualizaions ](../../media/ee0602f3-3df5-4930-b862-db1d90ae4ae2.png) .

13. Développez Titre et remplacez la valeur **Texte du titre** par **Nouveaux utilisateurs de Yammer par mois**.
    
14. Remplacez la valeur **Taille du texte** par **12**.
    
15. Modifiez le titre de la nouvelle page en le éditant en bas à droite.

16.  Enregistrez le rapport en cliquant sur **Lecture en haut,** puis **enregistrez.**
    
## <a name="customizing-the-reports-in-power-bi-desktop"></a>Personnaliser les rapports dans Power BI Desktop

Pour la plupart des clients, la version web de Power BI suffit pour modifier les éléments visuels des rapports et des graphiques. Pour d'autres, en revanche, il peut être nécessaire de joindre ces données à d'autres sources de données afin d'obtenir des informations contextuelles plus pertinentes sur leur entreprise. Dans ce cas, ils peuvent utiliser Power BI Desktop pour personnaliser et créer des rapports supplémentaires. Vous pouvez télécharger [Power BI Desktop](https://go.microsoft.com/fwlink/p/?linkid=849797) gratuitement. 
  
### <a name="use-the-reporting-apis"></a>Utiliser les API de création de rapports

Vous pouvez commencer par vous connecter directement aux API de rapports ODATA Microsoft 365 qui sont à l’Microsoft 365 ces rapports.
  
1. Accédez à **Obtenir des données** \> **Autres** \> **Flux ODATA** \> **Connexion**.
    
2. Dans la fenêtre URL, entrez « https:// <i></i> reports.office.com/pbi/v1.0/ \<tenantid\> »
    
    **REMARQUE :** Les API de création de rapports sont en prévisualisation et sont sujettes à modification jusqu’à leur mise en production. 
  
    ![OData feed URL for Power BI desktop](../../media/c0ef967e-a454-4eba-bc8e-61e113170053.png)
  
3. Entrez vos informations d Microsoft 365 d’administrateur (organisation ou scolaire) pour vous authentifier Microsoft 365 à l’invite.
    
    Pour plus [d’informations](usage-analytics.md#faq) sur les personnes autorisées à accéder aux rapports d’application du modèle d’adoption Microsoft 365, consultez la FAQ. 
    
4. Une fois la connexion autorisée, la fenêtre du Navigateur affichera les jeux de données auxquels vous pouvez vous connecter.
    
    Sélectionnez tout et choisissez **Charger.**
    
    Les données sont téléchargées dans votre instance de Power BI Desktop. Enregistrez ce fichier pour pouvoir commencer à créer les rapports dont vous avez besoin.
    
    ![Valeurs ODATA disponibles dans l’API de rapports](../../media/545b4d17-dbbd-4cfc-b75a-a8b27283d438.png)
  
### <a name="use-the-microsoft-365-usage-analytics-template"></a>Utiliser le modèle d Microsoft 365 d’utilisation

Vous pouvez également utiliser le fichier de modèle Power BI qui correspond aux rapports d’analyse Microsoft 365 d’utilisation de l’Microsoft 365 comme point de départ pour se connecter aux données. L'avantage du fichier pbit est qu'il contient une chaîne de connexion déjà établie. Vous pouvez également tirer parti de toutes les mesures personnalisées créées, en plus des données renvoyées par le schéma de base.
  
Vous pouvez télécharger le fichier Power BI modèle à partir du [Centre de téléchargement Microsoft.](https://download.microsoft.com/download/7/8/2/782ba8a7-8d89-4958-a315-dab04c3b620c/Microsoft%20365%20Usage%20Analytics.pbit) Après avoir téléchargé le fichier Power BI de modèle, suivez les étapes suivantes pour commencer :
  
1. Ouvrez le fichier pbit.
    
2. Entrez votre ID de locataire dans la boîte de dialogue.
    
    ![Enter your tenant ID to open the pbit file](../../media/071ed0bf-8b9d-49c6-81fc-fd4c6cc85bd3.png)
  
3. Entrez vos informations d’identification d’administrateur pour vous authentifier Microsoft 365 à l’invite.
    
     pour plus d’informations sur les personnes autorisées à accéder Microsoft 365 rapports d’analyse de l’utilisation. 
    
    Une fois autorisées, les données seront actualisées dans le fichier Power BI.
    
    Le chargement des données peut prendre un certain temps. Au terme de celui-ci, vous pouvez enregistrer le fichier au format .pbix et continuer à personnaliser les rapports ou associer une source de données supplémentaire à ce rapport.
    
4. Suivez la documentation [Prise en main de Power BI](/power-bi/fundamentals/desktop-getting-started) pour créer des rapports, les publier sur le service Power BI et les partager au sein de votre organisation. Pour poursuivre la personnalisation et le partage, des licences Power BI supplémentaires peuvent être nécessaires. Voir les [Conseils relatifs aux licences](https://go.microsoft.com/fwlink/p/?linkid=849803) Power BI pour plus d'informations. 
