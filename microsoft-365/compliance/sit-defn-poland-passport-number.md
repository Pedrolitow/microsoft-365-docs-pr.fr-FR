---
title: Définition de l’entité numéro de passeport en Pologne
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
description: Définition d’entité de type d’information sensible de numéro de passeport en Pologne.
ms.openlocfilehash: 10f6b0b849053773059232f5faeba8300a02131d
ms.sourcegitcommit: 176bbd29c92e1c0812e8bcd1e1e4938a3e1d7331
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/05/2022
ms.locfileid: "68469998"
---
# <a name="poland-passport-number"></a>Numéro de passeport polonais

Cette entité de type d’informations sensibles est incluse dans le type d’informations sensibles numéro de passeport de l’UE. Il est également disponible en tant qu’entité de type d’informations sensibles autonome.

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="format"></a>Format

deux lettres et sept chiffres

## <a name="pattern"></a>Modèle

Deux lettres (non sensibles à la casse) suivies de sept chiffres

## <a name="checksum"></a>Somme de contrôle

Oui

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_polish_passport_number_v2` trouve un contenu qui correspond au modèle.
- La somme de contrôle est correcte.
- Un mot clé figurant dans la liste `Keywords_eu_passport_number`ou `Keyword_polish_national_passport_number` est trouvé.
- Un mot clé figurant dans la liste `Keywords_eu_passport_date` est trouvé.

Une stratégie DLP a une confiance moyenne ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_polish_passport_number_v2` trouve un contenu qui correspond au modèle.
- La somme de contrôle est correcte.
- Un mot clé figurant dans la liste `Keywords_eu_passport_number`ou `Keyword_polish_national_passport_number` est trouvé.

Une stratégie DLP a une confiance faible ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_polish_passport_number_v2` trouve un contenu qui correspond au modèle.
- La somme de contrôle est correcte.

```xml
      <!-- Poland Passport Number -->
      <Entity id="03937FB5-D2B6-4487-B61F-0F8BFF7C3517" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_polish_passport_number_v2" />
          <Match idRef="Keywords_eu_passport_date" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keyword_polish_national_passport_number" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_polish_passport_number_v2" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keyword_polish_national_passport_number" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Func_polish_passport_number_v2" />
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

### <a name="keyword_polish_national_passport_number"></a>Keyword_polish_national_passport_number

- numer paszportu
- numery paszportów
- numery paszportowe
- nr paszportu
- nr. paszportu
- nr paszportów
- n° passeport
- passeport n°

### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- date du problème
- date d’expiration
