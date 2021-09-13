---
title: Ajouter des dépositaires à un Advanced eDiscovery de données
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
description: Découvrez comment utiliser l’outil de gestion des dépositaires intégré dans Advanced eDiscovery pour coordonner vos flux de travail et identifier les sources de données pertinentes dans un cas.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 3c5adf4b51cbb9898b0b4f7bc806c1392453c526
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59206420"
---
# <a name="add-custodians-to-an-advanced-ediscovery-case"></a>Ajouter des dépositaires à un Advanced eDiscovery de données

Utilisez l’outil de gestion des dépositaires intégré dans Advanced eDiscovery pour coordonner vos flux de travail autour de la gestion des dépositaires et de l’identification des sources de données pertinentes et privatives associées à un cas. Lorsque vous ajoutez un dépositaire, le système peut automatiquement identifier et placer une conservation sur sa boîte aux lettres Exchange et son OneDrive Entreprise compte. Au cours du processus de découverte de votre enquête, vous pouvez également identifier d’autres sources de données (telles que des boîtes aux lettres, des sites ou des Teams) qu’un dépositaire a accédées ou à qui il a contribué. Dans ce cas, vous pouvez utiliser l’outil de gestion des dépositaires pour associer ces sources de données à un dépositaire spécifique. Après avoir ajouté des dépositaires à un cas et associé une autre source de données à celui-ci, vous pouvez rapidement conserver les données et rechercher les données de conservation.

Vous pouvez ajouter et gérer des dépositaires dans Advanced eDiscovery cas en quatre étapes :

1. Identifiez les dépositaires.

2. Choisissez les emplacements de données des dépositaires.

3. Configurez les paramètres de mise en attente.

4. Examinez les dépositaires et terminez le processus.

   [![Onglet Sources dans Advanced eDiscovery cas. ](../media/AeD-Sources-Tab.png)](../media/AeD-Sources-Tab.png#lightbox)

## <a name="make-sure-you-have-the-necessary-permissions"></a>Assurez-vous que vous avez les autorisations nécessaires

Pour ajouter des dépositaires à un cas, vous devez être membre du groupe de rôles Gestionnaire eDiscovery. Vous disposez ainsi des autorisations nécessaires pour ajouter des dépositaires à un cas et placer une conservation sur les sources de données autorisées. Pour plus d'informations, voir [Attribution d'autorisations eDiscovery](get-started-with-advanced-ediscovery.md#step-2-assign-ediscovery-permissions).

## <a name="step-1-identify-custodians"></a>Étape 1 : Identifier les dépositaires

1. Go to [https://compliance.microsoft.com](https://compliance.microsoft.com) and sign in with a user account that has been assigned the appropriate eDiscovery permissions.

2. Dans le volet de navigation gauche du centre de conformité Microsoft 365, cliquez sur **Tout afficher**, puis cliquez sur **eDiscovery >avancée**.

3. Dans la page **Advanced eDiscovery,** cliquez sur l’onglet **Cas,** puis sélectionnez le cas à ajouter aux dépositaires.

4. Cliquez sur **l’onglet Sources** de données, puis sur **Ajouter** une source de données Ajouter de  >  **nouveaux dépositaires.**

5. Ajoutez un ou plusieurs utilisateurs de votre organisation en tant que dépositaires au cas en tapant la première partie du nom ou de l’alias d’une personne. Une fois que vous avez trouvé la personne correcte, sélectionnez son nom pour l’ajouter à la liste.

## <a name="step-2-choose-custodian-data-locations"></a>Étape 2 : Choisir les emplacements de données des dépositaires

Une fois que vous avez sélectionné des dépositaires, le système tente automatiquement d’identifier et de vérifier ces utilisateurs et leurs sources de données. Après avoir ajouté des dépositaires à la liste, l’outil inclut automatiquement la boîte aux lettres principale et le OneDrive pour chaque dépositaire. Vous pouvez choisir de ne pas inclure ces sources de données lors de l’ajout de dépositaires au cas.

Outre la boîte aux lettres et le compte OneDrive d’un dépositaire, vous pouvez également associer d’autres emplacements de données à un dépositaire, tel qu’un site SharePoint ou une équipe Microsoft dont le dépositaire est membre. Cela vous permet de conserver, de collecter, d’analyser et de réviser le contenu dans d’autres sources de données associées aux dépositaires du cas.

Pour désélectionner la boîte aux lettres principale et OneDrive compte d’un dépositaire :

1. Développez le dépositaire pour afficher les emplacements de données principaux qui ont été automatiquement associés à chaque dépositaire.

2. Sélectionnez **Effacer** en  OneDrive boîte aux lettres ou en OneDrive pour supprimer la boîte aux lettres ou le compte OneDrive d’un dépositaire d’être associé en tant qu’emplacement de données pour ce dépositaire. 

   ![Configurez les emplacements à associer à un dépositaire.](../media/ConfigureCustodianLocations.png)

Pour associer d’autres boîtes aux lettres, sites, Teams ou groupes Yammer à un dépositaire spécifique :

1. Développez un dépositaire pour afficher les services suivants afin d’associer des emplacements de données au dépositaire. Cliquez **sur Modifier** en côté d’un service pour ajouter un emplacement de données.

   - **Exchange**: utilisez cette approche pour associer d’autres boîtes aux lettres au dépositaire. Tapez dans la zone de recherche le nom ou l’alias (au minimum trois caractères) des boîtes aux lettres utilisateur ou des groupes de distribution. Sélectionnez les boîtes aux lettres à affecter au dépositaire, puis cliquez sur **Ajouter.**

   - **SharePoint**: utilisez cette valeur pour associer SharePoint sites au dépositaire. Sélectionnez un site dans la liste ou recherchez un site en tapant une URL dans la zone de recherche. Sélectionnez les sites à affecter au dépositaire, puis cliquez sur **Ajouter.**

   - **Teams**: utilisez cette valeur pour affecter Microsoft Teams le dépositaire est actuellement membre. Sélectionnez les équipes à affecter au dépositaire, puis cliquez sur **Ajouter.** Après avoir ajouté une équipe, le système identifie et localise automatiquement le site SharePoint et la boîte aux lettres de groupe associés à cette équipe et les affecte au dépositaire.

   - **Yammer**: utilisez cette valeur pour affecter les groupes Yammer dont le dépositaire est actuellement membre. Sélectionnez les groupes à affecter au dépositaire, puis cliquez sur **Ajouter.** Après avoir ajouté une équipe, le système identifie et localise automatiquement le site SharePoint et la boîte aux lettres de groupe associés à ce groupe et les affecte au dépositaire.

   > [!NOTE]
   > Vous pouvez utiliser les s sélectionneurs d’emplacement **Exchange** et **SharePoint** pour associer d’autres équipes ou groupes Yammer (dont un dépositaire n’est pas membre) à un dépositaire. Pour ce faire, vous devez ajouter la boîte aux lettres et le site associés à chaque équipe Yammer groupe.

2. Vous pouvez afficher le nombre total de boîtes aux lettres, sites, Teams et groupes Yammer affectés à chaque dépositaire en développez chaque dépositaire dans la table. Une fois que vous avez finalisé les emplacements de données affectés pour chaque dépositaire, ces associations sont conservées et utilisées pendant les étapes de collecte, de traitement et de révision du flux de travail Advanced eDiscovery.

3. Après avoir ajouté des dépositaires et  configuré leurs emplacements de données, cliquez sur Suivant pour aller à la page **paramètres de conservation.**  

## <a name="step-3-configure-hold-settings"></a>Étape 3 : Configurer les paramètres de mise en attente

 Une fois que vous avez finalisé les dépositaires et leurs emplacements de données, vous pouvez placer tout ou partie des dépositaires en conservation. Lorsque vous placez un dépositaire en conservation, tout le contenu de tous les emplacements de contenu associés au dépositaire est conservé jusqu’à ce que vous en ôtiez ou ôtiez la conservation. Dans certains cas, vous pouvez ajouter des dépositaires à un cas sans les placer en conservation.

Pour placer les dépositaires et les sources de données en conservation :

1. Dans la page **Paramètres de** la conservation, vous pouvez appliquer une conservation à des dépositaires individuels en selectant la case à cocher sous la colonne **Conservation.**

   Vous pouvez également placer tous les dépositaires  en conservation en cocher la case De conservation en haut de la colonne.

2. Vérifiez les sélections de conservation du dépositaire, puis cliquez sur **Suivant.**

   > [!NOTE]
   > Si vous ne placez pas de conservation sur un dépositaire, le dépositaire et ses sources de données associées seront ajoutés au cas, mais le contenu de ces sources de données ne sera pas conservé par la conservation associée au cas.

## <a name="step-4-review-the-custodians-and-complete-the-process"></a>Étape 4 : Passer en revue les dépositaires et terminer le processus

Avant d’ajouter réellement les dépositaires au cas, vous pouvez passer en revue la liste des dépositaires, les emplacements de données qui leur sont affectés et les paramètres de conservation.

1. Vérifiez et examinez tous les nombres de sources de données et le paramètre de conservation associé à chaque dépositaire de la table. Si nécessaire, revenir  aux pages de **paramètres** de conservation ou de dépositaire d’identification pour apporter des modifications.

2. Cliquez **sur Envoyer** pour ajouter des dépositaires et leurs emplacements de données au cas et appliquez tous les paramètres de conservation.

   Les nouveaux dépositaires sont ajoutés au cas et affichés sous l’onglet **Sources de** données.

   [![Dépositaires répertoriés sous l’onglet Sources de données. ](../media/DataSourcesTab.png)](../media/DataSourcesTab.png#lightbox)
