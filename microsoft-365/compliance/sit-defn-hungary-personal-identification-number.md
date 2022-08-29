---
title: Définition de l’entité numéro d’identification personnelle en Hongrie
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
description: Définition d’entité de type d’entité du numéro d’identification personnelle de Hongrie.
ms.openlocfilehash: ee3a22ffccdf9110d36e49013bfed912b2d2319b
ms.sourcegitcommit: 72d10d0bc29ecc8b19c395f1815dc48b549096d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2022
ms.locfileid: "67367266"
---
# <a name="hungary-personal-identification-number"></a>Numéro d’identification personnelle hongrois

## <a name="format"></a>Format

11 chiffres

## <a name="pattern"></a>Modèle

11 chiffres :

- Un chiffre qui correspond au sexe, 1 pour les hommes, 2 pour les femmes. D’autres chiffres sont également possibles pour les citoyens nés avant 1900 ou les citoyens ayant la double citoyenneté.
- Six chiffres correspondant à la date de naissance (AAAAMMD)
- Trois chiffres qui correspondent à un numéro de série
- Un chiffre à cocher

## <a name="checksum"></a>Somme de contrôle

Oui

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_hungary_eu_national_id_card` trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keywords_hungary_eu_national_id_card` est trouvé.

Une stratégie DLP a une confiance moyenne ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_hungary_eu_national_id_card` trouve un contenu qui correspond au modèle.

```xml
      <!-- Hungary Personal Identification Number -->
      <Entity id="7b5cc218-7046-47d9-80c9-f325b50896ca" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_hungary_eu_national_id_card" />
          <Match idRef="Keywords_hungary_eu_national_id_card" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_hungary_eu_national_id_card" />
          <Any minMatches="0" maxMatches="0">
            <Match idRef="Keywords_hungary_eu_telephone_number" />
            <Match idRef="Keywords_hungary_eu_mobile_number" />
          </Any>
        </Pattern>
      </Entity>
```

## <a name="keywords"></a>Mots-clés

### <a name="keywords_hungary_eu_national_id_card"></a>Keywords_hungary_eu_national_id_card

- numéro d’ID
- numéro d’identification
- sz ig
- Sz. Ig.
- sz.ig.
- személyazonosító igazolvány
- személyi igazolvány