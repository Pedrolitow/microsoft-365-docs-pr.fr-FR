---
title: Définition de l’entité numéro de carte d’identification malaisienne
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
description: Définition d’entité de type d’entité du numéro de carte d’identification malaisienne.
ms.openlocfilehash: ed233a9aa91c1c178644c4468271ee6839c55268
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2022
ms.locfileid: "66996830"
---
# <a name="malaysia-identification-card-number"></a>Numéro de carte d’identification malaisienne

## <a name="format"></a>Format

12 chiffres contenant éventuellement des traits d’union

## <a name="pattern"></a>Modèle

12 chiffres :

- six chiffres au format YYMMDD, qui sont la date de naissance
- un tiret (facultatif)
- code de lieu de naissance à deux lettres
- un tiret (facultatif)
- trois chiffres aléatoires
- code de genre à un chiffre

## <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- L’expression régulière `Regex_malaysia_id_card_number` trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keyword_malaysia_id_card_number` est trouvé.

```xml
<!-- Malaysia ID Card Number -->
</Entity>
      <Entity id="7f0e921c-9677-435b-aba2-bb8f1013c749" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
            <IdMatch idRef="Regex_malaysia_id_card_number" />
            <Match idRef="Keyword_malaysia_id_card_number" />
        </Pattern>
</Entity>
```

## <a name="keywords"></a>Mots-clés

### <a name="keyword_malaysia_id_card_number"></a>Keyword_malaysia_id_card_number

- carte d’application numérique
- i/c
- i/c no
- Ic
- ic no
- carte d’identité
- carte d’identification
- Carte d’identité
- k/p
- k/p no
- kad akuan diri
- kad aplikasi digital
- kad pengenalan malaysia
- Kp
- kp no
- mykad
- mykas
- mykid
- mypr
- mytentera
- carte d’identité malaysia
- carte d’identité malaisienne
- nric
- carte d’identification personnelle