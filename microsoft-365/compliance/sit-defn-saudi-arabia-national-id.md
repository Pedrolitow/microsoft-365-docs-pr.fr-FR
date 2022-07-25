---
title: Définition de l’entité d’ID national d’Arabie saoudite
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
description: Définition de type d’entité d’information sensible d’ID national d’Arabie saoudite.
ms.openlocfilehash: c5bfa2560959caa0aa6115f4e25e8d09c8dffb5e
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2022
ms.locfileid: "66996329"
---
# <a name="saudi-arabia-national-id"></a>ID national Arabie saoudite

## <a name="format"></a>Format

10 chiffres

## <a name="pattern"></a>Modèle

10 chiffres consécutifs

## <a name="checksum"></a>Somme de contrôle

Non

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- L’expression régulière `Regex_saudi_arabia_national_id` trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keyword_saudi_arabia_national_id` est trouvé.

```xml
<!-- Saudi Arabia National ID -->
<Entity id="8c5a0ba8-404a-41a3-8871-746aa21ee6c0" patternsProximity="300" recommendedConfidence="75">
    <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_saudi_arabia_national_id" />
        <Any minMatches="1">
          <Match idRef="Keyword_saudi_arabia_national_id" />
        </Any>
    </Pattern>
</Entity>
```

## <a name="keywords"></a>Mots-clés

### <a name="keyword_saudi_arabia_national_id"></a>Keyword_saudi_arabia_national_id

- Carte d’identification
- numéro de carte d’identité
- Numéro d’identification
- الوطنية الهوية بطاقة رقم