---
title: Définition d’entité d’ID nationale suédoise
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
description: Définition d’entité de type d’entité de type d’informations sensibles d’ID national de Suède.
ms.openlocfilehash: 77d0fd72a4293bdc8cae0aa806899b30baa21ed8
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2022
ms.locfileid: "66997319"
---
# <a name="sweden-national-id"></a>ID national suédois

## <a name="format"></a>Format

10 ou 12 chiffres et éventuellement un délimiteur

## <a name="pattern"></a>Modèle

10 ou 12 chiffres et un délimiteur facultatif :

- deux chiffres (facultatif)
- Six chiffres au format de date AAMMJJ
- délimiteur de « - » ou « + » (facultatif)
- quatre chiffres

## <a name="checksum"></a>Somme de contrôle

Oui

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_swedish_national_identifier` trouve un contenu qui correspond au modèle.
- Un mot clé à partir de `Keywords_swedish_national_identifier` est trouvé
- La somme de contrôle est correcte.

Une stratégie DLP a une confiance moyenne ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_swedish_national_identifier` trouve un contenu qui correspond au modèle.
- La somme de contrôle est correcte.

```xml
    <!-- Sweden National ID -->
    <Entity id="f69aaf40-79be-4fac-8f05-fd1910d272c8" patternsProximity="300" recommendedConfidence="85">
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_swedish_national_identifier" />
        <Match idRef="Keywords_swedish_national_identifier" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_swedish_national_identifier" />
      </Pattern>
    </Entity>
```

## <a name="keywords"></a>Mots-clés

### <a name="keywords_swedish_national_identifier"></a>Keywords_swedish_national_identifier

- id no
- numéro d’ID
- Id #
- identification no
- numéro d’identification
- identifikationsnumret #
- identifikationsnumret
- identitetshandling
- document d’identité
- identity no
- numéro d’identité
- id-nummer
- ID personnel
- personnummer #
- personnummer
- skatteidentifikationsnummer