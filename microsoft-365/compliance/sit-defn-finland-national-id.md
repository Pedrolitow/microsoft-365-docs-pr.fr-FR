---
title: Définition de l’entité d’ID nationale finlandaise
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
description: Définition d’entité de type d’entité de type d’informations sensibles d’ID national de finlande.
ms.openlocfilehash: 6c8c42d63610d91165c909f67845bf75aa182537
ms.sourcegitcommit: be2334dbcd4e1bf309349d981a68a30e06de0297
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2022
ms.locfileid: "68379640"
---
# <a name="finland-national-id"></a>ID national en Finlande

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="format"></a>Format

six chiffres plus un caractère indiquant un siècle plus trois chiffres plus un chiffre à cocher

## <a name="pattern"></a>Modèle

Le modèle doit inclure tous ces modèles :

- six chiffres au format DDMMYY, qui sont une date de naissance
- marqueur de siècle ('-', '+' ou 'a')
- Numéro d’identification personnelle à trois chiffres
- un chiffre ou une lettre (non sensible à la casse) qui est un chiffre à cocher

## <a name="checksum"></a>Somme de contrôle

Oui

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- la fonction `Func_finnish_national_id` recherche du contenu qui correspond au modèle
- un mot clé à partir de `Keyword_finnish_national_id` est trouvé
- la somme de contrôle réussit

Une stratégie DLP a une confiance moyenne ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- la fonction `Func_finnish_national_id` recherche du contenu qui correspond au modèle
- la somme de contrôle réussit

```xml
      <!-- Finnish National ID-->
      <Entity id="338FD995-4CB5-4F87-AD35-79BD1DD926C1" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_finnish_national_id" />
          <Match idRef="Keyword_finnish_national_id" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_finnish_national_id" />
        </Pattern>
      </Entity>
```

## <a name="keywords"></a>Mots-clés

- ainutlaatuinen henkilökohtainen tunnus
- henkilökohtainen tunnus
- henkilötunnus
- henkilötunnusnumero #
- henkilötunnusnumero
- hetu
- id no
- numéro d’ID
- numéro d’identification
- identiteetti numero
- numéro d’identité
- idnumber
- kansallinen henkilötunnus
- kansallisen henkilökortin
- carte d’identité nationale
- national id no.
- ID personnel
- code d’identité personnelle
- #numéroidpersonnel
- personbeteckning
- personnummer
- numéro de sécurité sociale
- sosiaaliturvatunnus
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
- tunnistenumero
- tunnus numero
- tunnusluku
- tunnusnumero
- verokortti
- veronumero
- verotunniste
- verotunnus
