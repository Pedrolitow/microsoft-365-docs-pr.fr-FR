---
title: Définition d’entité de numéro de protection sociale en Nouvelle-Zélande
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
description: Définition d’entité de type d’entité de type d’information sensible de numéro de protection sociale en Nouvelle-Zélande.
ms.openlocfilehash: 6bd9a61fd5e54d83fedf941afc7a97653f8bef7e
ms.sourcegitcommit: 6df492719fecc2b213d55465dc1cd60ab4627ed6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2022
ms.locfileid: "68382554"
---
# <a name="new-zealand-social-welfare-number"></a>Numéro de sécurité sociale néo-zélandais

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="format"></a>Format

neuf chiffres

## <a name="pattern"></a>Modèle

neuf chiffres

- trois chiffres
- un trait d’union facultatif
- trois chiffres
- un trait d’union facultatif
- trois chiffres

## <a name="checksum"></a>Somme de contrôle

Oui

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_newzealand_social_welfare_number` trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keywords_newzealand_social_welfare_number` est trouvé.

Une stratégie DLP a une confiance faible ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_newzealand_social_welfare_number` trouve un contenu qui correspond au modèle.

```xml
      <!-- Newzealand Social Welfare Number -->
      <Entity id="20f3c48d-4ac1-4cd2-86bd-34ecc1826e9d" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_newzealand_social_welfare_number" />
          <Match idRef="Keywords_newzealand_social_welfare_number" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Func_newzealand_social_welfare_number" />
        </Pattern>
      </Entity>
    </Version>
```

## <a name="keywords"></a>Mots-clés

### <a name="keyword_new_zealand_social_welfare_number"></a>Keyword_new_zealand_social_welfare_number

- Sociale #
- Sociale #
- bien-être social Non.
- numéro de bien-être social
- swn #
