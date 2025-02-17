---
title: Définition d’entité de code personnel en Lituanie
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
description: Définition d’entité de type d’entité de type code personnel lituanie.
ms.openlocfilehash: 2beee7d7afa48618c8d1e28c1538e47ba9040771
ms.sourcegitcommit: 6df492719fecc2b213d55465dc1cd60ab4627ed6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2022
ms.locfileid: "68381855"
---
# <a name="lithuania-personal-code"></a>Code personnel lituanien

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="format"></a>Format

11 chiffres sans espaces et délimiteurs

## <a name="pattern"></a>Modèle

11 chiffres sans espaces et délimiteurs :

- un chiffre (1-6) qui correspond au sexe et au siècle de naissance de la personne
- six chiffres qui correspondent à la date de naissance (AAAAMMD)
- trois chiffres qui correspondent au numéro de série de la date de naissance
- un chiffre de vérification

## <a name="checksum"></a>Somme de contrôle

Oui

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_lithuania_eu_tax_file_number` trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keywords_lithuania_eu_tax_file_number` est trouvé.

Une stratégie DLP a une confiance moyenne ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_lithuania_eu_tax_file_number` trouve un contenu qui correspond au modèle.

```xml
      <!-- Lithuania Personal Code -->
      <Entity id="cd6d3786-8ec3-4524-a2cf-1e0095379171" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_lithuania_eu_tax_file_number" />
          <Match idRef="Keywords_lithuania_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_lithuania_eu_tax_file_number" />
          <Any minMatches="0" maxMatches="0">
            <Match idRef="Keywords_lithuania_eu_telephone_number" />
            <Match idRef="Keywords_lithuania_eu_mobile_number" />
          </Any>
        </Pattern>
      </Entity>
```

## <a name="keywords"></a>Mots-clés

### <a name="keywords_lithuania_eu_national_id_card"></a>Keywords_lithuania_eu_national_id_card

- asmeninis skaitmeninis kodas
- asmens kodas
- numéro de service citoyen
- mokesčių id
- mokesčių identifikavimas numeris
- mokesčių identifikavimo numeris
- mokesčių numeris
- numéro d’identification nationale
- code personnel
- code numérique personnel
- piliečio paslaugos numeris
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
- unikalus identifikavimo kodas
- unikalus identifikavimo numeris
- numéro d’identification unique
- numéro d’identité unique
- uniqueidentityno #
