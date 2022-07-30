---
title: Définition de l’entité numéro de passeport en Allemagne
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
description: Définition d’entité de type d’entité de type d’informations sensibles de numéro de passeport en Allemagne.
ms.openlocfilehash: 3e58ded04d1507903c890598a7f2c7d892ac45e7
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2022
ms.locfileid: "66996709"
---
# <a name="germany-passport-number"></a>Numéro de passeport allemand

## <a name="format"></a>Format

9 à 11 caractères

## <a name="pattern"></a>Modèle

- une lettre en C, F, G, H, J, K (ne respectant pas la casse)
- huit chiffres ou lettres en C, F, G, H, J, K, L, M, N, P, R, T, V, W, X, Y et Z (ne respectant pas la casse)
- chiffre de vérification facultatif
- D/D facultatif

## <a name="checksum"></a>Somme de contrôle

Oui

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_german_passport_checksum` trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keyword_german_passport`ou `Keywords_eu_passport_number_common` est trouvé.
- La somme de contrôle est correcte.

Une stratégie DLP a une confiance moyenne ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_german_passport` recherche le contenu qui correspond au modèle de neuf caractères (sans chiffre de vérification et d/D facultatif).
- Un mot clé figurant dans la liste `Keyword_german_passport`ou `Keywords_eu_passport_number_common` est trouvé.

Une stratégie DLP a une confiance faible ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_german_passport_checksum` trouve un contenu qui correspond au modèle.
- La somme de contrôle est correcte.

```xml
    <!-- German Passport Number -->
    <Entity id="2e3da144-d42b-47ed-b123-fbf78604e52c" patternsProximity="300" recommendedConfidence="75">
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_german_passport" />
        <Any minMatches="1">
          <Match idRef="Keyword_german_passport" />
          <Match idRef="Keywords_eu_passport_number_common" />
        </Any>
      </Pattern>
      <Version minEngineVersion="15.20.4570.0">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_german_passport_checksum" />
          <Any minMatches="1">
            <Match idRef="Keyword_german_passport" />
            <Match idRef="Keywords_eu_passport_number_common" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Func_german_passport_checksum" />
        </Pattern>
      </Version>
    </Entity>
```

## <a name="keywords"></a>Mots-clés

### <a name="keyword_german_passport"></a>Keyword_german_passport

- reisepasse
- reisepassnummer
- No-Reisepass
- Nr-Reisepass
- Reisepass-Nr
- Passnummer
- reisepässe
- passeport non.
- passeport no

### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- Passeport #
- Passeport #
- passportid
- Passeports
- passportno
- passport no
- numéropasseport
- numéro de passeport
- passportnumbers
- numéros de passeport