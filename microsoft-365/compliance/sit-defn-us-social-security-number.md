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
- M365-security-compliance
hideEdit: true
feedback_system: None
recommendations: false
description: Définition d’entité de type d’information sensible de numéro de sécurité sociale (SSN) des États-Unis.
ms.openlocfilehash: 2644ff5be51d8316007d20ec3c8918ce0e2003c1
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2022
ms.locfileid: "66950553"
---
# <a name="us-social-security-number-ssn"></a>Numéro de sécurité sociale (SSN) des États-Unis

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

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction `Func_ssn` recherche le contenu qui correspond au modèle.
- Un mot clé est `Keyword_ssn` trouvé.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction `Func_unformatted_ssn` recherche le contenu qui correspond au modèle.
- Un mot clé est `Keyword_ssn` trouvé.

Une stratégie DLP a une faible confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- `Func_randomized_formatted_ssn` Fonction ou `Func_randomized_unformatted_ssn` recherche du contenu qui correspond au modèle.
- Un mot clé est `Keyword_ssn` trouvé.

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
- SSN
- SSNS
- SSN #
- SS #
- SSID