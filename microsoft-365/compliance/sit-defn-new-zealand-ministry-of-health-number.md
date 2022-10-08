---
title: Définition d’entité de numéro de santé du ministère néo-zélandais
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
description: Nouvelle-Zélande ministère de la santé numéro sensible information type définition d’entité.
ms.openlocfilehash: 187b0e49f6710c0fcb906dc7ba1db3563e4fa109
ms.sourcegitcommit: 6df492719fecc2b213d55465dc1cd60ab4627ed6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2022
ms.locfileid: "68383843"
---
# <a name="new-zealand-ministry-of-health-number"></a>Numéro du Ministère de la santé Nouvelle-Zélande

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="format"></a>Format

trois lettres et quatre chiffres

## <a name="pattern"></a>Modèle

- trois lettres (non sensibles à la casse) à l’exception de « I » et « O »
- quatre chiffres

## <a name="checksum"></a>Somme de contrôle

Oui

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_new_zealand_ministry_of_health_number` trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keyword_nz_terms` est trouvé.
- La somme de contrôle est correcte.

Une stratégie DLP a une confiance moyenne ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_new_zealand_ministry_of_health_number` trouve un contenu qui correspond au modèle.
- La somme de contrôle est correcte.

```xml
    <!-- New Zealand Health Number -->
    <Entity id="2b71c1c8-d14e-4430-82dc-fd1ed6bf05c7" patternsProximity="300" recommendedConfidence="85">
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_new_zealand_ministry_of_health_number" />
          <Match idRef="Keyword_nz_terms" />
      </Pattern>
      <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_new_zealand_ministry_of_health_number" />
       </Pattern>
    </Entity>
```

## <a name="keywords"></a>Mots-clés

### <a name="keyword_nz_terms"></a>Keyword_nz_terms

- NHI
- Nouvelle-Zélande
- National Health Index
- NHI #
- National Health Index #
