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
- tier3
- purview-compliance
hideEdit: true
feedback_system: None
recommendations: false
description: Définitions de l’entité du type d’informations sensibles du numéro d’identifiant fiscal français.
ms.openlocfilehash: 59fed01945647b483601a1917fe50f2b37732ac2
ms.sourcegitcommit: be2334dbcd4e1bf309349d981a68a30e06de0297
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2022
ms.locfileid: "68380005"
---
# <a name="france-health-insurance-number"></a>Numéro d’assurance maladie en France

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

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
