---
title: Modifier un type d’informations sensibles personnalisé à l’aide de PowerShell
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Découvrez comment modifier des informations sensibles personnalisées à l’aide de PowerShell.
ms.openlocfilehash: 9f8a9ef119e632c695113320ab86a3bdfef8a197
ms.sourcegitcommit: b0f464b6300e2977ed51395473a6b2e02b18fc9e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2021
ms.locfileid: "53322697"
---
# <a name="modify-a-custom-sensitive-information-type-using-powershell"></a>Modifier un type d’informations sensibles personnalisé à l’aide de PowerShell

Dans PowerShell du centre de conformité, la modification d’un type d’informations sensibles personnalisé nécessite :

1. Exportez le package de règles existant qui contient le type d’informations sensibles personnalisé dans un fichier XML (ou utilisez le fichier XML existant si vous avez un).

2. Modifier le type d’informations sensibles personnalisé dans un fichier exporté XML.

3. Importer le fichier XML mis à jour vers le package de règles existant.

Pour vous connecter à PowerShell du centre de conformité, consultez [Se connecter à PowerShell du centre de conformité](/powershell/exchange/exchange-online-powershell).

### <a name="step-1-export-the-existing-rule-package-to-an-xml-file"></a>Étape 1 : Exporter le package de règles existant vers un fichier XML

> [!NOTE]
> Si vous avez une copie du fichier XML (par exemple, vous venez de le créer et de l’importer), vous pouvez passer directement à l’étape suivante pour modifier le fichier XML.

1. Si vous ne connaissez pas encore le nom du package de règles personnalisé, exécutez la cmdlet [Get-DlpSensitiveInformationTypeRulePackage](/powershell/module/exchange/get-dlpsensitiveinformationtype) pour le trouver :

   ```powershell
   Get-DlpSensitiveInformationTypeRulePackage
   ```

   > [!NOTE]
   > Le package de règles intégré qui contient les types d’informations sensibles intégrés s’intitule Microsoft Rule Package. Le package de règles qui contient les types d’informations sensibles personnalisés que vous avez créés dans l’interface utilisateur du Centre de conformité est nommé Microsoft.SCCManaged.CustomRulePack.

2. Utilisez la cmdlet [Get-DlpSensitiveInformationTypeRulePackage](/powershell/module/exchange/get-dlpsensitiveinformationtyperulepackage) pour stocker le package de règles personnalisé dans une variable :

   ```powershell
   $rulepak = Get-DlpSensitiveInformationTypeRulePackage -Identity "RulePackageName"
   ```

   Par exemple, si le nom du package de règles est « Package de règles personnalisé d’ID d’employé », exécutez la cmdlet suivante :

   ```powershell
   $rulepak = Get-DlpSensitiveInformationTypeRulePackage -Identity "Employee ID Custom Rule Pack"
   ```

3. Utilisez la cmdlet [Set-Content](/powershell/module/microsoft.powershell.management/set-content) pour exporter le package de règles personnalisé dans un fichier XML :

   ```powershell
   Set-Content -Path "XMLFileAndPath" -Encoding Byte -Value $rulepak.SerializedClassificationRuleCollection
   ```

   Cet exemple exporte le package de règles dans le fichier nommé ExportedRulePackage.xml dans le dossier Documents C:\My Documents folder.

   ```powershell
   Set-Content -Path "C:\My Documents\ExportedRulePackage.xml" -Encoding Byte -Value $rulepak.SerializedClassificationRuleCollection
   ```

#### <a name="step-2-modify-the-sensitive-information-type-in-the-exported-xml-file"></a>Étape 2: Modifier le type d’informations sensibles personnalisé dans un fichier exporté XML.

Les types d’informations sensibles dans le fichier XML et d’autres éléments dans le fichier sont décrits précédemment dans cette rubrique.

#### <a name="step-3-import-the-updated-xml-file-back-into-the-existing-rule-package"></a>Étape 3: Importer de nouveau le fichier XML mis à jour vers le package de règles existant.

Pour réimporter le XML mis à jour dans le package de règles existant, utilisez la cmdlet [Set-DlpSensitiveInformationTypeRulePackage](/powershell/module/exchange/set-dlpsensitiveinformationtyperulepackage) :

```powershell
Set-DlpSensitiveInformationTypeRulePackage -FileData ([Byte[]]$(Get-Content -Path "C:\My Documents\External Sensitive Info Type Rule Collection.xml" -Encoding Byte -ReadCount 0))
```

Pour une syntaxe détaillée et des informations de paramétrage, voir [Set-DlpSensitiveInformationTypeRulePackage](/powershell/module/exchange/set-dlpsensitiveinformationtyperulepackage).


## <a name="more-information"></a>Plus d’informations

- [En savoir plus sur la protection contre la perte de données](dlp-learn-about-dlp.md)

- [Définitions d’entités des types d’informations sensibles](sensitive-information-type-entity-definitions.md)

- [Éléments recherchés par les fonctions DLP](what-the-dlp-functions-look-for.md)
