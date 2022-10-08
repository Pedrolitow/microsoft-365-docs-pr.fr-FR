---
title: Définition d’entité de numéro REGON en Pologne
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
description: Définition d’entité de type d’information sensible de numéro REGON en Pologne.
ms.openlocfilehash: 29b5d8a751a66dee94c78bdc79bf2f1eabf80107
ms.sourcegitcommit: 176bbd29c92e1c0812e8bcd1e1e4938a3e1d7331
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/05/2022
ms.locfileid: "68471637"
---
# <a name="poland-regon-number"></a>Numéro REGON polonais

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="format"></a>Format

9 chiffres ou 14 chiffres

## <a name="pattern"></a>Modèle

neuf chiffres ou 14 chiffres :

- neuf chiffres ou
- neuf chiffres
- Tiret
- cinq chiffres

## <a name="checksum"></a>Somme de contrôle

Oui

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_polish_regon_number` trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keywords_polish_regon_number` est trouvé.

Une stratégie DLP a une confiance faible ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_polish_regon_number` trouve un contenu qui correspond au modèle.

```xml
      <!-- Polish REGON Number  -->
      <Entity id="fc87b421-f437-4f8b-b739-29a735ead0d9" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_polish_regon_number" />
          <Match idRef="Keywords_polish_regon_number" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Func_polish_regon_number" />
        </Pattern>
      </Entity>
```

## <a name="keywords"></a>Mots-clés

### <a name="keywords_poland_regon_number"></a>Keywords_poland_regon_number

- regon id
- nombre statistique
- ID statistique
- statistiques non
- regon number
- regonid #
- regonno #
- ID d’entreprise
- companyid #
- companyidno #
- numer statystyczny
- numeru regon
- numerstatystyczny #
- numeruregon #
