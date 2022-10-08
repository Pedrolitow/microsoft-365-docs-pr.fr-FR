---
title: Définition d’entité de carte d’identité nationale (CNI) en France
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
description: Définition d’entité de type d’information sensible de carte d’identité nationale (CNI) en France.
ms.openlocfilehash: fae2db81a39de5ff583a363ce426484f54a52230
ms.sourcegitcommit: be2334dbcd4e1bf309349d981a68a30e06de0297
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2022
ms.locfileid: "68379565"
---
# <a name="france-national-id-card-cni"></a>Carte d’identité nationale de France (CNI)

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

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
