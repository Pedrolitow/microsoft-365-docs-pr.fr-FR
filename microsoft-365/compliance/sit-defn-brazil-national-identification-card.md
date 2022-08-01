---
title: Définition d’entité de carte d’identification nationale (RG) du Brésil
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
description: Définition d’entité de type d’entité de type d’information sensible de carte d’identification nationale (RG) du Brésil.
ms.openlocfilehash: 7f4fe7a0eda911639c0c7650d4ac71f07dfe4f3a
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2022
ms.locfileid: "66995570"
---
# <a name="brazil-national-identification-card-rg"></a>Carte d’identification nationale (RG) du Brésil

## <a name="format"></a>Format

Registro Geral (ancien format) : Neuf chiffres

Registro de Identidade (RIC) (nouveau format) : 11 chiffres

### <a name="pattern"></a>Modèle

Registro Geral (ancien format) :

- deux chiffres
- un point
- trois chiffres
- un point
- trois chiffres
- un trait d’union
- un chiffre qui est un chiffre à cocher

Registro de Identidade (RIC) (nouveau format) :

- 10 chiffres
- un trait d’union
- un chiffre qui est un chiffre à cocher

## <a name="checksum"></a>Somme de contrôle

Oui

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_brazil_rg` trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keyword_brazil_rg` est trouvé.
- La somme de contrôle est correcte.

```xml
      <!-- Brazil National ID Card (RG) -->
      <Entity id="486de900-db70-41b3-a886-abdf25af119c" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_brazil_rg" />
          <Match idRef="Keyword_brazil_rg" />
        </Pattern>
      </Entity>
```

## <a name="keywords"></a>Mots-clés

### <a name="keyword_brazil_rg"></a>Keyword_brazil_rg

- Cédula de identidade
- Carte d’identité
- id national
- Número de registro
- Registro de Identidade
- Registro Geral
- RG (ce mot clé respecte la casse)
- RIC (ce mot clé respecte la casse)