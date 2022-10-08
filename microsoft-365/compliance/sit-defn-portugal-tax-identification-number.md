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
- tier3
- purview-compliance
hideEdit: true
feedback_system: None
recommendations: false
description: Portugal tax identification number sensitive information type entity definition.
ms.openlocfilehash: 550c82b4b1b58d16e6a8701bf5155a0b99987259
ms.sourcegitcommit: 176bbd29c92e1c0812e8bcd1e1e4938a3e1d7331
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/05/2022
ms.locfileid: "68470415"
---
# <a name="portugal-tax-identification-number"></a>Numéro d’identification fiscale portugais

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

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

Une stratégie DLP a une confiance élevée ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_portugal_eu_tax_file_number` trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keywords_portugal_eu_tax_file_number` est trouvé.

Une stratégie DLP a une confiance faible ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_portugal_eu_tax_file_number` trouve un contenu qui correspond au modèle.

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
- n#if
- nif
- número de identificação fisca
- nombreuses
- id fiscal
- numéro d’identification fiscal
- numéro d’identification fiscal
- taxe nº#
- nº fiscal
- numéro de contribuable
- numéro d’identification fiscale
- taxid#
- taxidno#
- taxidnumber#
- taxno#
- taxnumber#
- taxnumber
- id de tin
- nº de tin
- tin#
