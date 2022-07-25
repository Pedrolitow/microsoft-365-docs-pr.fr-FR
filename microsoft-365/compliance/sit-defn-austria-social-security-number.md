---
title: Définition de l’entité numéro de sécurité sociale en Autriche
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
description: Définition d’entité de type d’entité de type d’information sensible de numéro de sécurité sociale en Autriche.
ms.openlocfilehash: 24b909e2b45bce3db5c4b4cfd1e0d3cf3d74296c
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2022
ms.locfileid: "66996579"
---
# <a name="austria-social-security-number"></a>Numéro de sécurité sociale autrichien

## <a name="format"></a>Format

10 chiffres au format spécifié

## <a name="pattern"></a>Modèle

10 chiffres :

- trois chiffres qui correspondent à un numéro de série
- un chiffre de vérification
- six chiffres qui correspondent à la date de naissance (DDMMYY)

## <a name="checksum"></a>Somme de contrôle

Oui

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_austria_eu_ssn_or_equivalent` trouve un contenu qui correspond au modèle.
- un mot clé à partir de `Keywords_austria_eu_ssn_or_equivalent` est trouvé.

Une stratégie DLP a une confiance moyenne ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_austria_eu_ssn_or_equivalent` trouve un contenu qui correspond au modèle.

```xml
      <!-- Austria Social Security Number -->
      <Entity id="6896a906-86c9-4d19-a2da-6e43ccd19b7b" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_austria_eu_ssn_or_equivalent" />
          <Match idRef="Keywords_austria_eu_ssn_or_equivalent" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_austria_eu_ssn_or_equivalent" />
          <Any minMatches="0" maxMatches="0">
            <Match idRef="Keywords_austria_eu_telephone_number" />
            <Match idRef="Keywords_austria_eu_mobile_number" />
          </Any>
        </Pattern>
      </Entity>
```

## <a name="keywords"></a>Mots-clés

### <a name="keywords_austria_eu_ssn_or_equivalent"></a>Keywords_austria_eu_ssn_or_equivalent

- ssn autrichien
- nombre ehic
- ehic no
- code d’assurance
- insurancecode #
- numéro d’assurance
- assurance no
- krankenkassennummer
- Krankenversicherung
- socialsecurityno
- socialsecurityno #
- sécurité sociale non
- numéro de sécurité sociale
- code de sécurité sociale
- sozialversicherungsnummer
- sozialversicherungsnummer #
- soziale sicherheit kein
- sozialesicherheitkein #
- nss#
- nss
- versicherungscode
- versicherungsnummer
- zdravstveno zavarovanje