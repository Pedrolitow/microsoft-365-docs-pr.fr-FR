---
title: Définition d’entité de carte d’identité de Chypre
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
description: Définition d’entité de type d’entité de type d’informations sensibles de carte d’identité de Chypre.
ms.openlocfilehash: 8ba4861932a1ac04941b850e8eb27f6498d3a455
ms.sourcegitcommit: 2ff545246fec060ea7829da5afbc1cdc698d51ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2022
ms.locfileid: "68361713"
---
# <a name="cyprus-identity-card"></a>Carte d’identité de l’Espagne

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="format"></a>Format

10 chiffres sans espaces et délimiteurs

## <a name="pattern"></a>Modèle

10 chiffres

## <a name="checksum"></a>Somme de contrôle

non applicable

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- L’expression régulière `Regex_cyprus_eu_national_id_card` trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keywords_cyprus_eu_national_id_card` est trouvé.

```xml
      <!-- Cyprus Identity Card -->
      <Entity id="3ba8afe5-7a6c-4929-8247-0001b6878438" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_cyprus_eu_national_id_card" />
          <Match idRef="Keywords_cyprus_eu_national_id_card" />
        </Pattern>
      </Entity>
```

## <a name="keywords"></a>Mots-clés

### <a name="keywords_cyprus_eu_national_id_card"></a>Keywords_cyprus_eu_national_id_card

- Numéro de carte d’ID
- numéro de carte d’identité
- kimlik karti
- numéro d’identification nationale
- numéro d’ID personnel
- ταυτοτητασ
