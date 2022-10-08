---
title: Royaume-Uni définition d’entité de numéro de service de santé national
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
description: Royaume-Uni définition d’entité de type d’information sensible de numéro de service de santé national.
ms.openlocfilehash: b16ac1cc66b53bff232967aedc8b9f5265908d0e
ms.sourcegitcommit: 176bbd29c92e1c0812e8bcd1e1e4938a3e1d7331
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/05/2022
ms.locfileid: "68472253"
---
# <a name="uk-national-health-service-number"></a>Royaume-Uni numéro de service de santé national

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="format"></a>Format

10 à 17 chiffres séparés par des espaces

## <a name="pattern"></a>Modèle

10 à 17 chiffres :

- 3 ou 10 chiffres
- un espace
- trois chiffres
- un espace
- quatre chiffres

## <a name="checksum"></a>Somme de contrôle

Oui

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_uk_nhs_number` trouve un contenu qui correspond au modèle.
- L’un des cas suivants est vrai :
    - Un mot clé figurant dans la liste `Keyword_uk_nhs_number` est trouvé.
    - Un mot clé figurant dans la liste `Keyword_uk_nhs_number1` est trouvé.
    - Un mot clé figurant dans la liste `Keyword_uk_nhs_number_dob` est trouvé.
- La somme de contrôle est correcte.

```xml
<!-- U.K. NHS Number -->
<Entity id="3192014e-2a16-44e9-aa69-4b20375c9a78" patternsProximity="300" recommendedConfidence="85">
    <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_uk_nhs_number" />
        <Any minMatches="1">
          <Match idRef="Keyword_uk_nhs_number" />
          <Match idRef="Keyword_uk_nhs_number1" />
          <Match idRef="Keyword_uk_nhs_number_dob" />
        </Any>
    </Pattern>
</Entity>
```

## <a name="keywords"></a>Mots-clés

### <a name="keyword_uk_nhs_number"></a>Keyword_uk_nhs_number

- service national de santé
- Nhs
- administration des services de santé
- administration de la santé

### <a name="keyword_uk_nhs_number1"></a>Keyword_uk_nhs_number1

- id du patient
- identification du patient
- n° patient
- numéro de patient

### <a name="keyword_uk_nhs_number_dob"></a>Keyword_uk_nhs_number_dob

- Gp
- DOB
- D.d.n
- Date of Birth
- Birth Date
