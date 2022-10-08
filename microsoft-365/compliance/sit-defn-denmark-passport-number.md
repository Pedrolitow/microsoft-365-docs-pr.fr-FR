---
title: Définition de l’entité numéro de passeport du Danemark
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
description: Définition d’entité du type d’entité du type d’informations sensibles du numéro de passeport du Danemark.
ms.openlocfilehash: b0ccef6edb192cf9f759c65de92fe603e7294c0e
ms.sourcegitcommit: 2ff545246fec060ea7829da5afbc1cdc698d51ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2022
ms.locfileid: "68363208"
---
# <a name="denmark-passport-number"></a>Numéro de passeport danois

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="format"></a>Format

neuf chiffres sans espaces et délimiteurs

## <a name="pattern"></a>Modèle

neuf chiffres

## <a name="checksum"></a>Somme de contrôle

Non

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- L’expression régulière `Regex_denmark_eu_passport_number` trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keywords_eu_passport_number`ou `Keywords_denmark_eu_passport_number` est trouvé.
- L’expression `Regex_eu_passport_date2` régulière recherche la date au format JJ MM YY ou un mot clé `Keywords_eu_passport_date` est trouvé

Une stratégie DLP a une confiance moyenne ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- L’expression régulière `Regex_denmark_eu_passport_number` trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keywords_eu_passport_number`ou `Keywords_denmark_eu_passport_number` est trouvé.

```xml
      <!-- Denmark Passport Number -->
      <Entity id="25e8c47e-e6fe-4884-a211-74898f8c0196" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_denmark_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_denmark_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_eu_passport_date2" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_denmark_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_denmark_eu_passport_number" />
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

### <a name="keywords_denmark_eu_passport_number"></a>Keywords_denmark_eu_passport_number

- pasnummer
- Passeport n°
- pasnumre

### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- date du problème
- date d’expiration
