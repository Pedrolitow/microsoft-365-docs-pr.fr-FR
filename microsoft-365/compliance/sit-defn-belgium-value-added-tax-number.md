---
title: Définition d’entité de numéro de taxe sur la valeur ajoutée en Belgique
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
description: Définition d’entité de type d’informations sensibles de numéro de taxe sur la valeur ajoutée en Belgique.
ms.openlocfilehash: c1099e69636f9b3dd0fdc5250df47f57506176fd
ms.sourcegitcommit: 72d10d0bc29ecc8b19c395f1815dc48b549096d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2022
ms.locfileid: "67367354"
---
# <a name="belgium-value-added-tax-number"></a>Numéro de taxe sur la valeur ajoutée en Belgique

## <a name="format"></a>Format

Modèle alphanumérique à 12 caractères

## <a name="pattern"></a>Modèle

Modèle alphanumérique à 12 caractères :

- une lettre B ou b
- une lettre E ou e
- un chiffre 0
- un chiffre de 1 à 9
- un point ou un trait d’union ou un espace facultatif
- quatre chiffres
- un point ou un trait d’union ou un espace facultatif
- quatre chiffres

## <a name="checksum"></a>Somme de contrôle

Oui

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_belgium_value_added_tax_number` trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keywords_belgium_value_added_tax_number` est trouvé.

Une stratégie DLP a une confiance moyenne ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_belgium_value_added_tax_number` trouve un contenu qui correspond au modèle.

```xml
      <!-- Belgium Value Added Tax Number -->
      <Entity id="85b5b3c3-f2de-4ae8-ac46-fd3cb38bf9ed" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_belgium_value_added_tax_number" />
          <Match idRef="Keywords_belgium_value_added_tax_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_belgium_value_added_tax_number" />
        </Pattern>
      </Entity>
    </Version>
```
## <a name="keywords"></a>Mots-clés

### <a name="keyword_belgium_value_added_tax_number"></a>Keyword_belgium_value_added_tax_number

- nº tva
- numéro de tva
- nº de TVA
- numéro t.v.a
- umsatzsteuer-identifikationsnummer
- umsatzsteuernummer
- btw
- btw#
- #tva
