---
title: Définition de l’entité de taxe sur la valeur ajoutée en Autriche
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
description: Définition d’entité de type d’information sensible à la taxe ajoutée en Autriche.
ms.openlocfilehash: 9ed66fd971857afad9cf5047643f60e58eb2e7f2
ms.sourcegitcommit: 72d10d0bc29ecc8b19c395f1815dc48b549096d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2022
ms.locfileid: "67368031"
---
# <a name="austria-value-added-tax"></a>Numéro de TVA autrichien

## <a name="format"></a>Format

Modèle alphanumérique à 11 caractères

## <a name="pattern"></a>Modèle

Modèle alphanumérique à 11 caractères :

- A ou a
- T ou t
- Espace facultatif
- U ou u
- espace facultatif
- deux ou trois chiffres
- espace facultatif
- quatre chiffres
- espace facultatif
- un ou deux chiffres

## <a name="checksum"></a>Somme de contrôle

Oui

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction Func_Austria_Value_Added_Tax recherche le contenu qui correspond au modèle.
- Un mot clé de Keyword_Austria_Value_Added_Tax est trouvé.

Une stratégie DLP a une confiance moyenne ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction Func_Austria_Value_Added_Tax recherche le contenu qui correspond au modèle.

```xml
      <!-- Austria Value Added Tax -->
      <Entity id="b6a3eda2-c56c-4b69-a5f7-dca34db00f48" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_Austria_Value_Added_Tax" />
          <Match idRef="Keyword_Austria_Value_Added_Tax" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_Austria_Value_Added_Tax" />
        </Pattern>
      </Entity>
```
## <a name="keywords"></a>Mots-clés

### <a name="keyword_austria_value_added_tax"></a>Keyword_austria_value_added_tax

- numéro de tva
- #tva
- numéro de tva autrichien
- vat no.
- vatno #
- numéro de taxe sur la valeur ajoutée
- tva autrichienne
- mwst
- umsatzsteuernummer
- mwstnummer
- ust.-identifikationsnummer
- umsatzsteuer-identifikationsnummer
- numéro d’identification de tva
- atu number
- uid number