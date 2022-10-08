---
title: Définition de l’entité numéro de licence des pilotes lituaniens
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
description: Définition d’entité de type d’entité du numéro de permis de conduire lituanien.
ms.openlocfilehash: dc40affca02befbd02d35e57a75ec497dd3ea657
ms.sourcegitcommit: 6df492719fecc2b213d55465dc1cd60ab4627ed6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2022
ms.locfileid: "68383849"
---
# <a name="lithuania-drivers-license-number"></a>Numéro de permis de conduire hongrois

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="format"></a>Format

huit chiffres sans espaces et délimiteurs

## <a name="pattern"></a>Modèle

huit chiffres

## <a name="checksum"></a>Somme de contrôle

Non

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- L’expression régulière `Regex_lithuania_eu_driver's_license_number` trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keywords_eu_driver's_license_number`ou `Keywords_lithuania_eu_driver's_license_number` est trouvé.

```xml
      <!-- Lithuania Driver's License Number -->
      <Entity id="86f7628b-e0f4-4dc3-9fbc-e4300e4c7d78" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_lithuania_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_lithuania_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

## <a name="keywords"></a>Mots-clés

### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver s_license_number

- permisconduire
- permisconduire
- permisconduire
- permisconduire
- permisconduire
- permisconduire
- permis de conduire
- permis de conduire
- Permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- permisconduire
- permisconduire
- permisconduire
- permisconduire
- permisconduire
- permisconduire
- permisconduire
- permisconduire
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- permisconduire
- permisconduire
- permisconduire
- permis de conduire
- permis de conduire
- permis de conduire
- permis conduire
- permis conduire
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- permisconduire
- permisconduire
- permisconduire
- permisconduire
- permisconduire
- permisconduire
- permis de conduire
- permis de conduire
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- pc#
- pc#
- permis de conduire n°
- permis de conduire n°
- permis de conduire n°
- permis de conduire n°
- permis de conduire n°
- permis de conduire n°
- permis de conduire n°
- permis de conduire n°
- permis de conduire n°
- permis de conduire n°
- permis de conduire n°
- permisconduire #
- permisconduire #
- permisconduire #
- permisconduire #
- permisconduire #
- permisconduire #
- permisconduire #
- permisconduire #
- permisconduire #
- permisconduire #
- permisconduire #
- permisconduire #
- permisconduire #
- permisconduire #
- permisconduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire n°
- permis de conduire n°
- permis de conduire n°
- permis de conduire n°
- permis de conduire n°
- permis de conduire n°
- permis de conduire n°
- permis de conduire n°
- permis de conduire n°
- permis de conduire n°
- permis de conduire n°
- permis de conduire n°
- permis de conduire n°
- permis de conduire n°
- permis de conduire n°
- permis de conduire n°
- permis de conduire n°
- permis de conduire n°
- permis de conduire
- permis de conduire
- pc #
- permis conduire
- permis conduire
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- permis conduire
- permis conduire
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduite
- pc no
- pcno
- pc numéro

### <a name="keywords_lithuania_eu_drivers_license_number"></a>Keywords_lithuania_eu_driver s_license_number

- vairuotojo pažymėjimas
- vairuotojo pažymėjimo numeris
- vairuotojo pažymėjimo numeriai
