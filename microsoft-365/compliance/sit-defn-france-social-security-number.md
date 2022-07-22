---
title: Définition d’entité du numéro de sécurité sociale français (INSEE)
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
description: Définition d’entité du type d’informations sensibles du numéro de sécurité sociale français (INSEE).
ms.openlocfilehash: 3378b452e8136e5ca62fe49932ba23949eb6a85d
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2022
ms.locfileid: "66950873"
---
# <a name="france-social-security-number-insee"></a>Numéro de sécurité sociale français (INSEE)

## <a name="format"></a>Format

15 chiffres

## <a name="pattern"></a>Modèle

Doit correspondre à l’un des deux modèles suivants :

- 13 chiffres suivis d’un espace suivi de deux chiffres

  ou

- 15 chiffres consécutifs

## <a name="checksum"></a>Somme de contrôle

Oui

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_french_insee` trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keyword_fr_insee` est trouvé.
- La somme de contrôle est correcte.

Une stratégie DLP a une confiance moyenne ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_french_insee` ou `Func_fr_insee` trouve un contenu qui correspond au modèle.
- La somme de contrôle est correcte.

```xml
    <!-- France INSEE -->
    <Entity id="71f62b97-efe0-4aa1-aa49-e14de253619d" patternsProximity="300" recommendedConfidence="75">
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_french_insee" />
        <Any minMatches="0" maxMatches="0">
          <Match idRef="Keyword_fr_insee" />
        </Any>
      </Pattern>
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_french_insee" />
        <Match idRef="Keyword_fr_insee" />
      </Pattern>
    </Entity>
```

## <a name="keywords"></a>Mots-clés

### <a name="keyword_fr_insee"></a>Keyword_fr_insee

- code sécu
- d’identité nationale
- insee
- fssn#
- le numéro d’identification nationale
- le code de la sécurité sociale
- id national
- numéro d’identification nationale
- n° d’identité
- N° d’identité
- numéro d’assurance
- numéro d’identité
- numéro d’identité
- numéro de sécu
- numéro de sécurité sociale
- n° d’identité
- N° d’identité
- nss
- nss#
- sécurité sociale
- securité sociale
- securite sociale
- socialsecuritynumber
- numéro de sécurité sociale
- code de sécurité sociale
- numéro d’assurance sociale