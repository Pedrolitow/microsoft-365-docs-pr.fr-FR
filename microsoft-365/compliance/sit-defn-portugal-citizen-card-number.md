---
title: Définition de l’entité numéro de carte de citoyen du Portugal
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
description: Définition d’entité de type d’entité de type d’information sensible de numéro de carte de citoyen du Portugal.
ms.openlocfilehash: 350391a56f6dfc46e9d037ff23da491a5035357a
ms.sourcegitcommit: 176bbd29c92e1c0812e8bcd1e1e4938a3e1d7331
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/05/2022
ms.locfileid: "68472845"
---
# <a name="portugal-citizen-card-number"></a>Numéro de carte de citoyen portugais

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="format"></a>Format

huit chiffres

## <a name="pattern"></a>Modèle

huit chiffres

## <a name="checksum"></a>Somme de contrôle

Non

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- L’expression régulière `Regex_portugal_citizen_card` trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keyword_portugal_citizen_card` est trouvé.

```xml
<!-- Portugal Citizen Card Number -->
<Entity id="91a7ece2-add4-4986-9a15-c84544d81ecd" recommendedConfidence="85" patternsProximity="300">
  <Pattern confidenceLevel="85">
     <IdMatch idRef="Regex_portugal_citizen_card"/>
     <Match idRef="Keyword_portugal_citizen_card"/>
  </Pattern>
</Entity>
```

## <a name="keywords"></a>Mots-clés

### <a name="keyword_portugal_citizen_card"></a>Keyword_portugal_citizen_card

- bilhete de identidade
- cartão de cidadão
- carte de citoyen
- numéro de document
- documento de identificação
- numéro d’ID
- identification no
- numéro d’identification
- identity card no
- numéro de carte d’identité
- carte d’identité nationale
- Nic
- número bi de portugal
- número de identificação civil
- número de identificação fiscal
- número do documento
- portugal bi number
