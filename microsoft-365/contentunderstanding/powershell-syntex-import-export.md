---
title: Exporter et importer des modèles de présentation de documents avec PowerShell
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
description: Découvrez comment exporter et importer des modèles de présentation de documents avec PowerShell dans SharePoint Syntex
ms.openlocfilehash: 289d802fdea50daa0261ec16ea760e9a57b0e9c5
ms.sourcegitcommit: dd6514ae173f1c821d4ec25298145df6cb232e2e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2022
ms.locfileid: "62074851"
---
# <a name="export-and-import-document-understanding-models-with-powershell"></a>Exporter et importer des modèles de présentation de documents avec PowerShell

> [!IMPORTANT]
> Les SharePoint Syntex PowerShell et tous les autres composants PnP sont des outils open source soutenus par une communauté active qui les aide. Il n’existe aucun contrat de niveau de service pour la prise en charge des outils open source des canaux de support Microsoft officiels.

SharePoint Syntex modèles peuvent être exportés en tant que modèles PnP, ce qui permet une réutilisation entre les centres de contenu ou les clients.

## <a name="export-all-models-in-a-content-center"></a>Exporter tous les modèles dans un centre de contenu

Pour exporter tous les modèles d’un centre de contenu dans un modèle PnP unique, utilisez les cmdlets [PowerShell PnP](https://pnp.github.io/powershell/) suivantes :

```powershell
Connect-PnPOnline -Url "https://contoso.sharepoint.com/sites/yourContentCenter"

Get-PnPSiteTemplate -Out MyModels.pnp -Handlers SyntexModels
```

## <a name="export-specific-models"></a>Exporter des modèles spécifiques

Pour exporter des modèles spécifiques d’un centre de contenu vers un modèle PnP, utilisez les cmdlets [PowerShell PnP](https://pnp.github.io/powershell/) suivantes :

```powershell
Connect-PnPOnline -Url "https://contoso.sharepoint.com/sites/yourContentCenter"

Get-PnPSiteTemplate -Out MyModels.pnp -Configuration .\extract.json
```

L’extract.json définit les modèles que vous souhaitez exporter, ce qui permet de spécifier le modèle par nom ou ID et éventuellement configurer pour ne pas extraire les données de formation

### <a name="example--specify-model-by-name"></a>Exemple : spécifier le modèle par nom

```json
{
    "$schema": "https://developer.microsoft.com/en-us/json-schemas/pnp/provisioning/202102/extract-configuration.schema.json",
    "persistAssetFiles": true,
    "handlers": [        
        "SyntexModels"
    ],
    "syntexModels": {
        "models": [
            {
                "name": "Sample - benefits change notice.classifier"
            }
        ]
    }
}
```

### <a name="example--specify-model-by-id"></a>Exemple : spécifier le modèle par ID

```json
{
    "$schema": "https://developer.microsoft.com/en-us/json-schemas/pnp/provisioning/202102/extract-configuration.schema.json",
    "persistAssetFiles": true,
    "handlers": [        
        "SyntexModels"
    ],
    "syntexModels": {
        "models": [
            {
                "id": 3,
                "excludeTrainingData": true
            }
        ]
    }
}
```

Si vous n’incluez pas la propriété « includeTrainingData », le comportement par défaut est à inclure.

> REMARQUE : les données de formation sont requises pour qu’un modèle soit modifiable lorsqu’il est importé dans un centre de contenu de destination

## <a name="import-models-to-a-content-center"></a>Importer des modèles dans un centre de contenu
Document understanding models that have been exported to PnP templates can be imported to a content center on any tenant. Si l’exportation inclut des données de formation, le modèle est modifiable une fois importé.

Pour importer un modèle, utilisez les commandes suivantes :

```PowerShell
Connect-PnPOnline -Url "https://contoso.sharepoint.com/sites/yourContentCenter"

Invoke-PnPSiteTemplate -Path .\sampleModel.pnp
```
