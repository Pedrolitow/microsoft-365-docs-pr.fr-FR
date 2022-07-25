---
title: Définition de l’entité numéro d’assurance sociale du Canada
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
description: Définition d’entité de type d’entité de type d’information sensible de numéro d’assurance sociale du Canada.
ms.openlocfilehash: 9af5cc026da5ac6bd414ebd80ded934efb90effb
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2022
ms.locfileid: "66996710"
---
# <a name="canada-social-insurance-number"></a>Numéro d’assurance sociale du Canada

## <a name="format"></a>Format

neuf chiffres avec des traits d’union ou des espaces facultatifs

## <a name="pattern"></a>Modèle

Formaté:

- trois chiffres
- un trait d’union ou un espace
- trois chiffres
- un trait d’union ou un espace
- trois chiffres

Non mis en forme : neuf chiffres

## <a name="checksum"></a>Somme de contrôle

Oui

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction Func_canadian_sin trouve un contenu qui correspond au modèle.
- Au moins deux des modèles suivants :
    - Un mot clé figurant dans la liste `Keyword_sin` est trouvé.
    - Un mot clé figurant dans la liste `Keyword_sin_collaborative` est trouvé.
    - La fonction `Func_eu_date` trouve une date au format de date approprié.
- La somme de contrôle est correcte.

Une stratégie DLP a une confiance moyenne ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction Func_unformatted_canadian_sin trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keyword_sin` est trouvé.
- La somme de contrôle est correcte.

```xml
<!-- Canada Social Insurance Number -->
<Entity id="a2f29c85-ecb8-4514-a610-364790c0773e" patternsProximity="300" recommendedConfidence="75">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_canadian_sin" />
        <Any minMatches="2">
          <Match idRef="Keyword_sin" />
          <Match idRef="Keyword_sin_collaborative" />
          <Match idRef="Func_eu_date" />
        </Any>
  </Pattern>
  <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_unformatted_canadian_sin" />
        <Match idRef="Keyword_sin" />
  </Pattern>
</Entity>
```

## <a name="keywords"></a>Mots-clés

### <a name="keyword_sin"></a>Keyword_sin

- assoc
- assurance sociale
- numéro d’assurance sociale
- Péchés
- nss
- ssns
- sécurité sociale
- numéro d’assurance sociale
- numéro d’identification nationale
- id national
- Péché #
- ass soc
- ass sociale

### <a name="keyword_sin_collaborative"></a>Keyword_sin_collaborative

- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- DOB
- Birthdate
- Birthday
- Date of Birth