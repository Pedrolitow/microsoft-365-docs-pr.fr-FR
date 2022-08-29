---
title: Définition d’entité numéro d’entreprise en Australie
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
description: Définition d’entité de type d’information sensible de numéro d’entreprise en Australie.
ms.openlocfilehash: 656dbc0315b0b7b09b112bdd7e423bcdec64a165
ms.sourcegitcommit: 72d10d0bc29ecc8b19c395f1815dc48b549096d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2022
ms.locfileid: "67368474"
---
# <a name="australia-business-number"></a>Numéro d’entreprise en Australie

## <a name="format"></a>Format

11 chiffres avec délimiteurs facultatifs

## <a name="pattern"></a>Modèle

11 chiffres avec délimiteurs facultatifs :

- deux chiffres
- un trait d’union ou un espace facultatif
- trois chiffres
- un trait d’union ou un espace facultatif
- trois chiffres
- un trait d’union ou un espace facultatif
- trois chiffres

## <a name="checksum"></a>Somme de contrôle

Oui

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction Func_australian_business_number recherche le contenu qui correspond au modèle.
- Un mot clé de Keywords_australian_business_number est trouvé.

Une stratégie DLP a une confiance moyenne ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction Func_australian_business_number recherche le contenu qui correspond au modèle.

```xml
      <!-- Australia Business Number -->
      <Entity id="76e83b3b-01ee-4530-aced-e667a6609f49" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_australian_business_number" />
          <Match idRef="Keywords_australian_business_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_australian_business_number" />
        </Pattern>
      </Entity>
```
## <a name="keywords"></a>Mots-clés

### <a name="keyword_australia_business_number"></a>Keyword_australia_business_number

- australie business no
- numéro d’entreprise
- Abn #
- Businessid #
- ID d’entreprise
- Abn
- businessno #