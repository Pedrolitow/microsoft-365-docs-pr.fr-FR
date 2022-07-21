---
title: Définition d’entité CURP (Unique Population Registry Code) du Mexique
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
description: Définition d’entité de type d’information sensible CURP (Code du Registre de la population unique du Mexique).
ms.openlocfilehash: 806f7e9b0d2dd797b17ad848d160c6f74c04e1e2
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2022
ms.locfileid: "66950825"
---
# <a name="mexico-unique-population-registry-code-curp"></a>Code du Registre de la population unique du Mexique (CURP)

## <a name="format"></a>Format

Modèle alphanumérique à 18 caractères

## <a name="pattern"></a>Modèle

- quatre lettres (ne respectant pas la casse)
- six chiffres indiquant une date valide
- une lettre - H/h ou M/m
- deux lettres indiquant un code d’état mexicain valide
- trois lettres
- une lettre ou un chiffre
- un chiffre

## <a name="checksum"></a>Somme de contrôle

Non

## <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction `Func_mexico_population_registry_code` recherche le contenu qui correspond au modèle.
- Un mot clé est `Keyword_mexico_population_registry_code` trouvé.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction `Func_mexico_population_registry_code` recherche le contenu qui correspond au modèle.

```xml
    <!-- Mexico Unique Population Registry Code (CURP) -->
      <Entity id="e905ad4d-5a74-406d-bf36-b1efca798af4" patternsProximity="300" recommendedConfidence="75" relaxProximity="true">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_mexico_population_registry_code" />
          <Match idRef="Keyword_mexico_population_registry_code" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_mexico_population_registry_code" />
        </Pattern>
      </Entity>
```

## <a name="keywords"></a>Mots-clés

### <a name="keyword_mexico_population_registry_code"></a>Keyword_mexico_population_registry_code

- Clave Única de Registro de Población
- Clave Unica de Registro de Poblacion
- Code unique du Registre de la population
- code de remplissage unique
- CURP
- ID personnel
- Unique ID
- personalid
- personalidnumber
- uniqueidkey
- uniqueidnumber
- clave única
- clave unica
- clave personal Identidad
- personal Identidad Clave
- ClaveÚnica
- claveunica
- clavepersonalIdentidad