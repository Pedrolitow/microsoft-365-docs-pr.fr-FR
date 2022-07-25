---
title: Définition de l’entité numéro de passeport en Australie
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
description: Définition d’entité de type d’entité de type d’informations sensibles de numéro de passeport en Australie.
ms.openlocfilehash: 9f879dc2f071398f7c3ba49b7fcded8be220e07b
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2022
ms.locfileid: "66996149"
---
# <a name="australia-passport-number"></a>Numéro de passeport Australie

## <a name="format"></a>Format

huit ou neuf caractères alphanumériques

## <a name="pattern"></a>Modèle

- une lettre (N, E, D, F, A, C, U, X) suivie de sept chiffres ou
- Deux lettres (PA, PB, PC, PD, PE, PF, PU, PW, PX, PZ) suivies de sept chiffres.

## <a name="checksum"></a>Somme de contrôle

Non

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- L’expression régulière `Regex_australia_passport_number` trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keyword_australia_passport_number` est trouvé.

Une stratégie DLP a une confiance faible ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- L’expression régulière `Regex_australia_passport_number` trouve un contenu qui correspond au modèle.

```xml
    <!-- Australia Passport Number -->
    <Entity id="29869db6-602d-4853-ab93-3484f905df50" patternsProximity="300" recommendedConfidence="75" relaxProximity="true">
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_australia_passport_number" />
        <Match idRef="Keyword_australia_passport_number" />
      </Pattern>
      <Pattern confidenceLevel="65">
        <IdMatch idRef="Regex_australia_passport_number" />
      </Pattern>
    </Entity>
```

## <a name="keywords"></a>Mots-clés

### <a name="keyword_australia_passport_number"></a>Keyword_australia_passport_number

- Passeport #
- Passeport #
- passportid
- Passeports
- passportno
- passport no
- numéropasseport
- numéro de passeport
- passportnumbers
- numéros de passeport
- informations sur le passeport
- immigration et citoyenneté
- Australie
- service de l’immigration
- Carte nationale d’identité
- document de voyage
- autorité émettrice