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
- M365-security-compliance
hideEdit: true
feedback_system: None
recommendations: false
description: Définition d’entité de type d’entité d’identificateur de bénéficiaire d’assurance-maladie (MBI).
ms.openlocfilehash: 601c34adcb0f9b19ab2c23a3df7d1c574cdd5031
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2022
ms.locfileid: "66950830"
---
# <a name="medicare-beneficiary-identifier-mbi-card"></a>Carte d’identificateur du bénéficiaire de l’assurance-maladie (MBI)

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

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression `Regex_mbi_card` régulière recherche le contenu qui correspond au modèle.
- Un mot clé est `Keyword_mbi_card` trouvé.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression `Regex_mbi_card` régulière recherche le contenu qui correspond au modèle.

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