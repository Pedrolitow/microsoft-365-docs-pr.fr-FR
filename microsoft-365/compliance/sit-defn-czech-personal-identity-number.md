---
title: Définition d’entité numéro d’identité personnelle tchèque
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
description: Définition d’entité de type d’entité de type d’informations sensibles de numéro d’identité personnelle tchèque.
ms.openlocfilehash: df2a7902f136c45e7f406061216e30e3fcec6372
ms.sourcegitcommit: 2ff545246fec060ea7829da5afbc1cdc698d51ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2022
ms.locfileid: "68362923"
---
# <a name="czech-personal-identity-number"></a>Numéro d’identité personnelle tchèque

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="format"></a>Format

neuf chiffres avec barre oblique facultative (ancien format)

10 chiffres avec barre oblique facultative (nouveau format)

## <a name="pattern"></a>Modèle

neuf chiffres (ancien format) :

- six chiffres qui représentent la date de naissance
- une barre oblique facultative
- trois chiffres

10 chiffres (nouveau format) :

- six chiffres qui représentent la date de naissance
- une barre oblique facultative
- quatre chiffres où le dernier chiffre est un chiffre à cocher

## <a name="checksum"></a>Somme de contrôle

Oui

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_czech_id_card` trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keyword_czech_id_card` est trouvé.
- La somme de contrôle est correcte.

Une stratégie DLP a une confiance moyenne ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_czech_id_card_new_format` trouve un contenu qui correspond au modèle.
- La somme de contrôle est correcte.

```xml
<!-- Czech Personal Identity Number -->
      <!-- Czech Personal Identity Number -->
      <Entity id="60c0725a-4eb6-455b-9dda-05d8a7396497" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_czech_id_card" />
          <Match idRef="Keyword_czech_id_card" />
        </Pattern>
        <Version minEngineVersion="15.20.3000.000">
          <Pattern confidenceLevel="75">
            <IdMatch idRef="Func_czech_id_card_new_format" />
          </Pattern>
        </Version>
      </Entity>
```
## <a name="keywords"></a>Mots-clés

### <a name="keyword_czech_id_card"></a>Keyword_czech_id_card

- nombre de naissances
- ID de république tchèque
- czechidno #
- daňové číslo
- identifikační číslo
- identity no
- numéro d’identité
- identityno #
- identityno
- numéro d’assurance
- numéro d’identification nationale
- #numéronational
- numéro national
- osobní číslo
- #numéroidpersonnel
- numéro d’ID personnel
- numéro d’identification personnelle
- numéro personnel
- Pid #
- pid
- pojištění číslo
- rč
- rodne cislo
- rodné číslo
- nss
- nss#
- numéro de sécurité sociale
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
