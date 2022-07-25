---
title: Définition de l’entité numéro de compte bancaire au Japon
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
description: Définition d’entité de type d’entité de type d’informations sensibles de numéro de compte bancaire au Japon.
ms.openlocfilehash: 1e762a32654e6aa14e0b20d7e09ab5167cc330a5
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2022
ms.locfileid: "66996490"
---
# <a name="japan-bank-account-number"></a>Numéro de compte bancaire Japon

## <a name="format"></a>Format

sept ou huit chiffres

## <a name="pattern"></a>Modèle

numéro de compte bancaire :

- sept ou huit chiffres
- code de branche de compte bancaire :

- quatre chiffres
- un espace ou un tiret (facultatif)
- trois chiffres

Somme de contrôle

Non

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_jp_bank_account` trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keyword_jp_bank_account` est trouvé.
- L’une des affirmations suivantes est vraie :

- La fonction `Func_jp_bank_account_branch_code` trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keyword_jp_bank_branch_code` est trouvé.

Une stratégie DLP a une confiance moyenne ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_jp_bank_account` trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keyword_jp_bank_account` est trouvé.

```xml
<!-- Japan Bank Account Number -->
<Entity id="d354f95b-96ee-4b80-80bc-4377312b55bc" patternsProximity="300" recommendedConfidence="75">
  <Version minEngineVersion="15.01.0131.000">
    <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_jp_bank_account" />
          <Match idRef="Keyword_jp_bank_account" />
          <Any minMatches="1">
            <Match idRef="Func_jp_bank_account_branch_code" />
            <Match idRef="Keyword_jp_bank_branch_code" />
          </Any>
      </Pattern>
  </Version>
     <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_jp_bank_account" />
        <Match idRef="Keyword_jp_bank_account" />
    </Pattern>
</Entity>
```

## <a name="keywords"></a>Mots-clés

### <a name="keyword_jp_bank_account"></a>Keyword_jp_bank_account

- Numéro de compte courant
- Compte courant
- # compte courant
- Numéro compte courant
- # compte courant
- N° de compte courant
- N° de compte courant
- Numéro de compte bancaire
- Compte bancaire
- # Compte bancaire
- Numéro de compte bancaire
- # Compte bancaire
- N° de compte bancaire
- N° de compte bancaire
- Numéro de compte d’épargne
- Compte d’épargne
- N° de compte d’épargne
- Numéro de compte d’épargne
- # compte d’épargne
- N° de compte d’épargne
- N° de compte d’épargne
- Numéro de compte de débit
- Compte de débit
- # Compte de débit
- Numéro de compte de débit
- # Compte de débit
- N° de compte de débit
- N° de compte de débit
- 口座番号
- 銀行口座
- 銀行口座番号
- 総合口座
- 普通預金口座
- 普通口座
- 当座預金口座
- 当座口座
- 預金口座
- 振替口座
- 銀行
- バンク

### <a name="keyword_jp_bank_branch_code"></a>Keyword_jp_bank_branch_code

- 支店番号
- 支店コード
- 店番号