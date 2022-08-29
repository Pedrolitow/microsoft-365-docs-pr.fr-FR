---
title: Définition d’entité de carte d’identité en Autriche
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
description: Définition d’entité de type d’entité de type d’informations sensibles de carte d’identité en Autriche.
ms.openlocfilehash: d180c3e46c3810997bfe54a3521c840f833aff02
ms.sourcegitcommit: 72d10d0bc29ecc8b19c395f1815dc48b549096d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2022
ms.locfileid: "67367618"
---
# <a name="austria-identity-card"></a>Carte d’identité Autriche

## <a name="format"></a>Format

Combinaison de 24 caractères de lettres, de chiffres et de caractères spéciaux

## <a name="pattern"></a>Modèle

24 caractères :

- 22 lettres (non sensibles à la casse), chiffres, barres obliques, barres obliques ou signes plus

- deux lettres (non sensibles à la casse), chiffres, barres obliques inverses, barres obliques, signes plus ou signes égaux

## <a name="checksum"></a>Somme de contrôle

Non applicable

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- L’expression régulière `Regex_austria_eu_national_id_card` trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keywords_austria_eu_national_id_card` est trouvé.

```xml
      <!-- Austria Identity Card -->
      <Entity id="5ec06c3b-007e-4820-8343-7ff73b889735" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_austria_eu_national_id_card" />
          <Match idRef="Keywords_austria_eu_national_id_card" />
        </Pattern>
      </Entity>
```

## <a name="keywords"></a>Mots-clés

### <a name="keywords_austria_eu_national_id_card"></a>Keywords_austria_eu_national_id_card

- numéro d’identité
- id national
- personalausweis republik österreich