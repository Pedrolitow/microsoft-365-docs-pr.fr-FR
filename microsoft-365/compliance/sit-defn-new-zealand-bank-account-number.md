---
title: Définition d’entité de numéro de compte bancaire en Nouvelle-Zélande
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
description: Définition d’entité de type d’entité de type d’informations sensibles de numéro de compte bancaire en Nouvelle-Zélande.
ms.openlocfilehash: 3e682641abeee0c6e48fa1df70c767f029d0af4c
ms.sourcegitcommit: 72d10d0bc29ecc8b19c395f1815dc48b549096d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2022
ms.locfileid: "67369696"
---
# <a name="new-zealand-bank-account-number"></a>Numéro de compte bancaire néo-zélandais

## <a name="format"></a>Format

Modèle à 14 chiffres à 16 chiffres avec délimiteur facultatif

## <a name="pattern"></a>Modèle

Modèle à 14 chiffres à 16 chiffres avec délimiteur facultatif :

- deux chiffres
- un trait d’union ou un espace facultatif
- trois à quatre chiffres
- un trait d’union ou un espace facultatif
- sept chiffres
- un trait d’union ou un espace facultatif
- deux à trois chiffres
- un trait d’union ou un espace d’options

## <a name="checksum"></a>Somme de contrôle

Oui

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_new_zealand_bank_account_number` trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keywords_new_zealand_bank_account_number` est trouvé.

Une stratégie DLP a une confiance moyenne ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_new_zealand_bank_account_number` trouve un contenu qui correspond au modèle.

```xml
      <!-- New Zealand Bank Account Number -->
      <Entity id="1a97fc2b-dd2f-48f1-bc4e-2ddf25813956" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_new_zealand_bank_account_number" />
          <Match idRef="Keywords_new_zFealand_bank_account_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_new_zealand_bank_account_number" />
        </Pattern>
      </Entity>
```

## <a name="keywords"></a>Mots-clés

### <a name="keyword_new_zealand_bank_account_number"></a>Keyword_new_zealand_bank_account_number

- numéro de compte
- compte bancaire
- bank_acct_id
- bank_acct_branch
- bank_acct_nbr