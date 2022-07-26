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
ms.openlocfilehash: 59411672288d3a9c47aef1a54a7d4727876a498f
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2022
ms.locfileid: "66995619"
---
# <a name="belgium-value-added-tax-number"></a>Numéro de taxe sur la valeur ajoutée en Belgique

Ce type d’informations sensibles est uniquement disponible pour une utilisation dans :

- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gestion du cycle de vie des données
- gestion des enregistrements
- Microsoft Defender for Cloud Apps

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
