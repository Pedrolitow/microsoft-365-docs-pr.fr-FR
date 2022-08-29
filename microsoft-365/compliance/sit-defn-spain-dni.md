---
title: Définition d’entité DNI en Espagne
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
description: Définition d’entité de type d’informations sensibles DNI en Espagne.
ms.openlocfilehash: 9128e04b9462b2d3768a62157e3798ddea17e54c
ms.sourcegitcommit: 72d10d0bc29ecc8b19c395f1815dc48b549096d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2022
ms.locfileid: "67367332"
---
# <a name="spain-dni"></a>Document national d’identité espagnol

## <a name="format"></a>Format

huit chiffres suivis d’un caractère

## <a name="pattern"></a>Modèle

sept chiffres suivis d’un caractère

- huit chiffres
- Espace ou trait d’union facultatif
- une lettre de vérification (non sensible à la casse)

## <a name="checksum"></a>Somme de contrôle

Oui

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_spain_eu_DL_and_NI_number_citizen` ou `Func_spain_eu_DL_and_NI_number_foreigner` trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keywords_spain_eu_national_id_card"` est trouvé.

Une stratégie DLP a une confiance moyenne ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_spain_eu_DL_and_NI_number_citizen` ou `Func_spain_eu_DL_and_NI_number_foreigner` trouve un contenu qui correspond au modèle.

```xml
      <!-- Spain DNI -->
      <Entity id="8e6251b9-47b4-40e8-a42b-0f80876be192" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_spain_eu_DL_and_NI_number_citizen" />
          <Match idRef="Keywords_spain_eu_national_id_card" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_spain_eu_DL_and_NI_number_citizen" />
        </Pattern>
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_spain_eu_DL_and_NI_number_foreigner" />
          <Match idRef="Keywords_spain_eu_national_id_card" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_spain_eu_DL_and_NI_number_foreigner" />
        </Pattern>
      </Entity>
```

## <a name="keywords"></a>Mots-clés

### <a name="keywords_spain_eu_national_id_card"></a>Keywords_spain_eu_national_id_card

- carné de identidad
- Dni #
- Dni
- dninúmero #
- documento nacional de identidad
- identidad único
- identidadúnico #
- numéro d’assurance
- numéro d’identification nationale
- nationale d’identité
- nationalid #
- nationalidno#
- nie #
- nie
- nienúmero #
- número de identificación
- número nacional identidad
- numéro d’identification personnelle
- identité personnelle non
- numéro d’identité unique
- Uniqueid #