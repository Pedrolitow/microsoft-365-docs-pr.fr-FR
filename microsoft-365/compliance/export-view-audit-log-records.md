---
title: Exporter, configurer et afficher des enregistrements du journal d’audit
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: 0d4d0f35-390b-4518-800e-0c7ec95e946c
ms.custom: seo-marvel-apr2020
description: Dans cet article, vous allez apprendre à exporter, configurer et afficher les enregistrements du journal d’audit Microsoft 365.
ms.openlocfilehash: b528dcd669749198490b028db4bbd18fe313f1ee
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66640091"
---
# <a name="export-configure-and-view-audit-log-records"></a>Exporter, configurer et afficher des enregistrements du journal d’audit

Après avoir recherché le journal d’audit et téléchargé les résultats de la recherche dans un fichier CSV, le fichier contient une colonne nommée **AuditData**, qui contient des informations supplémentaires sur chaque événement. Les données de cette colonne sont mises en forme en tant qu’objet JSON, qui contient plusieurs propriétés configurées en tant que paires *property:value* séparées par des virgules. Vous pouvez utiliser la fonctionnalité de transformation JSON dans le Éditeur Power Query dans Excel pour fractionner chaque propriété de l’objet JSON de la colonne **AuditData** en plusieurs colonnes afin que chaque propriété ait sa propre colonne. Cela vous permet de trier et de filtrer une ou plusieurs de ces propriétés, ce qui peut vous aider à localiser rapidement les données d’audit spécifiques que vous recherchez.

## <a name="step-1-export-audit-log-search-results"></a>Étape 1 : Exporter les résultats de la recherche dans le journal d’audit

La première étape consiste à rechercher dans le journal d’audit, puis à exporter les résultats dans un fichier de valeurs séparées par des virgules (CSV) sur votre ordinateur local.
  
1. Exécutez une recherche dans le [journal d’audit](search-the-audit-log-in-security-and-compliance.md#search-the-audit-log) et modifiez les critères de recherche si nécessaire jusqu’à ce que vous ayez les résultats souhaités.

2. Sur la page des résultats de la recherche, cliquez sur **Exporter** > **Télécharger tous les résultats**.

   ![Cliquez sur Télécharger tous les résultats.](../media/ExportAuditSearchResults.png)

   Cette option exporte tous les enregistrements d’audit de la recherche dans le journal d’audit que vous avez exécutée à l’étape 1 et ajoute les données brutes du journal d’audit à un fichier CSV. La préparation du fichier de téléchargement pour une recherche volumineuse prend un certain temps. Les fichiers volumineux se traduisent lors de la recherche de toutes les activités ou de l’utilisation d’une plage de dates étendue.

3. Une fois le processus d'exportation terminé, un message s'affiche en haut de la fenêtre et vous invite à ouvrir le fichier CSV et à l'enregistrer sur votre ordinateur local. Vous pouvez également accéder au fichier CSV dans le dossier Téléchargements.

   > [!NOTE]
   > Vous pouvez télécharger un maximum de 50 000 entrées dans un fichier .csv à partir d’une seule recherche dans le journal d’audit. Si 50 000 résultats sont téléchargés dans le fichier .csv, vous pouvez partir du principe que plus de 50 000 événements remplissent les critères de recherche. Pour exporter plus de cette limite, essayez d’utiliser une plage de dates plus étroite pour réduire le nombre d’enregistrements du journal d’audit. Vous devrez peut-être effectuer plusieurs recherches avec des plages de dates plus réduites pour exporter plus de 50 000 entrées.

## <a name="step-2-format-the-exported-audit-log-using-the-power-query-editor"></a>Étape 2 : Mettre en forme le journal d’audit exporté à l’aide du Éditeur Power Query

L’étape suivante consiste à utiliser la fonctionnalité de transformation JSON dans le Éditeur Power Query dans Excel pour fractionner chaque propriété de l’objet JSON de la colonne **AuditData** en sa propre colonne. Ensuite, vous filtrez les colonnes pour afficher les enregistrements en fonction des valeurs de propriétés spécifiques. Cela peut vous aider à localiser rapidement les données d’audit spécifiques que vous recherchez.

1. Ouvrez un classeur vide dans Excel pour Office 365, Excel 2019 ou Excel 2016.

2. Sous l’onglet **Données** , dans le groupe **Obtenir & Transformer des données** , cliquez sur **À partir du texte/CSV**.

    ![Sous l’onglet Données, cliquez sur Texte/CSV.](../media/JSONTransformOpenCSVFile.png)

3. Ouvrez le fichier CSV que vous avez téléchargé à l’étape 1.

4. Dans la fenêtre qui s’affiche, cliquez sur **Transformer les données**.

   ![Cliquez sur Transformer les données.](../media/JSONOpenPowerQuery.png)

   Le fichier CSV est ouvert dans le **Éditeur de requête**. Il existe quatre colonnes : **CreationDate**, **UserIds**, **Operations** et **AuditData**. La colonne **AuditData** est un objet JSON qui contient plusieurs propriétés. L’étape suivante consiste à créer une colonne pour chaque propriété dans l’objet JSON.

5. Cliquez avec le bouton droit sur le titre dans la colonne **AuditData** , cliquez sur **Transformer**, puis sur **JSON**. 

   ![Cliquez avec le bouton droit sur la colonne AuditData, cliquez sur Transformer, puis sélectionnez JSON.](../media/JSONTransform.png)

6. Dans le coin supérieur droit de la colonne **AuditData** , cliquez sur l’icône développer.

   ![Dans la colonne AuditData, cliquez sur l’icône Développer.](../media/JSONTransformExpandIcon.png)

   Une liste partielle des propriétés des objets JSON dans la colonne **AuditData** s’affiche.

7. Cliquez sur **Charger plus** pour afficher toutes les propriétés des objets JSON dans la colonne **AuditData** .

   ![Cliquez sur Charger plus pour afficher toutes les propriétés de l’objet JSON.](../media/JSONTransformLoadJSONProperties.png)

   Vous pouvez désélectionner la case à cocher en regard de toute propriété que vous ne souhaitez pas inclure. L’élimination des colonnes qui ne sont pas utiles pour votre investigation est un bon moyen de réduire la quantité de données affichées dans le journal d’audit. 

   > [!NOTE]
   > Les propriétés JSON affichées dans la capture d’écran précédente (après avoir cliqué sur **Charger plus**) sont basées sur les propriétés trouvées dans la colonne **AuditData** des 1 000 premières lignes du fichier CSV. S’il existe différentes propriétés JSON dans les enregistrements après les 1 000 premières lignes, ces propriétés (et une colonne correspondante) ne sont pas incluses lorsque la colonne **AuditData** est divisée en plusieurs colonnes. Pour éviter cela, envisagez de réexécuter la recherche dans le journal d’audit et d’affiner les critères de recherche afin de renvoyer moins d’enregistrements. Une autre solution de contournement consiste à filtrer les éléments de la colonne **Opérations** afin de réduire le nombre de lignes (avant d’effectuer l’étape 5 ci-dessus) avant de transformer l’objet JSON dans la colonne **AuditData** .

   > [!TIP]
   > Pour afficher un attribut dans une liste telle qu’AuditData.AffectedItems, cliquez sur l’icône **Développer** dans le coin supérieur droit de la colonne à partir de laquelle vous souhaitez extraire un attribut, puis **sélectionnez Développer vers la nouvelle ligne**.  À partir de là, il s’agit d’un enregistrement et vous pouvez cliquer sur l’icône **Développer** dans le coin supérieur droit de la colonne, afficher les attributs et sélectionner celui que vous souhaitez afficher ou extraire.

8. Effectuez l’une des opérations suivantes pour mettre en forme le titre des colonnes ajoutées pour chaque propriété JSON sélectionnée.

    - Désélectionnez la case à cocher **Utiliser le nom de colonne d’origine comme case à cocher de préfixe** pour utiliser le nom de la propriété JSON comme noms de colonnes ; par exemple, **RecordType** ou **SourceFileName**.

    - Laissez la case à cocher **Utiliser le nom de colonne d’origine comme** case à cocher préfixe sélectionnée pour ajouter le préfixe AuditData aux noms de colonnes ; par exemple **, AuditData.RecordType** ou **AuditData.SourceFileName**.

9. Cliquez sur **OK**.

    La colonne **AuditData** est divisée en plusieurs colonnes. Chaque nouvelle colonne correspond à une propriété dans l’objet JSON AuditData. Chaque ligne de la colonne contient la valeur de la propriété. Si la propriété ne contient pas de valeur, la valeur *null* s’affiche. Dans Excel, les cellules avec des valeurs Null sont vides.
  
10. Sous l’onglet **Accueil**, cliquez sur **Fermer & Charger** pour fermer le Éditeur Power Query et ouvrir le fichier CSV transformé dans un classeur Excel.

## <a name="use-powershell-to-search-and-export-audit-log-records"></a>Utiliser PowerShell pour rechercher et exporter des enregistrements de journal d’audit

Au lieu d’utiliser l’outil de recherche de journal d’audit dans le portail de conformité Microsoft Purview, vous pouvez utiliser l’applet de commande [Search-UnifiedAuditLog](/powershell/module/exchange/search-unifiedauditlog) dans Exchange Online PowerShell pour exporter les résultats d’une recherche dans le journal d’audit vers un fichier CSV. Vous pouvez ensuite suivre la même procédure décrite à l’étape 2 pour mettre en forme le journal d’audit à l’aide de l’éditeur Power Query. L’un des avantages de l’utilisation de l’applet de commande PowerShell est que vous pouvez rechercher des événements à partir d’un service spécifique à l’aide du paramètre *RecordType* . Voici quelques exemples d’utilisation de PowerShell pour exporter des enregistrements d’audit dans un fichier CSV afin que vous puissiez utiliser l’éditeur Power Query pour transformer l’objet JSON dans la colonne **AuditData**, comme décrit à l’étape 2.

Dans cet exemple, exécutez les commandes suivantes pour retourner tous les enregistrements liés aux opérations de partage SharePoint.

```powershell
$auditlog = Search-UnifiedAuditLog -StartDate 06/01/2019 -EndDate 06/30/2019 -RecordType SharePointSharingOperation
```

```powershell
$auditlog | Select-Object -Property CreationDate,UserIds,RecordType,AuditData | Export-Csv -Path c:\AuditLogs\PowerShellAuditlog.csv -NoTypeInformation
```

Les résultats de la recherche sont exportés vers un fichier CSV nommé *PowerShellAuditlog* qui contient quatre colonnes : CreationDate, UserIds, RecordType, AuditData).

Vous pouvez également utiliser le nom ou la valeur d’énumération pour le type d’enregistrement comme valeur du paramètre *RecordType* . Pour obtenir la liste des noms de types d’enregistrements et leurs valeurs d’énumération correspondantes, consultez la table *AuditLogRecordType* dans [Office 365 schéma de l’API Activité de gestion](/office/office-365-management-api/office-365-management-activity-api-schema#enum-auditlogrecordtype---type-edmint32).

Vous ne pouvez inclure qu’une seule valeur pour le paramètre *RecordType* . Pour rechercher des enregistrements d’audit pour d’autres types d’enregistrements, vous devez réexécuter les deux commandes précédentes pour spécifier un autre type d’enregistrement et ajouter ces résultats au fichier CSV d’origine. Par exemple, vous exécutez les deux commandes suivantes pour ajouter des activités de fichier SharePoint de la même plage de dates au fichier PowerShellAuditlog.csv.

```powershell
$auditlog = Search-UnifiedAuditLog -StartDate 06/01/2019 -EndDate 06/30/2019 -RecordType SharePointFileOperation
```

```powershell
$auditlog | Select-Object -Property CreationDate,UserIds,RecordType,AuditData | Export-Csv -Append -Path c:\AuditLogs\PowerShellAuditlog.csv -NoTypeInformation
```

## <a name="tips-for-exporting-and-viewing-the-audit-log"></a>Conseils pour l’exportation et l’affichage du journal d’audit

Voici quelques conseils et exemples d’exportation et d’affichage du journal d’audit avant et après l’utilisation de la fonctionnalité de transformation JSON pour fractionner la colonne **AuditData** en plusieurs colonnes.

- Filtrez la colonne **RecordType** pour afficher uniquement les enregistrements d’un service ou d’une zone fonctionnelle spécifique. Par exemple, pour afficher les événements liés au partage SharePoint, vous devez sélectionner **14** (valeur d’énumération pour les enregistrements déclenchés par les activités de partage SharePoint). Pour obtenir la liste des services qui correspondent aux valeurs d’énumération affichées dans la colonne **RecordType** , consultez [Propriétés détaillées dans le journal d’audit](detailed-properties-in-the-office-365-audit-log.md).

- Filtrez la colonne **Opérations** pour afficher les enregistrements pour des activités spécifiques. Pour obtenir la liste de la plupart des opérations qui correspondent à une activité pouvant faire l’objet d’une recherche dans l’outil de recherche de journal d’audit dans le portail de conformité, consultez la section « Activités auditées » dans [le journal d’audit](search-the-audit-log-in-security-and-compliance.md#audited-activities).
