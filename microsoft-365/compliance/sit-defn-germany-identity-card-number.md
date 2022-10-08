---
title: Définition de l’entité numéro de carte d’identité en Allemagne
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
description: Définition d’entité de type d’entité de type d’informations sensibles de numéro de carte d’identité en Allemagne.
ms.openlocfilehash: e37f941d959e633f1d51f8bed6b8164bb071e648
ms.sourcegitcommit: be2334dbcd4e1bf309349d981a68a30e06de0297
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2022
ms.locfileid: "68379961"
---
# <a name="germany-identity-card-number"></a>Numéro de carte d’identité Allemagne

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="format"></a>Format

depuis le 1er novembre 2010 : 9 à 11 lettres et chiffres

du 1er avril 1987 au 31 octobre 2010 : 10 chiffres

## <a name="pattern"></a>Modèle

depuis le 1er novembre 2010 : modèle alphanumérique de 9 à 11 caractères
- one L, M, N, P, R, T, V, W, X, Y (ne respectant pas la casse)
- huit chiffres ou lettres en C, F, G, H, J, K, L, M, N, P, R, T, V, W, X, Y et Z (ne respectant pas la casse)
- chiffre de vérification facultatif
- D/D facultatif

du 1er avril 1987 au 31 octobre 2010 :

- 10 chiffres

## <a name="checksum"></a>Somme de contrôle

Oui

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_german_id_card_with_check` trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keyword_germany_id_card` est trouvé.
- La somme de contrôle est correcte.

Une stratégie DLP a une confiance moyenne ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- L’expression `Regex_germany_id_card` régulière recherche du contenu qui correspond au modèle (9 caractères sans chiffre à cocher émis avant 2010 ou 10 chiffres avec le modèle posy 2010).
- Un mot clé figurant dans la liste `Keyword_germany_id_card` est trouvé.

Une stratégie DLP a une confiance faible ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_german_id_card_with_check` trouve un contenu qui correspond au modèle.
- La somme de contrôle est correcte.

```xml
      <!-- Germany Identity Card Number -->
      <Entity id="e577372f-c42e-47a0-9d85-bebed1c237d4" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
         <IdMatch idRef="Regex_germany_id_card" />
         <Match idRef="Keyword_germany_id_card" />
        </Pattern>
        <Version minEngineVersion="15.20.4545.000">
          <Pattern confidenceLevel="85">
           <IdMatch idRef="Func_german_id_card_with_check" />
            <Match idRef="Keyword_germany_id_card" />
          </Pattern>
          <Pattern confidenceLevel="65">
           <IdMatch idRef="Func_german_id_card_with_check" />
          </Pattern>
        </Version>
      </Entity>
```

## <a name="keywords"></a>Mots-clés

### <a name="keyword_germany_id_card"></a>Keyword_germany_id_card

- ausweis
- gpid
- identification
- identifikation
- identifizierungsnummer
- Carte d’identité
- numéro d’identité
- id-nummer
- ID personnel
- personalausweis
- persönliche id nummer
- persönliche identifikationsnummer
- persönliche-id-nummer
