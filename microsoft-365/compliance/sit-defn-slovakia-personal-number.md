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
ms.openlocfilehash: 4e576d4b4ac1c65ca72e2955c7617fe7d2badd22
ms.sourcegitcommit: 72d10d0bc29ecc8b19c395f1815dc48b549096d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2022
ms.locfileid: "67367640"
---
# <a name="slovakia-personal-number"></a>Numéro personnel slovaque

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

Une stratégie DLP a une confiance élevée ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_slovakia_eu_national_id_card` trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keywords_slovakia_eu_national_id_card` est trouvé.

Une stratégie DLP a une confiance faible ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_slovakia_eu_national_id_card` trouve un contenu qui correspond au modèle.

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
- #numéronational
- nemzeti személyazonosító igazolvány
- #numéroidpersonnel
- rč
- rodne cislo
- rodné číslo
- numéro de sécurité sociale
- nss#
- nss
- személyi igazolvány szám
- személyi igazolvány száma
- személyigazolvány szám
- fichier fiscal no
- numéro de dossier fiscal
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