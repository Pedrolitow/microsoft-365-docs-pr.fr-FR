---
title: ÉTATS-UNIS/ROYAUME-UNI définition d’entité de numéro de passeport
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
description: ÉTATS-UNIS/ROYAUME-UNI définition d’entité de type d’information sensible de numéro de passeport.
ms.openlocfilehash: 96e3f270cfa49cc63a263b54960afb19c27aa3df
ms.sourcegitcommit: 176bbd29c92e1c0812e8bcd1e1e4938a3e1d7331
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/05/2022
ms.locfileid: "68471879"
---
# <a name="usuk-passport-number"></a>ÉTATS-UNIS/ROYAUME-UNI numéro de passeport

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="format"></a>Format

neuf chiffres

## <a name="pattern"></a>Modèle

- une lettre ou un chiffre
- huit chiffres

## <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_usa_uk_passport` trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keywords_eu_passport_number`ou `Keywords_uk_eu_passport_number` est trouvé.
- Un mot clé à partir de `Keywords_eu_passport_date` est trouvé

Une stratégie DLP a une confiance moyenne ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_usa_uk_passport` trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keywords_eu_passport_number`ou `Keywords_uk_eu_passport_number` est trouvé.

```xml
    <!-- U.S. / U.K. Passport Number -->
    <Entity id="178ec42a-18b4-47cc-85c7-d62c92fd67f8" patternsProximity="300" recommendedConfidence="75">
       <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_usa_uk_passport" />
          <Match idRef="Keywords_eu_passport_date" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_uk_eu_passport_number" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_usa_uk_passport" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_uk_eu_passport_number" />
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

### <a name="keywords_uk_eu_passport_number"></a>Keywords_uk_eu_passport_number

- passeport britannique
- uk passport
