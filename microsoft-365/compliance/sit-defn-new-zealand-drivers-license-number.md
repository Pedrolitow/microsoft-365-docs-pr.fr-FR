---
title: Définition de l’entité numéro de licence des pilotes néo-zélandais
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
description: Définition d’entité de type d’entité du numéro de permis de conduire néo-zélandais.
ms.openlocfilehash: 56ca27a23cf328978dfc56628a0a5740c8f0ab6e
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2022
ms.locfileid: "66995910"
---
# <a name="new-zealand-drivers-license-number"></a>Numéro de permis de conduire en Nouvelle-Zélande

Ce type d’informations sensibles est uniquement disponible pour une utilisation dans :

- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gestion du cycle de vie des données
- gestion des enregistrements
- Microsoft Defender for Cloud Apps

## <a name="format"></a>Format

modèle alphanumérique à huit caractères

## <a name="pattern"></a>Modèle

modèle alphanumérique à huit caractères

- deux lettres
- six chiffres

## <a name="checksum"></a>Somme de contrôle

Oui

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_newzealand_driver_license_number` trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keywords_newzealand_driver_license_number` est trouvé.

Une stratégie DLP a une confiance faible ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_newzealand_driver_license_number` trouve un contenu qui correspond au modèle.

```xml
      <!-- New Zealand Driver License Number -->
      <Entity id="1924b377-d287-49c9-a737-cfe7a8a2615a" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_newzealand_driver_license_number" />
          <Match idRef="Keywords_newzealand_driver_license_number" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Func_newzealand_driver_license_number" />
        </Pattern>
      </Entity>
```

## <a name="keywords"></a>Mots-clés

### <a name="keyword_new_zealand_drivers_license_number"></a>Keyword_new_zealand_drivers_license_number

- driverlicence
- driverlicences
- driver lic
- permis de conduire
- permis de conduire
- driverslic
- driverslicence
- driverslicences
- drivers lic
- drivers lics
- permis de conduire
- permis de conduire
- driver’lic
- driver’lics
- permis de conduire
- permis de conduire
- driver' lic
- driver' lics
- permis de conduire
- permis de conduire
- driver’slic
- driver’slics
- driver’slicence
- driver’slicences
- driver’s lic
- driver’s lics
- permis de conduire
- permis de conduire
- driverlic #
- driverlics #
- driverlicence #
- driverlicences #
- driver lic #
- driver lics #
- permis de conduire #
- permis de conduire #
- driverslic #
- driverslics #
- driverslicence #
- driverslicences #
- drivers lic #
- drivers lics #
- permis de conduire #
- permis de conduire #
- driver’lic #
- driver’lics #
- permis de conduire #
- permis de conduire #
- driver' lic #
- driver' lics #
- permis de conduire #
- permis de conduire #
- driver’slic #
- driver’slics #
- driver’slicence #
- driver’slicences #
- driver’s lic #
- driver’s lics #
- permis de conduire #
- permis de conduire #
- permis de conduite international
- permis de conduite internationaux
- nz automobile association
- Association automobile néo-zélandaise