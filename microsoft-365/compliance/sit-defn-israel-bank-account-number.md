---
title: Définition de l’entité numéro de compte bancaire d’Israël
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
description: Israel bank account number sensitive information type entity definition.
ms.openlocfilehash: a68f90cd92432778d89d3f8494522a5ab2822d07
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2022
ms.locfileid: "66997609"
---
# <a name="israel-bank-account-number"></a>Numéro de compte bancaire Israël

## <a name="format"></a>Format

13 chiffres

## <a name="pattern"></a>Modèle

Formaté:

- deux chiffres
- un tiret
- trois chiffres
- un tiret
- huit chiffres

Mémoire:

- 	13 chiffres consécutifs

## <a name="checksum"></a>Somme de contrôle

Non

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- L’expression régulière `Regex_israel_bank_account_number` trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keyword_israel_bank_account_number` est trouvé.

```xml
<!-- Israel Bank Account Number -->
<Entity id="7d08b2ff-a0b9-437f-957c-aeddbf9b2b25" patternsProximity="300" recommendedConfidence="75">
    <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_israel_bank_account_number" />
        <Any minMatches="1">
          <Match idRef="Keyword_israel_bank_account_number" />
        </Any>
    </Pattern>
</Entity>
```

## <a name="keywords"></a>Mots-clés

### <a name="keyword_israel_bank_account_number"></a>Keyword_israel_bank_account_number

- Bank Account Number
- Bank Account
- Numéro de compte
- מספר חשבון בנק