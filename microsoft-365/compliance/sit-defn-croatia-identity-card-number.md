---
title: Définition d’entité de numéro de carte d’identité en Croatie
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
description: Définition d’entité de type d’entité de type d’informations sensibles du numéro de carte d’identité croatie.
ms.openlocfilehash: 9b657a4a59dfc9b1b142c7a68ce1e919a162a030
ms.sourcegitcommit: 2ff545246fec060ea7829da5afbc1cdc698d51ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2022
ms.locfileid: "68363142"
---
# <a name="croatia-identity-card-number"></a>Numéro de carte d’identité croate

Cette entité est incluse dans le type d’informations sensibles numéro d’identification nationale de l’UE. Il est disponible en tant qu’entité de type d’informations sensibles autonome.

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="format"></a>Format

neuf chiffres

## <a name="pattern"></a>Modèle

neuf chiffres consécutifs

## <a name="checksum"></a>Somme de contrôle

Non

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_croatia_id_card` trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keyword_croatia_id_card` est trouvé.

```xml
<!--Croatia Identity Card Number-->
<Entity id="ff12f884-c20a-4189-b185-34c8e7258d47" recommendedConfidence="75" patternsProximity="300">
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Func_croatia_id_card"/>
     <Match idRef="Keyword_croatia_id_card"/>
  </Pattern>
</Entity>
```

## <a name="keywords"></a>Mots-clés

### <a name="keyword_croatia_id_card"></a>Keyword_croatia_id_card

- majstorski broj građana
- numéro de citoyen maître
- nacionalni identifikacijski broj
- numéro d’identification nationale
- Oib #
- Oib
- osobna iskaznica
- iD osobni
- osobni identifikacijski broj
- numéro d’identification personnelle
- porezni broj
- porezni identifikacijski broj
- id fiscal
- numéro d’identification fiscal
- numéro d’identification fiscal
- taxe nº#
- nº fiscal
- numéro de contribuable
- numéro d’identification fiscale
- taxid#
- taxidno#
- taxidnumber#
- taxno#
- taxnumber#
- taxnumber
- id de tin
- nº de tin
- tin#
