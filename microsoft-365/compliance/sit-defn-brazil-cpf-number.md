---
title: Définition d’entité de numéro CPF au Brésil
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
description: Définition d’entité de type d’entité du type d’informations sensibles du nombre CPF au Brésil.
ms.openlocfilehash: b8164d44f20237b5eb74d45369f3bffbe1dc07e3
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2022
ms.locfileid: "66950483"
---
# <a name="brazil-cpf-number"></a>Numéro CPF du Brésil

## <a name="format"></a>Format

11 chiffres qui incluent un chiffre de contrôle et peuvent ou non être mis en forme 

## <a name="pattern"></a>Modèle

Formaté:

- trois chiffres
- un point
- trois chiffres
- un point
- trois chiffres
- un trait d’union
- deux chiffres qui sont des chiffres de vérification

Mémoire:

- 11 chiffres où les deux derniers sont des chiffres de contrôle

## <a name="checksum"></a>Somme de contrôle

Oui

## <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction `Func_brazil_cpf` recherche le contenu qui correspond au modèle.
- Un mot clé est `Keyword_brazil_cpf` trouvé.
- La somme de contrôle est correcte.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction `Func_brazil_cpf` recherche le contenu qui correspond au modèle.
- La somme de contrôle est correcte.

```xml
<!-- Brazil CPF Number -->
<Entity id="78e09124-f2c3-4656-b32a-c1a132cd2711" recommendedConfidence="85" patternsProximity="300">
  <Pattern confidenceLevel="85">
     <IdMatch idRef="Func_brazil_cpf"/>
     <Match idRef="Keyword_brazil_cpf"/>
  </Pattern>
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Func_brazil_cpf"/>
  </Pattern>
</Entity>
```

## <a name="keywords"></a>Mots-clés

### <a name="keyword_brazil_cpf"></a>Keyword_brazil_cpf

- CPF
- Identification
- Inscription
- Revenus
- Cadastro de Pessoas Físicas
- Imposto
- Identificação
- Inscrição
- Receita