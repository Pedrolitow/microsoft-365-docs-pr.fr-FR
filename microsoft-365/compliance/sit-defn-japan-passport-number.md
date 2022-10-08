---
title: Définition d’entité numéro de passeport au Japon
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
description: Définition d’entité de type d’information sensible numéro de passeport au Japon.
ms.openlocfilehash: bb9841bdf6c6e9d86d2bf7242f8e1252d4acc62c
ms.sourcegitcommit: 6df492719fecc2b213d55465dc1cd60ab4627ed6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2022
ms.locfileid: "68381459"
---
# <a name="japan-passport-number"></a>Numéro de passeport japonais

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="format"></a>Format

deux lettres suivies de sept chiffres

## <a name="pattern"></a>Modèle

deux lettres (non sensibles à la casse) suivies de sept chiffres

## <a name="checksum"></a>Somme de contrôle

Non

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_jp_passport` trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keyword_jp_passport` est trouvé.

```xml
<!-- Japan Passport Number -->
<Entity id="75177310-1a09-4613-bf6d-833aae3743f8" patternsProximity="300" recommendedConfidence="75">
    <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_jp_passport" />
        <Match idRef="Keyword_jp_passport" />
    </Pattern>
</Entity>
```

## <a name="keywords"></a>Mots-clés

### <a name="keyword_jp_passport"></a>Keyword_jp_passport

- Passeport
- Numéro de passeport
- Passeport Non.
- # Passeport
- パスポート
- パスポート番号
- パスポートナンバー
- パスポート＃
- パスポート #
- パスポートNo.
- 旅券番号
- 旅券番号＃
- 旅券番号♯
- 旅券ナンバー
