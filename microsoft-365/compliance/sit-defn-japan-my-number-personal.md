---
title: Japan My Number - Définition d’entité personnelle
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
description: Japan My Number - Définition d’entité de type Informations sensibles personnelles.
ms.openlocfilehash: 343bc26e3310c4c8586a50b635ef3d5b2398967c
ms.sourcegitcommit: 72d10d0bc29ecc8b19c395f1815dc48b549096d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2022
ms.locfileid: "67369804"
---
# <a name="japan-my-number---personal"></a>Mon numéro japonais personnel

## <a name="format"></a>Format

Numéro à 12 chiffres

## <a name="pattern"></a>Modèle

Numéro à 12 chiffres :

- quatre chiffres
- un espace, un point ou un trait d’union facultatif
- quatre chiffres
- un espace, un point ou un trait d’union facultatif
- quatre chiffres

## <a name="checksum"></a>Somme de contrôle

Oui

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_japanese_my_number_personal` trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keywords_japanese_my_number_personal` est trouvé.

Une stratégie DLP a une confiance faible ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_japanese_my_number_personal` trouve un contenu qui correspond au modèle.

```xml
      <!-- Japanese My Number – Personal -->
      <Entity id="98da8e66-7299-4ebd-9f82-c871ab37d3ef" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_japanese_my_number_personal" />
          <Match idRef="Keywords_japanese_my_number_personal" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Func_japanese_my_number_personal" />
        </Pattern>
      </Entity>
```

## <a name="keywords"></a>Mots-clés

### <a name="keyword_japan_my_number_personal"></a>Keyword_japan_my_number_personal

- mon numéro
- マイナンバー
- 個人番号
- 共通番号
- マイナンバーカード
- マイナンバーカード番号
- 個人番号カード
- 個人識別番号
- 個人識別ナンバー
- 通知カード