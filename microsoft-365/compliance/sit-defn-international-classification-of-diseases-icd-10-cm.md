---
title: Définition d’entité de classification internationale des maladies (ICD-10-CM)
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
description: Classification internationale des maladies (ICD-10-CM) définition d’entité de type d’information sensible.
ms.openlocfilehash: 414ad224f32a6eecb1fe244bdefde12afdc4b006
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2022
ms.locfileid: "66996230"
---
# <a name="international-classification-of-diseases-icd-10-cm"></a>Classification internationale des maladies (ICD-10-CM)

## <a name="format"></a>Format

Dictionary

## <a name="pattern"></a>Modèle

Mot clé

## <a name="checksum"></a>Somme de contrôle

Non

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- Un mot clé figurant dans la liste `Dictionary_icd_10_updated` est trouvé.
- Un mot clé figurant dans la liste `Dictionary_icd_10_codes` est trouvé.

Une stratégie DLP a une confiance moyenne ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- Un mot clé figurant dans la liste `Dictionary_icd_10_ updated` est trouvé.

```xml
      <!-- ICD-10 CM -->
      <Entity id="3356946c-6bb7-449b-b253-6ffa419c0ce7" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Dictionary_icd_10_updated" />
          <Match idRef="Dictionary_icd_10_codes" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Dictionary_icd_10_updated" />
        </Pattern>

```

## <a name="keywords"></a>Mots-clés

Tout terme du dictionnaire de `Dictionary_icd_10_updated` mots clés, qui est basé sur la [classification internationale des maladies, dixième révision, modification clinique (ICD-10-CM)](https://icd10cmtool.cdc.gov/) . Ce type recherche uniquement le terme, pas les codes d’assurance.

Tout terme du dictionnaire de `Dictionary_icd_10_codes` mots clés, qui est basé sur la [classification internationale des maladies, dixième révision, modification clinique (ICD-10-CM)](https://icd10cmtool.cdc.gov/) . Ce type recherche uniquement les codes d’assurance, pas la description.