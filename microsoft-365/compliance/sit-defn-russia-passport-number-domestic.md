---
title: Définition d’entité nationale du numéro de passeport de la Russie
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
description: Russie numéro de passeport national informations sensibles type définition d’entité.
ms.openlocfilehash: b28283b4bc01c74f7887fe67bc621631d8cdadcf
ms.sourcegitcommit: 176bbd29c92e1c0812e8bcd1e1e4938a3e1d7331
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/05/2022
ms.locfileid: "68470297"
---
# <a name="russia-passport-number-domestic"></a>Numéro de passeport national russe 

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="format"></a>Format

Nombre à 10 chiffres

## <a name="pattern"></a>Modèle

Nombre à 10 chiffres :

- deux chiffres
- un espace ou un trait d’union facultatif
- deux chiffres
- un espace facultatif
- six chiffres

## <a name="checksum"></a>Somme de contrôle

Non

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- L’expression `Regex_Russian_Passport_Number_Domestic` régulière recherche le contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keyword_Russian_Passport_Number` est trouvé.

```xml
      <!-- Russian Passport Number Domestic -->
      <Entity id="76ec2f5d-cedb-48e1-8070-1998794af445" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_Russian_Passport_Number_Domestic" />
          <Match idRef="Keyword_Russian_Passport_Number" />
        </Pattern>
      </Entity>
```

## <a name="keywords"></a>Mots-clés

### <a name="keyword_russia_passport_number_domestic"></a>Keyword_russia_passport_number_domestic

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
