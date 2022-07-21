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
- M365-security-compliance
hideEdit: true
feedback_system: None
recommendations: false
description: Définition d’entité de type d’entité de type d’informations sensibles du numéro d’enregistrement résident du Japon.
ms.openlocfilehash: 2cdff586ac9fe92e66a5844eae824f7df335eb31
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2022
ms.locfileid: "66950533"
---
# <a name="japan-resident-registration-number"></a>Numéro d’inscription des résidents du Japon

## <a name="format"></a>Format

11 chiffres

## <a name="pattern"></a>Modèle

11 chiffres consécutifs

## <a name="checksum"></a>Somme de contrôle

Non

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction `Func_jp_resident_registration_number` recherche le contenu qui correspond au modèle.
- Un mot clé est `Keyword_jp_resident_registration_number` trouvé.

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