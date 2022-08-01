---
title: Définition d’entité de numéro de carte d’identité de résident (PRC) en Chine
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
description: Définition d’entité de type d’information sensible de numéro de carte d’identité de résident (PRC) en Chine.
ms.openlocfilehash: 9ab0f1af6de2c8ffdcb835824e1559ab1a574718
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2022
ms.locfileid: "66995900"
---
# <a name="china-resident-identity-card-prc-number"></a>Numéro de carte d’identité résidente en Chine

## <a name="format"></a>Format

18 chiffres

## <a name="pattern"></a>Modèle

18 chiffres :

- six chiffres qui sont un code d’adresse
- huit chiffres sous la forme YYYYMMDD, qui sont la date de naissance
- trois chiffres qui sont un code de commande
- un chiffre qui est un chiffre à cocher

## <a name="checksum"></a>Somme de contrôle

Oui

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_china_resident_id` trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keyword_china_resident_id` est trouvé.
- La somme de contrôle est correcte.

Une stratégie DLP a une confiance moyenne ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_china_resident_id` trouve un contenu qui correspond au modèle.
- La somme de contrôle est correcte.

```xml
<!-- China Resident Identity Card (PRC) Number -->
<Entity id="c92daa86-2d16-4871-901f-816b3f554fc1" recommendedConfidence="85" patternsProximity="300">
  <Pattern confidenceLevel="85">
     <IdMatch idRef="Func_china_resident_id"/>
     <Match idRef="Keyword_china_resident_id"/>
  </Pattern>
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Func_china_resident_id"/>
  </Pattern>
</Entity>
```

## <a name="keywords"></a>Mots-clés

## <a name="keyword_china_resident_id"></a>Keyword_china_resident_id

- Resident Identity Card
- RPC
- National Identification Card
- 身份证
- 居民 身份证
- 居民身份证
- 鉴定
- 身分證
- 居民 身份證
- 鑑定