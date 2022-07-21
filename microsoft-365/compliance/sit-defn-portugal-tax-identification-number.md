---
title: Définition de l’entité numéro d’identification fiscale du Portugal
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
description: Portugal tax identification number sensitive information type entity definition.
ms.openlocfilehash: edb9197a7fa708452476fb2100748664623b4e88
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2022
ms.locfileid: "66950622"
---
# <a name="portugal-tax-identification-number"></a>Numéro d’identification fiscale du Portugal

## <a name="format"></a>Format

neuf chiffres avec des espaces facultatifs

## <a name="pattern"></a>Modèle

- trois chiffres
- un espace facultatif
- trois chiffres
- un espace facultatif
- trois chiffres

## <a name="checksum"></a>Somme de contrôle

Oui

## <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction `Func_portugal_eu_tax_file_number` recherche le contenu qui correspond au modèle.
- Un mot clé est `Keywords_portugal_eu_tax_file_number` trouvé.

Une stratégie DLP a une faible confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction `Func_portugal_eu_tax_file_number` recherche le contenu qui correspond au modèle.

```xml
      <!-- Portugal Tax Identification Number -->
      <Entity id="65372402-3131-4f1e-9983-4439841d1f15" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_portugal_eu_tax_file_number" />
          <Match idRef="Keywords_portugal_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Func_portugal_eu_tax_file_number" />
        </Pattern>
      </Entity>
```

## <a name="keywords"></a>Mots-clés

### <a name="keywords_portugal_eu_tax_file_number"></a>Keywords_portugal_eu_tax_file_number

- Cpf #
- Cpf
- Nif #
- Nif
- número de identificação fisca
- nombreuses
- id fiscal
- identification fiscale non
- numéro d’identification fiscale
- tax no #
- tax no
- numéro d’impôt
- numéro d’enregistrement fiscal
- taxid #
- taxidno #
- taxidnumber #
- taxno #
- taxnumber #
- taxnumber
- iD d’tin
- tin no
- Étain #