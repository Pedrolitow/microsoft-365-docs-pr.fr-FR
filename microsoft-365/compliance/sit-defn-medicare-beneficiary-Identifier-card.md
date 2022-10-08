---
title: Définition de l’entité de carte Medicare Beneficiary Identifier (MBI)
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
description: Définition d’entité de type d’entité d’identificateur de bénéficiaire d’assurance-maladie (MBI).
ms.openlocfilehash: 7ee3545a7a0eb177f7cf8cbb6581aa43546c8f88
ms.sourcegitcommit: 6df492719fecc2b213d55465dc1cd60ab4627ed6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2022
ms.locfileid: "68382449"
---
# <a name="medicare-beneficiary-identifier-mbi-card"></a>Carte d’identificateur du bénéficiaire (MBI)

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="format"></a>Format

Modèle alphanumérique à 11 caractères

## <a name="pattern"></a>Modèle

- un chiffre compris entre 1 et 9
- une lettre à l’exclusion de S, L, O, I, B, Z
- un chiffre ou une lettre à l’exclusion de S, L, O, I, B, Z
- un chiffre
- un trait d’union facultatif
- une lettre à l’exclusion de S, L, O, I, B, Z
- un chiffre ou une lettre à l’exclusion de S, L, O, I, B, Z
- un chiffre
- un trait d’union facultatif
- deux lettres à l’exclusion de S, L, O, I, B, Z
- deux chiffres

## <a name="checksum"></a>Somme de contrôle

Non

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- L’expression régulière `Regex_mbi_card` trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keyword_mbi_card` est trouvé.

Une stratégie DLP a une confiance moyenne ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- L’expression régulière `Regex_mbi_card` trouve un contenu qui correspond au modèle.

```xml
    <!-- Medicare Beneficiary Identifier (MBI) card -->
      <Entity id="f753a286-f5cc-47e6-a592-4be25fd02591" patternsProximity="300" recommendedConfidence="75" relaxProximity="true">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_mbi_card" />
          <Match idRef="Keyword_mbi_card" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_mbi_card" />
        </Pattern>
      </Entity>
```

## <a name="keywords"></a>Mots-clés

### <a name="keyword_mbi_card"></a>Keyword_mbi_card

- Mbi
- Mbi #
- bénéficiaire de l’assurance-maladie #
- Identificateur du bénéficiaire de l’assurance-maladie
- bénéficiaire de l’assurance-maladie non
- numéro de bénéficiaire de l’assurance-maladie
- bénéficiaire de l’assurance-maladie #
