---
title: Gérer les dépositaires dans un Advanced eDiscovery de gestion
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: Découvrez comment afficher les détails, modifier et modifier en bloc la liste des dépositaires dans Advanced eDiscovery cas.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: daf74c2e51d9a01fad97534a4e49068528e820054b147c09baf8d3b3a8099d45
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53879316"
---
# <a name="manage-custodians-in-an-advanced-ediscovery-case"></a>Gérer les dépositaires dans un Advanced eDiscovery de gestion

La page Des dépositaires sous l’onglet **Sources** dans un cas Advanced eDiscovery contient la liste de tous les dépositaires qui ont été ajoutés au cas. Une fois que vous avez ajouté des dépositaires à un cas, les détails sur chaque dépositaire sont collectés automatiquement à partir de Azure Active Directory et sont consultables dans Advanced eDiscovery.

![Gérer les dépositaires](../media/CustodianDetails.PNG)

## <a name="view-custodian-details"></a>Afficher les détails du dépositaire

Pour afficher les détails sur un dépositaire, cliquez sur le dépositaire dans la liste sous **l’onglet Dépositaires.** Une page de présentation s’affiche et contient les informations suivantes sur le dépositaire :

- Informations de contact

  - **Nom complet** : nom affiché dans le carnet d’adresses du dépositaire. Il s’agit généralement de la combinaison du prénom, de l’initiale du deuxième prénom et du nom du dépositaire.
  
   - **Courrier/SMTP :** adresse SMTP principale du dépositaire, par exemple, brianj@contoso.onmicrosoft.com. Le nom d’utilisateur principal (UPN) du dépositaire est également répertorié.

  - **Titre** : fonction du dépositaire.

  - **Service** : nom du service dans lequel travaille le dépositaire.

  - **Responsable** : responsable du dépositaire. Le responsable désigné recevra toutes les communications d’escalade pour ce dépositaire.
  
- Informations d’emplacement

  - **Ville** - ville dans laquelle se trouve le dépositaire.

  - **État** : état ou province dans l’adresse du dépositaire.

  - **Pays/région** : pays/région où se trouve le dépositaire.

  - **Office** : emplacement du bureau du dépositaire.

- Informations de cas

  - **Statut de conservation** : indique si le dépositaire a été mis en attente. 

  - **État de** la communication : indique si le dépositaire a reçu un avis de conservation. Si le dépositaire a reçu un avis, cette valeur de cette propriété est **Publiée**. Si le dépositaire n’a pas reçu d’avis, l’état **est Non publié**. 

  - **État** : état du dépositaire dans le cas. L’état **Actif** indique que le dépositaire fait partie du cas. Si un dépositaire est libéré d’un cas, l’état est modifié en **Released**. 

- Sources de données et informations d’indexation

    - **Sources de** données : indique le nombre et le type de sources de données (boîtes aux lettres, sites et Teams) qui sont associées au dépositaire et qui font partie du cas.

    - **Heure de mise à jour** de l’index : indique l’heure et la date du dernier déclenchement de la tâche d’indexation avancée. Cette propriété indique également quand le processus d’indexation avancé est en cours.


## <a name="edit-a-custodian"></a>Modifier un dépositaire

Au fur et à mesure de la progression de votre cas, vous pouvez découvrir qu’il peut y avoir d’autres sources de données pertinentes pour un dépositaire spécifique & votre cas. Dans d’autres scénarios, vous pouvez supprimer certaines sources de données qui ont été examinées et considérées comme non pertinentes.

Pour mettre à jour les sources de données associées à un dépositaire :

1. Go to **eDiscovery > Advanced eDiscovery** and open the case.
  
2. Cliquez sur **l’onglet Sources.**
  
3. Dans la page **Des dépositaires,** sélectionnez un dépositaire dans la liste, puis cliquez sur **Modifier** dans la page de flyout.

    ![Modifier les sources de données](../media/EditCustodianDataSource.PNG)
  
4. Cliquez **sur l’onglet** Choisir les sources de données pour modifier les paramètres de la boîte aux lettres du Exchange et du compte OneDrive, cliquez sur Choisir les **sources de données.**
  
5. Cliquez sur **l’onglet** Sélectionner des sources de données supplémentaires pour ajouter ou supprimer des Teams, SharePoint ou Exchange boîtes aux lettres associées au dépositaire. 

    Pour plus d’informations sur les sources de données associées à un dépositaire, voir [Ajouter des dépositaires à un cas.](add-custodians-to-case.md) 
  
6. Cliquez **sur Placer les conservations** en conservation pour activer ou désactiver la conservation pour le dépositaire.

## <a name="re-index-custodian-data"></a>Ré-indexer les données des dépositaires

Dans la plupart des flux de travail eDiscovery pour les enquêtes juridiques, un sous-ensemble des données d’un dépositaire est recherché une fois que le dépositaire est ajouté à un dossier juridique. En raison de très grandes tailles de fichiers ou d’une altération possible des données, certains éléments des sources de données associées à un dépositaire peuvent être partiellement indexés. À l’aide de la fonctionnalité [d’indexation](indexing-custodian-data.md) avancée dans le Advanced eDiscovery, la plupart des éléments partiellement indexés peuvent être automatiquement corrigés en réindexant ces éléments à la demande.

Lorsqu’un dépositaire est ajouté à un cas, les données situées dans les sources de données associées au dépositaire sont automatiquement ré-indexées (par le processus d’indexation avancé). Cela signifie que vous pouvez laisser les données en place au lieu de les télécharger et de les corriger, puis de les rechercher hors connexion. Toutefois, pendant le cycle de vie d’un dossier juridique, de nouvelles sources de données peuvent être associées à un dépositaire. Dans ce cas, vous pouvez ré-indexer les données du dépositaire en ré-exécutant le processus d’indexation avancé pour corriger les éléments partiellement indexés et mettre à jour l’index des données du dépositaire.

Pour déclencher le processus de ré-indexation afin de traiter les éléments partiellement indexés :

1. Go to **eDiscovery > Advanced eDiscovery** and open the case.

2. Cliquez sur **l’onglet Sources.**

3. Dans la page **Des dépositaires,** sélectionnez un dépositaire dont les données doivent être réindexées.

4. Dans la page volante, cliquez sur **Mettre à jour l’index**.

   Une boîte de dialogue s’affiche pour dire que le travail d’index a été créé.

La ré-indexation des données des dépositaires est un processus de longue durée . le travail correspondant créé est nommé **Re-indexation des données du dépositaire**. Vous pouvez suivre l’avancement sous l’onglet **Travaux** ou sous l’onglet **Dépositaires** en surveillant l’état dans la colonne État du travail **d’indexation.**

Pour plus d’informations, voir :

- [Utiliser les erreurs de traitement](processing-data-for-case.md)

- [Gérer les tâches](managing-jobs-ediscovery20.md)

## <a name="release-a-custodian-from-a-case"></a>Libérer un dépositaire d’un cas

Un dépositaire est libéré lorsqu’un cas est fermé, qu’il n’est plus tenu de conserver le contenu d’un cas ou lorsque le dépositaire est considéré comme n’étant plus pertinent pour le cas. 

Si vous relâchez un dépositaire après la publication d’une notification de conservation, une notification de publication est envoyée au dépositaire. En outre, les conservations placées sur les sources de données associées au dépositaire sont supprimées. Si le dépositaire *a* été placé en conservation silencieuse, où il n’a reçu aucune notification de conservation légale, aucune notification de publication n’est envoyée, mais les conservations placées sur les sources de données associées à ce dépositaire sont supprimées.

Pour libérer un dépositaire : 

1. Go to **eDiscovery > Advanced eDiscovery** and open the case.

2. Cliquez sur **l’onglet Sources.**

3. Dans la page **Des dépositaires,** puis sélectionnez le dépositaire qui est libéré du cas.

4. Dans la page volante, cliquez sur **Libérer le dépositaire**.

   Une page d’avertissement s’affiche, expliquant que si une conservation est placée sur une source de données associée au dépositaire, la conservation sera supprimée et que toute autre conservation associée à un cas Advanced eDiscovery différent s’appliquera toujours. Cela inclut d’autres types de fonctionnalités de conservation et de rétention (telles qu’Microsoft 365 stratégie de rétention).

5. Cliquez **sur Oui** pour confirmer que vous souhaitez libérer le dépositaire. 

    L’état de cet utilisateur sous l’onglet **Dépositaires** est définie sur Publication et l’état de conservation sur la page volante est modifié sur **False**.   

> [!NOTE]
> Un dépositaire peut être impliqué simultanément dans plusieurs dossiers juridiques. Lorsqu’un dépositaire est libéré d’un cas, les conservations et les notifications sur d’autres questions ne sont pas impactées.

## <a name="bulk-edit-custodians"></a>Modification en bloc des dépositaires

Vous pouvez utiliser l’éditeur en bloc pour modifier plusieurs dépositaires en même temps. Pour ce faire, sélectionnez simplement deux dépositaires ou plus sous l’onglet **Dépositaires** pour afficher l’éditeur en bloc, puis cliquez sur l’une des tâches.

![Page volante pour modifier les paramètres de plusieurs dépositaires](../media/AeDBulkEditCustodians.png)
