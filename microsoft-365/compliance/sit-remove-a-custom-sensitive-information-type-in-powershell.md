---
title: Supprimer un type d’informations sensibles personnalisé à l’aide de PowerShell
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
description: Découvrez comment supprimer un type d’informations sensibles personnalisé à l’aide de PowerShell
ms.openlocfilehash: ba29c2f20133b94d87c14f527d454980c41373c9
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66621686"
---
# <a name="remove-a-custom-sensitive-information-type-using-powershell"></a>Supprimer un type d’informations sensibles personnalisé à l’aide de PowerShell

Dans Security & Compliance PowerShell, il existe deux méthodes pour supprimer les types d’informations sensibles personnalisés :

- **Supprimer des types d’informations sensibles personnalisés individuels** : utilisez la méthode décrite dans [Modifier un type d’informations sensibles personnalisé à l’aide de PowerShell](sit-modify-a-custom-sensitive-information-type-in-powershell.md#modify-a-custom-sensitive-information-type-using-powershell). Vous exportez le package de règles personnalisées qui contient le type d’informations sensibles personnalisé, supprimez le type d’informations sensibles du fichier XML et réimportez le fichier XML mis à jour dans le package de règles personnalisé existant.

- **Supprimer un package de règles personnalisé et tous les types d’informations sensibles personnalisés qu’il contient**: cette méthode est présentée dans cette section.

> [!NOTE]
> Avant de supprimer un type d’informations sensibles personnalisé, vérifiez qu’aucune stratégie DLP ou règle de flux de courrier Exchange (également appelées règles de transport) ne référence toujours le type d’informations sensibles.

1. [Sécurité & Conformité PowerShell](/powershell/exchange/exchange-online-powershell)

2. Pour supprimer un règle de package personnalisé, utilisez la cmdlet [Remove-DlpSensitiveInformationTypeRulePackage](/powershell/module/exchange/remove-dlpsensitiveinformationtyperulepackage) :

   ```powershell
   Remove-DlpSensitiveInformationTypeRulePackage -Identity "RulePackageIdentity"
   ```

   Vous pouvez utiliser la valeur Nom (pour n’importe quelle langue) ou la`RulePack id` valeur (GUID) pour identifier le package de règles.

   Cet exemple supprime le package de règles nommé « Package règle personnalisé employé ID ».

   ```powershell
   Remove-DlpSensitiveInformationTypeRulePackage -Identity "Employee ID Custom Rule Pack"
   ```

   Pour une syntaxe détaillée et des informations de paramétrage, voir [Remove-DlpSensitiveInformationTypeRulePackage](/powershell/module/exchange/remove-dlpsensitiveinformationtyperulepackage).

3. Afin de vérifier que vous avez correctement retiré un nouveau type d’informations sensibles, effectuez l’une des opérations suivantes :

   - Exécutez la cmdlet [Get-DlpSensitiveInformationTypeRulePackage](/powershell/module/exchange/get-dlpsensitiveinformationtyperulepackage) et vérifiez que le package de règles n’est plus répertorié :

     ```powershell
     Get-DlpSensitiveInformationTypeRulePackage
     ```

   - Exécutez la cmdlet [Get-DlpSensitiveInformationType](/powershell/module/exchange/get-dlpsensitiveinformationtype) pour vérifier que les types d’informations sensibles dans le package de règles supprimé ne sont plus répertoriés :

     ```powershell
     Get-DlpSensitiveInformationType
     ```

     Pour les types d’informations sensibles personnalisés, la valeur de propriété Publisher sera un numéro autre que Microsoft Corporation.

   - Remplacez \<Name\> avec la valeur Name du type d’informations sensibles (par exemple, ID d’employé), puis exécutez la cmdlet [Get-DlpSensitiveInformationType](/powershell/module/exchange/get-dlpsensitiveinformationtype) pour vérifier que le type d’informations sensibles n’est plus répertorié :

     ```powershell
     Get-DlpSensitiveInformationType -Identity "<Name>"
     ```

## <a name="more-information"></a>Plus d’informations

- [En savoir plus sur la protection contre la perte de données Microsoft Purview](dlp-learn-about-dlp.md)

- [Définitions d’entités des types d’informations sensibles](sensitive-information-type-entity-definitions.md)

- [Fonctions de type d’informations sensibles](sit-functions.md)
