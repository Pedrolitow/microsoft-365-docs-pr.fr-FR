---
title: ROYAUME-UNI. définition de l’entité numéro d’assurance nationale (NINO)
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
description: ROYAUME-UNI. national insurance number (NINO) sensitive information type entity definition.
ms.openlocfilehash: 44b41cf2c19d001e142ff527b431990ebd3c80c6
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2022
ms.locfileid: "66950560"
---
# <a name="uk-national-insurance-number-nino"></a>ROYAUME-UNI. numéro d’assurance nationale (NINO)

Cette entité de type d’informations sensibles est incluse dans le type d’informations sensibles numéro d’identification nationale de l’UE. Il est également disponible en tant qu’entité de type d’informations sensibles autonome.

## <a name="format"></a>Format

sept caractères ou neuf caractères séparés par des espaces ou des tirets

## <a name="pattern"></a>Modèle

deux modèles possibles :

- deux lettres (les objets NINO valides utilisent uniquement certains caractères de ce préfixe, ce que ce modèle valide ; non sensibles à la casse)
- six chiffres
- 'A', 'B', 'C' ou 'D' (comme le préfixe, seuls certains caractères sont autorisés dans le suffixe ; non sensibles à la casse)

OR

- deux lettres
- un espace ou un tiret
- deux chiffres
- un espace ou un tiret
- deux chiffres
- un espace ou un tiret
- deux chiffres
- un espace ou un tiret
- 'A', 'B', 'C' ou 'D'

## <a name="checksum"></a>Somme de contrôle

Non

## <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction `Func_uk_nino` recherche le contenu qui correspond au modèle.
- Un mot clé est `Keyword_uk_nino` trouvé.

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction `Func_uk_nino` recherche le contenu qui correspond au modèle.

```xml
    <!-- U.K. NINO -->
    <Entity id="16c07343-c26f-49d2-a987-3daf717e94cc" patternsProximity="300" recommendedConfidence="75" relaxProximity="true">
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_uk_nino" />
        <Match idRef="Keyword_uk_nino" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_uk_nino" />
      </Pattern>
    </Entity>
```

## <a name="keywords"></a>Mots-clés

### <a name="keyword_uk_nino"></a>Keyword_uk_nino

- numéro d’assurance nationale
- cotisations sociales
- loi sur la protection
- Assurance
- numéro de sécurité sociale
- demande d’assurance
- demande de soins médicaux
- assurance sociale
- soins médicaux
- sécurité sociale
- grande-bretagne
- Numéro d’interface de commande
- Ni Non.
- NI #
- NI #
- Assurance #
- insurancenumber
- nationalinsurance #
- nationalinsurancenumber