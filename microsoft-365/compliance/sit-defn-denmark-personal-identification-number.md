---
title: Définition de l’entité numéro d’identification personnelle du Danemark
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
description: Définition d’entité du type d’entité du numéro d’identification personnelle du Danemark.
ms.openlocfilehash: a9e47db57f98ab2ad06ba34dee3bc73d3b558863
ms.sourcegitcommit: 2ff545246fec060ea7829da5afbc1cdc698d51ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2022
ms.locfileid: "68363120"
---
# <a name="denmark-personal-identification-number"></a>Numéro d’identification personnelle danois

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="format"></a>Format

10 chiffres contenant un trait d’union

## <a name="pattern"></a>Modèle

10 chiffres :

- six chiffres au format DDMMYY, qui sont la date de naissance
- un espace ou un trait d’union facultatif
- quatre chiffres où le chiffre final est un chiffre à cocher

## <a name="checksum"></a>Somme de contrôle

Oui

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- L’expression régulière `Func_denmark_eu_tax_file_number` trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keyword_denmark_id` est trouvé.
- La somme de contrôle est correcte.

Une stratégie DLP a une confiance faible ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- L’expression régulière `Func_denmark_eu_tax_file_number` trouve un contenu qui correspond au modèle.
- La somme de contrôle est correcte.

```xml
<!-- Denmark Personal Identification Number -->
    <!-- Denmark Personal Identification Number -->
      <Entity id="6c4f2fef-56e1-4c00-8093-88d7a01cf460" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_denmark_eu_tax_file_number" />
          <Match idRef="Keyword_denmark_id" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Func_denmark_eu_tax_file_number" />
        </Pattern>
      </Entity>
```

## <a name="keywords"></a>Mots-clés

### <a name="keyword_denmark_id"></a>Keyword_denmark_id

- centrale personregister
- civilt registreringssystem
- Cpr
- Cpr #
- gesundheitskarte nummer
- gesundheitsversicherungkarte nummer
- carte d’intégrité
- numéro de carte d’assurance maladie
- numéro d’assurance maladie
- numéro d’identification
- identifikationsnummer
- identifikationsnummer #
- numéro d’identité
- krankenkassennummer
- nationalid #
- #numéronational
- numéro national
- #numéroidpersonnel
- personalidentityno #
- numéro d’ID personnel
- personnummer
- personnummer #
- reisekrankenversicherungskartenummer
- rejsesygesikringskort
- nss
- nss#
- skat id
- skat kode
- skat nummer
- skattenummer
- numéro de sécurité sociale
- sundhedsforsikringskort
- sundhedsforsikringsnummer
- sundhedskort
- sundhedskortnummer
- sygesikring
- sygesikringkortnummer
- code fiscal
- carte d’assurance maladie de voyage
- uniqueidentityno #
- numéro de contribuable
- numéro d’identification fiscale
- id fiscal
- numéro d’identification fiscal
- taxid#
- taxnumber#
- nº fiscal
- taxno#
- taxnumber
- numéro d’identification fiscal
- tin#
- taxidno#
- taxidnumber#
- taxe nº#
- id de tin
- nº de tin
- cpr.nr
- cpnr
- cprnummer
- personnr
- personregister
- sygesikringsbevis
- sygesikringsbevisnr
- sygesikringsbevisnummer
- sygesikringskort
- sygesikringskortnr
- sygesikringskortnummer
- sygesikringsnr
- sygesikringsnummer
