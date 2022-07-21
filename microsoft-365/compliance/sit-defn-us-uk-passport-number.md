---
title: États-Unis/Royaume-Uni définition d’entité de numéro de passeport
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
description: États-Unis/Royaume-Uni définition d’entité de type d’information sensible de numéro de passeport.
ms.openlocfilehash: 88caf63983d6f459f5ff201ae695f909489569cb
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2022
ms.locfileid: "66950633"
---
# <a name="usuk-passport-number"></a>États-Unis/Royaume-Uni numéro de passeport

## <a name="format"></a>Format

neuf chiffres

## <a name="pattern"></a>Modèle

- une lettre ou un chiffre
- huit chiffres

## <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction `Func_usa_uk_passport` recherche le contenu qui correspond au modèle.
- Un mot clé à partir ou `Keywords_eu_passport_number` `Keywords_uk_eu_passport_number` est trouvé.
- Un mot clé à partir de `Keywords_eu_passport_date` est trouvé

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction `Func_usa_uk_passport` recherche le contenu qui correspond au modèle.
- Un mot clé à partir ou `Keywords_eu_passport_number` `Keywords_uk_eu_passport_number` est trouvé.

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

- Passeport #
- Passeport #
- passportid
- Passeports
- passportno
- passport no
- passportnumber
- numéro de passeport
- passportnumbers
- numéros de passeport

### <a name="keywords_uk_eu_passport_number"></a>Keywords_uk_eu_passport_number

- passeport britannique
- uk passport