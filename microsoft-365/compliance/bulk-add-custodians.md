---
title: Ajouter des dépositaires en bloc à un cas avancé de découverte électronique
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
ROBOTS: NOINDEX, NOFOLLOW
description: Utilisez l’outil Bulk-Add pour ajouter rapidement plusieurs dépositaires et leurs sources de données associées à un cas dans Advanced eDiscovery.
ms.openlocfilehash: 921d4a1616d97f2adde7e40baa5c73f607c849b6
ms.sourcegitcommit: 956dd3f87adb4e6173517550a662c3bacc2d2d79
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/16/2020
ms.locfileid: "44741644"
---
# <a name="bulk-add-custodians-to-an-advanced-ediscovery-case"></a>Ajouter des dépositaires en bloc à un cas avancé de découverte électronique

Pour les cas avancés de découverte électronique qui impliquent un grand nombre de dépositaires, vous pouvez importer plusieurs dépositaires à la fois par un fichier CSV qui contient toutes les informations nécessaires pour les ajouter à un cas.

## <a name="bulk-add-custodians"></a>Ajouter des dépositaires en bloc

1. Saisissez case et accédez à l’onglet **sources** .

2. Cliquez sur **importer des dépositaires** .

3. Sur la page de menu volant, cliquez sur **Télécharger un modèle vierge** pour télécharger un fichier de modèle de dépositaire CSV.

4. Ajoutez les informations privatives de Troie au fichier CSV et enregistrez-le sur votre ordinateur local. Pour plus d’informations sur les propriétés du fichier CSV, consultez la section suivante.

5. Sous l’onglet **sources** , cliquez de nouveau sur **importer des dépositaires** . 
6. Sur la page de menu volant, cliquez sur **Parcourir** et téléchargez votre fichier CSV.

   Une fois le fichier CSV téléchargé, un travail BulkAddCustodian est créé et affiché sous l’onglet **travaux** . Le travail valide les dépositaires et leurs sources de données correspondantes, puis les ajoute à l’onglet **dépositaires** de la page **sources** du cas.

## <a name="custodian-csv-file"></a>Fichier CSV de dépositaire

Après avoir téléchargé le modèle CSV, vous pouvez ajouter des dépositaires et leur source de données dans chaque ligne. Veillez à ne pas modifier les noms de colonne dans la ligne d’en-tête.

| Nom de colonne|Description|
|:------- |:------------------------------------------------------------|
|**Adresse dépositaire**     | Adresse de messagerie UPN du dépositaire. Exemple : sarad@onmicrosoft.contoso.com           |
|**Exchange activé** | Valeur TRUE/FALSe indiquant si la boîte aux lettres du dépositaire doit être ajoutée ou non.      |
|**OneDrive activé** | Valeur TRUE/FALSe indique s’il faut ajouter le compte OneDrive entreprise du dépositaire. |
|**Est OnHold**        | Valeur TRUE/FALSe indiquant si le dépositaire doit être placé en conservation.       |
|**Type Workload1**         | Valeur de chaîne indiquant le type de source de données à associer au dépositaire. <br />Les valeurs admises sont les suivantes : <br />ExchangeMailbox, SharePointSite, TeamsMailbox, TeamsSite, YammerMailbox, YammerSite |
|**Emplacement Workload1**     | En fonction de votre type de charge de travail, il s’agit de l’emplacement des données de votre charge de travail (par exemple, l’adresse de messagerie d’une boîte aux lettres Exchange ou l’URL d’un site SharePoint). |
|||

Voici un exemple de fichier CSV contenant des informations sur les dépositaires :  

| ContactEmail      | Exchange activé | OneDrive activé | Est OnHold | Type Workload1 | Emplacement Workload1             |
| ----------------- | ---------------- | ---------------- | --------- | -------------- | ------------------------------ |
|sarad@onmicrosoft.contoso.com | TRUE             | TRUE             | TRUE      | SharePointSite | https://contoso.sharepoint.com |
|pillarp@onmicrosoft.contoso.com | TRUE             | TRUE             | TRUE      | |  |
||||||

## <a name="custodian-and-data-source-validation"></a>Validation des dépositaires et des sources de données

Lorsque vous chargez le fichier CSV de dépositaire, Advanced eDiscovery effectue les opérations suivantes :

1. Valide les dépositaires et leurs sources de données. 

2. Indexe toutes les sources de données pour chaque dépositaire et les place en conservation (si la propriété is OnHold est définie sur TRUE).

### <a name="custodian-validation"></a>Validation des dépositaires

Actuellement, nous ne prenons en charge que les dépositaires d’importation dans Azure Active Directory (AAD).

Nous vérifions et trouvons des dépositaires à l’aide de la valeur UPN dans la colonne **adresse de messagerie du contact** dans le fichier CSV. Les dépositaires validés sont automatiquement ajoutés à l’incident et répertoriés sous l’onglet **dépositaire** de la page **sources** du cas. Si un dépositaire ne peut pas être validé, il est répertorié dans le journal des erreurs pour le travail BulkAddCustodian qui est répertorié sous l’onglet **travaux** dans le cas. Les dépositaires non validés ne sont pas ajoutés à l’incident.

### <a name="data-source-validation"></a>Validation de la source de données

Une fois les dépositaires validés et ajoutés au cas, chaque source de données associée à un dépositaire est validée. Si une source de données pour un dépositaire est introuvable, la valeur **non validée** s’affiche dans la colonne **validé** de l’onglet **dépositaire** .

### <a name="remediating-unvalidated-data-sources"></a>Correction de sources de données non validées

Pour corriger les dépositaires avec des sources de données non validées : 

1. Sous l’onglet **dépositaire** , sélectionnez un dépositaire qui n’est pas validé.

2. Sur la page de menu volant dépositaire, faites défiler jusqu’à la section **sources de données** pour afficher les sources de données associées au dépositaire. Les sources de données validées et non validées sont répertoriées.

3. Dans la section **sources de données** , cliquez sur **modifier**.

4. Sur la page **choisir les emplacements privatives d’adresses** , supprimez une source de données non validée.

5. Sur la page **Sélectionner des emplacements supplémentaires** , cliquez sur **mettre à jour** pour ajouter des sources de données supplémentaires pour un dépositaire.
