---
title: Définition de l’entité numéro d’identification fiscale de Malte
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
description: Malta tax identification number sensitive information type entity definition.
ms.openlocfilehash: 5f77f6755ff69bf200a3999e684901bf39bdf6d9
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2022
ms.locfileid: "66996220"
---
# <a name="malta-tax-identification-number"></a>Numéro d’identification fiscale de l’Île-de-France

## <a name="format"></a>Format

Pour les ressortissants maltais :

- sept chiffres et une lettre dans le modèle spécifié

Ressortissants non maltais et entités maltaises :

- neuf chiffres

## <a name="pattern"></a>Modèle

Ressortissants maltais : sept chiffres et une lettre

- sept chiffres
- une lettre (non sensible à la casse)

Ressortissants non maltais et entités maltaises : neuf chiffres

- neuf chiffres

## <a name="checksum"></a>Somme de contrôle

Non applicable

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- L’expression `Regex_malta_eu_tax_file_number`  régulière ou `Regex_malta_eu_tax_file_number_non_maltese_national` recherche du contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keywords_malta_eu_tax_file_number` est trouvé.

Une stratégie DLP a une confiance faible ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- L’expression `Regex_malta_eu_tax_file_number` régulière ou `Regex_malta_eu_tax_file_number_non_maltese_national` recherche du contenu qui correspond au modèle.

```xml
      <!-- Malta Tax ID Number -->
      <Entity id="ec830c63-65f4-45d0-9d8c-910dc8334b20" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_malta_eu_tax_file_number" />
          <Match idRef="Keywords_malta_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Regex_malta_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_malta_eu_tax_file_number_non_maltese_national" />
          <Match idRef="Keywords_malta_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Regex_malta_eu_tax_file_number_non_maltese_national" />
        </Pattern>
      </Entity>
```

## <a name="keywords"></a>Mots-clés

### <a name="keywords_malta_eu_tax_file_number"></a>Keywords_malta_eu_tax_file_number

- numéro de service citoyen
- id tat-taxxa
- identifika numru tal-biljett
- kodiċi numerali personali
- numru ta 'identifikazzjoni personali
- numru ta 'identifikazzjoni tat-taxxa
- numru ta 'identifikazzjoni uniku
- numru ta' identità uniku
- numru tas-servizz taċ-ċittadin
- numru tat-taxxa
- code numérique personnel
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
- numéro d’identification unique
- numéro d’identité unique
- uniqueidentityno #