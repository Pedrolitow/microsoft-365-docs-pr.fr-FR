---
title: Royaume-Uni définition d’entité de numéro de service de santé national
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
description: Royaume-Uni définition d’entité de type d’information sensible de numéro de service de santé national.
ms.openlocfilehash: d636be281b1652934fa7b4b83b3a4b5da7794a09
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2022
ms.locfileid: "66995689"
---
# <a name="uk-national-health-service-number"></a>Royaume-Uni numéro de service de santé national

## <a name="format"></a>Format

10 à 17 chiffres séparés par des espaces

## <a name="pattern"></a>Modèle

10 à 17 chiffres :

- 3 ou 10 chiffres
- un espace
- trois chiffres
- un espace
- quatre chiffres

## <a name="checksum"></a>Somme de contrôle

Oui

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_uk_nhs_number` trouve un contenu qui correspond au modèle.
- L’une des affirmations suivantes est vraie :
    - Un mot clé figurant dans la liste `Keyword_uk_nhs_number` est trouvé.
    - Un mot clé figurant dans la liste `Keyword_uk_nhs_number1` est trouvé.
    - Un mot clé figurant dans la liste `Keyword_uk_nhs_number_dob` est trouvé.
- La somme de contrôle est correcte.

```xml
<!-- U.K. NHS Number -->
<Entity id="3192014e-2a16-44e9-aa69-4b20375c9a78" patternsProximity="300" recommendedConfidence="85">
    <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_uk_nhs_number" />
        <Any minMatches="1">
          <Match idRef="Keyword_uk_nhs_number" />
          <Match idRef="Keyword_uk_nhs_number1" />
          <Match idRef="Keyword_uk_nhs_number_dob" />
        </Any>
    </Pattern>
</Entity>
```

## <a name="keywords"></a>Mots-clés

### <a name="keyword_uk_nhs_number"></a>Keyword_uk_nhs_number

- service national de santé
- Nhs
- administration des services de santé
- administration de la santé

### <a name="keyword_uk_nhs_number1"></a>Keyword_uk_nhs_number1

- id du patient
- identification du patient
- n° patient
- numéro de patient

### <a name="keyword_uk_nhs_number_dob"></a>Keyword_uk_nhs_number_dob

- GP
- DOB
- D.D.N
- Date of Birth
- Birth Date