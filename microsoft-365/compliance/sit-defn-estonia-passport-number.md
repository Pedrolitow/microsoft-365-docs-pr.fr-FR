---
title: Définition de l’entité numéro de passeport estonien
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
description: Définition d’entité de type d’entité de type d’information sensible de numéro de passeport estonienne.
ms.openlocfilehash: 6e06e2fd3eff5bdce3a74b9e78f8892b75764a3b
ms.sourcegitcommit: 2ff545246fec060ea7829da5afbc1cdc698d51ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2022
ms.locfileid: "68362813"
---
# <a name="estonia-passport-number"></a>Numéro de passeport estonien

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="format"></a>Format

une lettre suivie de sept chiffres sans espaces ni délimiteurs

## <a name="pattern"></a>Modèle

une lettre suivie de sept chiffres

## <a name="checksum"></a>Somme de contrôle

Non

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- L’expression régulière `Regex_estonia_eu_passport_number` trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keywords_eu_passport_number`ou `Keywords_estonia_eu_passport_number` est trouvé.
- L’expression `Regex_eu_passport_date1` régulière recherche la date au format DD.MM.AAAA ou un mot clé `Keywords_eu_passport_date` est trouvé

Une stratégie DLP a une confiance moyenne ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- L’expression régulière `Regex_estonia_eu_passport_number` trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keywords_eu_passport_number`ou `Keywords_estonia_eu_passport_number` est trouvé.

```xml
      <!-- Estonia Passport Number -->
      <Entity id="61f7073a-509e-425b-a754-bc01bb5d5b8c" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_estonia_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_estonia_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_eu_passport_date1" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_estonia_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_estonia_eu_passport_number" />
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

### <a name="keywords_estonia_eu_passport_number"></a>Keywords_estonia_eu_passport_number

eesti kodaniku pass passi number passinumbrid document number no dokumendi nr

### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- date du problème
- date d’expiration
