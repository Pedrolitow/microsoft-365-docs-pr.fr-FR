---
title: Utiliser PowerShell pour demander le traitement par un modèle personnalisé
ms.author: jaeccles
author: jameseccles
ms.reviewer: ssquires
manager: ssquires
audience: admin
ms.topic: article
ms.service: microsoft-syntex
ms.collection:
- enabler-strategic
- m365initiative-syntex
search.appverid: MET150
ms.localizationpriority: medium
description: Découvrez comment utiliser PowerShell pour demander le traitement par un modèle personnalisé Microsoft Syntex.
ms.openlocfilehash: b28bc8945c4704354d351185a5ff2cf1c72031ea
ms.sourcegitcommit: 87283bb02ca750286f7c069f811b788730ed5832
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2022
ms.locfileid: "68662070"
---
# <a name="use-powershell-to-request-processing-by-a-custom-model"></a>Utiliser PowerShell pour demander le traitement par un modèle personnalisé

<sup>**S’applique à :**  &ensp; &#10003; Tous les modèles personnalisés</sup>

> [!IMPORTANT]
> Les applets de commande Microsoft Syntex PowerShell et tous les autres composants PnP sont des outils open source soutenus par une communauté active qui les prend en charge. Il n’existe aucun contrat de niveau de service pour la prise en charge des outils open source des canaux de support Microsoft officiels.

Les modèles personnalisés traitent les fichiers nouvellement chargés dans une bibliothèque. Il est également possible de demander manuellement le traitement dans l’interface utilisateur. Toutefois, il peut y avoir des scénarios où il est plus efficace de déclencher le traitement via PowerShell.

## <a name="request-processing-of-all-items-that-havent-been-previously-classified"></a>Traitement des demandes de tous les éléments qui n’ont pas été classés précédemment

Vous pouvez demander le traitement de tous les éléments de la bibliothèque qui n’ont pas été classés précédemment à l’aide de cette commande :

```PowerShell
#Note: you're connecting here to the site that holds the document library you want to process
Connect-PnPOnline -Url "https://contoso.sharepoint.com/sites/finance"

Request-PnPSyntexClassifyAndExtract -List "Documents"
```

Pour le traitement de priorité inférieure, vous pouvez également envisager d’utiliser le paramètre -OffPeak, qui met en file d’attente les fichiers à traiter en dehors des heures d’ouverture où se trouve votre locataire. Pour plus d’informations, consultez [Request-PnPSyntexClassifyAndExtract](https://pnp.github.io/powershell/cmdlets/Request-PnPSyntexClassifyAndExtract.html).

## <a name="request-processing-of-all-items-in-a-library"></a>Demander le traitement de tous les éléments d’une bibliothèque

Vous pouvez demander le traitement de tous les fichiers de la bibliothèque, même s’ils ont été précédemment classifiés. Cette étape peut être utile si vous avez mis à jour un modèle ou ajouté un autre modèle à la bibliothèque.

```PowerShell
#Note: you're connecting here to the site that holds the document library you want to process
Connect-PnPOnline -Url "https://contoso.sharepoint.com/sites/finance"

Request-PnPSyntexClassifyAndExtract -List "Documents" -Force
```

> [!NOTE]
> L’utilisation de l’option -Force avec plus de 5 000 éléments active automatiquement le traitement en dehors des heures creuses.

## <a name="request-processing-of-all-items-based-on-a-property"></a>Traitement des demandes de tous les éléments en fonction d’une propriété

Si vous souhaitez limiter le traitement à un sous-ensemble spécifique d’éléments dans une bibliothèque, vous pouvez utiliser un script pour sélectionner un groupe spécifique de fichiers. Dans l’exemple suivant, le script autorise la sélection d’un champ et la valeur d’un champ à filtrer. Des requêtes plus complexes peuvent être effectuées à l’aide [de Get-PnPListItem](https://pnp.github.io/powershell/cmdlets/Get-PnPListItem.html).

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

## <a name="request-processing-of-specific-files"></a>Demander le traitement de fichiers spécifiques

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
