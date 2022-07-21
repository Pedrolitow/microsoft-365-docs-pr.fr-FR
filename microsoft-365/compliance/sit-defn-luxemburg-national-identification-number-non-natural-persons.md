---
title: Définition d’entité du numéro d’identification national du Luxembourg (personnes non naturelles)
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
description: Définition d’entité de type d’information sensible du numéro d’identification national de Luxemburg (personnes non naturelles).
ms.openlocfilehash: 0e5a82862c51aafcc6d3033fccb1a8ec1b561671
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2022
ms.locfileid: "66950838"
---
# <a name="luxemburg-national-identification-number-non-natural-persons"></a>Numéro d’identification national du Luxembourg (personnes non naturelles)

## <a name="format"></a>Format

11 chiffres

## <a name="pattern"></a>Modèle

11 chiffres

- deux chiffres
- un espace facultatif
- trois chiffres
- un espace facultatif
- trois chiffres
- un espace facultatif
- deux chiffres
- un chiffre de vérification

## <a name="checksum"></a>Somme de contrôle

Oui

## <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction `Func_luxemburg_eu_tax_file_number_non_natural` recherche le contenu qui correspond au modèle.
- Un mot clé est `Keywords_luxemburg_eu_tax_file_number` trouvé.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction `Func_luxemburg_eu_tax_file_number_non_natural` recherche le contenu qui correspond au modèle.

```xml
      <!-- Luxemburg National Identification Number (Non-natural persons) -->
      <Entity id="84bffa3a-d805-4788-a613-b1e4df3804cf" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_luxemburg_eu_tax_file_number_non_natural" />
          <Match idRef="Keywords_luxemburg_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_luxemburg_eu_tax_file_number_non_natural" />
          <Any minMatches="0" maxMatches="0">
            <Match idRef="Keywords_luxemburg_eu_telephone_number" />
            <Match idRef="Keywords_luxemburg_eu_mobile_number" />
          </Any>
        </Pattern>
      </Entity>
```

## <a name="keywords"></a>Mots-clés

### <a name="keywords_luxemburg_eu_tax_file_number"></a>Keywords_luxemburg_eu_tax_file_number

- carte de sécurité sociale
- non resserr
- resserr #
- identifiant d’impôt
- luxembourg tax identifikatiounsnummer
- numéro d’resser
- numéro d’identification fiscal luxembourgeois
- numéro d’identification fiscale
- sécurité sociale
- sozialunterstützung
- sozialversécherung
- sozialversicherungsausweis
- steier id
- steier identifikatiounsnummer
- steier nummer
- steuer id
- steueridentifikationsnummer
- steuernummer
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
- Zinn #
- Zinn
- zinnzahl