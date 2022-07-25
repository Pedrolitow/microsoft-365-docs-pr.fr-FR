---
title: Définition de l’entité Clé d’identification fiscale unique argentine (CUIT/CUIL)
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
description: Définition d’entité de type d’information sensible de type clé d’identification fiscale unique (CUIT/CUIL) argentine.
ms.openlocfilehash: d38cb0a972add240087c816399abf30d3d9ef670
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2022
ms.locfileid: "66996979"
---
# <a name="argentina-unique-tax-identification-key-cuitcuil"></a>Clé d’identification fiscale unique argentine (CUIT/CUIL)

## <a name="format"></a>Format

11 chiffres avec tiret

## <a name="pattern"></a>Modèle

11 chiffres avec un tiret :

- deux chiffres dans 20, 23, 24, 27, 30, 33 ou 34
- un trait d’union (-)
- huit chiffres
- un trait d’union (-)
- un chiffre de vérification

## <a name="checksum"></a>Somme de contrôle

Oui

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_Argentina_Unique_Tax_Key` trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keyword_Argentina_Unique_Tax_Key` est trouvé.

Une stratégie DLP a une confiance moyenne ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_Argentina_Unique_Tax_Key` trouve un contenu qui correspond au modèle.

```xml
    <!-- Argentina Unique Tax Identification Key (CUIT/CUIL) -->
      <Entity id="98da3da1-9199-4571-b7c4-b6522980b507" patternsProximity="300" recommendedConfidence="75" relaxProximity="true">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_Argentina_Unique_Tax_Key" />
          <Match idRef="Keyword_Argentina_Unique_Tax_Key" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_Argentina_Unique_Tax_Key" />
        </Pattern>
      </Entity>
```

## <a name="keywords"></a>Mots-clés

### <a name="keyword_argentina_unique_tax_key"></a>Keyword_Argentina_Unique_Tax_Key

- Clave Unica de Identificacion Tributaria
- CUIT
- code unique d’identification du travail
- Clave Única de Identificación Tributaria
- code unique d’identification du travail
- CUIL
- Clé d’identification fiscale unique
- Clé unique d’identification du travail
- Clé unique de l’identification du travail
- Code d’identification de travail unique
- Code unique d’identification du travail
- Clé d’identification de travail unique
- Clé unique d’identification du travail
- Code unique d’identification fiscale
- Clé unique d’identification fiscale
- Code d’identification du travail unique
- Code unique d’identification du travail
- Clé d’identification du travail unique
- Clé unique de l’identification du travail
- ID d’impôt
- taxID #
- taxId
- taxidnumber
- numéro de contribuable
- nº fiscal
- Taxe #
- Taxe #
- ID du contribuable
- numéro de contribuable
- contribuable non
- Contribuable #
- Contribuable #
- identité fiscale
- identification fiscale
- Número de Identificación Fiscal
- número de contribuyente