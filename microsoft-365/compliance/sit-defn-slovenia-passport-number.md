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
- M365-security-compliance
hideEdit: true
feedback_system: None
recommendations: false
description: Définition d’entité de type d’entité de type d’information sensible de numéro de passeport de slovénie.
ms.openlocfilehash: 76594c43b38c45b614698f0ceb3117263b5ca10a
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2022
ms.locfileid: "66950181"
---
# <a name="slovenia-passport-number"></a>Numéro de passeport en Slovénie

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

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression `Regex_slovenia_eu_passport_number` régulière recherche le contenu qui correspond au modèle.
- Un mot clé à partir ou `Keywords_eu_passport_number` `Keywords_slovenia_eu_passport_number` est trouvé.
- L’expression `Regex_eu_passport_date1` régulière recherche la date au format DD.MM.AAAA ou un mot clé `Keywords_eu_passport_date` est trouvé

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression `Regex_slovenia_eu_passport_number` régulière recherche le contenu qui correspond au modèle.
- Un mot clé à partir ou `Keywords_eu_passport_number` `Keywords_slovenia_eu_passport_number` est trouvé.

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