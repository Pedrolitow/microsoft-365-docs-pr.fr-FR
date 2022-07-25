---
title: Définition de l’entité numéro de service de santé du Canada
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
description: Définition d’entité de type d’entité de type d’information sensible de numéro de service de santé du Canada.
ms.openlocfilehash: ea98e3861b1969506ecbd4f35f23d72b8f92a295
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2022
ms.locfileid: "66997694"
---
# <a name="canada-health-service-number"></a>Numéro du service de santé du Canada

## <a name="format"></a>Format

 10 chiffres

## <a name="pattern"></a>Modèle

10 chiffres

## <a name="checksum"></a>Somme de contrôle

Non

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- L’expression régulière `Regex_canada_health_service_number` trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keyword_canada_health_service_number` est trouvé.

```xml
<!-- Canada Health Service Number -->
<Entity id="59c0bf39-7fab-482c-af25-00faa4384c94" patternsProximity="300" recommendedConfidence="75">
  <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_canada_health_service_number" />
        <Any minMatches="1">
          <Match idRef="Keyword_canada_health_service_number" />
        </Any>
  </Pattern>
</Entity>
```

## <a name="keywords"></a>Mots-clés

### <a name="keyword_canada_health_service_number"></a>Keyword_canada_health_service_number

- numéro d’assurance-maladie
- informations sur le patient
- services de santé
- services spécialisés
- accident automobile
- hôpital pour malades
- Psychiatre
- indemnisation des salariés
- Handicap