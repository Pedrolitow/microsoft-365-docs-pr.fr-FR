---
title: Définition de l’entité numéro de passeport tchèque
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
description: Définition d’entité de type d’entité de type d’informations sensibles de numéro de passeport tchèque.
ms.openlocfilehash: afc5fb2c3831fc57ca72aede35f0f87cf143f529
ms.sourcegitcommit: 2ff545246fec060ea7829da5afbc1cdc698d51ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2022
ms.locfileid: "68363055"
---
# <a name="czech-passport-number"></a>Numéro de passeport tchèque

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="format"></a>Format

huit chiffres sans espaces ni délimiteurs

## <a name="pattern"></a>Modèle

huit chiffres sans espaces ni délimiteurs

## <a name="checksum"></a>Somme de contrôle

Non

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- L’expression régulière `Regex_czech_republic_eu_passport_number` trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keywords_eu_passport_number`ou `Keywords_czech_republic_eu_passport_number` est trouvé.
- L’expression `Regex_eu_passport_date1` régulière recherche la date au format DD.MM.AAAA ou un mot clé `Keywords_eu_passport_date` est trouvé

Une stratégie DLP a une confiance moyenne ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- L’expression régulière `Regex_czech_republic_eu_passport_number` trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keywords_eu_passport_number`ou `Keywords_czech_republic_eu_passport_number` est trouvé.

```xml
      <!-- Czech Republic Passport Number -->
      <Entity id="7bcd8ce8-5e92-4bbe-bc92-fa669f0369fa" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_czech_republic_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_czech_republic_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_eu_passport_date1" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_czech_republic_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_czech_republic_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```

## <a name="keywords"></a>Mots-clés

### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

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

### <a name="keywords_czech_republic_eu_passport_number"></a>Keywords_czech_republic_eu_passport_number

- cestovní pas
- číslo pasu
- cestovní pasu
- passeport no
- čísla pasu

### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- date du problème
- date d’expiration
