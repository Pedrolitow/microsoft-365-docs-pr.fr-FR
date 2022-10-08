---
title: Définition d’entité de carte d’identité en Pologne
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
description: Définition d’entité de type d’entité de type d’informations sensibles de carte d’identité en Pologne.
ms.openlocfilehash: cf0cd4abe57c3b27bb97d17673be0f855c1bab96
ms.sourcegitcommit: 176bbd29c92e1c0812e8bcd1e1e4938a3e1d7331
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/05/2022
ms.locfileid: "68469997"
---
# <a name="poland-identity-card"></a>Carte d'identité polonaise

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="format"></a>Format

trois lettres et six chiffres

## <a name="pattern"></a>Modèle

trois lettres (non sensibles à la casse) suivies de six chiffres

## <a name="checksum"></a>Somme de contrôle

Oui

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_polish_national_id` trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keyword_polish_national_id_passport_number` est trouvé.
- La somme de contrôle est correcte.

```xml
<!-- Poland Identity Card-->
<Entity id="25E64989-ED5D-40CA-A939-6C14183BB7BF" patternsProximity="300" recommendedConfidence="85">
      <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_polish_national_id" />
          <Match idRef="Keyword_polish_national_id_passport_number" />
      </Pattern>
</Entity>
```

## <a name="keywords"></a>Mots-clés

### <a name="keyword_poland_national_id_passport_number"></a>Keyword_poland_national_id_passport_number

- Dowód osobisty
- Numer dowodu osobistego
- Nazwa i numer dowodu osobistego
- Nazwa i nr dowodu osobistego
- Nazwa je nr dowodu tożsamości
- Dowód Tożsamości
- Dow. Os.
