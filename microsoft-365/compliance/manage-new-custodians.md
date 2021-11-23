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
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: Découvrez comment afficher les détails, modifier et modifier en bloc la liste des dépositaires dans Advanced eDiscovery cas.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 794677c8675f044bafb1c9a441e6c2bbee3e1c86
ms.sourcegitcommit: b19e54b3888a0b07d08dbd23172daec303c7c95b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2021
ms.locfileid: "61152417"
---
# <a name="manage-custodians-in-an-advanced-ediscovery-case"></a>Gérer les dépositaires dans un Advanced eDiscovery de gestion

La page **Des dépositaires** sous l’onglet **Sources** de données dans un cas Advanced eDiscovery contient la liste de tous les dépositaires qui ont été ajoutés au cas. Une fois que vous avez ajouté des dépositaires à un cas, les détails sur chaque dépositaire sont collectés automatiquement à partir de Azure Active Directory et sont consultables dans Advanced eDiscovery.

## <a name="view-custodian-details"></a>Afficher les détails du dépositaire

Pour afficher les détails sur un dépositaire, cliquez sur le dépositaire dans la liste sous **l’onglet Dépositaires.** Une page volante s’affiche et contient les informations suivantes sur le dépositaire.

![Détails du dépositaire.](../media/CustodianDetails.PNG)

- Informations de contact

  - **Titre** Fonction du dépositaire.
  
  - **Nom d’utilisateur principal**. Nom d’utilisateur principal (UPN) du dépositaire, par exemple, AdeleV@contoso.onmicrosoft.com.
  
  - **Emplacement :** L’emplacement du bureau dans le lieu de travail du dépositaire.
  
  - **Responsable**. Responsable du dépositaire. Le responsable désigné recevra toutes les communications d’escalade pour ce dépositaire.
  
  - **Service**. Nom du service dans lequel travaille le dépositaire.

- Informations de cas

  - **État**. État du dépositaire dans le cas. L’état **Actif** indique que le dépositaire fait partie du cas. Si un dépositaire est libéré d’un cas, l’état est modifié en **Released**.
  
  - **Hold**. Indique si le dépositaire a été mis en attente.

- Emplacements de données et informations de la conserver

  ![Emplacements de données des dépositaires et informations de conservation.](../media/CustodianHoldDetails.PNG)

  - **Emplacements de garde**. Indique le nombre et le type de sources de données (boîtes aux lettres, sites et Teams) qui sont associées au dépositaire et qui font partie du cas.

    - Chaque emplacement de données affiche son état de mise en attente. Valeurs possibles pour l’état de la attente : **En attente,** Non **en attente** et **En cours**.

    - Si vous ne voyez pas d’état de conservation pour une source de données,  vérifiez l’état de la conservation du dépositaire répertorié dans l’onglet Conservation pour le cas. La conservation du dépositaire identifie les sources de données spécifiques qui sont en conservation.

## <a name="edit-a-custodian"></a>Modifier un dépositaire

Au fur et à mesure de l’avancement de votre cas, vous pouvez découvrir qu’il peut y avoir d’autres sources de données pertinentes pour un dépositaire spécifique et le cas. Dans d’autres scénarios, vous pouvez supprimer certaines sources de données qui ont été examinées et considérées comme non pertinentes.

Pour mettre à jour les sources de données associées à un dépositaire :

1. Go to **eDiscovery > Advanced eDiscovery** and open the case.
  
2. Cliquez sur **l’onglet Sources de** données.
  
3. Sélectionnez un dépositaire dans la liste, puis cliquez sur **Modifier** dans la page volante.

    ![Modifier les sources de données.](../media/EditCustodianDataSource.PNG)
  
4. Pour ajouter ou supprimer la boîte aux lettres principale et OneDrive compte du dépositaire :

    - Développez le dépositaire pour afficher les emplacements de données principaux qui ont été précédemment associés au dépositaire.

    - Cliquez **sur Modifier** en OneDrive boîte aux lettres ou en OneDrive pour ajouter la boîte aux lettres ou l’emplacement OneDrive du dépositaire.  

    - Sélectionnez **Effacer** en  OneDrive boîte aux lettres ou en OneDrive pour supprimer la boîte aux lettres ou le compte OneDrive du dépositaire d’être associé en tant qu’emplacement de données pour ce dépositaire. 

5. Pour ajouter ou supprimer d’autres boîtes aux lettres, sites, Teams ou groupes  Yammer à un dépositaire spécifique, cliquez sur Modifier à côté du service pour ajouter un emplacement de données.

   - **Exchange**: utiliser pour associer d’autres boîtes aux lettres au dépositaire. Tapez dans la zone de recherche le nom ou l’alias (au moins trois caractères) des boîtes aux lettres utilisateur ou des groupes de distribution. Sélectionnez les boîtes aux lettres à affecter au dépositaire, puis cliquez sur **Ajouter.**

   - **SharePoint**: utilisez cette valeur pour associer SharePoint sites au dépositaire. Sélectionnez un site dans la liste ou recherchez un site en tapant une URL dans la zone de recherche. Sélectionnez les sites à affecter au dépositaire, puis cliquez sur **Ajouter.**

   - **Teams**: utilisez cette valeur pour affecter Microsoft Teams le dépositaire est actuellement membre. Sélectionnez les équipes à affecter au dépositaire, puis cliquez sur **Ajouter.** Après avoir ajouté une équipe, le système identifie et localise automatiquement le site SharePoint et la boîte aux lettres de groupe associés à cette équipe et les affecte au dépositaire.

   - **Yammer**: utilisez cette valeur pour affecter les groupes Yammer dont le dépositaire est actuellement membre. Sélectionnez les groupes à affecter au dépositaire, puis cliquez sur **Ajouter.** Après avoir ajouté une équipe, le système identifie et localise automatiquement le site SharePoint et la boîte aux lettres de groupe associés à ce groupe et les affecte au dépositaire.

   > [!NOTE]
   > Vous pouvez utiliser les s pickeurs d’emplacement **Exchange** et **SharePoint** pour associer une boîte aux lettres ou un site de votre organisation, y compris des équipes ou des groupes Yammer dont un dépositaire n’est pas membre, à un dépositaire. Pour ce faire, vous devez ajouter la boîte aux lettres et le site associés à chaque équipe Yammer groupe.

6. Après avoir modifié les emplacements de données pour le dépositaire, cliquez sur **Suivant** pour aller à la page **paramètres de conservation.**  

7. Dans la page **Paramètres de conservation,** mettez à jour les paramètres de conservation pour le dépositaire.

## <a name="reindex-custodian-data"></a>Réindexer les données des dépositaires

Dans la plupart des flux de travail eDiscovery pour les enquêtes juridiques, un sous-ensemble des données d’un dépositaire est recherché une fois que le dépositaire est ajouté à un dossier juridique. En raison de très grandes tailles de fichiers ou d’une altération possible des données, certains éléments des sources de données associées à un dépositaire peuvent être partiellement indexés. À l’aide de la fonctionnalité [d’indexation](indexing-custodian-data.md) avancée dans le Advanced eDiscovery, la plupart des éléments partiellement indexés peuvent être automatiquement corrigés en réindexant ces éléments à la demande.

Lorsqu’un dépositaire est ajouté à un cas, les données situées dans les sources de données associées au dépositaire sont réindexées automatiquement (par le processus d’indexation avancé). Cela signifie que vous pouvez laisser les données en place au lieu de les télécharger et de les corriger, puis de les rechercher hors connexion. Toutefois, pendant le cycle de vie d’un dossier juridique, de nouvelles sources de données peuvent être associées à un dépositaire. Dans ce cas, vous pouvez réindexer les données du dépositaire en réructuant le processus d’indexation avancé pour corriger les éléments partiellement indexés et mettre à jour l’index pour les données du dépositaire.

Pour déclencher le processus de réindexation afin de traiter les éléments partiellement indexés :

1. Go to **eDiscovery > Advanced eDiscovery** and open the case.

2. Cliquez sur **l’onglet Sources.**

3. Dans la page **Des dépositaires,** sélectionnez un dépositaire dont les données doivent être réindexées.

4. Dans la page volante, cliquez sur **Mettre à jour l’index**.

   Une boîte de dialogue s’affiche pour dire que le travail d’index a été créé.

La réindexation des données des dépositaires est un processus de longue durée . le travail correspondant créé est nommé **Re-indexation des données du dépositaire**. Vous pouvez suivre l’avancement sous l’onglet **Travaux** ou sous l’onglet **Dépositaires** en surveillant l’état dans la colonne État du travail **d’indexation.**

Pour plus d’informations, reportez-vous aux rubriques suivantes :

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

   Une page d’avertissement s’affiche, expliquant que si une conservation est placée sur une source de données associée au dépositaire, la conservation est supprimée et que toute autre conservation associée à un cas Advanced eDiscovery différent s’applique toujours. Cela inclut d’autres types de fonctionnalités de conservation et de rétention (telles qu’Microsoft 365 stratégie de rétention).

5. Cliquez **sur Oui** pour confirmer que vous souhaitez libérer le dépositaire. 

    L’état de cet utilisateur sous l’onglet **Dépositaires** est définie sur Publication et l’état de conservation sur la page volante est modifié sur **False**.  

> [!NOTE]
> Un dépositaire peut être impliqué simultanément dans plusieurs dossiers juridiques. Lorsqu’un dépositaire est libéré d’un cas spécifique, les conservations et les notifications dans d’autres cas ne sont pas impactées.
