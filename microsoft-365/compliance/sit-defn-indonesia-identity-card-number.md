---
title: Définition de l’entité de numéro de carte d’identité de l’Indonésie (KTP)
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
description: Définition d’entité de type d’entité de type d’informations sensibles de numéro de carte d’identité (KTP) de l’Indonésie.
ms.openlocfilehash: 0569be435baf2763c6de63db77926189bfb4a78c
ms.sourcegitcommit: be2334dbcd4e1bf309349d981a68a30e06de0297
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2022
ms.locfileid: "68380600"
---
# <a name="indonesia-identity-card-ktp-number"></a>Numéro de carte d’identité (KTP) en Indonésie

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="format"></a>Format

16 chiffres contenant éventuellement des points

## <a name="pattern"></a>Modèle

16 chiffres :

- Code à deux chiffres désignant la province 
- Un point (facultatif) 
- Code à deux chiffres désignant une régence ou une ville 
- Code à deux chiffres désignant un sous-district 
- Un point (facultatif) 
- Six chiffres au format DDMMYY, qui sont la date de naissance
- Un point (facultatif) 
- Quatre chiffres

## <a name="checksum"></a>Somme de contrôle

Non

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- L’expression régulière `Regex_indonesia_id_card` trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keyword_indonesia_id_card` est trouvé.

```xml
<!-- Indonesia Identity Card (KTP) Number -->
<Entity id="da68fdb0-f383-4981-8c86-82689d3b7d55" recommendedConfidence="85" patternsProximity="300">
  <Pattern confidenceLevel="85">
     <IdMatch idRef="Regex_indonesia_id_card"/>
     <Match idRef="Keyword_indonesia_id_card"/>
</Entity>
```

## <a name="keywords"></a>Mots-clés

### <a name="keyword_indonesia_id_card"></a>Keyword_indonesia_id_card

- Ktp
- Kartu Tanda Penduduk
- Nomor Induk Kependudukan
