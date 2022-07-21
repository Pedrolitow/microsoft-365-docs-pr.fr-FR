---
title: Définition de l’entité numéro de permis de conduire en Slovaquie
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
description: Définition d’entité de type d’entité du numéro de permis de conduire slovaque.
ms.openlocfilehash: c08bbccf21ed33939a36012d44fb448ad6fd7c56
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2022
ms.locfileid: "66950138"
---
# <a name="slovakia-drivers-license-number"></a>Numéro de permis de conduire en Slovaquie

## <a name="format"></a>Format

un caractère suivi de sept chiffres

## <a name="pattern"></a>Modèle

un caractère suivi de sept chiffres

- une lettre (non sensible à la casse) ou un chiffre
- sept chiffres

## <a name="checksum"></a>Somme de contrôle

Non

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression `Regex_slovakia_eu_driver's_license_number` régulière recherche le contenu qui correspond au modèle.
- Un mot clé à partir ou `Keywords_eu_driver's_license_number` `Keywords_slovakia_eu_driver's_license_number` est trouvé.

```xml
      <!-- Slovakia Driver's License Number -->
      <Entity id="14240c22-b6de-4ce5-a90b-137f74252513" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_slovakia_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_slovakia_eu_driver's_license_number" />
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

### <a name="keywords_slovakia_eu_drivers_license_number"></a>Keywords_slovakia_eu_driver s_license_number

- vodičský preukaz
- vodičské preukazy
- vodičského preukazu
- vodičských preukazov