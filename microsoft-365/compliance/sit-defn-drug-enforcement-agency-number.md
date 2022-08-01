---
title: Définition de l’entité de numéro de la Drug Enforcement Agency (DEA)
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
description: Définition d’entité de type d’information sensible de numéro de la Drug Enforcement Agency (DEA).
ms.openlocfilehash: 7b1ade056621f619d8be0293708dd51cfc2e85dd
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2022
ms.locfileid: "66995820"
---
# <a name="drug-enforcement-agency-dea-number"></a>Numéro de l’Agence de contrôle de la drogue (DEA)

## <a name="format"></a>Format

deux lettres suivies de sept chiffres

## <a name="pattern"></a>Modèle

Le modèle doit inclure tous les éléments suivants :

- une lettre (non sensible à la casse) de cet ensemble de lettres possibles : A/B/F/G/M/P/R, qui est un code inscrit
- une lettre (non sensible à la casse), qui est la première lettre du nom ou du chiffre de l’inscrit « 9 »
- sept chiffres, dont le dernier est le chiffre à cocher

## <a name="checksum"></a>Somme de contrôle

Oui

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_dea_number` trouve un contenu qui correspond au modèle.
- Un mot clé à partir de `Keyword_dea_number` est trouvé
- La somme de contrôle est correcte.

Une stratégie DLP a une confiance moyenne ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_dea_number` trouve un contenu qui correspond au modèle.
- La somme de contrôle est correcte.

```xml
    <!-- DEA Number -->
    <Entity id="9a5445ad-406e-43eb-8bd7-cac17ab6d0e4" patternsProximity="300" recommendedConfidence="85">
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_dea_number" />
      </Pattern>
      <Version minEngineVersion="15.20.1207.000" maxEngineVersion="15.20.3134.000">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_dea_number" />
        </Pattern>
      </Version>
      <Version minEngineVersion="15.20.3135.000">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_dea_number" />
          <Match idRef="Keyword_dea_number" />
        </Pattern>
      </Version>
    </Entity>
```

## <a name="keywords"></a>Mots-clés

### <a name="keyword_dea_number"></a>Keyword_dea_number

- Dea
- Dea #
- administration de l’application des drogues
- agence de lutte contre les drogues