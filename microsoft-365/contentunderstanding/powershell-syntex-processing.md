---
title: Utiliser PowerShell pour demander le traitement par un modèle de présentation de document
ms.author: jaeccles
author: jameseccles
ms.reviewer: ssquires
manager: serdars
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.collection:
- enabler-strategic
- m365initiative-syntex
search.appverid: MET150
ms.localizationpriority: medium
description: Découvrez comment utiliser PowerShell pour demander le traitement par un modèle SharePoint Syntex document.
ms.openlocfilehash: 8f66a0cc5e59ad2ccb6b92d98cfaee8ce84470f2
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2022
ms.locfileid: "63526441"
---
# <a name="use-powershell-to-request-processing-by-a-document-understanding-model"></a>Utiliser PowerShell pour demander le traitement par un modèle de présentation de document

> [!IMPORTANT]
> Les SharePoint Syntex PowerShell et tous les autres composants PnP sont des outils open source soutenus par une communauté active qui les aide. Il n’existe aucun contrat de niveau de service pour la prise en charge des outils open source des canaux de support Microsoft officiels.

Les modèles de compréhension des documents traitera les fichiers nouvellement téléchargés dans une bibliothèque. Il est également possible de demander manuellement le traitement dans l’interface utilisateur. Toutefois, dans certains scénarios, il peut être plus efficace de déclencher le traitement via PowerShell.

## <a name="request-processing-of-all-items-that-have-not-been-previously-classified"></a>Demande de traitement de tous les éléments qui n’ont pas été classés précédemment

Vous pouvez demander le traitement de tous les éléments de la bibliothèque qui n’ont pas été classés précédemment à l’aide de cette commande :

```PowerShell
#Note: you're connecting here to the site that holds the document library you want to process
Connect-PnPOnline -Url "https://contoso.sharepoint.com/sites/finance"

Request-PnPSyntexClassifyAndExtract -List "Documents"
```

Pour un traitement de priorité inférieure, vous pouvez également envisager d’utiliser le paramètre -OffPeak, qui placera les fichiers en file d’attente pour traitement en dehors des heures d’ouverture où se trouve votre client. Pour [plus d’informations, voir Request-PnPSyntexClassifyAndExtract](https://pnp.github.io/powershell/cmdlets/Request-PnPSyntexClassifyAndExtract.html) .

## <a name="request-processing-of-all-items-in-a-library"></a>Demande de traitement de tous les éléments d’une bibliothèque

Vous pouvez demander le traitement de tous les fichiers de la bibliothèque, même s’ils ont été classés précédemment. Cela peut être utile si vous avez mis à jour un modèle ou ajouté un autre modèle à la bibliothèque.

```PowerShell
#Note: you're connecting here to the site that holds the document library you want to process
Connect-PnPOnline -Url "https://contoso.sharepoint.com/sites/finance"

Request-PnPSyntexClassifyAndExtract -List "Documents" -Force
```

> [!NOTE]
> L’utilisation de l’option -Force avec plus de 5 000 éléments active automatiquement le traitement hors pointe.

## <a name="request-processing-of-all-items-based-on-a-property"></a>Demander le traitement de tous les éléments en fonction d’une propriété

Si vous souhaitez limiter le traitement à un sous-ensemble spécifique d’éléments dans une bibliothèque, vous pouvez utiliser un script pour sélectionner un groupe spécifique de fichiers. Dans l’exemple suivant, le script permet de sélectionner un champ et d’en filtrer une valeur. Des requêtes plus complexes peuvent être effectuées [à l’aide de Get-PnPListItem](https://pnp.github.io/powershell/cmdlets/Get-PnPListItem.html).

```PowerShell
#Note: you're connecting here to the site that holds the document library you want to process
Connect-PnPOnline -Url "https://contoso.sharepoint.com/sites/finance"
$list = Get-PnPList -Identity "Documents"
# Set the field name to filter items by
$fieldName = "Vendor"
# Set the field value to filter by
$fieldFilter = "Fabrikam"

$listItems = (Get-PnPListItem -List $list -fields $fieldName).fieldValues
$targetItems = $listItems | Where-Object -Property Provider -EQ -Value $fieldFilter

# Create a new batch
$batch = New-PnPBatch

# Add files to classify to the batch
foreach ($listItem in $targetItems) {
    Request-PnPSyntexClassifyAndExtract -FileUrl $listItem.FileRef -Batch $classifyBatch
}

# Execute batch
Invoke-PnPBatch -Batch $batch
```

## <a name="request-processing-of-specific-files"></a>Traitement des demandes de fichiers spécifiques

Le traitement peut également être demandé pour des fichiers spécifiques.

```PowerShell
#Note: you're connecting here to the site that holds the document library you want to process
Connect-PnPOnline -Url "https://contoso.sharepoint.com/sites/finance"

Request-PnPSyntexClassifyAndExtract -FileUrl "/sites/finance/documents/contoso contract.docx"
```

Le modèle de fichier par fichier prend également en charge le traitement par lots :

```PowerShell
#Note: you're connecting here to the site that holds the document library you want to process
Connect-PnPOnline -Url "https://contoso.sharepoint.com/sites/finance"

# Create a new batch
$batch = New-PnPBatch

# Add files to classify to the batch
Request-PnPSyntexClassifyAndExtract -FileUrl "/sites/finance/documents/contoso contract.docx" -Batch $batch
Request-PnPSyntexClassifyAndExtract -FileUrl "/sites/finance/documents/relecloud contract.docx" -Batch $batch

# Execute batch
Invoke-PnPBatch -Batch $batch
```
