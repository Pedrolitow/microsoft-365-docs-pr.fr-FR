---
title: Importer des dépositaires dans un cas avancé eDiscovery
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
description: Utilisation de l’outil d’importation le DTO permet d’ajouter rapidement plusieurs dépositaires et leurs sources de données associées à un cas dans Advanced eDiscovery.
ms.openlocfilehash: 65ae932fac759896690e5fa65ec1d4173439ccb6
ms.sourcegitcommit: 36d12e02f6fda199ae7f2fb72fe52d7e2b5b4efd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/31/2020
ms.locfileid: "49740301"
---
# <a name="import-custodians-to-an-advanced-ediscovery-case"></a>Importer des dépositaires dans un cas avancé eDiscovery

Pour les cas avancés de découverte électronique qui impliquent de nombreux dépositaires, vous pouvez importer plusieurs dépositaires à la fois à l’aide d’un fichier CSV contenant les informations nécessaires pour les ajouter à un cas.

## <a name="import-custodians"></a>Importer des dépositaires

1. Ouvrez le cas avancé eDiscovery et sélectionnez l’onglet **sources de données** .

2. Cliquez sur **Ajouter** des  >  **dépositaires d’importation** de sources de données.

3. Sur la page flyout **importer des dépositaires** , cliquez sur **Télécharger un modèle vierge** pour télécharger un fichier CSV de modèle de dépositaire.

   ![Télécharger un modèle CSV à partir de la page de menu démenu importer les dépositaires](../media/ImportCustodians1.png)

4. Ajoutez les informations privatives de Troie au fichier CSV et enregistrez-le sur votre ordinateur local. Pour plus d’informations sur les propriétés requises dans le fichier CSV, voir la section relative au [fichier CSV](#custodian-csv-file) .

5. Une fois que vous avez préparé le fichier CSV avec les informations concernant le dépositaire, revenez à l’onglet **sources de données** , puis cliquez à nouveau sur Ajouter la **source de données**  >  **Importer les dépositaires** .

6. Sur la page flyout **importer des dépositaires** , cliquez sur **Parcourir** , puis téléchargez le fichier csv contenant les informations sur le dépositaire.

   Une fois le fichier CSV téléchargé, un travail nommé **BulkAddCustodian** est créé et affiché sous l’onglet **travaux** . Le travail valide les dépositaires et les sources de données associées, puis les ajoute à la page **sources de données** du cas.

## <a name="custodian-csv-file"></a>Fichier CSV de dépositaire

Une fois que vous avez téléchargé le modèle de dépositaire CSV, vous pouvez ajouter des dépositaires et leur source de données dans chaque ligne. Veillez à ne pas modifier les noms de colonne dans la ligne d’en-tête. Utilisez les colonnes type de charge de travail et emplacement de la charge de travail pour associer d’autres sources de données à un dépositaire.

| Nom de colonne|Description|
|:------- |:------------------------------------------------------------|
|**Adresse dépositaire**     |Adresse de messagerie UPN du dépositaire. Par exemple, sarad@contoso.onmicrosoft.com.           |
|**Exchange activé** | Valeur TRUE/FALSe pour inclure ou ne pas inclure la boîte aux lettres du dépositaire.      |
|**OneDrive activé** | Valeur TRUE/FALSe pour inclure ou non le compte OneDrive entreprise du dépositaire. |
|**Est OnHold**        | Valeur TRUE/FALSe pour indiquer si les sources de données du dépositaire doivent être placées en conservation.       |
|**Type Workload1**         |Valeur de chaîne indiquant le type de source de données à associer au dépositaire. Les valeurs admises sont les suivantes : <br/>- ExchangeMailbox<br/> - SharePointSite<br/>- TeamsMailbox<br/>- TeamsSite<br/> - YammerMailbox<br/>- YammerSite |
|**Emplacement Workload1**     | En fonction de votre type de charge de travail, il s’agit de l’emplacement de la source de données. Par exemple, l’adresse de messagerie d’une boîte aux lettres Exchange ou l’URL d’un site SharePoint. |
|||

Voici un exemple de fichier CSV contenant des informations sur les dépositaires :<br/><br/>

|Adresse dépositaire      | Exchange activé | OneDrive activé | Est OnHold | Type Workload1 | Emplacement Workload1             |
| ----------------- | ---------------- | ---------------- | --------- | -------------- | ------------------------------ |
|robinc@onmicrosoft.contoso.com | TRUE             | TRUE             | TRUE      | SharePointSite | https://contoso.sharepoint.com |
|pillarp@onmicrosoft.contoso.com | TRUE             | TRUE             | TRUE      | |  |
||||||

## <a name="custodian-and-data-source-validation"></a>Validation des dépositaires et des sources de données

Après avoir téléchargé le fichier CSV de dépositaire, Advanced eDiscovery effectue les opérations suivantes :

1. Valide les dépositaires et leurs sources de données.

2. Indexe toutes les sources de données pour chaque dépositaire et les place en conservation (si la propriété **is OnHold** dans le fichier CSV est définie sur true).

### <a name="custodian-validation"></a>Validation des dépositaires

Actuellement, nous ne prenons en charge que les dépositaires qui sont inclus dans l’Azure Active Directory de votre organisation (Azure AD).

L’outil Import dépositaire recherche et valide les dépositaires à l’aide de la valeur UPN dans la colonne **dépositaire adresse** dans le fichier CSV. Les dépositaires validés sont automatiquement ajoutés à l’incident et répertoriés sous l’onglet **sources de données** du cas. Si un dépositaire ne peut pas être validé, il est répertorié dans le journal des erreurs pour le travail BulkAddCustodian qui est répertorié sous l’onglet **travaux** dans le cas. Les dépositaires non validés ne sont pas ajoutés à l’incident ou répertoriés sous l’onglet **sources de données** .

### <a name="data-source-validation"></a>Validation de la source de données

Une fois que les dépositaires sont validés et ajoutés à l’incident, chaque boîte aux lettres principale et chaque compte OneDrive associé à un dépositaire est ajouté.

Toutefois, si l’une des autres sources de données (par exemple, les sites SharePoint, Microsoft Teams, les groupes Microsoft 365 ou les groupes Yammer) associés à un dépositaire est introuvable, aucune d’entre elles n’est affectée au dépositaire et la valeur **non validée** est affichée dans la colonne **État** en regard du dépositaire sous l’onglet **sources de données** .

Pour ajouter des sources de données validées pour un dépositaire, procédez comme suit :

1. Sous l’onglet **sources de données** , sélectionnez un dépositaire qui contient des sources de données qui ne sont pas validées.

2. Sur la page flyout dépositaire, faites défiler jusqu’à la section **emplacements privatives** de main pour afficher les sources de données validées et non validées associées au dépositaire.

3. Cliquez sur **modifier** en haut de la page de la fenêtre volante pour supprimer des sources de données non valides ou en ajouter de nouvelles.

4. Une fois que vous avez supprimé des sources de données non validées ou ajouté une nouvelle, la valeur **active** est affichée dans la colonne **État** du dépositaire, sous l’onglet **sources de données** . Pour ajouter des sources qui semblaient auparavant être non valides, suivez les étapes de correction ci-dessous pour les ajouter manuellement à un dépositaire.

### <a name="remediating-invalid-data-sources"></a>Correction de sources de données non valides

Pour ajouter et associer manuellement une source de données qui était précédemment non valide :

1. Sous l’onglet **sources de données** , sélectionnez un dépositaire pour ajouter et associer manuellement une source de données qui était précédemment incorrecte.

2. Cliquez sur **modifier** en haut de la page de menu volant pour associer des boîtes aux lettres, des sites, des équipes ou des groupes Yammer au dépositaire. Pour ce faire, cliquez sur **modifier** en regard du type d’emplacement de données approprié.

3. Cliquez sur **suivant** pour afficher la page des **paramètres de suspension** et configurer le blocage pour les sources de données que vous avez ajoutées.

4. Cliquez sur **suivant** pour afficher la page **vérifier les dépositaires** , puis cliquez sur **Envoyer** pour enregistrer vos modifications.
