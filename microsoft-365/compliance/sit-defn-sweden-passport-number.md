---
title: Définition de l’entité numéro de passeport en Suède
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
description: Définition d’entité de type d’entité de type d’informations sensibles de numéro de passeport en Suède.
ms.openlocfilehash: 7328b3ebae0a59c5a9c8e23446e4d5302924da09
ms.sourcegitcommit: 176bbd29c92e1c0812e8bcd1e1e4938a3e1d7331
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/05/2022
ms.locfileid: "68472110"
---
# <a name="sweden-passport-number"></a>Numéro de passeport suédois

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="format"></a>Format

huit chiffres

## <a name="pattern"></a>Modèle

huit chiffres consécutifs

## <a name="checksum"></a>Somme de contrôle

Non

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- l’expression régulière Regex_sweden_passport_number recherche le contenu qui correspond au modèle.
- un mot clé à partir ou `Keywords_eu_passport_number` `Keyword_sweden_passport` est trouvé.
- l’expression `Regex_sweden_eu_passport_date` régulière trouve une date au format DD MMM/MMM YY (01 JAN/JAN 12) ou un mot clé `Keywords_eu_passport_date` est trouvé.

Une stratégie DLP a une confiance moyenne ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- l’expression régulière Regex_sweden_passport_number recherche le contenu qui correspond au modèle.
- un mot clé à partir ou `Keywords_eu_passport_number` `Keyword_sweden_passport` est trouvé.

```xml
    <!-- Sweden Passport Number -->
    <Entity id="ba4e7456-55a9-4d89-9140-c33673553526" patternsProximity="300" recommendedConfidence="75">
      <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_sweden_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keyword_sweden_passport" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_sweden_eu_passport_date" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_sweden_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keyword_sweden_passport" />
          </Any>
      </Pattern>
    </Entity>
```

## <a name="keywords"></a>Mots-clés

### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- #passeport
- # passeport
- passportID
- passeports
- n° de passeport
- n° de passeport
- numéropasseport
- numéro de passeport
- numérospasseport
- numéros de passeport

### <a name="keyword_sweden_passport"></a>Keyword_sweden_passport

- carte d’inscription alien
- Frais de traitement g3
- entrée multiple
- Numéro de passeport
- passeport n°
- passeport numéro
- # passeport
- #passeport
- passeportnon
- passeportn °
- passnummer
- pass nr
- visa schengen
- visas schengen
- entrée unique
- passe sverige
- exigences en matière de visa
- traitement des visas
- type de visa

### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- date du problème
- date d’expiration
