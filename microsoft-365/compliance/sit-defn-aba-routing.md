---
title: Définition d’entité de numéro de routage ABA
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
description: Définition d’entité de type d’entité de type d’informations sensibles de routage ABA.
ms.openlocfilehash: 5efc835b5d5dced7fbfe9a0b1ce7c59b89b60ac0
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2022
ms.locfileid: "66996509"
---
# <a name="aba-routing-number"></a>Numéro de routage ABA

## <a name="format"></a>Format

neuf chiffres qui peuvent être dans un modèle mis en forme ou non mis en forme

## <a name="pattern"></a>Modèle

- deux chiffres dans les plages 00-12, 21-32, 61-72 ou 80
- deux chiffres
- un trait d’union facultatif
- quatre chiffres
- un trait d’union facultatif
- un chiffre

## <a name="checksum"></a>Somme de contrôle

Oui

## <a name="definition"></a>Définition

Une stratégie a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction Func_aba_routing trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_ABA_Routing est trouvé.

Une stratégie DLP a une confiance faible ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction Func_aba_routing trouve un contenu qui correspond au modèle.

```xml
    <!-- ABA Routing Number -->
    <Entity id="cb353f78-2b72-4c3c-8827-92ebe4f69fdf" patternsProximity="300" recommendedConfidence="75">
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_aba_routing" />
        <Match idRef="Keyword_ABA_Routing" />
      </Pattern>
      <Pattern confidenceLevel="65">
        <IdMatch idRef="Func_aba_routing" />
      </Pattern>
    </Entity>
```

## <a name="keywords"></a>Mots-clés

### <a name="keyword_aba_routing"></a>Keyword_aba_routing

- numéro aba
- Aba #
- Aba
- abarouting #
- abaroutingnumber
- americanbankassociationrouting #
- americanbankassociationroutingnumber
- bankrouting #
- bankroutingnumber
- Routage #
- routage non
- numéro de routage
- numéro de routage
- Routage #
- RTN
