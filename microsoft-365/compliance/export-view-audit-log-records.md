---
title: Exporter, configurer et afficher des enregistrements du journal d’audit
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: 0d4d0f35-390b-4518-800e-0c7ec95e946c
ms.custom: seo-marvel-apr2020
description: Dans cet article, vous allez apprendre à exporter, configurer et afficher les enregistrements du journal d’audit Microsoft 365'audit.
ms.openlocfilehash: 33bcf3ee79a7ee27cc87825458d7d98cda590773
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59182400"
---
# <a name="export-configure-and-view-audit-log-records"></a>Exporter, configurer et afficher des enregistrements du journal d’audit

Une fois que vous avez recherché le journal d’audit et téléchargé les résultats de la recherche dans un fichier CSV, le fichier contient une colonne nommée **AuditData**, qui contient des informations supplémentaires sur chaque événement. Les données de cette colonne sont formatées en tant qu’objet JSON, qui contient plusieurs propriétés configurées en tant que paires *property:value* séparées par des virgules. Vous pouvez utiliser la fonctionnalité de transformation JSON dans Power Query Editor dans Excel pour fractionner chaque propriété de l’objet JSON dans la colonne **AuditData** en plusieurs colonnes afin que chaque propriété possède sa propre colonne. Cela vous permet de trier et de filtrer une ou plusieurs de ces propriétés, ce qui peut vous aider à localiser rapidement les données d’audit spécifiques que vous recherchez.

## <a name="step-1-export-audit-log-search-results"></a>Étape 1 : Exporter les résultats de recherche du journal d’audit

La première étape consiste à effectuer une recherche dans le journal d’audit, puis à exporter les résultats dans un fichier de valeurs séparées par des virgules (CSV) vers votre ordinateur local.
  
1. Exécutez une [recherche dans le journal d’audit](search-the-audit-log-in-security-and-compliance.md#search-the-audit-log) et révisez les critères de recherche si nécessaire jusqu’à obtenir les résultats souhaités.

2. Cliquez **sur Exporter les résultats,** puis **sélectionnez Télécharger tous les résultats.** 

   ![Cliquez sur Télécharger tous les résultats.](../media/ExportAuditSearchResults.png)

   Cette option permet d’exporter tous les enregistrements d’audit à partir de la recherche de journal d’audit que vous avez elle-même, à l’étape 1, et de télécharger les données brutes du journal d’audit dans un fichier CSV. 

   Un message s’affiche en bas de la fenêtre pour vous demander d’ouvrir ou d’enregistrer le fichier CSV. 

3. Cliquez **sur Enregistrer > enregistrer sous** et enregistrer le fichier CSV sur votre ordinateur local. Le téléchargement de nombreux résultats de recherche prend un certain temps. C’est généralement le cas lorsque vous recherchez toutes les activités ou une plage de dates étendue. Un message en bas des fenêtres s’affiche lorsque le téléchargement du fichier CSV est terminé.

   ![Message affiché lorsque le téléchargement du fichier CSV est terminé.](../media/ExportAuditSearchResultsFinish.png)

> [!NOTE]
  > Vous pouvez télécharger un maximum de 50 000 entrées dans un fichier .csv à partir d’une seule recherche dans le journal d’audit. Si 50 000 résultats sont téléchargés dans le fichier .csv, vous pouvez partir du principe que plus de 50 000 événements remplissent les critères de recherche. Pour exporter plus de données que cette limite, essayez d’utiliser une plage de dates pour réduire le nombre d’enregistrements du journal d’audit. Vous devrez peut-être effectuer plusieurs recherches avec des plages de dates plus réduites pour exporter plus de 50 000 entrées.

## <a name="step-2-format-the-exported-audit-log-using-the-power-query-editor"></a>Étape 2 : Mise en forme du journal d’audit exporté à l’aide de Power Query Editor

L’étape suivante consiste à utiliser la fonctionnalité de transformation JSON dans Power Query Editor dans Excel pour fractionner chaque propriété de l’objet JSON de la colonne **AuditData** en sa propre colonne. Ensuite, vous filtrez les colonnes pour afficher les enregistrements en fonction des valeurs de propriétés spécifiques. Cela peut vous aider à localiser rapidement les données d’audit spécifiques que vous recherchez.

1. Ouvrez un Excel vide pour Office 365, Excel 2019 ou Excel 2016.

2. Sous **l’onglet** Données, dans le groupe **& Transformer** les données, cliquez sur **Texte/CSV**.

    ![Sous l’onglet Données, cliquez sur Texte/CSV.](../media/JSONTransformOpenCSVFile.png)

3. Ouvrez le fichier CSV que vous avez téléchargé à l’étape 1.

4. Dans la fenêtre qui s’affiche, cliquez sur **Transformer les données.**

   ![Cliquez sur Transformer les données.](../media/JSONOpenPowerQuery.png)

   Le fichier CSV est ouvert dans **l’Éditeur de requêtes.** Il existe quatre colonnes **: CreationDate**, **UserIds**, **Operations** et **AuditData**. La **colonne AuditData** est un objet JSON qui contient plusieurs propriétés. L’étape suivante consiste à créer une colonne pour chaque propriété dans l’objet JSON.

5. Cliquez avec le bouton droit sur le titre dans **la colonne AuditData,** cliquez sur **Transformer,** puis cliquez sur **JSON**. 

   ![Cliquez avec le bouton droit sur la colonne AuditData, cliquez sur Transformer, puis sélectionnez JSON.](../media/JSONTransform.png)

6. Dans le coin supérieur droit de la colonne **AuditData,** cliquez sur l’icône développer.

   ![Dans la colonne AuditData, cliquez sur l’icône développer.](../media/JSONTransformExpandIcon.png)

   Une liste partielle des propriétés des objets JSON dans la colonne **AuditData** s’affiche.

7. Cliquez **sur Charger plus** pour afficher toutes les propriétés des objets JSON dans la colonne **AuditData.**

   ![Cliquez sur Charger plus pour afficher toutes les propriétés dans l’objet JSON.](../media/JSONTransformLoadJSONProperties.png)

   Vous pouvez désélectionner la case à cocher en regard de toute propriété que vous ne souhaitez pas inclure. L’élimination des colonnes qui ne sont pas utiles pour votre examen est un bon moyen de réduire la quantité de données affichées dans le journal d’audit. 

   > [!NOTE]
   > Les propriétés JSON affichées dans la capture d’écran précédente (après avoir cliqué sur Charger **plus)** sont basées sur les propriétés trouvées dans la colonne **AuditData** des 1 000 premières lignes du fichier CSV. S’il existe différentes propriétés JSON dans les enregistrements après les 1 000 premières lignes, ces propriétés (et une colonne correspondante) ne sont pas incluses lorsque la colonne **AuditData** est fractionnées en plusieurs colonnes. Pour éviter cela, envisagez de ré-exécutez la recherche dans le journal d’audit et limitez les critères de recherche afin que moins d’enregistrements soient renvoyés. Une autre solution consiste à filtrer les éléments de la colonne **Opérations** pour réduire le nombre de lignes (avant d’effectuer l’étape 5 ci-dessus) avant de transformer l’objet JSON dans la colonne **AuditData.**

   > [!TIP]
   > Pour afficher un attribut dans une liste telle qu’AuditData.AffectedItems, cliquez sur l’icône Développer dans le coin supérieur droit de la colonne à partir de la colonne à partir de qui vous souhaitez tirer un attribut, puis sélectionnez Développer vers la nouvelle **ligne.**   À partir de là, il s’agit d’un enregistrement et vous pouvez cliquer sur l’icône Développer dans le coin supérieur droit de la colonne, afficher les attributs et sélectionner celui que vous souhaitez afficher ou extraire. 

8. Pour mettre en forme le titre des colonnes ajoutées pour chaque propriété JSON sélectionnée, faites l’une des choses suivantes.

    - Désélectionner la case à cocher Utiliser le nom de colonne d’origine comme **préfixe** pour utiliser le nom de la propriété JSON comme noms de colonne ; par exemple, **RecordType** ou **SourceFileName**.

    - Laissez la case à cocher Utiliser le nom de colonne d’origine comme **préfixe** sélectionnée pour ajouter le préfixe AuditData aux noms de colonnes ; par exemple, **AuditData.RecordType** ou **AuditData.SourceFileName**.

9. Cliquez sur **OK**.

    La **colonne AuditData** est divisée en plusieurs colonnes. Chaque nouvelle colonne correspond à une propriété dans l’objet JSON AuditData. Chaque ligne de la colonne contient la valeur de la propriété. Si la propriété ne contient pas de valeur, la valeur *null* s’affiche. Dans Excel, les cellules avec des valeurs null sont vides.
  
10. Sous **l’onglet** Accueil, cliquez sur Fermer **& charger** pour fermer l’éditeur power query et ouvrir le fichier CSV transformé dans un classe Excel classer.

## <a name="use-powershell-to-search-and-export-audit-log-records"></a>Utiliser PowerShell pour rechercher et exporter des enregistrements de journal d’audit

Au lieu d’utiliser l’outil de recherche du journal d’audit dans le Centre de conformité Microsoft 365, vous pouvez utiliser l’cmdlet [Search-UnifiedAuditLog](/powershell/module/exchange/search-unifiedauditlog) dans Exchange Online PowerShell pour exporter les résultats d’une recherche de journal d’audit dans un fichier CSV. Vous pouvez ensuite suivre la même procédure décrite à l’étape 2 pour mettre en forme le journal d’audit à l’aide de l’éditeur Power Query. L’un des avantages de l’utilisation de l’cmdlet PowerShell est que vous pouvez rechercher des événements à partir d’un service spécifique à l’aide du *paramètre RecordType.* Voici quelques exemples d’utilisation de PowerShell pour exporter des enregistrements d’audit vers un fichier CSV afin que vous pouvez utiliser l’éditeur Power Query pour transformer l’objet JSON dans la colonne **AuditData,** comme décrit à l’étape 2.

Dans cet exemple, exécutez les commandes suivantes pour renvoyer tous les enregistrements liés SharePoint opérations de partage.

```powershell
$auditlog = Search-UnifiedAuditLog -StartDate 06/01/2019 -EndDate 06/30/2019 -RecordType SharePointSharingOperation
```

```powershell
$auditlog | Select-Object -Property CreationDate,UserIds,RecordType,AuditData | Export-Csv -Path c:\AuditLogs\PowerShellAuditlog.csv -NoTypeInformation
```

Les résultats de la recherche sont exportés vers un fichier CSV nommé *PowerShellAuditlog* qui contient quatre colonnes : CreationDate, UserIds, RecordType, AuditData).

Vous pouvez également utiliser le nom ou la valeur d’enum pour le type d’enregistrement comme valeur pour le *paramètre RecordType.* Pour obtenir la liste des noms de types d’enregistrement et leurs valeurs d’énumérer correspondantes, voir la table *AuditLogRecordType* dans le schéma de l Office 365 [API Activité de gestion.](/office/office-365-management-api/office-365-management-activity-api-schema#enum-auditlogrecordtype---type-edmint32)

Vous ne pouvez inclure qu’une seule valeur pour le *paramètre RecordType.* Pour rechercher des enregistrements d’audit pour d’autres types d’enregistrements, vous devez ré-exécuter les deux commandes précédentes pour spécifier un type d’enregistrement différent et les appendre au fichier CSV d’origine. Par exemple, vous pouvez exécuter les deux commandes suivantes pour ajouter SharePoint activités de fichier de la même plage de dates au PowerShellAuditlog.csv fichier.

```powershell
$auditlog = Search-UnifiedAuditLog -StartDate 06/01/2019 -EndDate 06/30/2019 -RecordType SharePointFileOperation
```

```powershell
$auditlog | Select-Object -Property CreationDate,UserIds,RecordType,AuditData | Export-Csv -Append -Path c:\AuditLogs\PowerShellAuditlog.csv -NoTypeInformation
```

## <a name="tips-for-exporting-and-viewing-the-audit-log"></a>Astuces pour l’exportation et l’affichage du journal d’audit

Voici quelques conseils et exemples d’exportation et d’affichage du journal d’audit avant et après l’utilisation de la fonctionnalité de transformation JSON pour fractionner la colonne **AuditData** en plusieurs colonnes.

- Filtrez la **colonne RecordType** pour afficher uniquement les enregistrements d’un service ou d’une zone fonctionnelle spécifique. Par exemple, pour afficher les événements liés au partage SharePoint, vous devez sélectionner **14** (valeur d’enum pour les enregistrements déclenchés par SharePoint activités de partage). Pour obtenir la liste des services qui correspondent aux valeurs enum affichées dans la colonne **RecordType,** voir Propriétés détaillées dans le journal [d’audit.](detailed-properties-in-the-office-365-audit-log.md)

- Filtrez **la colonne Opérations** pour afficher les enregistrements pour des activités spécifiques. Pour obtenir la liste de la plupart des opérations qui correspondent à une activité de recherche dans l’outil de recherche du journal d’audit dans le Centre de conformité Microsoft 365, consultez la section « Activités auditées » dans le journal [d’audit.](search-the-audit-log-in-security-and-compliance.md#audited-activities)
