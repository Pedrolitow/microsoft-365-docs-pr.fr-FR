---
title: Gestion de la découverte de rubrique dans Microsoft 365
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
ms.reviewer: nkokoye
audience: admin
ms.topic: article
ms.service: o365-administration
search.appverid: MET150
localization_priority: Normal
ROBOTS: NOINDEX, NOFOLLOW
description: Découvrez comment administrer la découverte de rubrique dans Microsoft 365.
ms.openlocfilehash: dec8aeef9dda390fb19f5067638c2ebea6b6a2fe
ms.sourcegitcommit: 884ac262443c50362d0c3ded961d36d6b15d8b73
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/16/2020
ms.locfileid: "49698542"
---
# <a name="manage-topic-discovery-in-microsoft-365"></a>Gestion de la découverte de rubrique dans Microsoft 365

Vous pouvez gérer les paramètres de découverte de rubrique dans le [Centre d’administration 365 de Microsoft](https://admin.microsoft.com). Vous devez être un administrateur général ou un administrateur SharePoint pour effectuer ces tâches.

## <a name="to-access-topics-management-settings"></a>Pour accéder aux paramètres de gestion des rubriques :

1. Dans le centre d’administration Microsoft 365, cliquez sur **paramètres**, puis sur paramètres de l' **organisation**.
2. Sous l’onglet **services** , cliquez sur le **réseau de connaissances**.

    ![Connecter des personnes aux connaissances](../media/admin-org-knowledge-options-completed.png) 

3. Sélectionnez l’onglet découverte de la **rubrique** . Consultez les sections suivantes pour obtenir des informations sur chaque paramètre.

    ![connaissances-réseau-paramètres](../media/knowledge-network-settings-topic-discovery.png) 

## <a name="select-sharepoint-topic-sources"></a>Sélectionner les sources des rubriques SharePoint

Vous pouvez modifier les sites SharePoint de votre organisation qui seront analysés pour rechercher des rubriques.

Si vous souhaitez inclure ou exclure une liste de sites spécifique, vous pouvez utiliser le modèle. csv suivant :

``` csv
Site name,URL
```

Si vous ajoutez des sites à l’aide du sélecteur de site, ils sont ajoutés à la liste de sites existante à inclure ou à exclure. Si vous téléchargez un fichier. csv, il remplace toutes les listes existantes. Si vous avez déjà inclus ou exclu des sites spécifiques, vous devez télécharger la liste en tant que fichier. csv, les modifier et télécharger la nouvelle liste.

Pour choisir les sites pour la découverte de rubrique

1. Sous l’onglet découverte de la **rubrique** , sous sélectionner les **sources des rubriques SharePoint**, sélectionnez **modifier**.
2. Sur la page **Sélectionner les sources des rubriques SharePoint** , sélectionnez les sites SharePoint qui seront analysés en tant que sources pour vos rubriques lors de la découverte. Cela inclut les opérations suivantes :
    - **Tous les sites**: tous les sites SharePoint de votre client. Ceci capture les sites actuels et futurs.
    - **Tout, à l’exception des sites sélectionnés**: saisissez les noms des sites à exclure.  Vous pouvez également télécharger une liste de sites que vous souhaitez exclure de la découverte. Les sites créés à l’avenir seront inclus en tant que sources pour la découverte de rubriques. 
    - **Sites sélectionnés uniquement**: saisissez les noms des sites que vous souhaitez inclure. Vous pouvez également télécharger une liste de sites. Les sites créés à l’avenir ne seront pas inclus en tant que sources pour la découverte des rubriques.
    - **Aucun site**: les rubriques ne seront pas générées ni mises à jour automatiquement avec le contenu SharePoint. Les rubriques existantes restent dans le centre de la rubrique.

    ![Capture d’écran de l’interface utilisateur des sources de rubrique SharePoint](../media/k-manage-select-topic-source.png)
   
3. Cliquez sur **Enregistrer**.

## <a name="exclude-topics-by-name"></a>Exclure les rubriques par nom

Vous pouvez exclure des rubriques de la découverte en téléchargeant une liste à l’aide d’un fichier. csv. Si vous avez déjà exclu des rubriques, vous pouvez télécharger le fichier. csv, le modifier et le charger à nouveau.

1. Sous l’onglet **découverte de rubrique** , sous exclure des **rubriques**, sélectionnez **modifier**.
2. Cliquez sur **exclure des rubriques par nom**.
3. Si vous devez créer une liste, téléchargez le modèle. csv et ajoutez les rubriques à exclure (voir *utilisation du modèle. csv* ci-dessous). Lorsque le fichier est prêt, cliquez sur **Parcourir** et téléchargez le fichier. S’il existe une liste existante, vous pouvez télécharger le fichier. csv contenant la liste.
4. Cliquez sur **Enregistrer**.

    ![Capture d’écran de l’interface utilisateur exclure des rubriques](../media/km-manage-exclude-topics.png)

### <a name="working-with-the-csv-template"></a>Utilisation du modèle. csv

Vous pouvez copier le modèle CSV ci-dessous :

``` csv
Name (required),Expansion,MatchType- Exact/Partial (required)
```

Dans le modèle CSV, entrez les informations suivantes sur les rubriques à exclure :

- **Nom**: tapez le nom de la rubrique à exclure. Vous pouvez procéder de deux manières :
    - Correspondance exacte : vous pouvez inclure le nom exact ou un acronyme (par exemple, *contoso* ou *ATL*).
    - Correspondance partielle : vous pouvez exclure toutes les rubriques qui contiennent un mot spécifique.  Par exemple, *arc* exclut toutes les rubriques contenant le mot *arc* , comme un *cercle arc*, un *soudage* à l’arc de plasma ou un *arc de formation*. Notez qu’il n’exclura pas les rubriques dans lesquelles le texte est inclus dans un mot, tel que *architecture*.
- **Abréviation de (facultatif)**: Si vous souhaitez exclure un acronyme, tapez les mots de l’acronyme.
- **MatchType-exacte/partielle**: spécifiez si le nom que vous avez entré est un type de correspondance *exacte* ou *partielle* .

    ![Exclure les rubriques du modèle CSV](../media/exclude-topics-csv.png) 

## <a name="see-also"></a>Voir aussi

[Gestion de la visibilité des rubriques dans Microsoft 365](topic-experiences-knowledge-rules.md)

[Gérer les autorisations de rubrique dans Microsoft 365](topic-experiences-user-permissions.md)

[Modifier le nom du centre de rubrique dans Microsoft 365](topic-experiences-administration.md)
