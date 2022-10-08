---
title: Définition de l’entité numéro de carte de résidence du Japon
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
description: Définition d’entité de type d’entité de type d’information sensible de numéro de résidence du Japon.
ms.openlocfilehash: a4e9c090515f25ffcf22504e171f94e1ceaee7b3
ms.sourcegitcommit: 6df492719fecc2b213d55465dc1cd60ab4627ed6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2022
ms.locfileid: "68381696"
---
# <a name="japan-residence-card-number"></a>Numéro de carte de résidence au Japon

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="format"></a>Format

12 lettres et chiffres

## <a name="pattern"></a>Modèle

12 lettres et chiffres :

- deux lettres (non sensibles à la casse)
- huit chiffres
- deux lettres (non sensibles à la casse)

## <a name="checksum"></a>Somme de contrôle

Non

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- L’expression régulière `Regex_jp_residence_card_number` trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keyword_jp_residence_card_number` est trouvé.

```xml
<!--Japan Residence Card Number-->
-<Entity id="ac36fef2-a289-4e2c-bb48-b02366e89fc0" recommendedConfidence="75" patternsProximity="300">
   -<Pattern confidenceLevel="75">
      <IdMatch idRef="Regex_jp_residence_card_number"/>
      <Match idRef="Keyword_jp_residence_card_number"/>
   </Pattern>
</Entity>
```

## <a name="keywords"></a>Mots-clés

### <a name="keyword_jp_residence_card_number"></a>Keyword_jp_residence_card_number

- Numéro de carte de séjour
- Carte de séjour no
- Carte de séjour #
- 在留カード番号
- 在留カード
- 在留番号
