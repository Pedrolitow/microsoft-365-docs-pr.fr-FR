---
title: Définition de l’entité numéro de permis de conduire slovène
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
description: Définition d’entité de type d’entité du numéro de permis de conduire slovène.
ms.openlocfilehash: 22b0eb92d1be845bca8ebde1b887eb8494a44de6
ms.sourcegitcommit: 176bbd29c92e1c0812e8bcd1e1e4938a3e1d7331
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/05/2022
ms.locfileid: "68472999"
---
# <a name="slovenia-drivers-license-number"></a>Numéro de permis de conduire en Slovenia

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="format"></a>Format

neuf chiffres sans espaces et délimiteurs

## <a name="pattern"></a>Modèle

neuf chiffres

## <a name="checksum"></a>Somme de contrôle

Non

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- L’expression régulière `Regex_slovenia_eu_driver's_license_number` trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keywords_eu_driver's_license_number`ou `Keywords_slovenia_eu_driver's_license_number` est trouvé.

```xml
      <!-- Slovenia Driver's License Number -->
      <Entity id="d5bc089a-f2ee-433d-a6b1-5c253051d6f2" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_slovenia_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_slovenia_eu_driver's_license_number" />
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

### <a name="keywords_slovenia_eu_drivers_license_number"></a>Keywords_slovenia_eu_driver s_license_number

- vozniško dovoljenje
- vozniška številka licence
- vozniških dovoljenj
- številka vozniškega dovoljenja
- številke vozniških dovoljenj
