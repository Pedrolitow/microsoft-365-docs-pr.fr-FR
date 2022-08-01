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
ms.openlocfilehash: 5d3b238dc631086be26399e3adf6c4fa2ef0cf99
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2022
ms.locfileid: "66995630"
---
# <a name="australia-business-number"></a>Numéro d’entreprise en Australie

Ce type d’informations sensibles est uniquement disponible pour une utilisation dans :

- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gestion du cycle de vie des données
- gestion des enregistrements
- Microsoft Defender for Cloud Apps

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