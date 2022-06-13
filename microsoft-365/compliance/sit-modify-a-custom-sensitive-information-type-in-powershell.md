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
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Découvrez comment modifier des informations sensibles personnalisées à l’aide de PowerShell.
ms.openlocfilehash: deb50679702cec69187392337511b4dde2d1ceb3
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/10/2022
ms.locfileid: "66014385"
---
# <a name="modify-a-custom-sensitive-information-type-using-powershell"></a>Modifier un type d’informations sensibles personnalisé à l’aide de PowerShell

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Dans Security & Compliance PowerShell, la modification d’un type d’informations sensibles personnalisé vous oblige à :

1. Exportez le package de règles existant qui contient le type d’informations sensibles personnalisé dans un fichier XML (ou utilisez le fichier XML existant si vous avez un).

2. Modifier le type d’informations sensibles personnalisé dans un fichier exporté XML.

3. Importer le fichier XML mis à jour vers le package de règles existant.

Pour vous connecter à Security & Compliance PowerShell, consultez [Security & Compliance PowerShell](/powershell/exchange/exchange-online-powershell).

## <a name="step-1-export-the-existing-rule-package-to-an-xml-file"></a>Étape 1 : Exporter le package de règles existant vers un fichier XML

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

3. Utilisez la syntaxe suivante afin d’exporter le package de règles personnalisé vers un fichier XML:

   ```powershell
   [System.IO.File]::WriteAllBytes('XMLFileAndPath', $rulepak.SerializedClassificationRuleCollection)
   ```

   Cet exemple exporte le package de règles dans le fichier nommé ExportedRulePackage.xml dans le dossier C:\Mes documents.

   ```powershell
   [System.IO.File]::WriteAllBytes('C:\My Documents\ExportedRulePackage.xml', $rulepak.SerializedClassificationRuleCollection)
   ```

## <a name="step-2-modify-the-sensitive-information-type-in-the-exported-xml-file"></a>Étape 2: Modifier le type d’informations sensibles personnalisé dans un fichier exporté XML.

Les types d’informations sensibles dans le fichier XML et d’autres éléments dans le fichier sont décrits précédemment dans cette rubrique.

## <a name="step-3-import-the-updated-xml-file-back-into-the-existing-rule-package"></a>Étape 3: Importer de nouveau le fichier XML mis à jour vers le package de règles existant.

Pour réimporter le XML mis à jour dans le package de règles existant, utilisez la cmdlet [Set-DlpSensitiveInformationTypeRulePackage](/powershell/module/exchange/set-dlpsensitiveinformationtyperulepackage) :

```powershell
Set-DlpSensitiveInformationTypeRulePackage -FileData ([System.IO.File]::ReadAllBytes('C:\My Documents\External Sensitive Info Type Rule Collection.xml'))
```

Pour une syntaxe détaillée et des informations de paramétrage, voir [Set-DlpSensitiveInformationTypeRulePackage](/powershell/module/exchange/set-dlpsensitiveinformationtyperulepackage).

## <a name="more-information"></a>Plus d’informations

- [En savoir plus sur la protection contre la perte de données Microsoft Purview](dlp-learn-about-dlp.md)
- [Définitions d’entités des types d’informations sensibles](sensitive-information-type-entity-definitions.md)
- [Fonctions de type d’informations sensibles](sit-functions.md)
