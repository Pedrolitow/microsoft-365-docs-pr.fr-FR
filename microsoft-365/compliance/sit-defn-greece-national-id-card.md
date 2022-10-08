---
title: Définition de l’entité de carte d’identité nationale grecque
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
description: Définition d’entité de type d’entité de type d’informations sensibles de carte d’identité nationale grecque.
ms.openlocfilehash: 9f4ae0728138a33640a4afddfb73ed04692e1723
ms.sourcegitcommit: be2334dbcd4e1bf309349d981a68a30e06de0297
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2022
ms.locfileid: "68379699"
---
# <a name="greece-national-id-card"></a>Carte d’ID nationale grecque

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="format"></a>Format

Combinaison de 7 ou 8 lettres et chiffres, plus un tiret

## <a name="pattern"></a>Modèle

Sept lettres et chiffres (ancien format) :

- Une lettre (de l’alphabet grec) 
- Un tiret
- Six chiffres

Huit lettres et chiffres (nouveau format) :

- Deux lettres dont le caractère majuscule figure à la fois dans l’alphabet grec et l’alphabet latin (ABEZHIKMNOPTYX) 
- Un tiret
- Six chiffres

## <a name="checksum"></a>Somme de contrôle

Non

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- L’expression régulière `Regex_greece_id_card` trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keyword_greece_id_card` est trouvé.

Une stratégie DLP a une confiance faible ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- L’expression régulière `Regex_greece_id_card` trouve un contenu qui correspond au modèle.

```xml
      <!-- Greece National ID Card -->
      <Entity id="82568215-1da1-46d3-874a-d2294d81b5ac" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_greece_id_card" />
          <Match idRef="Keyword_greece_id_card" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Regex_greece_id_card" />
        </Pattern>
      </Entity>
```

## <a name="keywords"></a>Mots-clés

### <a name="keyword_greece_id_card"></a>Keyword_greece_id_card

- ID grec
- greek national id
- carte d’ID personnelle grecque
- ID de police grec
- Carte d’identité
- Tautotita
- ταυτότητα
- ταυτότητας
