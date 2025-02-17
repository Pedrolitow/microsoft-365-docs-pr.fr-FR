---
title: Définition de l’entité numéro d’identification fiscale aux Pays-Bas
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
description: Définition d’entité de type d’information sensible du numéro d’identification fiscale pays-bas.
ms.openlocfilehash: 964d1dcf408fc132cc7fc99f0dd71690e24d5a62
ms.sourcegitcommit: 6df492719fecc2b213d55465dc1cd60ab4627ed6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2022
ms.locfileid: "68383984"
---
# <a name="netherlands-tax-identification-number"></a>Numéro d’identifiant fiscal hollandais

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="format"></a>Format

neuf chiffres sans espaces ni délimiteurs

## <a name="pattern"></a>Modèle

neuf chiffres

## <a name="checksum"></a>Somme de contrôle

Oui

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_netherlands_eu_tax_file_number` trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keywords_netherlands_eu_tax_file_number` est trouvé.

Une stratégie DLP a une confiance faible ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_netherlands_eu_tax_file_number` trouve un contenu qui correspond au modèle.

```xml
      <!-- Netherlands Tax Identification Number -->
      <Entity id="01f42a64-eba7-4892-a67b-398237e4ade2" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_netherlands_eu_tax_file_number" />
          <Match idRef="Keywords_netherlands_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Func_netherlands_eu_tax_file_number" />
        </Pattern>
      </Entity>
```

## <a name="keywords"></a>Mots-clés

### <a name="keywords_netherlands_eu_tax_file_number"></a>Keywords_netherlands_eu_tax_file_number

- btw nummer
- hollânske identification fiscale
- hulandes impuesto id number
- hulandes impuesto identification
- identificatienummer belasting
- identificatienummer van belasting
- numéro d’identification impuesto
- impuesto number
- nederlands belasting id nummer
- nederlands belasting identificatie
- nederlands belasting identificatienummer
- nederlands belastingnummer
- nederlandse belasting identificatie
- identification fiscale aux Pays-Bas
- l’identification fiscale de netherland
- boîte pays-bas
- netherland’s tin
- id fiscal
- numéro d’identification fiscal
- numéro d’identification fiscal
- tax identification tal
- taxe nº#
- nº fiscal
- numéro de contribuable
- numéro d’identification fiscale
- tax tal
- taxid#
- taxidno#
- taxidnumber#
- taxno#
- taxnumber#
- taxnumber
- id de tin
- nº de tin
- tin#
