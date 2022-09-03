---
title: Exporter et importer des modèles de compréhension de document avec PowerShell
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
description: Découvrez comment exporter et importer des modèles de compréhension de document avec PowerShell dans SharePoint Syntex.
ms.openlocfilehash: a022ee3be11470892cc62dda06173e83ee50f865
ms.sourcegitcommit: d3ef9391f621e8f4ca70661184b3bb82c6cbda94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2022
ms.locfileid: "67585221"
---
# <a name="export-and-import-document-understanding-models-with-powershell"></a>Exporter et importer des modèles de compréhension de document avec PowerShell

> [!IMPORTANT]
> Les applets de commande PowerShell SharePoint Syntex et tous les autres composants PnP sont des outils open source soutenus par une communauté active qui les prend en charge. Il n’existe aucun contrat de niveau de service pour la prise en charge des outils open source des canaux de support Microsoft officiels.

SharePoint Syntex modèles peuvent être exportés en tant que modèles PnP, ce qui permet une réutilisation entre les centres de contenu ou les locataires.

## <a name="export-all-models-in-a-content-center"></a>Exporter tous les modèles dans un centre de contenu

Pour exporter tous les modèles d’un centre de contenu dans un modèle PnP unique, utilisez les applets de commande [PowerShell PnP](https://pnp.github.io/powershell/) suivantes :

```powershell
Connect-PnPOnline -Url "https://contoso.sharepoint.com/sites/yourContentCenter"

Get-PnPSiteTemplate -Out MyModels.pnp -Handlers SyntexModels
```

## <a name="export-specific-models"></a>Exporter des modèles spécifiques

Pour exporter des modèles spécifiques à partir d’un centre de contenu dans un modèle PnP, utilisez les applets de commande [PowerShell PnP](https://pnp.github.io/powershell/) suivantes :

```powershell
Connect-PnPOnline -Url "https://contoso.sharepoint.com/sites/yourContentCenter"

Get-PnPSiteTemplate -Out MyModels.pnp -Configuration .\extract.json
```

Extract.json définit les modèles que vous souhaitez exporter, ce qui permet de spécifier le modèle par nom ou ID et éventuellement en configurant pour ne pas extraire les données d’entraînement.

### <a name="example---specify-model-by-name"></a>Exemple - Spécifier le modèle par nom

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

### <a name="example---specify-model-by-id"></a>Exemple - Spécifier le modèle par ID

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

Si vous n’incluez pas la propriété « includeTrainingData », le comportement par défaut est d’inclure.

> [!NOTE]
> Des données d’entraînement sont nécessaires pour qu’un modèle soit modifiable lors de l’importation dans un centre de contenu de destination.

## <a name="import-models-to-a-content-center"></a>Importer des modèles dans un centre de contenu
Les modèles de compréhension de document qui ont été exportés vers des modèles PnP peuvent être importés dans un centre de contenu sur n’importe quel locataire. Si l’exportation incluait des données d’apprentissage, le modèle sera modifiable une fois importé.

Pour importer un modèle, utilisez les commandes suivantes :

```PowerShell
Connect-PnPOnline -Url "https://contoso.sharepoint.com/sites/yourContentCenter"

Invoke-PnPSiteTemplate -Path .\sampleModel.pnp
```
