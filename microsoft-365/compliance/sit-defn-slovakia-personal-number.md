---
title: Définition d’entité de numéro personnel en Slovaquie
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
description: Définition d’entité de type d’entité de type d’informations sensibles de numéro personnel en Slovaquie.
ms.openlocfilehash: 4f923c714cf94543828d184164631d5e0c60e9e8
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2022
ms.locfileid: "66950137"
---
# <a name="slovakia-personal-number"></a>Numéro personnel en Slovaquie

Ce type d’informations sensibles est uniquement disponible pour une utilisation dans :

- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gestion du cycle de vie des données
- gestion des enregistrements
- Microsoft Defender for Cloud Apps

## <a name="format"></a>Format

neuf ou 10 chiffres contenant une barre oblique inverse facultative

## <a name="pattern"></a>Modèle

- six chiffres représentant la date de naissance
- barre oblique facultative (/)
- trois chiffres
- un chiffre de vérification facultatif

## <a name="checksum"></a>Somme de contrôle

Oui

## <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction `Func_slovakia_eu_national_id_card` recherche le contenu qui correspond au modèle.
- Un mot clé est `Keywords_slovakia_eu_national_id_card` trouvé.

Une stratégie DLP a une faible confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction `Func_slovakia_eu_national_id_card` recherche le contenu qui correspond au modèle.

```xml
      <!-- Slovakia Personal Number -->
      <Entity id="951c26b7-3b35-4f73-924b-15dd599cb9ab" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_slovakia_eu_national_id_card" />
          <Match idRef="Keywords_slovakia_eu_national_id_card" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Func_slovakia_eu_national_id_card" />
        </Pattern>
      </Entity>
    </Version>
```

## <a name="keywords"></a>Mots-clés

### <a name="keywords_slovakia_eu_national_id_card"></a>Keywords_slovakia_eu_national_id_card

- azonosító szám
- nombre de naissances
- číslo národnej identifikačnej karty
- číslo občianského preukazu
- daňové číslo
- numéro d’ID
- identification no
- numéro d’identification
- identifikačná karta č
- identifikačné číslo
- identity card no
- numéro de carte d’identité
- národná identifikačná značka č
- numéro national
- nationalnumber #
- nemzeti személyazonosító igazolvány
- personalidnumber #
- rč
- rodne cislo
- rodné číslo
- numéro de sécurité sociale
- Ssn #
- Ssn
- személyi igazolvány szám
- személyi igazolvány száma
- személyigazolvány szám
- fichier fiscal no
- numéro de dossier fiscal
- id fiscal
- identification fiscale non
- numéro d’identification fiscale
- tax no #
- tax no
- numéro d’impôt
- numéro d’enregistrement fiscal
- taxid #
- taxidno #
- taxidnumber #
- taxno #
- taxnumber #
- taxnumber
- iD d’tin
- tin no
- Étain #