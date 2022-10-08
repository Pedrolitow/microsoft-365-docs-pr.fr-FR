---
title: Royaume-Uni définition de l’entité numéro d’assurance nationale (NINO)
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
description: Royaume-Uni national insurance number (NINO) sensitive information type entity definition.
ms.openlocfilehash: a975ec23f2677846503e87087470452e952a7df6
ms.sourcegitcommit: 176bbd29c92e1c0812e8bcd1e1e4938a3e1d7331
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/05/2022
ms.locfileid: "68472889"
---
# <a name="uk-national-insurance-number-nino"></a>Royaume-Uni numéro d’assurance nationale (NINO)

Cette entité de type d’informations sensibles est incluse dans le type d’informations sensibles numéro d’identification nationale de l’UE. Il est également disponible en tant qu’entité de type d’informations sensibles autonome.

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

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

Une stratégie DLP a une confiance élevée ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_uk_nino` trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keyword_uk_nino` est trouvé.

Une stratégie DLP a une confiance moyenne ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_uk_nino` trouve un contenu qui correspond au modèle.

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
