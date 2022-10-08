---
title: Définition de l’entité numéro de licence des pilotes américains
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
description: Définition d’entité de type d’entité du numéro de permis de conduire américain.
ms.openlocfilehash: 9659bfce35958409e54ffe7ff15e948e5b980d6f
ms.sourcegitcommit: 176bbd29c92e1c0812e8bcd1e1e4938a3e1d7331
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/05/2022
ms.locfileid: "68472560"
---
# <a name="us-drivers-license-number"></a>Numéro de permis de conduire américain

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="format"></a>Format

Dépend de l’État

## <a name="pattern"></a>Modèle

dépend de l’état , par exemple, New York :

- neuf chiffres mis en forme comme ddd ddd ddd ddd correspondent.
- neuf chiffres comme dddddddddd ne correspondent pas.

## <a name="checksum"></a>Somme de contrôle

Non

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_new_york_drivers_license_number` trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keyword_[state_name]_drivers_license_name` est trouvé.
- Un mot clé figurant dans la liste `Keyword_us_drivers_license` est trouvé.

Une stratégie DLP a une confiance faible ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_new_york_drivers_license_number` trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keyword_[state_name]_drivers_license_name` est trouvé.
- Un mot clé figurant dans la liste `Keyword_us_drivers_license_abbreviations` est trouvé.
- Aucun mot clé n’est `Keyword_us_drivers_license` trouvé.

```xml
<Entity id="dfeb356f-61cd-459e-bf0f-7c6d28b458c6 patternsProximity="300">
    <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_new_york_drivers_license_number" />
        <Match idRef="Keyword_new_york_drivers_license_name" />
        <Match idRef="Keyword_us_drivers_license" />
    </Pattern>
    <Pattern confidenceLevel="65">
        <IdMatch idRef="Func_new_york_drivers_license_number" />
        <Match idRef="Keyword_new_york_drivers_license_name" />
        <Match idRef="Keyword_us_drivers_license_abbreviations" />
        <Any minMatches="0" maxMatches="0">
          <Match idRef="Keyword_us_drivers_license" />
        </Any>
    </Pattern>
</Entity>
```

## <a name="keywords"></a>Mots-clés

### <a name="keyword_us_drivers_license_abbreviations"></a>Keyword_us_drivers_license_abbreviations

- PC
- PC
- PCD
- PCD
- ID
- Id
- # PC
- # PC
- # PCD
- # PCD
- Id #
- Id #
- Numéro d’identification
- Numéros d’identification
- Lic
- Lic #
- Dln

### <a name="keyword_us_drivers_license"></a>Keyword_us_drivers_license

- PermisConduire
- DriverLics
- DriverLicense
- DriverLicenses
- Permis conduire
- Permis conduire
- Permis de conduire
- Permis de conduire
- PermisConduire
- DriversLics
- DriversLicense
- PermisConduire
- Permis conduire
- Permis conduire
- Permis de conduire
- Permis de conduire
- Driver’Lic
- Permisconduire
- Permisdeconduire
- Permisdeconduire
- Permis conduire
- Permis conduire
- Permis de conduire
- Permis de conduire
- PermisConduire
- Driver'sLics
- Driver'sLicense
- Driver'sLicenses
- Permis de conduire
- Permis de conduire
- Permis de conduire
- Driver’s Licenses
- numéro d’identification
- numéros d’identification
- # identification
- carte d’identité
- cartes d’identité
- carte d’identification
- cartes d’identification
- #PermisConduire
- DriverLics#
- DriverLicense#
- DriverLicenses#
- #Permis conduire
- #Permis conduire
- #Permis de conduire
- #Permis de conduire
- #PermisConduire
- DriversLics#
- DriversLicense#
- DriversLicenses#
- #Permis conduire
- #Permis conduire
- #Permis de conduire
- #Permis de conduire
- Driver’Lic#
- #Permisconduire
- #Permisdeconduire
- #Permisdeconduire
- #Permis conduire
- #Permis conduire
- #Permis de conduire
- #Permis de conduire
- #PermisConduire
- Driver'sLics#
- Driver'sLicense#
- Driver'sLicenses#
- #Permisconduire
- #Permisconduire
- #Permis de conduire
- #Permis de conduire
- # carte d’identité
- # cartes d’identité
- #carte d’identification
- #cartes d’identification

### <a name="keyword_state_name_drivers_license_name"></a>Keyword_[state_name]_drivers_license_name

- abréviation d’état (par exemple, « NY »)
- nom de l’état (par exemple, « New York »)
