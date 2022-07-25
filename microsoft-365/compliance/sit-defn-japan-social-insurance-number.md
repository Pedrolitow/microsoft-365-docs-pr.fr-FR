---
title: Définition de l’entité numéro d’assurance sociale (SIN) au Japon
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
description: Définition d’entité de type d’information sensible du numéro d’assurance sociale (SIN) au Japon.
ms.openlocfilehash: 27f812ec99c1ef7c2e4d3a913c039cab4fda65e7
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2022
ms.locfileid: "66996400"
---
# <a name="japan-social-insurance-number-sin"></a>Numéro d'assurance sociale Japon

## <a name="format"></a>Format

7 à 12 chiffres

## <a name="pattern"></a>Modèle

7 à 12 chiffres :

- quatre chiffres
- un trait d’union (facultatif)
- six chiffres OR
- 7 à 12 chiffres consécutifs

## <a name="checksum"></a>Somme de contrôle

Non

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- Contenu de la fonction `Func_jp_sin finds` qui correspond au modèle.
- Un mot clé figurant dans la liste `Keyword_jp_sin` est trouvé.

Une stratégie DLP a une confiance moyenne ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_jp_sin_pre_1997` trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keyword_jp_sin` est trouvé.

```xml
<!-- Japan Social Insurance Number -->
<Entity id="c840e719-0896-45bb-84fd-1ed5c95e45ff" patternsProximity="300" recommendedConfidence="75">
    <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_jp_sin" />
        <Match idRef="Keyword_jp_sin" />
    </Pattern>
    <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_jp_sin_pre_1997" />
        <Match idRef="Keyword_jp_sin" />
    </Pattern>
</Entity>
```

## <a name="keywords"></a>Mots-clés

### <a name="keyword_jp_sin"></a>Keyword_jp_sin

- N° d’assurance sociale
- Numéro d’assurance sociale
- Numéro d’assurance sociale
- 健康保険被保険者番号
- 健保番号
- 基礎年金番号
- 雇用保険被保険者番号
- 雇用保険番号
- 保険証番号
- 社会保険番号
- 社会保険No.
- 社会保険
- 介護保険
- 介護保険被保険者番号
- 健康保険被保険者整理番号
- 雇用保険被保険者整理番号
- 厚生年金
- 厚生年金被保険者整理番号