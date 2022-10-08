---
title: Définition d’entité de numéro d’identification personnelle (OIB) en Croatie
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
description: Définition d’entité de type d’information sensible de numéro d’identification personnelle (OIB) en Croatie.
ms.openlocfilehash: 683ee32f3e12255583958766e1d94efd6eeedfb7
ms.sourcegitcommit: 2ff545246fec060ea7829da5afbc1cdc698d51ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2022
ms.locfileid: "68362967"
---
# <a name="croatia-personal-identification-oib-number"></a>Numéro d’identification personnelle (OIB) en Croatie

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="format"></a>Format

11 chiffres

## <a name="pattern"></a>Modèle

11 chiffres :

- 10 chiffres
- chiffre final est un chiffre à cocher

## <a name="checksum"></a>Somme de contrôle

Oui

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_croatia_oib_number` trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keywords_croatia_eu_tax_file_number` est trouvé.
- La somme de contrôle est correcte.

Une stratégie DLP a une confiance moyenne ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_croatia_oib_number` trouve un contenu qui correspond au modèle.
- La somme de contrôle est correcte.

```xml
      <!-- Croatia Personal Identification (OIB) Number -->
      <Entity id="31983b6d-db95-4eb2-a630-b44bd091968d" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_croatia_oib_number" />
          <Match idRef="Keywords_croatia_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_croatia_oib_number" />
        </Pattern>
      </Entity>
```

## <a name="keywords"></a>Mots-clés

### <a name="keyword_croatia_oib_number"></a>Keyword_croatia_oib_number

- majstorski broj građana
- numéro de citoyen maître
- nacionalni identifikacijski broj
- numéro d’identification nationale
- Oib #
- Oib
- osobna iskaznica
- iD osobni
- osobni identifikacijski broj
- numéro d’identification personnelle
- porezni broj
- porezni identifikacijski broj
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
