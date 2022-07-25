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
- M365-security-compliance
hideEdit: true
feedback_system: None
recommendations: false
description: Définition d’entité de type d’information sensible sur le numéro de permis de conduire en Hongrie.
ms.openlocfilehash: 8e6354455c81bff01b7637132c43f88073fb8bd7
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2022
ms.locfileid: "66996410"
---
# <a name="hungary-drivers-license-number"></a>Numéro de permis de conduire hongrois

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

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- driver lic
- driver lics
- Permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- driverslic
- driverslics
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- drivers lic
- drivers lics
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- driver’lic
- driver’lics
- driver’license
- permis de conduire
- permis de conduire
- permis de conduire
- driver' lic
- driver' lics
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- driver’slic
- driver’slics
- driver’slicense
- driver’slicenses
- driver’slicence
- driver’slicences
- driver’s lic
- driver’s lics
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- Dl #
- Dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- driver lic #
- driver lics #
- permis de conduire #
- licences de pilote #
- permis de conduire #
- driverslic #
- driverslics #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- drivers lic #
- drivers lics #
- permis de conduire #
- licences de pilotes #
- permis de conduire #
- permis de conduire #
- driver’lic #
- driver’lics #
- driver’license #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver' lic #
- driver' lics #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- driver’slic #
- driver’slics #
- driver’slicense #
- driver’slicenses #
- driver’slicence #
- driver’slicences #
- driver’s lic #
- driver’s lics #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire
- permis de conduire
- dlno #
- driv lic
- driv licen
- licence driv
- licences driv
- licence driv
- licences driv
- licen du pilote
- drivers licen
- licen du conducteur
- conduite lic
- conduite licen
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- dl no
- dlno
- numéro dl

### <a name="keywords_hungary_eu_drivers_license_number"></a>Keywords_hungary_eu_driver s_license_number

- vezetoi engedely
- vezetői engedély
- vezetői engedélyek