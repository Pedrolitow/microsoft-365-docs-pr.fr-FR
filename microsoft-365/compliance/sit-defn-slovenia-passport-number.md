---
title: Slovénie - Définition de l’entité numéro de passeport
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
description: Définition d’entité de type d’entité de type d’information sensible de numéro de passeport de slovénie.
ms.openlocfilehash: d01581a14f50c41252f134b12a5ffe00d5971f77
ms.sourcegitcommit: 176bbd29c92e1c0812e8bcd1e1e4938a3e1d7331
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/05/2022
ms.locfileid: "68470583"
---
# <a name="slovenia-passport-number"></a>Numéro de passeport slovène

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="format"></a>Format

deux lettres suivies de sept chiffres sans espaces ni délimiteurs

## <a name="pattern"></a>Modèle

deux lettres suivies de sept chiffres :

- la lettre « P »
- une lettre majuscule
- sept chiffres

## <a name="checksum"></a>Somme de contrôle

Non

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- L’expression régulière `Regex_slovenia_eu_passport_number` trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keywords_eu_passport_number`ou `Keywords_slovenia_eu_passport_number` est trouvé.
- L’expression `Regex_eu_passport_date1` régulière recherche la date au format DD.MM.AAAA ou un mot clé `Keywords_eu_passport_date` est trouvé

Une stratégie DLP a une confiance moyenne ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- L’expression régulière `Regex_slovenia_eu_passport_number` trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keywords_eu_passport_number`ou `Keywords_slovenia_eu_passport_number` est trouvé.

```xml
      <!-- Slovenia Passport Number -->
      <Entity id="235b7976-7bbe-4df5-bb40-08678e749d1a" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_slovenia_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_slovenia_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_eu_passport_date1" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_slovenia_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_slovenia_eu_passport_number" />
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

### <a name="keywords_slovenia_eu_passport_number"></a>Keywords_slovenia_eu_passport_number

- številka potnega lista
- potek veljavnosti
- liste potni #
- datum rojstva
- liste potni
- številke potnih listov

### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- date du problème
- date d’expiration
