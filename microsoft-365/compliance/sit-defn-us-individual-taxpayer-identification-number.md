---
title: Définition d’entité ITIN (Individual Taxpayer Identification Number) des États-Unis
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
description: Définition d’entité de type d’information sensible du numéro d’identification du contribuable (ITIN) des États-Unis.
ms.openlocfilehash: c99635c29bb5b720ecc2d70577fe66d508ce9d9c
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2022
ms.locfileid: "66997329"
---
# <a name="us-individual-taxpayer-identification-number-itin"></a>Numéro d’identification des particuliers américains (ITIN)

## <a name="format"></a>Format

neuf chiffres qui commencent par un « 9 » et contiennent « 7 » ou « 8 » comme quatrième chiffre, éventuellement mis en forme avec des espaces ou des tirets

## <a name="pattern"></a>Modèle

Formaté:

- le chiffre « 9 »
- deux chiffres
- un espace ou un tiret
- un « 7 » ou « 8 »
- un chiffre
- un espace ou un tiret
- quatre chiffres

Mémoire:

- le chiffre « 9 »
- deux chiffres
- un « 7 » ou « 8 »
- cinq chiffres

## <a name="checksum"></a>Somme de contrôle

Non

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_formatted_itin` trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keyword_itin` est trouvé.

Une stratégie DLP a une confiance moyenne ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_unformatted_itin` trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keyword_itin` est trouvé.

Une stratégie DLP a une confiance faible ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_formatted_itin` ou `Func_unformatted_itin` trouve un contenu qui correspond au modèle.

```xml
    <!-- U.S. Individual Taxpayer Identification Number (ITIN) -->
    <Entity id="e55e2a32-f92d-4985-a35d-a0b269eb687b" patternsProximity="300" recommendedConfidence="75">
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_formatted_itin" />
        <Match idRef="Keyword_itin" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_unformatted_itin" />
        <Match idRef="Keyword_itin" />
      </Pattern>
      <Pattern confidenceLevel="65">
        <IdMatch idRef="Func_formatted_itin" />
      </Pattern>
      <Pattern confidenceLevel="65">
        <IdMatch idRef="Func_unformatted_itin" />
      </Pattern>
    </Entity>
```

## <a name="keywords"></a>Mots-clés

### <a name="keyword_itin"></a>Keyword_itin

- Contribuable
- id fiscal
- identification fiscale
- itin
- i.t.i.n.
- nss
- Étain
- sécurité sociale
- contribuable
- itins
- taxid
- contribuable individuel