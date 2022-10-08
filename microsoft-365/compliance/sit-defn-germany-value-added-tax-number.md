---
title: Définition de l’entité numéro de taxe sur la valeur ajoutée en Allemagne
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
description: Définition d’entité de type d’information sensible de numéro de taxe à valeur ajoutée en Allemagne.
ms.openlocfilehash: 53fc7e75d2a9758336d4ba65acdfef6fbad68a08
ms.sourcegitcommit: be2334dbcd4e1bf309349d981a68a30e06de0297
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2022
ms.locfileid: "68378817"
---
# <a name="germany-value-added-tax-number"></a>Numéro de taxe sur la valeur ajoutée en Allemagne

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="format"></a>Format

Modèle alphanumérique à 11 caractères

## <a name="pattern"></a>Modèle

Modèle alphanumérique à 11 caractères :

- une lettre D ou d
- une lettre E ou e
- un espace facultatif
- trois chiffres
- un espace facultatif ou une virgule
- trois chiffres
- un espace facultatif ou une virgule
- trois chiffres

## <a name="checksum"></a>Somme de contrôle

Oui

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_germany_value_added_tax_number` trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keywords_germany_value_added_tax_number` est trouvé.

Une stratégie DLP a une confiance moyenne ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_germany_value_added_tax_number` trouve un contenu qui correspond au modèle.

```xml
      <!-- Germany Value Added Tax Number -->
      <Entity id="db177eb2-8811-4842-bffc-128c14aa219f" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_germany_value_added_tax_number" />
          <Match idRef="Keywords_germany_value_added_tax_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_germany_value_added_tax_number" />
        </Pattern>
      </Entity>
```
## <a name="keywords"></a>Mots-clés

### <a name="keyword_germany_value_added_tax_number"></a>Keyword_germany_value_added_tax_number

- numéro de tva
- nº de TVA
- nº de TVA
- vat# mehrwertsteuer
- mwst
- mehrwertsteuer identifikationsnummer
- mehrwertsteuer nummer
