---
title: Utiliser PowerShell pour demander le traitement par un modèle de compréhension de document
ms.author: jaeccles
author: jameseccles
ms.reviewer: ssquires
manager: serdars
audience: admin
ms.topic: article
ms.service: microsoft-365-enterprise
ms.collection:
- enabler-strategic
- m365initiative-syntex
search.appverid: MET150
ms.localizationpriority: medium
description: Découvrez comment utiliser PowerShell pour demander le traitement par un modèle de compréhension de document Microsoft Syntex.
ms.openlocfilehash: 1f537c3759ee8783c18bee5e8241e004c73f2eec
ms.sourcegitcommit: 04e517c7e00323b5c33d8ea937115725cf2cfd4d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2022
ms.locfileid: "68563227"
---
# <a name="use-powershell-to-request-processing-by-a-document-understanding-model"></a>Utiliser PowerShell pour demander le traitement par un modèle de compréhension de document

> [!IMPORTANT]
> Les applets de commande Microsoft Syntex PowerShell et tous les autres composants PnP sont des outils open source soutenus par une communauté active qui les prend en charge. Il n’existe aucun contrat de niveau de service pour la prise en charge des outils open source des canaux de support Microsoft officiels.

Les modèles de compréhension de document traitent les fichiers nouvellement chargés dans une bibliothèque. Il est également possible de demander manuellement le traitement dans l’interface utilisateur. Toutefois, il peut y avoir des scénarios où il est plus efficace de déclencher le traitement via PowerShell.

## <a name="request-processing-of-all-items-that-have-not-been-previously-classified"></a>Traitement des demandes de tous les éléments qui n’ont pas été précédemment classés

Vous pouvez demander le traitement de tous les éléments de la bibliothèque qui n’ont pas déjà été classés à l’aide de cette commande :

```PowerShell
#Note: you're connecting here to the site that holds the document library you want to process
Connect-PnPOnline -Url "https://contoso.sharepoint.com/sites/finance"

Request-PnPSyntexClassifyAndExtract -List "Documents"
```

Pour un traitement de priorité inférieure, vous pouvez également envisager d’utiliser le paramètre -OffPeak, qui met en file d’attente les fichiers pour le traitement en dehors des heures d’ouverture où se trouve votre locataire. Pour plus d’informations, consultez [Request-PnPSyntexClassifyAndExtract](https://pnp.github.io/powershell/cmdlets/Request-PnPSyntexClassifyAndExtract.html) .

## <a name="request-processing-of-all-items-in-a-library"></a>Demande de traitement de tous les éléments d’une bibliothèque

Vous pouvez demander le traitement de tous les fichiers de la bibliothèque, même s’ils ont été précédemment classifiés. Cela peut être utile si vous avez mis à jour un modèle ou ajouté un autre modèle à la bibliothèque.

```PowerShell
#Note: you're connecting here to the site that holds the document library you want to process
Connect-PnPOnline -Url "https://contoso.sharepoint.com/sites/finance"

Request-PnPSyntexClassifyAndExtract -List "Documents" -Force
```

> [!NOTE]
> L’utilisation de l’option -Force avec plus de 5 000 éléments active automatiquement le traitement de pointe.

## <a name="request-processing-of-all-items-based-on-a-property"></a>Demander le traitement de tous les éléments en fonction d’une propriété

Si vous souhaitez limiter le traitement à un sous-ensemble spécifique d’éléments dans une bibliothèque, vous pouvez utiliser un script pour sélectionner un groupe spécifique de fichiers. Dans l’exemple suivant, le script permet de sélectionner un champ et de filtrer une valeur de champ. Des requêtes plus complexes peuvent être effectuées à l’aide de [Get-PnPListItem](https://pnp.github.io/powershell/cmdlets/Get-PnPListItem.html).

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

## <a name="request-processing-of-specific-files"></a>Demande de traitement de fichiers spécifiques

Le traitement peut également être demandé pour des fichiers spécifiques.

```PowerShell
#Note: you're connecting here to the site that holds the document library you want to process
Connect-PnPOnline -Url "https://contoso.sharepoint.com/sites/finance"

Request-PnPSyntexClassifyAndExtract -FileUrl "/sites/finance/documents/contoso contract.docx"
```

Le modèle fichier par fichier prend également en charge le traitement par lot :

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
