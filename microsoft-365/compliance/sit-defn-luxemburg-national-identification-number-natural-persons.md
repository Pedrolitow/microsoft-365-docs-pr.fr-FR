---
title: Définition d’entité du numéro d’identification national de Luxembourg (personnes physiques)
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
description: Définition d’entité de type d’information sensible du numéro d’identification national de Luxemburg (personnes physiques).
ms.openlocfilehash: b6f718c25e79a6a59f30135e579c55d17ab06a2d
ms.sourcegitcommit: 6df492719fecc2b213d55465dc1cd60ab4627ed6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2022
ms.locfileid: "68381938"
---
# <a name="luxemburg-national-identification-number-natural-persons"></a>Numéro national d’identité luxembourgeois (personnes physiques)

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="format"></a>Format

13 chiffres sans espaces ni délimiteurs

## <a name="pattern"></a>Modèle

13 chiffres :

- 11 chiffres
- deux chiffres de contrôle

## <a name="checksum"></a>Somme de contrôle

oui

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_luxemburg_eu_tax_file_number` trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keywords_luxemburg_eu_national_id_card` est trouvé.

Une stratégie DLP a une confiance moyenne ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_luxemburg_eu_tax_file_number` trouve un contenu qui correspond au modèle.

```xml
      <!-- Luxemburg National Identification Number (Natural persons) -->
      <Entity id="aaf661ed-29ec-426d-8bf9-880cad298ebb" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_luxemburg_eu_tax_file_number" />
          <Match idRef="Keywords_luxemburg_eu_national_id_card" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_luxemburg_eu_tax_file_number" />
          <Any minMatches="0" maxMatches="0">
            <Match idRef="Keywords_luxemburg_eu_telephone_number" />
            <Match idRef="Keywords_luxemburg_eu_mobile_number" />
          </Any>
        </Pattern>
      </Entity>
```

## <a name="keywords"></a>Mots-clés

### <a name="keywords_luxemburg_eu_national_id_card"></a>Keywords_luxemburg_eu_national_id_card

- eindeutige id
- eindeutige id-nummer
- eindeutigeid #
- id personnelle
- idpersonnelle #
- idpersonnelle
- code individuel
- ID individuel
- identification individuelle
- identité individuelle
- numéro d’identification personnel
- ID personnel
- identification personnelle
- identité personnelle
- personalidno #
- #numéroidpersonnel
- persönliche identifikationsnummer
- ID unique
- identité unique
- uniqueidkey #
