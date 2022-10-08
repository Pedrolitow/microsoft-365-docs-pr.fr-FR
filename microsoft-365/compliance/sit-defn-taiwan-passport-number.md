---
title: Définition de l’entité numéro de passeport taïwanais
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
description: Définition d’entité de type d’entité de type d’informations sensibles de numéro de passeport de Taïwan.
ms.openlocfilehash: ab4284b88be490c7c56c058fa9b73ce337516b7a
ms.sourcegitcommit: 176bbd29c92e1c0812e8bcd1e1e4938a3e1d7331
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/05/2022
ms.locfileid: "68471989"
---
# <a name="taiwan-passport-number"></a>Numéro de passeport taïwanais

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="format"></a>Format

- numéro de passeport biométrique : neuf chiffres
- Numéro de passeport non biométrique : neuf chiffres

## <a name="pattern"></a>Modèle

numéro de passeport biométrique :

- le caractère « 3 »
- huit chiffres

numéro de passeport non biométrique :

- neuf chiffres

## <a name="checksum"></a>Somme de contrôle

Non

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- L’expression régulière `Regex_taiwan_passport` trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keyword_taiwan_passport` est trouvé.

```xml
<!-- Taiwan Passport Number -->
<Entity id="e7251cb4-4c2c-41df-963e-924eb3dae04a" recommendedConfidence="75" patternsProximity="300">
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Regex_taiwan_passport"/>
     <Match idRef="Keyword_taiwan_passport"/>
  </Pattern>
</Entity>
```

## <a name="keywords"></a>Mots-clés

### <a name="keyword_taiwan_passport"></a>Keyword_taiwan_passport

- ROC passport number
- Passport number
- Passport no
- Passport Num
- Passport #
- 护照
- 中華民國護照
- Zhōnghuá Mínguó hùzhào
