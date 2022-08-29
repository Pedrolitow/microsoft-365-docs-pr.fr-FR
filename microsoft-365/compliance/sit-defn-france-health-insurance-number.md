---
title: Définition de l’entité du numéro d’assurance maladie en France
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
description: Définitions de l’entité du type d’informations sensibles du numéro d’identifiant fiscal français.
ms.openlocfilehash: 34076914498182076196c6335980d9653ba9e1f9
ms.sourcegitcommit: 72d10d0bc29ecc8b19c395f1815dc48b549096d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2022
ms.locfileid: "67369966"
---
# <a name="france-health-insurance-number"></a>Numéro d’assurance maladie en France

## <a name="format"></a>Format

Nombre à 21 chiffres

## <a name="pattern"></a>Modèle

Nombre à 21 chiffres :

- 10 chiffres
- un espace facultatif
- 10 chiffres
- un espace facultatif
- un chiffre

## <a name="checksum"></a>Somme de contrôle

Non

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- le regex `Regex_France_Health_Insurance_Number` trouve un contenu qui correspond au modèle.
- un mot clé figurant dans la liste `Keyword_France_Health_Insurance_Number` est trouvé.

```xml
      <!-- France Health Insurance Number -->
      <Entity id="9bc2069e-76df-4ff9-ac02-2f519469e236" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_France_Health_Insurance_Number"/>
          <Match idRef="Keyword_France_Health_Insurance_Number"/>
        </Pattern>
      </Entity>
```
## <a name="keywords"></a>Mots-clés

### <a name="keyword_france_health_insurance_number"></a>Keyword_France_health_insurance_number

- carte d’assurance
- carte vitale
- carte d’assuré social