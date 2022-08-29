---
title: Définition de l’entité nationale de passeport de l’Ukraine
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
description: Définition d’entité de type d’information sensible nationale de passeport de l’Ukraine.
ms.openlocfilehash: 7a941d28dc92f54ceb1c2f00d910b0ba1722bfa0
ms.sourcegitcommit: 72d10d0bc29ecc8b19c395f1815dc48b549096d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2022
ms.locfileid: "67367310"
---
# <a name="ukraine-passport-domestic"></a>Passeport interne ukrainien

## <a name="format"></a>Format

neuf chiffres

## <a name="pattern"></a>Modèle

neuf chiffres

## <a name="checksum"></a>Somme de contrôle

Non

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- L’expression `Regex_Ukraine_Passport_Domestic` régulière recherche le contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keyword_Ukraine_Passport_Domestic` est trouvé.

```xml
      <!-- Ukraine Passport Domestic -->
      <Entity id="1817a540-221f-4459-9202-3bd78b81d803" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_Ukraine_Passport_Domestic"/>
          <Match idRef="Keyword_Ukraine_Passport_Domestic"/>
        </Pattern>
      </Entity>
```

## <a name="keywords"></a>Mots-clés

### <a name="keyword_ukraine_passport_domestic"></a>Keyword_ukraine_passport_domestic

- passeport ukraine
- numéro de passeport
- n° de passeport
- паспорт України
- номер паспорта
- персональний