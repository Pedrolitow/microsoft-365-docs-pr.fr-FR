---
title: Définition d’entité pan (Permanent Account Number) en Inde
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
description: Définition d’entité de type d’information sensible du numéro de compte permanent (PAN) de l’Inde.
ms.openlocfilehash: f997fa774b7fb85e083004d8c2f8296a70e11a40
ms.sourcegitcommit: be2334dbcd4e1bf309349d981a68a30e06de0297
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2022
ms.locfileid: "68380225"
---
# <a name="india-permanent-account-number-pan"></a>Numéro de compte permanent de l’Inde (PAN)

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="format"></a>Format

10 lettres ou chiffres

## <a name="pattern"></a>Modèle

10 lettres ou chiffres :

- Trois lettres (non sensibles à la casse)
- Lettre en C, P, H, F, A, T, B, L, J, G (non sensible à la casse)
- Une lettre
- Quatre chiffres
- Lettre qui est un chiffre à cocher alphabétique

## <a name="checksum"></a>Somme de contrôle

Non

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- L’expression régulière `Regex_india_permanent_account_number` trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keyword_india_permanent_account_number` est trouvé.

Une stratégie DLP a une confiance faible ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- L’expression régulière `Regex_india_permanent_account_number` trouve un contenu qui correspond au modèle.

```xml
      <!-- India Permanent Account Number -->
      <Entity id="2602bfee-9bb0-47a5-a7a6-2bf3053e2804" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_india_permanent_account_number" />
          <Match idRef="Keyword_india_permanent_account_number" />
        </Pattern>
        <Version minEngineVersion="15.20.3520.000">
          <Pattern confidenceLevel="65">
            <IdMatch idRef="Regex_india_permanent_account_number" />
          </Pattern>
        </Version>
      </Entity>
```

## <a name="keywords"></a>Mots-clés

### <a name="keyword_india_permanent_account_number"></a>Keyword_india_permanent_account_number

- Permanent Account Number
- Pan
