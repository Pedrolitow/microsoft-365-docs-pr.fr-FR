---
title: Définition d’entité du numéro de passeport canadien
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
description: Définitions d’entité de type d’informations sensibles du numéro de passeport canadien.
ms.openlocfilehash: 5a645a71bd9cdb27727fd493bcd09ceca7340c22
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2022
ms.locfileid: "66950163"
---
# <a name="canada-passport-number"></a>Numéro de passeport du Canada

## <a name="format"></a>Format

deux lettres majuscules suivies de six chiffres

## <a name="pattern"></a>Modèle

deux lettres majuscules suivies de six chiffres

## <a name="checksum"></a>Somme de contrôle

Non

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- L’expression régulière `Regex_canada_passport_number` trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keyword_canada_passport_number`ou `Keyword_passport` est trouvé.

```xml
<!-- Canada Passport Number -->
<Entity id="14d0db8b-498a-43ed-9fca-f6097ae687eb" patternsProximity="300" recommendedConfidence="75">
  <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_canada_passport_number" />
        <Any minMatches="1">
          <Match idRef="Keyword_canada_passport_number" />
          <Match idRef="Keyword_passport" />
        </Any>
  </Pattern>
</Entity>
```

## <a name="keywords"></a>Mots-clés

### <a name="keyword_canada_passport_number"></a>Keyword_canada_passport_number

- citoyenneté canadienne
- passeport canadien
- demande de passeport
- photos pour passeport
- traducteur agréé
- citoyens canadiens
- temps de traitement
- demande de renouvellement

### <a name="keyword_passport"></a>Keyword_passport

- Numéro de passeport
- N° de passeport
- # Passeport
- #Passeport
- PassportID
- N° de passeport
- numéropasseport
- パスポート
- パスポート番号
- パスポートのNum
- パスポート＃
- Numéro de passeport
- Passeport n°
- Passeport numéro
- # Passeport
- # Passeport
- PasseportNon
- Passeportn °