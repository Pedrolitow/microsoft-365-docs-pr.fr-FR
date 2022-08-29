---
title: Définition de l’entité internationale numéro de passeport de la Russie
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
description: Russie numéro de passeport international de type d’information sensible définition d’entité.
ms.openlocfilehash: 4f8c581dccac25d3c7f402e2d273037918c05868
ms.sourcegitcommit: 72d10d0bc29ecc8b19c395f1815dc48b549096d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2022
ms.locfileid: "67367420"
---
# <a name="russia-passport-number-international"></a>Numéro de passeport russe international

## <a name="format"></a>Format

numéro à neuf chiffres

## <a name="pattern"></a>Modèle

Nombre à neuf chiffres :

- deux chiffres
- un espace ou un trait d’union facultatif
- sept chiffres

## <a name="checksum"></a>Somme de contrôle

Non

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- L’expression `Regex_Russian_Passport_Number_International` régulière recherche le contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keyword_Russian_Passport_Number` est trouvé.

```xml
      <!-- Russian Passport Number International -->
      <Entity id="ac5f4878-75e4-4b82-af2d-02e13ea9f411" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_Russian_Passport_Number_International" />
          <Match idRef="Keyword_Russian_Passport_Number" />
        </Pattern>
      </Entity>
```

## <a name="keywords"></a>Mots-clés

### <a name="keywords_russia_passport_number_international"></a>Keywords_russia_passport_number_international

- numéro de passeport
- n° de passeport
- # passeport
- iD passport
- passportno #
- passportnumber #
- паспорт нет
- паспорт id
- pоссийской паспорт
- pусский номер паспорта
- паспорт #
- паспортid #
- номер паспорта
- номерпаспорта #