---
title: Définition de l’entité numéro de chiffre d’affaires intérieur de la Nouvelle-Zélande
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
description: Définition d’entité de type d’information sensible du numéro de revenu intérieur de la Nouvelle-Zélande.
ms.openlocfilehash: 7df444660c59bd12526d979dd93d5313814083f3
ms.sourcegitcommit: 72d10d0bc29ecc8b19c395f1815dc48b549096d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2022
ms.locfileid: "67368058"
---
# <a name="new-zealand-inland-revenue-number"></a>Numéro de revenu intérieur néo-zélandais

## <a name="format"></a>Format

huit ou neuf chiffres avec délimiteurs facultatifs

## <a name="pattern"></a>Modèle

huit ou neuf chiffres avec délimiteurs facultatifs

- deux ou trois chiffres
- un espace ou un trait d’union facultatif
- trois chiffres
- un espace ou un trait d’union facultatif
- trois chiffres

## <a name="checksum"></a>Somme de contrôle

Oui

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_new_zealand_inland_revenue_number` trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keywords_new_zealand_inland_revenue_number` est trouvé.

Une stratégie DLP a une confiance moyenne ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_new_zealand_inland_revenue_number` trouve un contenu qui correspond au modèle.

```xml
      <!-- New Zealand Inland Revenue Number -->
      <Entity id="dd0fe2bc-7bcf-455f-bac1-83b1e3eb25fd" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_new_zealand_inland_revenue_number" />
          <Match idRef="Keywords_new_zealand_inland_revenue_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_new_zealand_inland_revenue_number" />
        </Pattern>
      </Entity>
```

## <a name="keywords"></a>Mots-clés

### <a name="keyword_new_zealand_inland_revenue_number"></a>Keyword_new_zealand_inland_revenue_number

- ird no.
- ird no #
- nz ird
- nouvelle zélande ird
- ird number
- chiffre d’affaires intérieur