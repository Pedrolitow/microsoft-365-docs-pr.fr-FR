---
title: Définition d’entité de code numérique personnel (CNP) en Roumanie
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
description: Définition d’entité de type d’information sensible de type code numérique personnel (CNP) en Roumanie.
ms.openlocfilehash: c1241d3bdd3035b053713137a4e64feb50a6dba0
ms.sourcegitcommit: 176bbd29c92e1c0812e8bcd1e1e4938a3e1d7331
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/05/2022
ms.locfileid: "68470363"
---
# <a name="romania-personal-numeric-code-cnp"></a>Code numérique personnel (CNP) roumain

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="format"></a>Format

13 chiffres sans espaces et délimiteurs

## <a name="pattern"></a>Modèle

- un chiffre de 1 à 9
- six chiffres représentant la date de naissance (AAAAMMD)
- deux chiffres, qui peuvent être 01-52 ou 99
- quatre chiffres

## <a name="checksum"></a>Somme de contrôle

Oui

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_romania_eu_national_id_card` trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keywords_romania_eu_national_id_card` est trouvé.

Une stratégie DLP a une confiance moyenne ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_romania_eu_national_id_card` trouve un contenu qui correspond au modèle.

```xml
      <!-- Romania Personal Numerical Code (CNP) -->
      <Entity id="eb5fa399-fe28-4c67-8188-d63a616ed89c" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_romania_eu_national_id_card" />
          <Match idRef="Keywords_romania_eu_national_id_card" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_romania_eu_national_id_card" />
        </Pattern>
      </Entity>
```

## <a name="keywords"></a>Mots-clés

### <a name="keywords_romania_eu_national_id_card"></a>Keywords_romania_eu_national_id_card

- cnp #
- cnp
- cod identificare personnel
- cod numeric personal
- cod unic identificare
- codnumericpersonal #
- codul fiscal nr.
- identificarea fiscală nr #
- id-ul taxei
- numéro d’assurance
- insurancenumber #
- ID national #
- id national
- numéro d’identification nationale
- număr identificare personnel
- număr identitate
- număr personal unic
- număridentitate #
- număridentitate
- numărpersonalunic #
- numărpersonalunic
- număru de identificare fiscală
- numărul de identificare fiscală
- code numérique personnel
- épingler #
- épingler
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
- numéro d’identification unique
- numéro d’identité unique
- uniqueidentityno #
- uniqueidentityno
