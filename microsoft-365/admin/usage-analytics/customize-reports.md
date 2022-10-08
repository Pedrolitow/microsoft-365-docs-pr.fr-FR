---
title: Personnaliser les rapports dans l’analytique de l’utilisation de Microsoft 365
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: microsoft-365-business
ms.localizationpriority: medium
ms.collection:
- scotvorg
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 9b76065f-29b9-4b89-8059-c5f9db9ddbf6
description: Apprenez à personnaliser les rapports dans le navigateur et Power BI Desktop.
ms.openlocfilehash: 97ff462478b7172382aa797e8c4acb3a863bbe3f
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68193518"
---
# <a name="customize-the-reports-in-microsoft-365-usage-analytics"></a>Personnaliser les rapports dans l’analytique de l’utilisation de Microsoft 365

L’analytique de l’utilisation de Microsoft 365 fournit un tableau de bord dans Power BI qui fournit des insights sur la façon dont les utilisateurs adoptent et utilisent Microsoft 365. Le tableau de bord n'est qu'un point de départ pour interagir avec les données d'utilisation. Les rapports peuvent être personnalisés pour fournir des informations plus pertinentes.

Vous pouvez également utiliser Power BI Desktop pour approfondir la personnalisation de vos rapports en les connectant à d'autres sources de données afin d'obtenir des informations plus pertinentes sur votre activité.

## <a name="customizing-reports-in-the-browser"></a>Personnaliser les rapports dans le navigateur

Les deux exemples suivants montrent comment modifier un élément visuel existant et comment créer un élément visuel.

### <a name="modify-an-existing-visual"></a>Modifier un élément visuel existant

Cet exemple montre comment modifier l’onglet **Activation** dans le rapport **Activation/Licences** .

1. Dans le rapport **Activation/Licences** , sélectionnez **l’onglet Activation** .

2. Entrez le mode d’édition en choisissant le bouton **Modifier** en haut par le biais du ![bouton Plus de page dans Power BI.](../../media/d8da3c19-3f2d-4bf6-811e-faa804f74770.png) .

    ![Cliquez sur Modifier le rapport en haut à droite.](../../media/e2c16663-1fbd-4d7f-887c-0cbb891d3b3d.png)

3. En haut à droite, choisissez **Dupliquer cette page**.

    ![Choisissez Dupliquer cette page.](../../media/b2d18dcd-6b82-4ce7-ab79-1b24e3721309.png)

4. En bas à droite, choisissez l’un des graphiques à barres montrant le nombre d’utilisateurs qui s’activent en fonction du système d’exploitation, comme Android, iOS, Mac, etc.

5. Dans la zone **Visualisations** à droite, pour supprimer **Mac Count** du visuel, sélectionnez le **X** en regard de celui-ci.

    ![Supprimez le nombre de Mac.](../../media/ce3d8358-df57-4f64-bd25-ac5be7fc8713.png)

### <a name="create-a-new-visual"></a>Créer un élément visuel

L'exemple suivant montre comment créer un élément visuel pour assurer le suivi mensuel des nouveaux utilisateurs de Yammer.

1. Accédez au rapport **d’utilisation du produit** à l’aide du volet de navigation gauche et sélectionnez l’onglet **Yammer** .

2. Basculez en mode Édition en ![choisissant le bouton Plus de page dans Power BI.](../../media/d8da3c19-3f2d-4bf6-811e-faa804f74770.png) et **Modifier**.

3. En bas de la page, sélectionnez ![Bouton Ajouter une page dans Power BI.](../../media/d3b8c117-17d4-4f53-b078-8fefc2155b24.png) pour créer une page.

4. Dans la zone **Visualisations** à droite, choisissez le **graphique à barres empilées** (ligne supérieure, en premier à partir de la gauche).

    ![Sélectionnez Graphique à barres.](../../media/214c3fed-6eae-43e6-83fb-708a2d74406e.png)

5. Sélectionnez le bas à droite de cette visualisation et faites-la glisser pour la rendre plus grande.

6. Dans la zone **Champs** à droite, développez la table **Calendrier** .

7. Faites glisser **MonthName** vers la zone Champs, juste en-dessous du titre **Axe** de la zone **Visualisations**.

    ![Faites glisser le nom du mois.](../../media/bff99987-8c4b-4618-89fd-47df557b0ed7.png)

8. Dans la zone **Champs** de droite, développez la table **TenantProductUsage**.

9. Faites glisser **FirstTimeUsers** vers la zone Champs, juste en-dessous du titre **Valeur**.

10. Faites glisser **Produit** vers la zone **Filtres**, juste en-dessous du titre **Filtres au niveau de l'élément visuel**.

11. Dans la zone **Type de filtre** qui s'affiche, cochez la case **Yammer**.

    ![Cochez la case Yammer.](../../media/82e99730-0de9-42da-928a-76aab0c3e609.png)

12. Juste en dessous de la liste des visualisations, choisissez l’icône **Format** de l’icône ![Format dans Power BI Visualizaions.](../../media/ee0602f3-3df5-4930-b862-db1d90ae4ae2.png)

13. Développez Titre et remplacez la valeur **Texte du titre** par **Nouveaux utilisateurs de Yammer par mois**.

14. Remplacez la valeur **Taille du texte** par **12**.

15. Modifiez le titre de la nouvelle page en modifiant le nom de la page en bas à droite.

16. Enregistrez le rapport en cliquant sur **Mode Lecture** en haut, puis **enregistrez**.

## <a name="customizing-the-reports-in-power-bi-desktop"></a>Personnaliser les rapports dans Power BI Desktop

For most customers modifying the reports and chart visuals in Power BI web will be sufficient. For some however, there may be a need to join this data with other data sources to gain richer insights contextual to their own business, in which case they can customize and build additional reports using Power BI Desktop. You can download [Power BI Desktop](https://go.microsoft.com/fwlink/p/?linkid=849797) for free.

### <a name="use-the-reporting-apis"></a>Utiliser les API de création de rapports

Vous pouvez commencer par vous connecter directement aux API de création de rapports ODATA de Microsoft 365 qui alimentent ces rapports.

1. Accédez à **Obtenir des données** \> **Autres** \> **Flux ODATA** \> **Connexion**.

2. Dans la fenêtre URL, entrez « https://<i></i> reports.office.com/pbi/v1.0/\<tenantid\> »

    **NOTE:** Les API de création de rapports sont en préversion et peuvent être modifiées jusqu’à ce qu’elles passent en production.

    ![URL du flux OData pour Power BI Desktop.](../../media/c0ef967e-a454-4eba-bc8e-61e113170053.png)

3. Entrez vos informations d’identification d’administrateur Microsoft 365 (organisation ou école) pour vous authentifier auprès de Microsoft 365 lorsque vous y êtes invité.

    Pour plus d’informations sur les personnes autorisées à accéder aux rapports d’application modèle d’adoption de Microsoft 365, consultez la [FAQ](usage-analytics.md#faq) .

4. Une fois la connexion autorisée, la fenêtre du Navigateur affichera les jeux de données auxquels vous pouvez vous connecter.

    Sélectionnez tout et choisissez **Charger**.

    Les données sont téléchargées dans votre instance de Power BI Desktop. Enregistrez ce fichier pour pouvoir commencer à créer les rapports dont vous avez besoin.

    ![Valeurs ODATA disponibles dans l’API de création de rapports.](../../media/545b4d17-dbbd-4cfc-b75a-a8b27283d438.png)

### <a name="use-the-microsoft-365-usage-analytics-template"></a>Utiliser le modèle d’analyse de l’utilisation de Microsoft 365

Vous pouvez également utiliser le fichier de modèle Power BI qui correspond aux rapports d’analyse de l’utilisation de Microsoft 365 comme point de départ pour vous connecter aux données. L'avantage du fichier pbit est qu'il contient une chaîne de connexion déjà établie. Vous pouvez également tirer parti de toutes les mesures personnalisées créées, en plus des données renvoyées par le schéma de base.

Vous pouvez télécharger le fichier de modèle Power BI à partir du [Centre de téléchargement Microsoft](https://download.microsoft.com/download/7/8/2/782ba8a7-8d89-4958-a315-dab04c3b620c/Microsoft%20365%20Usage%20Analytics.pbit). Après avoir téléchargé le fichier de modèle Power BI, procédez comme suit pour commencer :

1. Ouvrez le fichier pbit.

2. Entrez votre ID de locataire dans la boîte de dialogue.

    ![Entrez votre ID de locataire pour ouvrir le fichier pbit.](../../media/071ed0bf-8b9d-49c6-81fc-fd4c6cc85bd3.png)

3. Entrez vos informations d’identification d’administrateur pour vous authentifier auprès de Microsoft 365 lorsque vous y êtes invité.

     pour plus d’informations sur les personnes autorisées à accéder aux rapports d’analyse de l’utilisation de Microsoft 365.

    Une fois autorisées, les données seront actualisées dans le fichier Power BI.

    Le chargement des données peut prendre un certain temps. Au terme de celui-ci, vous pouvez enregistrer le fichier au format .pbix et continuer à personnaliser les rapports ou associer une source de données supplémentaire à ce rapport.

4. Follow [Getting started with Power BI](/power-bi/fundamentals/desktop-getting-started) documentation to understand how to build reports, publish them to the Power BI service, and share with your organization. Following this path for customization and sharing may require additional Power BI licenses. See Power BI [licensing guidance](https://go.microsoft.com/fwlink/p/?linkid=849803) for details.
