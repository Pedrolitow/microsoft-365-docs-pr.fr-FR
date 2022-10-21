---
title: Exporter et importer des modèles de traitement de documents non structurés avec PowerShell
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
description: Découvrez comment exporter et importer des modèles avec PowerShell dans Microsoft Syntex.
ms.openlocfilehash: 975a4f463d80c273f31912c30c70c5e7c07fd6c9
ms.sourcegitcommit: 87283bb02ca750286f7c069f811b788730ed5832
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2022
ms.locfileid: "68662092"
---
# <a name="export-and-import-unstructured-document-processing-models-with-powershell"></a>Exporter et importer des modèles de traitement de documents non structurés avec PowerShell

<sup>**S’applique à :**  &ensp; &#10003; traitement de documents non structurés</sup>

> [!IMPORTANT]
> Les applets de commande Microsoft Syntex PowerShell et tous les autres composants PnP sont des outils open source soutenus par une communauté active qui les prend en charge. Il n’existe aucun contrat de niveau de service pour la prise en charge des outils open source des canaux de support Microsoft officiels.

Les modèles Syntex peuvent être exportés en tant que modèles PnP, ce qui permet une réutilisation dans des centres de contenu ou des locataires.

## <a name="export-all-models-in-a-content-center"></a>Exporter tous les modèles dans un centre de contenu

Pour exporter tous les modèles de traitement de documents non structurés dans un centre de contenu dans un seul modèle PnP, utilisez les applets de commande [PowerShell PnP](https://pnp.github.io/powershell/) suivantes :

```powershell
Connect-PnPOnline -Url "https://contoso.sharepoint.com/sites/yourContentCenter"

Get-PnPSiteTemplate -Out MyModels.pnp -Handlers SyntexModels
```

## <a name="export-specific-models"></a>Exporter des modèles spécifiques

Pour exporter des modèles de traitement de documents non structurés spécifiques à partir d’un centre de contenu vers un modèle PnP, utilisez les applets de commande [PowerShell PnP](https://pnp.github.io/powershell/) suivantes :

```powershell
Connect-PnPOnline -Url "https://contoso.sharepoint.com/sites/yourContentCenter"

Get-PnPSiteTemplate -Out MyModels.pnp -Configuration .\extract.json
```

Le fichier extract.json définit les modèles que vous souhaitez exporter, ce qui permet de spécifier le modèle par nom ou ID et éventuellement de configurer pour ne pas extraire les données d’apprentissage.

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
> Les données d’entraînement sont requises pour qu’un modèle puisse être modifié lorsqu’il est importé dans un centre de contenu de destination.

## <a name="import-models-to-a-content-center"></a>Importer des modèles dans un centre de contenu

Les modèles de traitement de documents non structurés qui ont été exportés vers des modèles PnP peuvent être importés dans un centre de contenu sur n’importe quel locataire. Si l’exportation incluait des données d’entraînement, le modèle sera modifiable une fois importé.

Pour importer un modèle, utilisez les commandes suivantes :

```PowerShell
Connect-PnPOnline -Url "https://contoso.sharepoint.com/sites/yourContentCenter"

Invoke-PnPSiteTemplate -Path .\sampleModel.pnp
```
