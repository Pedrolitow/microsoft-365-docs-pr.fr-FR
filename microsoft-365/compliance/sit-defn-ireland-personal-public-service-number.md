---
title: Définition d’entité de numéro de service public personnel (PPS) en Irlande
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
description: Définition d’entité de type d’information sensible de numéro de service public personnel (PPS) en Irlande.
ms.openlocfilehash: da0451a437ad3ab7dd8437352c2f7b539b9d9a9c
ms.sourcegitcommit: be2334dbcd4e1bf309349d981a68a30e06de0297
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2022
ms.locfileid: "68378311"
---
# <a name="ireland-personal-public-service-pps-number"></a>Numéro personnel pour le service public irlandais (PPS)

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="format"></a>Format

Ancien format (jusqu’au 31 décembre 2012) :

- sept chiffres suivis de 1 à 2 lettres

Nouveau format (1er janvier 2013 et après) :

- sept chiffres suivis de deux lettres

## <a name="pattern"></a>Modèle

Ancien format (jusqu’au 31 décembre 2012) :

- sept chiffres
- une à deux lettres (sans respect de la casse)

Nouveau format (1er janvier 2013 et après) :

- sept chiffres
- une lettre (non sensible à la casse) qui est un chiffre à cocher alphabétique
- Lettre facultative dans la plage A-I ou « W »

## <a name="checksum"></a>Somme de contrôle

Oui

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- Contenu de la fonction `Func_ireland_pps finds` qui correspond au modèle.
- Un mot clé figurant dans la liste `Keywords_ireland_eu_national_id_card` est trouvé.
- La somme de contrôle est correcte.

Une stratégie DLP a une confiance faible ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_ireland_pps` trouve un contenu qui correspond au modèle.
- La somme de contrôle est correcte.

```xml
      <!-- Ireland Personal Public Service (PPS) Number -->
      <Entity id="1cdb674d-c19a-4fcf-9f4b-7f56cc87345a" patternsProximity="300" recommendedConfidence="85" relaxProximity="true">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_ireland_pps" />
          <Match idRef="Keywords_ireland_eu_national_id_card" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Func_ireland_pps" />
        </Pattern>
      </Entity>
```

## <a name="keywords"></a>Mots-clés

### <a name="keywords_ireland_eu_national_id_card"></a>Keywords_ireland_eu_national_id_card

- service d’identité du client
- numéro d’identification
- numéro d’ID personnel
- numéro de service public personnel
- service personnel non
- phearsanta seirbhíse poiblí
- pps no
- pps number
- pps num
- pps service no
- ppsn
- ppsno #
- ppsno
- Psp
- service public non
- publicserviceno #
- publicserviceno
- chiffre d’affaires et d’assurance sociale
- rsi no
- nombre rsi
- rsin
- client seirbhís aitheantais
- uimh
- uimhir aitheantais chánach
- uimhir aitheantais phearsanta
- uimhir phearsanta seirbhíse poiblí
- id fiscal
- numéro d’identification fiscal
- numéro d’identification fiscal
- taxe nº#
- nº fiscal
- numéro de contribuable
- numéro d’identification fiscale
- taxid#
- taxidno#
- taxidnumber#
- taxno#
- taxnumber#
- taxnumber
- id de tin
- nº de tin
- tin#
