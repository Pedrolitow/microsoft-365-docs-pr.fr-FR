---
title: Définition d’entité du numéro de taxe sur la valeur ajoutée en France
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
description: Définition d’entité du type d’informations sensibles du numéro de taxe sur la valeur ajoutée en France.
ms.openlocfilehash: c34426d3bcbb8d6ec9d86618232f6be2607f960b
ms.sourcegitcommit: be2334dbcd4e1bf309349d981a68a30e06de0297
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2022
ms.locfileid: "68378839"
---
# <a name="france-value-added-tax-number"></a>Numéro de taxe sur la valeur ajoutée en France

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="format"></a>Format

Modèle alphanumérique de 13 caractères

## <a name="pattern"></a>Modèle

Modèle alphanumérique de 13 caractères :

- deux lettres : FR (ne respectant pas la casse)
- un espace ou un trait d’union facultatif
- deux lettres ou chiffres
- un espace, un point, un trait d’union ou une virgule facultative
- trois chiffres
- un espace, un point, un trait d’union ou une virgule facultative
- trois chiffres
- un espace, un point, un trait d’union ou une virgule facultative
- trois chiffres

## <a name="checksum"></a>Somme de contrôle

Oui

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_france_value_added_tax_number` trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keywords_france_value_added_tax_number` est trouvé.

Une stratégie DLP a une confiance moyenne ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_france_value_added_tax_number` trouve un contenu qui correspond au modèle.

```xml
      <!-- France Value Added Tax Number -->
      <Entity id="949121e6-ad9f-4379-8731-710342baea78" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_france_value_added_tax_number" />
          <Match idRef="Keywords_france_value_added_tax_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_france_value_added_tax_number" />
        </Pattern>
      </Entity>
```
## <a name="keywords"></a>Mots-clés

### <a name="keyword_france_value_added_tax_number"></a>Keyword_France_value_added_tax_number

- numéro de tva
- nº de TVA
- nº de TVA
- taxe sur la valeur ajoutée
- identification siren aucun numéro d’identification taxe sur valeur ajoutée
- taxe valeur ajoutée
- taxe sur la valeur ajoutée
- n° tva
- numéro de tva
- numéro d’identification siren
