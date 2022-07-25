---
title: Définition de l’entité numéro de permis de conduire canada
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
description: Définition d’entité de type d’entité de type d’information sensible sur le numéro de permis de conduire au Canada.
ms.openlocfilehash: a42af206eef8508bd971fad60d213c15f131e2b2
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2022
ms.locfileid: "66997695"
---
# <a name="canada-drivers-license-number"></a>Numéro de permis de conduire du Canada

## <a name="format"></a>Format

Varie selon la province

## <a name="pattern"></a>Modèle

Différents modèles couvrant :

- Alberta
- Colombie-britannique
- Manitoba
- Nouveau-Brunswick
- Terre-Neuve-et-Labrador
- Nouvelle-Écosse
- Ontario
- Île-du-Prince-Édouard
- Quebec
- Saskatchewan

## <a name="checksum"></a>Somme de contrôle

Non

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_[province_name]_drivers_license_number` trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keyword_[province_name]_drivers_license_name` est trouvé.
- Un mot clé figurant dans la liste `Keyword_canada_drivers_license` est trouvé.

```xml
<!-- Canada Driver's License Number -->
    <Entity id="37186abb-8e48-4800-ad3c-e3d1610b3db0" patternsProximity="300" recommendedConfidence="75">
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_alberta_drivers_license_number" />
        <Match idRef="Keyword_alberta_drivers_license_name" />
        <Match idRef="Keyword_canada_drivers_license" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_british_columbia_drivers_license_number" />
        <Match idRef="Keyword_british_columbia_drivers_license_name" />
        <Match idRef="Keyword_canada_drivers_license" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_manitoba_drivers_license_number" />
        <Match idRef="Keyword_manitoba_drivers_license_name" />
        <Match idRef="Keyword_canada_drivers_license" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_new_brunswick_drivers_license_number" />
        <Match idRef="Keyword_new_brunswick_drivers_license_name" />
        <Match idRef="Keyword_canada_drivers_license" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_newfoundland_labrador_drivers_license_number" />
        <Match idRef="Keyword_newfoundland_labrador_drivers_license_name" />
        <Match idRef="Keyword_canada_drivers_license" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_nova_scotia_drivers_license_number" />
        <Match idRef="Keyword_nova_scotia_drivers_license_name" />
        <Match idRef="Keyword_canada_drivers_license" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_ontario_drivers_license_number" />
        <Match idRef="Keyword_ontario_drivers_license_name" />
        <Match idRef="Keyword_canada_drivers_license" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_prince_edward_island_drivers_license_number" />
        <Match idRef="Keyword_prince_edward_island_drivers_license_name" />
        <Match idRef="Keyword_canada_drivers_license" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_quebec_drivers_license_number" />
        <Match idRef="Keyword_quebec_drivers_license_name" />
        <Match idRef="Keyword_canada_drivers_license" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_saskatchewan_drivers_license_number" />
        <Match idRef="Keyword_saskatchewan_drivers_license_name" />
        <Match idRef="Keyword_canada_drivers_license" />
      </Pattern>
    </Entity>
```

## <a name="keywords"></a>Mots-clés

### <a name="keyword_province_name_drivers_license_name"></a>Keyword_[province_name]_drivers_license_name

- L’abréviation de la province, par exemple AB
- Le nom de la province, par exemple Alberta

### <a name="keyword_canada_drivers_license"></a>Keyword_canada_drivers_license

- DL
- DLS
- CDL
- CDLS
- DriverLic
- DriverLics
- DriverLicense
- DriverLicenses
- DriverLicence
- DriverLicences
- Permis conduire
- Permis conduire
- Permis de conduire
- Permis de conduire
- Permis de conduire
- Permis de conduire
- DriversLic
- DriversLics
- DriversLicence
- DriversLicences
- DriversLicense
- DriversLicenses
- Permis conduire
- Permis conduire
- Permis de conduire
- Permis de conduire
- Permis de conduire
- Permis de conduire
- Driver’Lic
- Driver’Lics
- Driver’License
- Licences de pilote
- Permis de conduire
- Permis de conduire
- Permis conduire
- Permis conduire
- Permis de conduire
- Permis de conduire
- Permis de conduire
- Permis de conduire
- Driver’sLic
- Driver’sLics
- Driver’sLicense
- Driver’sLicenses
- Driver’sLicence
- Driver’sLicences
- Permis de conduire
- Permis de conduire
- Permis de conduire
- Permis de conduire
- Permis de conduire
- Permis de conduire
- Permis de conduire
- id
- Ids
- numéro carte d’identification
- numéros carte d’identification
- # carte d’identification
- # carte d’identification
- carte d’identification
- cartes d’identification
- idcard
- numéro d’identification
- numéros d’identification
- # identification
- # identification
- carte d’identification
- cartes d’identification
- Identification
- DL #
- DLS #
- CDL #
- CDLS #
- DriverLic #
- DriverLics #
- DriverLicense #
- DriverLicenses #
- DriverLicence #
- DriverLicences #
- #Permis conduire
- #Permis conduire
- #Permis de conduire
- #Permis de conduire
- #Permis de conduire
- #Permis de conduire
- DriversLic #
- DriversLics #
- DriversLicense #
- DriversLicenses #
- DriversLicence #
- DriversLicences #
- #Permis conduire
- #Permis conduire
- #Permis de conduire
- #Permis de conduire
- #Permis de conduire
- #Permis de conduire
- Driver’Lic #
- Driver’Lics #
- Driver’License #
- Licences de pilote #
- Permis de conduire #
- Permis de conduire #
- #Permis conduire
- #Permis conduire
- #Permis de conduire
- #Permis de conduire
- #Permis de conduire
- #Permis de conduire
- Driver’sLic #
- Driver’sLics #
- Driver’sLicense #
- Driver’sLicenses #
- Driver’sLicence #
- Driver’sLicences #
- #Permisconduire
- #Permisconduire
- #Permis de conduire
- #Permis de conduire
- #Permis de conduire
- #Permis de conduire
- Permis de conduire #
- Id #
- Id #
- #carte carte d’identification
- #cartes carte d’identification
- idcard #
- #carte d’identification
- #cartes d’identification
- Identification #