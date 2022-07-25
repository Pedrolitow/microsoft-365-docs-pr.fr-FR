---
title: Slovénie Unique Master Citizen Number entity definition
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
description: Slovénie Unique Master Citizen Number sensitive information type entity definition.
ms.openlocfilehash: 23c484946c8e73e7f21b251aa35935dba37b110b
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2022
ms.locfileid: "66996540"
---
# <a name="slovenia-unique-master-citizen-number"></a>Numéro de citoyen principal unique slovène

Ce type d’informations sensibles est uniquement disponible pour une utilisation dans :

- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gestion du cycle de vie des données
- gestion des enregistrements
- Microsoft Defender for Cloud Apps

## <a name="format"></a>Format

13 chiffres sans espaces ni délimiteurs

## <a name="pattern"></a>Modèle

13 chiffres dans le modèle spécifié :

- sept chiffres qui correspondent à la date de naissance (DDMMLLL) où « LLL » correspond aux trois derniers chiffres de l’année de naissance
- deux chiffres qui correspondent à la zone de naissance « 50 »
- trois chiffres qui correspondent à une combinaison de sexe et de numéro de série pour les personnes nées le même jour. 000-499 pour les hommes et 500-999 pour les femmes.
- un chiffre de vérification

## <a name="checksum"></a>Somme de contrôle

Oui

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_slovenia_eu_national_id_card` trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keywords_slovenia_eu_national_id_card` est trouvé.

Une stratégie DLP a une confiance moyenne ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_slovenia_eu_national_id_card` trouve un contenu qui correspond au modèle.

```xml
      <!-- Slovenia Unique Master Citizen Number -->
      <Entity id="68948b27-803d-41e4-adf1-13e05eb541bb" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_slovenia_eu_national_id_card" />
          <Match idRef="Keywords_slovenia_eu_national_id_card" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_slovenia_eu_national_id_card" />
        </Pattern>
      </Entity>
```

## <a name="keywords"></a>Mots-clés

### <a name="keywords_slovenia_eu_national_id_card"></a>Keywords_slovenia_eu_national_id_card

- edinstvena številka glavnega državljana
- emšo
- enotna maticna številka obcana
- carte d’identité
- numéro d’identification
- identifikacijska številka
- Carte d’identité
- id de la nacionalna
- list nacionalni potni
- id national
- osebna izkaznica
- osebni koda
- osebni ne
- osebni številka
- code personnel
- numéro personnel
- code numérique personnel
- številka državljana
- numéro de citoyen unique
- numéro d’ID unique
- numéro d’identité unique
- numéro de citoyen maître unique
- numéro d’inscription unique
- uniqueidentityno #
- uniqueidentityno #