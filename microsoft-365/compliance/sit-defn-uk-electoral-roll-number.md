---
title: Royaume-Uni définition d’entité de numéro de liste électorale
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
description: Royaume-Uni définition d’entité de type d’information sensible de numéro de liste électorale.
ms.openlocfilehash: c4eb8c66e389f81c1f9f99e7fd3e662203e07ed7
ms.sourcegitcommit: 176bbd29c92e1c0812e8bcd1e1e4938a3e1d7331
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/05/2022
ms.locfileid: "68472911"
---
# <a name="uk-electoral-roll-number"></a>Royaume-Uni numéro de roll de la série de nœuds

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="format"></a>Format

deux lettres suivies de 1 à 4 chiffres

## <a name="pattern"></a>Modèle

deux lettres (non sensibles à la casse) suivies de 1 à 4 chiffres

## <a name="checksum"></a>Somme de contrôle

Non

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- L’expression régulière `Regex_uk_electoral` trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keyword_uk_electoral` est trouvé.

```xml
<!-- U.K. Electoral Number -->
<Entity id="a3eea206-dc0c-4f06-9e22-aa1be3059963" patternsProximity="300" recommendedConfidence="75">
    <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_uk_electoral" />
        <Any minMatches="1">
          <Match idRef="Keyword_uk_electoral" />
        </Any>
    </Pattern>
</Entity>
```

## <a name="keywords"></a>Mots-clés

### <a name="keyword_uk_electoral"></a>Keyword_uk_electoral

- nomination au conseil
- formulaire de nomination
- registre électoral
- liste électorale
