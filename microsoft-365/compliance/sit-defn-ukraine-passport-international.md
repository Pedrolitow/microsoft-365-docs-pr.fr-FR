---
title: Définition de l’entité internationale passeport ukraine
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
description: Définition d’entité du type d’informations sensibles internationales passeport en Ukraine.
ms.openlocfilehash: 91e15a1d39c95ceb00186b6521d79cd4172b72cb
ms.sourcegitcommit: 176bbd29c92e1c0812e8bcd1e1e4938a3e1d7331
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/05/2022
ms.locfileid: "68470416"
---
# <a name="ukraine-passport-international"></a>Passeport Ukrainien International

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="format"></a>Format

Modèle alphanumérique à huit caractères

## <a name="pattern"></a>Modèle

Modèle alphanumérique à huit caractères :

- deux lettres ou chiffres
- six chiffres

## <a name="checksum"></a>Somme de contrôle

Non

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- L’expression `Regex_Ukraine_Passport_International` régulière recherche le contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keyword_Ukraine_Passport_International` est trouvé.

```xml
      <!-- Ukraine Passport International -->
      <Entity id="cfbe032d-22e0-4f28-ab68-d66e9641f1e2" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_Ukraine_Passport_International"/>
          <Match idRef="Keyword_Ukraine_Passport_International"/>
        </Pattern>
      </Entity>
```

## <a name="keywords"></a>Mots-clés

### <a name="keyword_ukraine_passport_international"></a>Keyword_ukraine_passport_international

- passeport ukraine
- numéro de passeport
- n° de passeport
- паспорт України
- номер паспорта
