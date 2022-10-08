---
title: Définition d’entité de numéro de sécurité sociale (SSN) des États-Unis
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
description: Définition d’entité de type d’information sensible de numéro de sécurité sociale (SSN) des États-Unis.
ms.openlocfilehash: 4efa2b71c062f03a93c568641e894281666d078c
ms.sourcegitcommit: 176bbd29c92e1c0812e8bcd1e1e4938a3e1d7331
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/05/2022
ms.locfileid: "68472220"
---
# <a name="us-social-security-number-ssn"></a>Numéro de sécurité sociale (SSN) américain

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="format"></a>Format

neuf chiffres, qui peuvent être dans un modèle mis en forme ou non mis en forme

> [!NOTE]
> La mise en forme d’un numéro de sécurité sociale émis avant le milieu de l’année 2011 est fixe et certaines parties du numéro doivent se situer dans certaines plages pour qu’il soit valide (mais il n’y a pas de somme de contrôle).

## <a name="pattern"></a>Modèle

quatre fonctions recherchent des SSN dans quatre modèles différents :

- `Func_ssn` recherche des SSN avec une mise en forme forte antérieure à 2011 qui sont mises en forme avec des tirets ou des espaces (ddd-dd-dd-dddd OR ddd dd dddd)
- `Func_unformatted_ssn` recherche des SSN avec une mise en forme forte antérieure à 2011 qui ne sont pas mises en forme sous la forme de neuf chiffres consécutifs (ddddddddddd)
- `Func_randomized_formatted_ssn` recherche des SSN post-2011 mis en forme avec des tirets ou des espaces (ddd-dd-dd-dddd OR ddd dd dddd)
- `Func_randomized_unformatted_ssn` recherche des SSN post-2011 qui ne sont pas mis en forme sous la forme de neuf chiffres consécutifs (dddddddddd)

## <a name="checksum"></a>Somme de contrôle

Non

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_ssn` trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keyword_ssn` est trouvé.

Une stratégie DLP a une confiance moyenne ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_unformatted_ssn` trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keyword_ssn` est trouvé.

Une stratégie DLP a une confiance faible ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_randomized_formatted_ssn` ou `Func_randomized_unformatted_ssn` trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keyword_ssn` est trouvé.

```xml
<!-- U.S. Social Security Number (SSN) -->
  <Entity id="a44669fe-0d48-453d-a9b1-2cc83f2cba77" patternsProximity="300" recommendedConfidence="75">
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_ssn" />
        <Match idRef="Keyword_ssn" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_unformatted_ssn" />
        <Match idRef="Keyword_ssn" />
      </Pattern>
      <Pattern confidenceLevel="65">
        <IdMatch idRef="Func_randomized_formatted_ssn" />
        <Match idRef="Keyword_ssn" />
      </Pattern>
      <Pattern confidenceLevel="55">
        <IdMatch idRef="Func_randomized_unformatted_ssn" />
        <Match idRef="Keyword_ssn" />
      </Pattern>
  </Entity>
```

## <a name="keywords"></a>Mots-clés

### <a name="keyword_ssn"></a>Keyword_ssn

- Numéro SSA
- numéro de sécurité sociale
- sécurité sociale #
- sécurité sociale #
- sécurité sociale non
- # sécurité sociale
- Sécu sociale
- Ssn
- SSNS
- Ssn #
- Ss #
- SSID
