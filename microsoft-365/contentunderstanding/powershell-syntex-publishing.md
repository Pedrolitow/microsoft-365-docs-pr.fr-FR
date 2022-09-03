---
title: Publier des modèles de compréhension de document avec PowerShell
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
description: Découvrez comment publier un document SharePoint Syntex comprendre des modèles avec PowerShell.
ms.openlocfilehash: 20c100473207d246f7f1d3b8d9a1f52063c418e0
ms.sourcegitcommit: d3ef9391f621e8f4ca70661184b3bb82c6cbda94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2022
ms.locfileid: "67585793"
---
# <a name="publish-document-understanding-models-with-powershell"></a>Publier des modèles de compréhension de document avec PowerShell

> [!IMPORTANT]
> Les applets de commande PowerShell SharePoint Syntex et tous les autres composants PnP sont des outils open source soutenus par une communauté active qui les prend en charge. Il n’existe aucun contrat de niveau de service pour la prise en charge des outils open source des canaux de support Microsoft officiels.

SharePoint Syntex modèles sont généralement déployés sur des bibliothèques de documents dans votre locataire. Pour ce faire, vous pouvez utiliser le site du centre de contenu, mais cela peut également être fait à l’aide de [PnP PowerShell](https://pnp.github.io/powershell/) , comme expliqué dans cet article.

## <a name="listing-the-available-models-in-a-content-center"></a>Liste des modèles disponibles dans un centre de contenu

Pour obtenir une vue d’ensemble des modèles ajoutés au site actuel du centre de contenu SharePoint Syntex, utilisez l’applet [de commande Get-PnPSyntexModel](https://pnp.github.io/powershell/cmdlets/Get-PnPSyntexModel.html) :

```PowerShell
Connect-PnPOnline -Url "https://contoso.sharepoint.com/sites/yourContentCenter"
Get-PnPSyntexModel
```

## <a name="apply-a-model-to-a-library"></a>Appliquer un modèle à une bibliothèque

Pour appliquer un modèle à une bibliothèque, utilisez l’applet [de commande Publish-PnPSyntexModel](https://pnp.github.io/powershell/cmdlets/Publish-PnPSyntexModel.html) :

```PowerShell
Connect-PnPOnline -Url "https://contoso.sharepoint.com/sites/yourContentCenter"
Publish-PnPSyntexModel -Model "Contract Notice" -ListWebUrl "https://contoso.sharepoint.com/sites/finance" -List "Documents"
```

## <a name="understanding-where-a-model-is-used"></a>Comprendre où un modèle est utilisé

Une fois que vous avez déployé un modèle dans de nombreuses bibliothèques, vous pouvez consulter la liste des bibliothèques à l’aide de votre modèle. Pour ce faire, utilisez l’applet de commande [Get-PnPSyntexModelPublication](https://pnp.github.io/powershell/cmdlets/Get-PnPSyntexModelPublication.html) :

```PowerShell
Connect-PnPOnline -Url "https://contoso.sharepoint.com/sites/yourContentCenter"
Get-PnPSyntexModelPublication -Identity "Contract Notice"
```

## <a name="removing-a-model-from-a-library"></a>Suppression d’un modèle d’une bibliothèque

La suppression d’un modèle d’une bibliothèque suit le même modèle que l’application et peut être effectuée à l’aide de l’applet de commande [Unpublish-PnPSyntexModel](https://pnp.github.io/powershell/cmdlets/Unpublish-PnPSyntexModel.html) de manière interactive ou en tant que lot de plusieurs actions.

```PowerShell
Connect-PnPOnline -Url "https://contoso.sharepoint.com/sites/yourSite"
Unpublish-PnPSyntexModel -Model "Invoice model" -ListWebUrl "https://contoso.sharepoint.com/sites/finance" -List "Documents"
```

## <a name="apply-models-in-bulk"></a>Appliquer des modèles en bloc

Si vous souhaitez publier plusieurs modèles dans plusieurs bibliothèques, créez un fichier CSV d’entrée répertoriant les modèles et les emplacements cibles :

```CSV
ModelName,TargetSiteUrl,TargetWebServerRelativeUrl,TargetLibraryServerRelativeUrl
Contract Notice,https://contoso.sharepoint.com/sites/Site1,/sites/Site1,/sites/site1/shared%20documents
Contract Notice,https://contoso.sharepoint.com/sites/Site1,/sites/Site1,/sites/site1/other
Trade Confirmation,https://contoso.sharepoint.com/sites/Site2,/sites/Site2,/sites/site2/shared%20documents
```

Ce fichier CSV peut ensuite être utilisé comme entrée dans un script qui publiera les modèles répertoriés dans les bibliothèques appropriées. Dans l’exemple suivant, le traitement par lot est utilisé pour augmenter l’efficacité des requêtes.

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
