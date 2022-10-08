---
title: Définition d’entité du code d’identification de la population thaïlandaise
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
description: Définition d’entité de type d’entité du code d’identification de la population thaïlandaise.
ms.openlocfilehash: 6d39a5a95a4969af61b32bec474d8d3b025f8f8a
ms.sourcegitcommit: 176bbd29c92e1c0812e8bcd1e1e4938a3e1d7331
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/05/2022
ms.locfileid: "68471956"
---
# <a name="thai-population-identification-code"></a>Code d’identification de la population thaïe

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="format"></a>Format

13 chiffres

## <a name="pattern"></a>Modèle

13 chiffres :

- premier chiffre n’est pas zéro ou neuf
- 12 chiffres

## <a name="checksum"></a>Somme de contrôle

Oui

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_Thai_Citizen_Id` trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keyword_Thai_Citizen_Id` est trouvé.

Une stratégie DLP a une confiance moyenne ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_Thai_Citizen_Id` trouve un contenu qui correspond au modèle.

```xml
<!-- Thai Citizen ID -->
-<Entity id="44ca9e86-ead7-4c5d-884a-e2eaa401515e" recommendedConfidence="75" patternsProximity="300">
   -<Pattern confidenceLevel="85">
      <IdMatch idRef="Func_Thai_Citizen_Id"/>
      <Match idRef="Keyword_Thai_Citizen_Id"/>
   </Pattern>
   -<Pattern confidenceLevel="75">
      <IdMatch idRef="Func_Thai_Citizen_Id"/>
   </Pattern>
</Entity>
```

## <a name="keywords"></a>Mots-clés

### <a name="keyword_thai_citizen_id"></a>Keyword_thai_citizen_Id

- ID Number
- Numéro d’identification
- บัตรประชาชน
- รหัสบัตรประชาชน
- บัตรประชาชน
- รหัสบัตรประชาชน
