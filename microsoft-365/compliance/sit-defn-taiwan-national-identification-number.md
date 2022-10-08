---
title: Définition de l’entité numéro d’identification nationale taïwanaise
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
description: Définition d’entité de type d’entité de type d’informations sensibles du numéro d’identification national de Taiwan.
ms.openlocfilehash: 52f8bbd3f7d43cc57d655febdef7c218453581d8
ms.sourcegitcommit: 176bbd29c92e1c0812e8bcd1e1e4938a3e1d7331
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/05/2022
ms.locfileid: "68472319"
---
# <a name="taiwan-national-identification-number"></a>Numéro d’identification nationale taïwanais

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="format"></a>Format

une lettre (en anglais) suivie de neuf chiffres

## <a name="pattern"></a>Modèle

une lettre (en anglais) suivie de neuf chiffres :

- une lettre (en anglais, non sensible à la casse)
- le chiffre « 1 » ou « 2 »
- huit chiffres

## <a name="checksum"></a>Somme de contrôle

Oui

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_taiwanese_national_id` trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keyword_taiwanese_national_id` est trouvé.
- La somme de contrôle est correcte.

Une stratégie DLP a une confiance moyenne ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_taiwanese_national_id` trouve un contenu qui correspond au modèle.
- La somme de contrôle est correcte.

```xml
<!-- Taiwanese National ID -->
<Entity id="4C7BFC34-8DD1-421D-8FB7-6C6182C2AF03" patternsProximity="300" recommendedConfidence="85">
      <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_taiwanese_national_id" />
          <Match idRef="Keyword_taiwanese_national_id" />
      </Pattern>
       <Pattern confidenceLevel="75">
         <IdMatch idRef="Func_taiwanese_national_id" />
       </Pattern>
</Entity>
```

## <a name="keywords"></a>Mots-clés

### <a name="keyword_taiwan_national_id"></a>Keyword_taiwan_national_id

- 身份證字號
- 身份證
- 身份證號碼
- 身份證號
- 身分證字號
- 身分證
- 身分證號碼
- 身份證號
- 身分證統一編號
- 國民身分證統一編號
- 簽名
- 蓋章
- 簽名或蓋章
- 簽章
