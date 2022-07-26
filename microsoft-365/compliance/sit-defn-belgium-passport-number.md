---
title: Définition d’entité du numéro de passeport belge
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
description: Définition d’entité de type d’informations sensibles du numéro de passeport belge.
ms.openlocfilehash: accf853a7c832ba1a7fb8a3f25da7fa688181a20
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2022
ms.locfileid: "66997310"
---
# <a name="belgium-passport-number"></a>Numéro de passeport en Belgique

## <a name="format"></a>Format

deux lettres suivies de six chiffres sans espaces ni délimiteurs

## <a name="pattern"></a>Modèle

deux lettres majuscules suivies de six chiffres

## <a name="checksum"></a>Somme de contrôle

non applicable

## <a name="definition"></a>Définition

 Une stratégie DLP a une confiance élevée ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- L’expression régulière `Regex_belgium_eu_passport_number` trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keywords_eu_passport_number`ou `Keywords_belgium_eu_passport_number` est trouvé.
- L’expression `Regex_eu_passport_date2` régulière recherche la date au format JJ MM AA ou un mot clé à partir de `Keywords_eu_passport_date` ou de `Keywords_belgium_eu_passport_number` trouvé

Une stratégie DLP a une confiance moyenne ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- L’expression régulière `Regex_belgium_eu_passport_number` trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keywords_eu_passport_number`ou `Keywords_belgium_eu_passport_number` est trouvé.

```xml
      <!-- Belgium Passport Number -->
      <Entity id="d7b1315b-21ca-4774-a32a-596010ff78fd" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_belgium_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_belgium_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_eu_passport_date2" />
            <Match idRef="Keywords_eu_passport_date" />
            <Match idRef="Keywords_belgium_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_belgium_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_belgium_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>

```

## <a name="keywords"></a>Mots-clés

### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- #passeport
- # passeport
- passportid
- passeports
- N° de passeport
- N° de passeport
- numéropasseport
- numéro de passeport
- numérospasseport
- numéros de passeport

### <a name="keywords_belgium_eu_passport_number"></a>Keywords_belgium_eu_passport_number

- numéro passeport
- paspoort nr
- paspoort-nr
- paspoortnummer
- paspoortnummers
- Carte de passeport
- Passeport livre
- Pass-Nr
- Passnummer
- reisepass kein

### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- date du problème
- date d’expiration