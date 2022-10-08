---
title: Définition de l’entité numéro de permis de conduire en Hongrie
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
description: Définition d’entité de type d’information sensible sur le numéro de permis de conduire en Hongrie.
ms.openlocfilehash: b1e679c5a56092818807ba464603ac2742736c16
ms.sourcegitcommit: be2334dbcd4e1bf309349d981a68a30e06de0297
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2022
ms.locfileid: "68380577"
---
# <a name="hungary-drivers-license-number"></a>Numéro de permis de conduire hongrois

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="format"></a>Format

Deux lettres suivies de six chiffres

## <a name="pattern"></a>Modèle

Deux lettres et six chiffres :

- Deux lettres (non sensibles à la casse)
- Six chiffres

## <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- L’expression régulière `Regex_hungary_eu_driver's_license_number` trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keywords_eu_driver's_license_number`ou `Keywords_hungary_eu_driver's_license_number` est trouvé.

```xml
      <Entity id="9d31c46b-6e6b-444c-aeb1-6dd7e604bb24" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_hungary_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_hungary_eu_driver's_license_number" />
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

### <a name="keywords_hungary_eu_drivers_license_number"></a>Keywords_hungary_eu_driver s_license_number

- vezetoi engedely
- vezetői engedély
- vezetői engedélyek
