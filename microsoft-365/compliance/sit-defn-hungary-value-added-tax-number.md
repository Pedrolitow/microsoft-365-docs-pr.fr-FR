---
title: Définition d’entité de numéro de taxe sur la valeur ajoutée en Hongrie
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
description: Définition d’entité de type d’information sensible de numéro de taxe à valeur ajoutée en Hongrie.
ms.openlocfilehash: 7523bc370177884d058faad4b6313552e8ba3964
ms.sourcegitcommit: 72d10d0bc29ecc8b19c395f1815dc48b549096d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2022
ms.locfileid: "67367398"
---
# <a name="hungary-value-added-tax-number"></a>Numéro de taxe sur la valeur ajoutée en Hongrie

## <a name="format"></a>Format

Modèle alphanumérique de 10 caractères

## <a name="pattern"></a>Modèle

Modèle alphanumérique de 10 caractères :

- deux lettres - HU ou hu
- espace facultatif
- huit chiffres

## <a name="checksum"></a>Somme de contrôle

Oui

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_hungarian_value_added_tax_number` trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keywords_hungarian_value_added_tax_number` est trouvé.

Une stratégie DLP a une confiance moyenne ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_hungarian_value_added_tax_number` trouve un contenu qui correspond au modèle.

```xml
      <!-- Hungarian Value Added Tax Number -->
      <Entity id="976349a0-683b-477a-90f8-ff0a220d5592" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_hungarian_value_added_tax_number" />
          <Match idRef="Keywords_hungarian_value_added_tax_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_hungarian_value_added_tax_number" />
        </Pattern>
      </Entity>
```

## <a name="keywords"></a>Mots-clés

### <a name="keyword_hungary_value_added_tax_number"></a>Keyword_Hungary_value_added_tax_number

- Tva
- numéro de taxe sur la valeur ajoutée
- #tva
- vatno #
- hungarianvatno #
- tax no.
- taxe sur la valeur ajoutée áfa
- közösségi adószám
- általános forgalmi adó szám
- hozzáadottérték adó
- áfa szám