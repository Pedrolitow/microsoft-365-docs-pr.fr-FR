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
- tier3
- purview-compliance
hideEdit: true
feedback_system: None
recommendations: false
description: Définition d’entité de type d’entité de type d’informations sensibles de numéro de compte bancaire en Nouvelle-Zélande.
ms.openlocfilehash: 0afeadefe65844be7d86ea2f53154510423c41de
ms.sourcegitcommit: 6df492719fecc2b213d55465dc1cd60ab4627ed6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2022
ms.locfileid: "68381674"
---
# <a name="new-zealand-bank-account-number"></a>Numéro de compte bancaire néo-zélandais

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

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
