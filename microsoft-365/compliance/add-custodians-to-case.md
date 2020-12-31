---
title: Ajouter des dépositaires à un cas avancé eDiscovery
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
ms.openlocfilehash: 9468fb889e9115b3652d1dba8a6c6632bb367fe3
ms.sourcegitcommit: 36d12e02f6fda199ae7f2fb72fe52d7e2b5b4efd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/31/2020
ms.locfileid: "49740341"
---
# <a name="add-custodians-to-an-advanced-ediscovery-case"></a>Ajouter des dépositaires à un cas avancé eDiscovery

Utilisez l’outil de gestion des dépositaires intégré dans Advanced eDiscovery pour coordonner vos flux de travail concernant la gestion des dépositaires et l’identification des sources de données appropriées et privatives de ressources associées à un cas. Lorsque vous ajoutez un dépositaire, le système peut automatiquement identifier et placer un blocage sur sa boîte aux lettres Exchange et sur son compte OneDrive entreprise. Lors du processus de découverte de votre enquête, vous pouvez également identifier d’autres sources de données (par exemple, des boîtes aux lettres, des sites ou des équipes) auxquelles un dépositaire a accédé ou auquel il a contribué. Dans ce cas, vous pouvez utiliser l’outil de gestion des dépositaires pour associer ces sources de données à un dépositaire spécifique. Après avoir ajouté des dépositaires à un cas et associé à d’autres sources de données, vous pouvez conserver rapidement les données et rechercher les données privatives de temps.

Vous pouvez ajouter et gérer des dépositaires dans les cas de découverte électronique avancée en quatre étapes :

1. Identifier les dépositaires.

2. Choisissez emplacements de données des dépositaires.

3. Configurez les paramètres de conservation.

4. Passez en revue les dépositaires et terminez le processus.

   [![Onglet sources dans le cas ](../media/AeD-Sources-Tab.png) de eDiscovery avancé](../media/AeD-Sources-Tab.png#lightbox)

## <a name="make-sure-you-have-the-necessary-permissions"></a>Vérifiez que vous disposez des autorisations nécessaires

Pour ajouter des dépositaires à un cas, vous devez être membre du groupe de rôles gestionnaire de découverte électronique. Vous disposez ainsi des autorisations nécessaires pour ajouter des dépositaires à un cas et mettre en place une conservation sur les sources de données privatives de Troie. Pour plus d'informations, voir [Attribution d'autorisations eDiscovery](get-started-with-advanced-ediscovery.md#step-2-assign-ediscovery-permissions).

## <a name="step-1-identify-custodians"></a>Étape 1 : identifier les dépositaires

1. Accédez à [https://compliance.microsoft.com](https://compliance.microsoft.com) et connectez-vous à l’aide d’un compte d’utilisateur disposant des autorisations eDiscovery appropriées.

2. Dans le volet de navigation gauche du centre de conformité Microsoft 365, cliquez sur **Tout afficher**, puis cliquez sur **eDiscovery >avancée**.

3. Sur la page **Advanced eDiscovery** , cliquez sur l’onglet **incidents** , puis sélectionnez l’incident auquel vous souhaitez ajouter des dépositaires.

4. Cliquez sur l’onglet **sources de données** , puis cliquez sur Ajouter une **source de données** pour  >  **ajouter de nouveaux dépositaires**.

5. Ajoutez un ou plusieurs utilisateurs de votre organisation en tant que dépositaires à la casse en tapant la première partie du nom ou de l’alias de la personne. Une fois que vous avez trouvé la personne appropriée, sélectionnez son nom pour l’ajouter à la liste.

## <a name="step-2-choose-custodian-data-locations"></a>Étape 2 : choisir les emplacements de données des dépositaires

Une fois que vous avez sélectionné les dépositaires, le système tente automatiquement d’identifier et de vérifier ces utilisateurs et leurs sources de données. Une fois que vous avez ajouté des dépositaires à la liste, l’outil inclut automatiquement la boîte aux lettres principale et le compte OneDrive pour chaque dépositaire. Vous pouvez choisir de ne pas inclure ces sources de données lorsque vous ajoutez des dépositaires à la demande de devis.

En plus de la boîte aux lettres et du compte OneDrive d’un dépositaire, vous pouvez également associer d’autres emplacements de données à un dépositaire, tel qu’un site SharePoint ou une équipe Microsoft dont le dépositaire est membre. Cela vous permet de conserver, de collecter, d’analyser et d’examiner le contenu d’autres sources de données associées aux dépositaires du cas.

Pour désélectionner la boîte aux lettres principale et le compte OneDrive d’un dépositaire, procédez comme suit :

1. Développez le dépositaire pour afficher les emplacements de données principaux qui ont été automatiquement associés à chaque dépositaire.

2. Sélectionnez **Effacer** en regard de **boîte aux lettres** ou **onedrive** pour supprimer la boîte aux lettres ou le compte onedrive d’un dépositaire en tant qu’emplacement de données pour ce dépositaire.

   ![Configurer les emplacements à associer à un dépositaire](../media/ConfigureCustodianLocations.png)

Pour associer d’autres boîtes aux lettres, sites, équipes ou groupes Yammer à un dépositaire spécifique :

1. Développez un dépositaire pour afficher les services suivants afin d’associer des emplacements de données au dépositaire. Cliquez sur **modifier** en regard d’un service pour ajouter un emplacement de données.

   - **Exchange**: utilisez pour associer d’autres boîtes aux lettres au dépositaire. Tapez dans la zone de recherche le nom ou l’alias (un minimum de trois caractères) des boîtes aux lettres utilisateur ou des groupes de distribution. Sélectionnez les boîtes aux lettres à affecter au dépositaire, puis cliquez sur **Ajouter**.

   - **SharePoint**: utilisez pour associer des sites SharePoint au dépositaire. Sélectionnez un site dans la liste ou recherchez un site en tapant une URL dans la zone de recherche. Sélectionnez les sites à affecter au dépositaire, puis cliquez sur **Ajouter**.

   - **Teams**: utilisez pour affecter Microsoft teams dont le dépositaire est actuellement membre. Sélectionnez les équipes à affecter au dépositaire, puis cliquez sur **Ajouter**. Une fois que vous avez ajouté une équipe, le système identifie et localise automatiquement le site SharePoint et la boîte aux lettres de groupe associés à cette équipe et les affecte au dépositaire.

   - **Yammer**: utilisez pour attribuer les groupes Yammer dont le dépositaire est actuellement membre. Sélectionnez les groupes à affecter au dépositaire, puis cliquez sur **Ajouter**. Une fois que vous avez ajouté une équipe, le système identifie et localise automatiquement le site SharePoint et la boîte aux lettres de groupe associés à ce groupe et les affecte au dépositaire.

   > [!NOTE]
   > Vous pouvez utiliser les sélecteurs d’emplacement **Exchange** et **SharePoint** pour associer d’autres équipes ou groupes Yammer (dont un dépositaire n’est pas membre) à un dépositaire. Pour ce faire, vous devez ajouter la boîte aux lettres et le site associés à chaque équipe ou groupe Yammer.

2. Vous pouvez afficher le nombre total de boîtes aux lettres, de sites, d’équipes et de groupes Yammer attribués à chaque dépositaire en développant chaque dépositaire dans le tableau. Une fois que vous avez finalisé les emplacements de données affectés pour chaque dépositaire, ces associations seront conservées et utilisées pendant les étapes de collecte, de traitement et de révision dans le flux de travail eDiscovery avancé.

3. Après avoir ajouté des dépositaires et configuré leurs emplacements de données, cliquez sur **suivant** pour accéder à la page **paramètres de suspension** .  

## <a name="step-3-configure-hold-settings"></a>Étape 3 : configurer les paramètres de conservation

 Une fois que vous avez finalisé les dépositaires et leurs emplacements de données, vous pouvez placer tout ou partie des dépositaires en attente. Lorsque vous mettez un dépositaire en conservation, tout le contenu de tous les emplacements de contenu associés au dépositaire est conservé jusqu’à ce que vous supprimiez le blocage ou que le dépositaire soit libéré de la suspension. Dans certains cas, vous souhaiterez peut-être ajouter des dépositaires à un cas sans les mettre en attente.

Pour placer les dépositaires et les sources de données en conservation :

1. Sur la page **conserver les paramètres** , vous pouvez appliquer une suspension à des dépositaires individuels en activant la case à cocher située sous la colonne **conservation** .

   Vous pouvez également placer tous les dépositaires en conservation en activant la case à cocher en **attente** en haut de la colonne.

2. Vérifiez que le dépositaire contient des sélections, puis cliquez sur **suivant**.

   > [!NOTE]
   > Si vous ne placez pas de conservation sur un dépositaire, le dépositaire et les sources de données associées seront ajoutés à la casse, mais le contenu de ces sources de données n’est pas conservé par le blocage associé au cas.

## <a name="step-4-review-the-custodians-and-complete-the-process"></a>Étape 4 : passez en revue les dépositaires et terminez le processus

Avant d’ajouter les dépositaires à l’incident, vous pouvez passer en revue la liste des dépositaires, les emplacements de données qui leur sont affectés et les paramètres de conservation.

1. Vérifiez et examinez le nombre de sources de données et le paramètre de blocage associé à chaque dépositaire de la table. Si nécessaire, revenez à la page **identifier le dépositaire** ou conserver les **paramètres** pour effectuer les modifications.

2. Cliquez sur **Envoyer** pour ajouter des dépositaires et leurs emplacements de données à l’incident et appliquer tous les paramètres de conservation des privatives de ressources.

   Les nouveaux dépositaires sont ajoutés à l’incident et s’affichent sous l’onglet **sources de données** .

   [![Dépositaires affichés sous l’onglet ](../media/DataSourcesTab.png) sources de données](../media/DataSourcesTab.png#lightbox)
