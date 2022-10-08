---
title: Définition de l’entité numéro de compte bancaire aux États-Unis
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
description: Définition d’entité de type d’entité de type d’informations sensibles de numéro de compte bancaire américain.
ms.openlocfilehash: 94eec07def3ffc9d4c8b5b7bf9e7a85dc988ecb1
ms.sourcegitcommit: 176bbd29c92e1c0812e8bcd1e1e4938a3e1d7331
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/05/2022
ms.locfileid: "68471923"
---
# <a name="us-bank-account-number"></a>Numéro de compte bancaire américain

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="format"></a>Format

6 à 17 chiffres

## <a name="pattern"></a>Modèle

6 à 17 chiffres consécutifs

## <a name="checksum"></a>Somme de contrôle

Non

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- L’expression régulière `Regex_usa_bank_account_number` trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keyword_usa_Bank_Account` est trouvé.

```xml
<!-- U.S. Bank Account Number -->
<Entity id="a2ce32a8-f935-4bb6-8e96-2a5157672e2c" patternsProximity="300" recommendedConfidence="75">
    <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_usa_bank_account_number" />
        <Match idRef="Keyword_usa_Bank_Account" />
    </Pattern>
</Entity>
```

## <a name="keywords"></a>Mots-clés

### <a name="keyword_usa_bank_account"></a>Keyword_usa_Bank_Account

- Numéro de compte courant
- Compte courant
- # compte courant
- Numéro compte courant
- # compte courant
- N° de compte courant
- N° de compte courant
- Numéro de compte bancaire
- # Compte bancaire
- Numéro de compte bancaire
- # Compte bancaire
- N° de compte bancaire
- N° de compte bancaire
- Numéro de compte d’épargne
- Compte d’épargne.
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
