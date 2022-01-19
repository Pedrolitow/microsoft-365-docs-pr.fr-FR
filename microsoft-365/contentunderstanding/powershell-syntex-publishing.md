---
title: Publier des modèles de présentation de documents avec PowerShell
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
ms.localizationpriority: normal
description: Découvrez comment publier un document SharePoint Syntex modèles de présentation avec PowerShell.
ms.openlocfilehash: 4aa5639d50145cabe5b95a11d3d927b7d2e06749
ms.sourcegitcommit: dd6514ae173f1c821d4ec25298145df6cb232e2e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2022
ms.locfileid: "62074831"
---
# <a name="publish-document-understanding-models-with-powershell"></a>Publier des modèles de présentation de documents avec PowerShell

> [!IMPORTANT]
> Les SharePoint Syntex PowerShell et tous les autres composants PnP sont des outils open source soutenus par une communauté active qui les aide. Il n’existe aucun contrat de niveau de service pour la prise en charge des outils open source des canaux de support Microsoft officiels.

SharePoint Syntex modèles sont généralement déployés dans des bibliothèques de documents au sein de votre client. Pour ce faire, vous pouvez utiliser le site Centre de contenu, mais également à l’aide de [PowerShell PnP,](https://pnp.github.io/powershell/) comme expliqué dans cet article.

## <a name="listing-the-available-models-in-a-content-center"></a>Liste des modèles disponibles dans un centre de contenu

Pour obtenir une vue d’ensemble des modèles ajoutés au site centre de contenu SharePoint Syntex utilisez la cmdlet [Get-PnPSyntexModel](https://pnp.github.io/powershell/cmdlets/Get-PnPSyntexModel.html) :

```PowerShell
Connect-PnPOnline -Url "https://contoso.sharepoint.com/sites/yourContentCenter"
Get-PnPSyntexModel
```

## <a name="apply-a-model-to-a-library"></a>Appliquer un modèle à une bibliothèque

Pour appliquer un modèle à une bibliothèque, vous pouvez utiliser la cmdlet [Publish-PnPSyntexModel](https://pnp.github.io/powershell/cmdlets/Publish-PnPSyntexModel.html) :

```PowerShell
Connect-PnPOnline -Url "https://contoso.sharepoint.com/sites/yourContentCenter"
Publish-PnPSyntexModel -Model "Contract Notice" -ListWebUrl "https://contoso.sharepoint.com/sites/finance" -List "Documents"
```

## <a name="understanding-where-a-model-is-used"></a>Comprendre où un modèle est utilisé

Une fois que vous avez déployé un modèle dans de nombreuses bibliothèques, vous pouvez consulter la liste des bibliothèques à l’aide de votre modèle. Pour ce faire, vous pouvez utiliser l’cmdlet [Get-PnPSyntexModelPublication](https://pnp.github.io/powershell/cmdlets/Get-PnPSyntexModelPublication.html) :

```PowerShell
Connect-PnPOnline -Url "https://contoso.sharepoint.com/sites/yourContentCenter"
Get-PnPSyntexModelPublication -Identity "Contract Notice"
```

## <a name="removing-a-model-from-a-library"></a>Suppression d’un modèle d’une bibliothèque

La suppression d’un modèle d’une bibliothèque suit le même modèle que l’application et peut être effectuée à l’aide de la cmdlet [Unpublish-PnPSyntexModel](https://pnp.github.io/powershell/cmdlets/Unpublish-PnPSyntexModel.html) de manière interactive ou en tant que lot de plusieurs actions.

```PowerShell
Connect-PnPOnline -Url "https://contoso.sharepoint.com/sites/yourSite"
Unpublish-PnPSyntexModel -Model "Invoice model" -ListWebUrl "https://contoso.sharepoint.com/sites/finance" -List "Documents"
```

## <a name="apply-models-in-bulk"></a>Appliquer des modèles en bloc

Si vous souhaitez publier plusieurs modèles dans plusieurs bibliothèques, 

Tout d’abord, créez un fichier CSV d’entrée répertoriant les modèles et les emplacements cibles :

```CSV
ModelName,TargetSiteUrl,TargetWebServerRelativeUrl,TargetLibraryServerRelativeUrl
Contract Notice,https://contoso.sharepoint.com/sites/Site1,/sites/Site1,/sites/site1/shared%20documents
Contract Notice,https://contoso.sharepoint.com/sites/Site1,/sites/Site1,/sites/site1/other
Trade Confirmation,https://contoso.sharepoint.com/sites/Site2,/sites/Site2,/sites/site2/shared%20documents
```

Ce fichier CSV peut ensuite être utilisé comme entrée dans un script qui publiera les modèles répertoriés dans les bibliothèques appropriées. Dans l’exemple ci-dessous, le traitement par lots est utilisé pour augmenter l’efficacité des demandes.

```PowerShell
$contentCenterURL = "https://contoso.sharepoint.com/sites/yourSite"
$targetsCSV = "./Publish-SyntexModelBulk.csv"

Connect-PnPOnline -url $contentCenterURL

$targetLibraries = Import-Csv -Path $targetsCSV

$batch = New-PnPBatch

foreach ($target in $targetLibraries) {
    Publish-PnPSyntexModel -Model $target.ModelName -TargetSiteUrl $target.TargetSiteUrl -TargetWebServerRelativeUrl $target.TargetWebServerRelativeUrl -TargetLibraryServerRelativeUrl $target.TargetLibraryServerRelativeUrl -Batch $batch
}

Invoke-PnPBatch -Batch $batch
```
