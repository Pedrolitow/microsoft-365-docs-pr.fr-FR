---
title: Letton personal code entity definition
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
description: Letton personal code sensitive information type entity definition.
ms.openlocfilehash: cfcd9dd792494154601a9cafda179be64fb08078
ms.sourcegitcommit: 6df492719fecc2b213d55465dc1cd60ab4627ed6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2022
ms.locfileid: "68384182"
---
# <a name="latvia-personal-code"></a>Code personnel lettons

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="format"></a>Format

11 chiffres et un trait d’union facultatif

## <a name="pattern"></a>Modèle

Ancien format

11 chiffres et un trait d’union :

- six chiffres qui correspondent à la date de naissance (DDMMYY)
- un trait d’union
- un chiffre qui correspond au siècle de naissance (« 0 » pour le 19ème siècle, « 1 » pour le 20ème siècle et « 2 » pour le 21ème siècle)
- quatre chiffres, générés de manière aléatoire

Nouveau format

11 chiffres

- Deux chiffres « 32 »
- Neuf chiffres

## <a name="checksum"></a>Somme de contrôle

Oui

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_latvia_eu_national_id_card` ou l’expression `Regex_latvia_eu_national_id_card_new_format` régulière recherche du contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keywords_latvia_eu_national_id_card` est trouvé.

Une stratégie DLP a une confiance moyenne ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_latvia_eu_national_id_card` ou l’expression `Regex_latvia_eu_national_id_card_new_format` régulière recherche du contenu qui correspond au modèle.

```xml
      <!-- Latvia Personal Code -->
      <Entity id="03fcf763-27c2-49ed-9422-2641c6c895c9" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_latvia_eu_national_id_card" />
          <Match idRef="Keywords_latvia_eu_national_id_card" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_latvia_eu_national_id_card" />
          <Any minMatches="0" maxMatches="0">
            <Match idRef="Keywords_latvia_eu_telephone_number" />
            <Match idRef="Keywords_latvia_eu_mobile_number" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_latvia_eu_national_id_card_new_format" />
          <Match idRef="Keywords_latvia_eu_national_id_card" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_latvia_eu_national_id_card_new_format" />
          <Any minMatches="0" maxMatches="0">
            <Match idRef="Keywords_latvia_eu_telephone_number" />
            <Match idRef="Keywords_latvia_eu_mobile_number" />
          </Any>
        </Pattern>
      </Entity>

```

## <a name="keywords"></a>Mots-clés

### <a name="keywords_latvia_eu_national_id_card"></a>Keywords_latvia_eu_national_id_card

- numéro d’administration
- alvas nē
- nombre de naissances
- numéro de citoyen
- numéro civil
- numéro de recensement électronique
- numéro électronique
- code fiscal
- numéro d’utilisateur de soins de santé
- id#
- id-code
- numéro d’identification
- identifikācijas numurs
- id-number
- nombre individuel
- latvija alva
- nacionālais id
- id national
- numéro d’identification national
- numéro d’identité nationale
- numéro d’assurance nationale
- numéro de registre national
- nodokļa numurs
- nodokļu id
- nodokļu identifikācija numurs
- numéro de certificat personnel
- code personnel
- code d’ID personnel
- numéro d’ID personnel
- code d’identification personnelle
- identificateur personnel
- numéro d’identité personnelle
- numéro personnel
- code numérique personnel
- personalcodeno #
- personas kods
- code d’identification de la population
- numéro de service public
- numéro d’enregistrement
- numéro de chiffre d’affaires
- numéro d’assurance sociale
- numéro de sécurité sociale
- code fiscal d’état
- numéro de dossier fiscal
- id fiscal
- numéro d’identification fiscal
- numéro d’identification fiscal
- taxe nº#
- nº fiscal
- numéro de contribuable
- taxid#
- taxidno#
- taxidnumber#
- taxno#
- taxnumber#
- taxnumber
- id de tin
- nº de tin
- tin#
- numéro de l’électeur
