---
title: Définition de l’entité numéro d’enregistrement des résidents du Japon
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
description: Définition d’entité de type d’entité de type d’informations sensibles du numéro d’enregistrement résident du Japon.
ms.openlocfilehash: 59e9b4a8eeef1ecc206cccd34ecccbf27de1a2e7
ms.sourcegitcommit: 6df492719fecc2b213d55465dc1cd60ab4627ed6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2022
ms.locfileid: "68382576"
---
# <a name="japan-resident-registration-number"></a>Matricule de résident Japon

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="format"></a>Format

11 chiffres

## <a name="pattern"></a>Modèle

11 chiffres consécutifs

## <a name="checksum"></a>Somme de contrôle

Non

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_jp_resident_registration_number` trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keyword_jp_resident_registration_number` est trouvé.

```xml
<!-- Japan Resident Registration Number -->
<Entity id="01c1209b-6389-4faf-a5f8-3f7e13899652" patternsProximity="300" recommendedConfidence="75">
    <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_jp_resident_registration_number" />
        <Match idRef ="Keyword_jp_resident_registration_number" />
    </Pattern>
</Entity>
```

## <a name="keywords"></a>Mots-clés

### <a name="keyword_jp_resident_registration_number"></a>Keyword_jp_resident_registration_number

- Numéro d’enregistrement du résident
- Numéro de base d’enregistrement des résidents
- N° d’enregistrement du résident
- N° d’enregistrement du résident
- N° de base d’enregistrement des résidents
- N° d’enregistrement du résident de base
- 外国人登録証明書番号
- 証明書番号
- 登録番号
- 外国人登録証
