---
title: Définition d’entité de classification internationale des maladies (ICD-9-CM)
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
description: Classification internationale des maladies (ICD-9-CM) définition d’entité de type d’information sensible.
ms.openlocfilehash: f2f482eb951066c0d3bdae084d9082cd8992da8f
ms.sourcegitcommit: be2334dbcd4e1bf309349d981a68a30e06de0297
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2022
ms.locfileid: "68378289"
---
# <a name="international-classification-of-diseases-icd-9-cm"></a>Classification internationale des maladies (ICD-9-CM)

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="format"></a>Format

Dictionary

## <a name="pattern"></a>Modèle

Mot clé

## <a name="checksum"></a>Somme de contrôle

Non

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- Un mot clé figurant dans la liste `Dictionary_icd_9_updated` est trouvé.
- Un mot clé figurant dans la liste `Dictionary_icd_9_codes` est trouvé.

Une stratégie DLP a une confiance moyenne ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- Un mot clé figurant dans la liste `Dictionary_icd_9_updated` est trouvé.

```xml
    <Entity id="fa3f9c74-ee07-4c52-b5f2-085d6b2c0ec4" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Dictionary_icd_9_updated" />
          <Match idRef="Dictionary_icd_9_codes" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Dictionary_icd_9_updated" />
        </Pattern>
      </Entity>
```

## <a name="keywords"></a>Mots-clés

Tout terme du dictionnaire de `Dictionary_icd_9_updated` mots clés, qui est basé sur la [classification internationale des maladies, neuvième révision, modification clinique (ICD-9-CM)](https://go.microsoft.com/fwlink/?linkid=852605). Ce type recherche uniquement le terme, pas les codes d’assurance.

Tout terme du dictionnaire de `Dictionary_icd_9_codes` mots clés, qui est basé sur la [classification internationale des maladies, neuvième révision, modification clinique (ICD-9-CM)](https://go.microsoft.com/fwlink/?linkid=852605). Ce type recherche uniquement les codes d’assurance, pas la description.
