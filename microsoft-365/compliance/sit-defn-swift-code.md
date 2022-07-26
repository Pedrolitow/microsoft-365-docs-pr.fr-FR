---
title: Définition d’entité de code SWIFT
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
description: Définition d’entité de type d’informations sensibles au code SWIFT.
ms.openlocfilehash: b1bbadf8f2b56218a90eec1cfd2fac7d550efe0e
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2022
ms.locfileid: "66992706"
---
# <a name="swift-code"></a>Code SWIFT

## <a name="format"></a>Format

quatre lettres suivies de 5 à 31 lettres ou chiffres

## <a name="pattern"></a>Modèle

quatre lettres suivies de 5 à 31 lettres ou chiffres :

- Code bancaire à quatre lettres (non sensible à la casse)
- un espace facultatif
- 4 à 28 lettres ou chiffres (numéro de compte bancaire de base (BBAN))
- un espace facultatif
- une à trois lettres ou chiffres (reste du BBAN)

## <a name="checksum"></a>Somme de contrôle

Non

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- L’expression régulière `Regex_swift` trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keyword_swift` est trouvé.

```xml
<Entity id="cb2ab58c-9cb8-4c81-baf8-a4e106791df4" patternsProximity="300" recommendedConfidence="75">
<Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_swift" />
        <Match idRef="Keyword_swift" />
    </Pattern>
</Entity>
```

## <a name="keywords"></a>Mots-clés

### <a name="keyword_swift"></a>Keyword_swift

- organisation internationale de normalisation 9362
- ISO 9362
- iso9362
- Swift #
- swiftcode
- swiftnumber
- swiftroutingnumber
- code swift
- # numéro swift
- numéro d’acheminement swift
- numéro BIC
- code BIC
- # bic
- Bic #
- code d’identification bancaire
- Organisation internationale de normalisation 9362
- rapide #
- code SWIFT
- le numéro de swift
- swift numéro d’acheminement
- le numéro BIC
- \# BIC
- code identificateur de banque
- SWIFTコード
- SWIFT番号
- BIC番号
- BICコード
- SWIFT コード
- SWIFT 番号
- BIC 番号
- BIC コード
- 金融機関識別コード
- 金融機関コード
- 銀行コード