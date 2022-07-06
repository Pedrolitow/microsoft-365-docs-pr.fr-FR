---
title: Ajouter des consignats à un cas eDiscovery (Premium)
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
description: Découvrez comment utiliser l’outil de gestion des consignats intégré dans Microsoft Purview eDiscovery (Premium) pour coordonner vos flux de travail et identifier les sources de données pertinentes dans un cas.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 4e7734e886651cb0169d5823a23790761791eb4e
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66640983"
---
# <a name="add-custodians-to-an-ediscovery-premium-case"></a>Ajouter des consignats à un cas eDiscovery (Premium)

Utilisez l’outil de gestion des consignats intégré dans Microsoft Purview eDiscovery (Premium) pour coordonner vos flux de travail autour de la gestion des consignatateurs et de l’identification des sources de données de garde pertinentes associées à un cas. Lorsque vous ajoutez un consignateur, le système peut automatiquement identifier et placer une conservation sur sa boîte aux lettres Exchange et son compte OneDrive Entreprise. Pendant le processus de découverte de votre enquête, vous pouvez également identifier d’autres sources de données (telles que des boîtes aux lettres, des sites ou des équipes) auxquelles un consignateur a accédé ou y a contribué. Dans ce cas, vous pouvez utiliser l’outil de gestion des consignats pour associer ces sources de données à un dépositaire spécifique. Après avoir ajouté des consignataires à un cas et associé à une autre source de données, vous pouvez rapidement conserver les données et rechercher les données de garde.

Vous pouvez ajouter et gérer des consignatateurs dans les cas eDiscovery (Premium) en quatre étapes :

1. Identifiez les consignatateurs.

2. Choisissez les emplacements de données des consignatateurs.

3. Configurez les paramètres de conservation.

4. Passez en revue les consignatateurs et terminez le processus.

## <a name="make-sure-you-have-the-necessary-permissions"></a>Vérifiez que vous disposez des autorisations nécessaires

Pour ajouter des consignatateurs à un cas, vous devez être membre du groupe de rôles gestionnaire eDiscovery. Vous disposez ainsi des autorisations nécessaires pour ajouter des consignatateurs à un cas et placer une conservation sur les sources de données de garde. Pour plus d'informations, voir [Attribution d'autorisations eDiscovery](get-started-with-advanced-ediscovery.md#step-2-assign-ediscovery-permissions).

## <a name="step-1-identify-custodians"></a>Étape 1 : Identifier les consignatateurs

1. Accédez à [https://compliance.microsoft.com](https://compliance.microsoft.com) et connectez-vous avec un compte d’utilisateur qui a reçu les autorisations eDiscovery appropriées.

2. Dans le volet de navigation gauche du portail de conformité Microsoft Purview, sélectionnez **eDiscovery****eDiscovery** >  (Premium) et l’onglet [**Cas**](https://go.microsoft.com/fwlink/p/?linkid=2173764).

3. Sélectionnez le cas auquel vous souhaitez ajouter des consignatateurs.

4. Sélectionnez l’onglet **Sources** de données, puis **Ajouter une source de** >  données **Ajouter de nouveaux consignatateurs**.

5. Ajoutez un ou plusieurs utilisateurs de votre organisation en tant que gardiens au cas en tapant la première partie du nom ou de l’alias d’une personne. Les utilisateurs actifs et inactifs sont recherchés. Une fois que vous avez trouvé la personne appropriée, sélectionnez son nom pour l’ajouter à la liste. 

## <a name="step-2-choose-custodian-data-locations"></a>Étape 2 : Choisir les emplacements des données des consignatateurs

Une fois que vous avez sélectionné les consignatateurs, le système tente automatiquement d’identifier et de vérifier ces utilisateurs et leurs sources de données. Après avoir ajouté des consignats à la liste, l’outil inclut automatiquement la boîte aux lettres principale et le compte OneDrive pour chaque utilisateur actif qui a été ajouté en tant que consignateur. Si l’utilisateur est inactif, l’outil identifie uniquement la boîte aux lettres principale. Vous pouvez choisir de ne pas inclure ces sources de données lors de l’ajout de consignatateurs au cas.

En plus de la boîte aux lettres d’un consignateur et du compte OneDrive, vous pouvez également associer d’autres emplacements de données à un consignaateur, tel qu’un site SharePoint ou une équipe Microsoft dont le gardien est membre. Cela vous permet de conserver, collecter, analyser et examiner le contenu dans d’autres sources de données associées aux consignataires du cas.

Pour désélectionner la boîte aux lettres principale et le compte OneDrive d’un consignateur :

1. Développez le consignat pour afficher les emplacements de données principaux qui ont été automatiquement associés à chaque consignateur.

2. Sélectionnez **Effacer** en regard de boîte **aux lettres** ou **OneDrive** pour supprimer l’association de la boîte aux lettres ou du compte OneDrive d’un consignateur en tant qu’emplacement de données pour ce consignateur.

   ![Configurez des emplacements à associer à un consignateur.](../media/ConfigureCustodianLocations.png)

Pour associer d’autres boîtes aux lettres, sites, équipes ou groupes Yammer à un consignaateur spécifique :

1. Développez un dépositaire pour afficher les services suivants afin d’associer des emplacements de données au consignatateur. Cliquez sur **Modifier** en regard d’un service pour ajouter un emplacement de données.

   - **Exchange** : permet d’associer d’autres boîtes aux lettres au consignateur. Tapez dans la zone de recherche le nom ou l’alias (au moins trois caractères) des boîtes aux lettres utilisateur ou des groupes de distribution. Sélectionnez les boîtes aux lettres à affecter au consignateur, puis cliquez sur **Ajouter**.

   - **SharePoint** : permet d’associer des sites SharePoint au consignaateur. Sélectionnez un site dans la liste ou recherchez un site en tapant une URL dans la zone de recherche. Sélectionnez les sites à affecter au consignateur, puis cliquez sur **Ajouter**. Si un utilisateur est inactif, son site OneDrive doit être ajouté en tant qu’emplacement SharePoint supplémentaire ici. 

   - **Teams** : permet d’affecter à Microsoft Teams dont le gardien est actuellement membre. Sélectionnez les équipes à affecter au consignateur, puis cliquez sur **Ajouter**. Une fois que vous avez ajouté une équipe, le système identifie et localise automatiquement le site SharePoint et la boîte aux lettres de groupe associé à cette équipe et les affecte au consignateur.

   - **Yammer** : permet d’affecter les groupes Yammer dont le consignateur est actuellement membre. Sélectionnez les groupes à affecter au consignateur, puis cliquez sur **Ajouter**. Une fois que vous avez ajouté une équipe, le système identifie et localise automatiquement le site SharePoint et la boîte aux lettres de groupe associés à ce groupe, puis les affecte au consignateur.

   > [!NOTE]
   > Vous pouvez utiliser les sélecteurs d’emplacement **Exchange** et **SharePoint** pour associer n’importe quelle boîte aux lettres ou site de votre organisation à un consignateur. , cela inclut l’association de la boîte aux lettres et du site pour une équipe Microsoft ou un groupe Yammer dont un gardien n’est pas membre. Pour ce faire, vous devez ajouter la boîte aux lettres et le site associés à chaque équipe ou groupe Yammer.

2. Vous pouvez afficher le nombre total de boîtes aux lettres, de sites, de teams et de groupes Yammer affectés à chaque gardien en développant chaque consignateur dans la table. Une fois que vous avez finalisé les emplacements de données affectés pour chaque dépositaire, ces associations sont conservées et utilisées pendant les étapes de collecte, de traitement et de révision du flux de travail eDiscovery (Premium).

3. Après avoir ajouté des consignats et configuré leurs emplacements de données, cliquez sur **Suivant** pour accéder à la page **Paramètres de** conservation.  

## <a name="step-3-configure-hold-settings"></a>Étape 3 : Configurer les paramètres de conservation

 Une fois que vous avez finalisé les consignats et leurs emplacements de données, vous pouvez mettre en attente une partie ou la totalité des consignatateurs. Lorsque vous mettez un consigna ateur en attente, tout le contenu dans tous les emplacements de contenu associés au consignateur est conservé jusqu’à ce que vous supprimiez la conservation ou libériez le consignatien de la conservation. Dans certains cas, vous souhaiterez peut-être ajouter des consignatateurs à un cas sans les mettre en attente.

Pour mettre les consignatateurs et les sources de données en attente :

1. Dans la page **Paramètres** de conservation, vous pouvez appliquer une conservation à des consignats individuels en cochant la case sous la colonne **De** suspension.

   Vous pouvez également mettre tous les consignats en attente en cochant la case **De** suspension en haut de la colonne.

2. Vérifiez les sélections de conservation du consignateur, puis cliquez sur **Suivant**.

   > [!NOTE]
   > Si vous ne placez pas de conservation sur un consignateur, le consignatateur et ses sources de données associées seront ajoutés au cas, mais le contenu de ces sources de données ne sera pas conservé par la conservation associée au cas.

## <a name="step-4-review-the-custodians-and-complete-the-process"></a>Étape 4 : Examiner les consignatateurs et terminer le processus

Avant d’ajouter réellement les consignats au cas, vous pouvez passer en revue la liste des consignatateurs, les emplacements de données qui leur sont affectés et les paramètres de conservation.

1. Vérifiez et examinez le nombre de sources de données et le paramètre de conservation associé à chaque consignateur dans la table. Si nécessaire, revenez aux pages Identifier les **paramètres** de **conservation ou de conservation** pour apporter des modifications.

2. Cliquez sur **Envoyer** pour ajouter des consignatateurs et leurs emplacements de données au cas et appliquer tous les paramètres de conservation.

   Les nouveaux consignats sont ajoutés à la casse et affichés sous l’onglet **Sources de données** .

   [![Consignats répertoriés sous l’onglet Sources de données.](../media/DataSourcesTab.png) ](../media/DataSourcesTab.png#lightbox)
