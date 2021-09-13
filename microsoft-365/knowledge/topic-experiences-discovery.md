---
title: Gérer la découverte de rubriques dans Sujets Microsoft Viva
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
ms.reviewer: nkokoye
audience: admin
ms.topic: article
ms.service: o365-administration
search.appverid: MET150
localization_priority: Normal
description: Découvrez comment administrer la découverte de rubriques dans Sujets Microsoft Viva.
ms.openlocfilehash: 2316df8df7a1d8fb2b8e0951e12810398bcb2e40
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59207532"
---
# <a name="manage-topic-discovery-in-microsoft-viva-topics"></a>Gérer la découverte de rubriques dans Sujets Microsoft Viva

Vous pouvez gérer les paramètres de découverte de rubrique dans le [Centre d'administration Microsoft 365](https://admin.microsoft.com). Vous devez être administrateur général ou administrateur SharePoint pour effectuer ces tâches.

## <a name="to-access-topics-management-settings"></a>Pour accéder aux paramètres de gestion des rubriques :

1. Dans la Centre d'administration Microsoft 365, cliquez **sur Paramètres,** puis sur **Paramètres de l’organisation.**
2. Sous **l’onglet Services,** cliquez sur **Expériences de rubrique.**

    ![Connecter personnes à connaître.](../media/admin-org-knowledge-options-completed.png) 

3. Sélectionnez **l’onglet Découverte de** rubrique. Consultez les sections suivantes pour plus d’informations sur chaque paramètre.

    ![knowledge-network-settings.](../media/knowledge-network-settings-topic-discovery.png) 

## <a name="select-sharepoint-topic-sources"></a>Sélectionner SharePoint sources de rubriques

Vous pouvez modifier les SharePoint sites de votre organisation qui seront analyser pour les rubriques.

Si vous souhaitez inclure ou exclure une liste spécifique de sites, vous pouvez utiliser le modèle .csv suivant :

``` csv
Site name,URL
```

Si vous ajoutez des sites à l'aide du sélecteur de sites, ils sont ajoutés à la liste existante des sites à inclure ou à exclure. Si vous téléchargez un fichier .csv, il remplace toute liste existante. Si vous avez précédemment inclus ou exclu des sites spécifiques, vous et téléchargez la liste en tant que fichier .csv, a apporté des modifications et chargez la nouvelle liste.

Pour choisir des sites pour la découverte de rubriques

1. Sous l’onglet **Découverte de rubrique** , sous **Sélectionner les sources de rubrique SharePoint**, sélectionnez **Modifier**.
2. Dans la page **Sélectionner SharePoint sources** de rubriques, sélectionnez les sites SharePoint seront analyser en tant que sources pour vos rubriques lors de la découverte. Cela inclut les opérations suivantes :
    - **Tous les sites**: tous SharePoint sites de votre client. Cela capture les sites actuels et futurs.
    - **Tous, sauf les sites sélectionnés**: tapez les noms des sites que vous souhaitez exclure.  Vous pouvez également charger une liste de sites que vous souhaitez refuser de découvrir. Les sites créés dans le futur seront inclus comme sources pour la découverte de rubriques. 
    - **Seuls les sites** sélectionnés : tapez les noms des sites que vous souhaitez inclure. Vous pouvez également charger une liste de sites. Les sites créés dans le futur ne seront pas inclus comme sources pour la découverte de rubriques.
    - **Aucun site**: les rubriques ne seront pas générées ou mises à jour automatiquement avec SharePoint contenu. Les rubriques existantes restent dans le centre de rubriques.

    ![Capture d’écran SharePoint’interface utilisateur des sources de rubriques.](../media/k-manage-select-topic-source.png)
   
3. Cliquez sur **Enregistrer**.

## <a name="exclude-topics-by-name"></a>Exclure les rubriques par nom

Vous pouvez exclure des rubriques de la découverte en téléchargeant une liste à l'aide d'un fichier .csv. Si vous avez précédemment exclu des sujets, vous pouvez télécharger le fichier .csv, apporter des modifications , puis le télécharger à nouveau.

1. Sous l’onglet **Découverte de rubrique**, sous **Exclure les rubriques**, sélectionnez **Modifier**.
2. Cliquez **sur Exclure des rubriques par nom.**
3. Si vous avez besoin de créer une liste, téléchargez le modèle .csv et ajoutez les rubriques que vous souhaitez exclure (voir Utiliser le modèle *.csv ci-dessous).* Lorsque le fichier est prêt, cliquez sur **Parcourir** et téléchargez le fichier. S’il existe une liste, vous pouvez télécharger le .csv contenant la liste.
4. Cliquez sur **Enregistrer**.

    ![Capture d’écran de l’interface utilisateur exclure des rubriques.](../media/km-manage-exclude-topics.png)

### <a name="working-with-the-csv-template"></a>Utiliser le modèle .csv modèle

Vous pouvez copier le modèle csv ci-dessous :

``` csv
Name (required),Expansion,MatchType- Exact/Partial (required)
```

Dans le modèle CSV, entrez les informations suivantes sur les rubriques à exclure :

- **Nom** : tapez le nom de la rubrique à exclure. Il existe deux méthodes pour y parvenir :
    - Correspondance exacte : vous pouvez exclure le nom exact ou l’acronyme (par exemple, *Contoso* ou *ATL*).
    - Correspondance partielle : vous pouvez exclure toutes les rubriques qui ont un mot spécifique.  Par exemple, *arc exclura* toutes les rubriques avec le mot *arc* dans celui-ci, telles que le cercle *d’arc,* *l’arc de Pierre ou* *l’arc de formation*. Notez qu’il n’exclura pas les rubriques dans lesquelles le texte est inclus dans le cadre d’un mot, comme *Architecture*.
- **Signifie (facultatif)**: si vous souhaitez exclure un acronyme, tapez les mots qu’il signifie.
- **MatchType-Exact/Partial**: tapez si le nom que vous avez entré était un type de correspondance *exact* *ou* partiel.

    ![Exclure des rubriques dans le modèle CSV.](../media/exclude-topics-csv.png) 

## <a name="see-also"></a>Voir aussi

[Gérer la visibilité des rubriques dans Microsoft 365](topic-experiences-knowledge-rules.md)

[Gérer les autorisations de rubrique dans Microsoft 365](topic-experiences-user-permissions.md)

[Modifier le nom du centre de rubriques dans Microsoft 365](topic-experiences-administration.md)
