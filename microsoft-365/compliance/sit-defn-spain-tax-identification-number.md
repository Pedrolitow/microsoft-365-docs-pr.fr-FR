---
title: Définition de l’entité numéro d’identification fiscale en Espagne
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
description: Définition d’entité de type d’entité de type d’informations sensibles numéro d’identification fiscale en Espagne.
ms.openlocfilehash: 096a76e011f3ffb19fbe21e268b79023c4153bf6
ms.sourcegitcommit: 176bbd29c92e1c0812e8bcd1e1e4938a3e1d7331
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/05/2022
ms.locfileid: "68472407"
---
# <a name="spain-tax-identification-number"></a>Numéro d’identifiant fiscal espagnol

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="format"></a>Format

sept ou huit chiffres et une ou deux lettres dans le modèle spécifié

## <a name="pattern"></a>Modèle

Personnes physiques espagnoles avec une carte d’identité nationale d’Espagne :

- huit chiffres
- une lettre majuscule (respect de la casse)

Espagnols non résidents sans carte d’identité nationale d’Espagne

- une lettre majuscule « L » (respect de la casse)
- sept chiffres
- une lettre majuscule (respect de la casse)

Résidents espagnols âgés de moins de 14 ans sans carte d’identité nationale d’Espagne :

- une lettre majuscule « K » (respect de la casse)
- sept chiffres
- une lettre majuscule (respect de la casse)

Étrangers avec le numéro d’identification d’un étranger

- une lettre majuscule qui est « X », « Y » ou « Z » (respectant la casse)
- sept chiffres
- une lettre majuscule (respect de la casse)

Étrangers sans numéro d’identification d’étranger

- une lettre majuscule qui est « M » (respect de la casse)
- sept chiffres
- une lettre majuscule (respect de la casse)

## <a name="checksum"></a>Somme de contrôle

Oui

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_spain_eu_tax_file_number` ou `Func_spain_eu_DL_and_NI_number_citizen` trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keywords_spain_eu_tax_file_number` est trouvé.

Une stratégie DLP a une confiance moyenne ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_spain_eu_tax_file_number` ou `Func_spain_eu_DL_and_NI_number_citizen` trouve un contenu qui correspond au modèle.

```xml
      <!-- Spain Tax Identification Number -->
      <Entity id="10f0d113-b0e1-47dc-872a-a4f45b9376a3" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_spain_eu_tax_file_number" />
          <Match idRef="Keywords_spain_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_spain_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_spain_eu_DL_and_NI_number_citizen" />
          <Match idRef="Keywords_spain_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_spain_eu_DL_and_NI_number_citizen" />
        </Pattern>
      </Entity>
```

## <a name="keywords"></a>Mots-clés

### <a name="keywords_spain_eu_tax_file_number"></a>Keywords_spain_eu_tax_file_number

- Caf
- cifid #
- cifnúmero #
- número de contribuyente
- número de identificación fiscal
- número de impuesto corporativo
- spanishcifid #
- spanishcifid
- spanishcifno #
- spanishcifno
- fichier fiscal no
- numéro de dossier fiscal
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
