---
title: Définition de l’entité Estonie Personal Identification Code
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
description: Définition d’entité de type d’entité du code d’identification personnelle estonienne.
ms.openlocfilehash: d14d5cade3a714cdae5983470960dd0144d2082e
ms.sourcegitcommit: 2ff545246fec060ea7829da5afbc1cdc698d51ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2022
ms.locfileid: "68361663"
---
# <a name="estonia-personal-identification-code"></a>Code d’identification personnelle estonienne

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="format"></a>Format

11 chiffres sans espaces et délimiteurs

## <a name="pattern"></a>Modèle

11 chiffres :

- un chiffre qui correspond au sexe et au siècle de naissance (nombre impair masculin, même nombre féminin ; 1-2 : 19e siècle ; 3-4 : 20e siècle ; 5-6 : 21e siècle)
- six chiffres qui correspondent à la date de naissance (AAAAMMD)
- trois chiffres qui correspondent à un numéro de série séparant les personnes nées à la même date
- un chiffre de vérification

## <a name="checksum"></a>Somme de contrôle

Oui

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_estonia_eu_national_id_card` trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keywords_estonia_eu_national_id_card` est trouvé.

Une stratégie DLP a une confiance moyenne ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_estonia_eu_national_id_card` trouve un contenu qui correspond au modèle.

```xml
      <!-- Estonia Personal Identification Code -->
      <Entity id="bfb26de6-dad5-4d48-ab72-4789cdd0654c" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_estonia_eu_national_id_card" />
          <Match idRef="Keywords_estonia_eu_national_id_card" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_estonia_eu_national_id_card" />
          <Any minMatches="0" maxMatches="0">
            <Match idRef="Keywords_estonia_eu_telephone_number" />
            <Match idRef="Keywords_estonia_eu_mobile_number" />
          </Any>
        </Pattern>
      </Entity>
```

## <a name="keywords"></a>Mots-clés

### <a name="keywords_estonia_eu_national_id_card"></a>Keywords_estonia_eu_national_id_card

- id-kaart
- Ik
- isikukood #
- isikukood
- maksu id
- maksukohustuslase identifitseerimisnumber
- maksunumber
- numéro d’identification nationale
- numéro national
- code personnel
- numéro d’ID personnel
- code d’identification personnelle
- numéro d’identification personnelle
- #numéroidpersonnel
- id fiscal
- numéro d’identification fiscal
- numéro d’identification fiscal
- taxe nº#
- nº fiscal
- numéro de contribuable
- numéro d’identification fiscale
- taxid#
- taxidno#
- taxidnumber#
- taxno#
- taxnumber#
- taxnumber
- id de tin
- nº de tin
- tin#
