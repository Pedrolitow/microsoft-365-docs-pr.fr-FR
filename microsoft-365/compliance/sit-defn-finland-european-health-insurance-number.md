---
title: Définition de l’entité numéro d’assurance maladie européenne en Finlande
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
description: Définition d’entité de type d’entité de type d’information sensible de numéro d’assurance maladie européen en Finlande.
ms.openlocfilehash: d2a1a509bc2a466d504eb9cd9766ed1c998498db
ms.sourcegitcommit: be2334dbcd4e1bf309349d981a68a30e06de0297
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2022
ms.locfileid: "68379873"
---
# <a name="finland-european-health-insurance-number"></a>Numéro d’assurance maladie européen en Finlande

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="format"></a>Format

Nombre à 20 chiffres

## <a name="pattern"></a>Modèle

Nombre à 20 chiffres :

- 10 chiffres - 8024680246
- un espace ou un trait d’union facultatif
- 10 chiffres

## <a name="checksum"></a>Somme de contrôle

Non

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- L’expression `Regex_Finland_European_Health_Insurance_Number` régulière recherche le contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keyword_Finland_European_Health_Insurance_Number` est trouvé.

```xml
      <!-- Finland European Health Insurance Number -->
      <Entity id="60f75aed-81bf-4625-89b0-0846b9248ee7" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_Finland_European_Health_Insurance_Number"/>
          <Match idRef="Keyword_Finland_European_Health_Insurance_Number"/>
        </Pattern>
      </Entity>
```

## <a name="keywords"></a>Mots-clés

### <a name="keyword_finland_european_health_insurance_number"></a>Keyword_finland_european_health_insurance_number

- Ceam #
- Ceam
- finlandehicnumber #
- finska sjukförsäkringskort
- carte d’intégrité
- carte d’assurance maladie
- numéro d’assurance maladie
- hälsokort
- sairaanhoitokortin
- sairausvakuutuskortti
- sairausvakuutusnumero
- sjukförsäkring nummer
- sjukförsäkringskort
- suomen sairausvakuutuskortti
- terveyskortti
