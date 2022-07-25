---
title: Définition de l’entité numéro de sécurité sociale (SSN) en Espagne
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
description: Définition d’entité de type d’entité du numéro de sécurité sociale (SSN) espagnol.
ms.openlocfilehash: 4a531f0548aba2caa330423d493cf8e524c4ed73
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2022
ms.locfileid: "66996789"
---
# <a name="spain-social-security-number-ssn"></a>Numéro de sécurité sociale (N° S.S.) espagnol

## <a name="format"></a>Format

11 à 12 chiffres

## <a name="pattern"></a>Modèle

11 à 12 chiffres :

- deux chiffres
- une barre oblique (facultatif)
- sept à huit chiffres
- une barre oblique (facultatif)
- deux chiffres

## <a name="checksum"></a>Somme de contrôle

Oui

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_spanish_social_security_number` trouve un contenu qui correspond au modèle.
- La somme de contrôle est correcte.
    - Un mot clé figurant dans la liste `Keywords_spain_eu_ssn_or_equivalent` est trouvé.

Une stratégie DLP a une confiance moyenne ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_spanish_social_security_number` trouve un contenu qui correspond au modèle.
- La somme de contrôle est correcte.

```xml
    <!-- Spain SSN -->
    <Entity id="5df987c0-8eae-4bce-ace7-b316347f3070" patternsProximity="300" recommendedConfidence="85" relaxProximity="true" >
      <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_spanish_social_security_number" />
          <Match idRef="Keywords_spain_eu_ssn_or_equivalent" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_spanish_social_security_number" />
        </Pattern>
    </Entity>
```

## <a name="keywords"></a>Mots-clés

### <a name="keywords_spain_eu_passport_number"></a>Keywords_spain_eu_passport_number

- nss
- nss#
- socialsecurityno
- sécurité sociale non
- numéro de sécurité sociale
- número de la seguridad social