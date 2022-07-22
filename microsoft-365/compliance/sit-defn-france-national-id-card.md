---
title: Définition d’entité de la Carte nationale d’identité (CNI) en France
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
description: Définitions d’entité des type d’informations sensibles de la Carte nationale d’identité (CNI) en France.
ms.openlocfilehash: 35a6481e657d20a83ed1b80a6d06ad8ebf1c9cdf
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2022
ms.locfileid: "66950881"
---
# <a name="france-national-id-card-cni"></a>Carte d’ID nationale (CNI) en France

## <a name="format"></a>Format

12 chiffres

## <a name="pattern"></a>Modèle

12 chiffres

## <a name="checksum"></a>Somme de contrôle

Non

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance faible ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- L’expression régulière `Regex_france_cni` trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keywords_france_eu_national_id_card` est trouvé.

```xml
    <!-- France CNI -->
    <Entity id="f741ac74-1bc0-4665-b69b-f0c7f927c0c4" patternsProximity="300" recommendedConfidence="65">
      <Pattern confidenceLevel="65">
        <IdMatch idRef="Regex_france_cni" />
        <Match idRef="Keywords_france_eu_national_id_card" />
      </Pattern>
    </Entity>
```

## <a name="keywords"></a>Mots-clés

### <a name="keywords_france_eu_national_id_card"></a>Keywords_france_eu_national_id_card

- numéro de carte
- carte nationale d'identité
- carte nationale d'identité no
- cni#
- cni
- compte bancaire
- numéro d’identification nationale
- nationale d’identité
- nationalidno#
- numéro d'assurance maladie
- numéro de carte vitale