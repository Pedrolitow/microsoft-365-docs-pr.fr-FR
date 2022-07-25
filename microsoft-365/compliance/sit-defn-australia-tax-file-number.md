---
title: Définition de l’entité numéro de fichier fiscal australien
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: Admin
search.appverid: MET150
ms.topic: reference
f1_keywords:
- ms.o365.cc.UnifiedDLPRuleContainsSensitiveInformation
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
hideEdit: true
feedback_system: None
recommendations: false
description: Définition d’entité de type d’entité du numéro de fichier fiscal australien.
ms.openlocfilehash: 155bdbd2142d0c6c097907b0ab651ff74cfac46d
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2022
ms.locfileid: "66997249"
---
# <a name="australia-tax-file-number"></a>Numéro de dossier fiscal Australie

## <a name="format"></a>Format

huit à neuf chiffres

## <a name="pattern"></a>Modèle

Huit à neuf chiffres sont généralement présentés avec des espaces comme suit :

- trois chiffres
- un espace facultatif
- trois chiffres
- un espace facultatif
- deux à trois chiffres où le dernier chiffre est un chiffre à cocher

## <a name="checksum"></a>Somme de contrôle

Oui

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction Func_australian_tax_file_number trouve un contenu qui correspond au modèle.
- Aucun mot clé figurant dans la liste Keyword_Australia_Tax_File_Number ou Keyword_number_exclusions n’est trouvé.
- La somme de contrôle est correcte.

```xml
   <!-- Australia Tax File Number -->
    <Entity id="e29bc95f-ff70-4a37-aa01-04d17360a4c5" patternsProximity="300" recommendedConfidence="85">
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_australian_tax_file_number" />
        <Match idRef="Keyword_Australia_Tax_File_Number" />
      </Pattern>
    </Entity>
```

## <a name="keywords"></a>Mots-clés

### <a name="keyword_australia_tax_file_number"></a>Keyword_australia_tax_file_number

- numéro d’entreprise australien
- taux d’imposition marginale
- prélèvement d’assurance maladie
- numéro de portefeuille
- service des vétérans
- retenue à la source
- déclaration d’impôts individuels
- numéro de dossier fiscal
- Tfn
