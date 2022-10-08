---
title: Définition d’entité de numéro de taxe à valeur ajoutée aux Pays-Bas
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
description: Définition d’entité de type d’entité de type d’informations sensibles de numéro de taxe à valeur ajoutée aux Pays-Bas.
ms.openlocfilehash: 58a366d6d13efde59b79c9078fd3d721cbf8ce78
ms.sourcegitcommit: 6df492719fecc2b213d55465dc1cd60ab4627ed6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2022
ms.locfileid: "68381432"
---
# <a name="netherlands-value-added-tax-number"></a>Numéro de TVA hollandais

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="format"></a>Format

Modèle alphanumérique à 14 caractères

## <a name="pattern"></a>Modèle

Modèle alphanumérique à 14 caractères :

- N ou n
- L ou l
- espace facultatif, point ou trait d’union
- neuf chiffres
- espace facultatif, point ou trait d’union
- B ou b
- deux chiffres

## <a name="checksum"></a>Somme de contrôle

Oui

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_netherlands_value_added_tax_number` trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keywords_netherlands_value_added_tax_number` est trouvé.

Une stratégie DLP a une confiance moyenne ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_netherlands_value_added_tax_number` trouve un contenu qui correspond au modèle.

```xml
      <!-- Netherlands Value Added Tax Number -->
      <Entity id="4f320d9b-4972-41ae-b337-88d499bb1ade" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_netherlands_value_added_tax_number" />
          <Match idRef="Keywords_netherlands_value_added_tax_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_netherlands_value_added_tax_number" />
        </Pattern>
      </Entity>
```

## <a name="keywords"></a>Mots-clés

### <a name="keyword_netherlands_value_added_tax_number"></a>Keyword_netherlands_value_added_tax_number

- numéro de tva
- nº de TVA
- nº de TVA
- wearde tafoege tax getal
- btw nûmer
- btw-nummer
