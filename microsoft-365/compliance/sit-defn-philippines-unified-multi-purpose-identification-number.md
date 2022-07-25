---
title: Définition d’entité de numéro d’identification multi-usage unifiée aux Philippines
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
description: Définition d’entité de type d’information sensible de numéro d’identification multi-usage unifiée aux Philippines.
ms.openlocfilehash: d5e880ff8c021cdcee195077f419f3b7ab87ed36
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2022
ms.locfileid: "66997470"
---
# <a name="philippines-unified-multi-purpose-identification-number"></a>Numéro d’identification multi-usage unifié aux Philippines

## <a name="format"></a>Format

12 chiffres séparés par des traits d’union

## <a name="pattern"></a>Modèle

12 chiffres :

- quatre chiffres
- un trait d’union
- sept chiffres
- un trait d’union
- un chiffre

## <a name="checksum"></a>Somme de contrôle

Non

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- L’expression régulière `Regex_philippines_unified_id` trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keyword_philippines_id` est trouvé.

```xml
<!-- Philippines Unified Multi-Purpose ID number -->
<Entity id="019b39dd-8c25-4765-91a3-d9c6baf3c3b3" recommendedConfidence="75" patternsProximity="300">
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Regex_philippines_unified_id"/>
     <Match idRef="Keyword_philippines_id"/>
  </Pattern>
</Entity>
```

## <a name="keywords"></a>Mots-clés

### <a name="keyword_philippines_id"></a>Keyword_philippines_id

- Unified Multi-Purpose ID
- UMID
- Identity Card
- Pinag-isang Multi-Layunin ID