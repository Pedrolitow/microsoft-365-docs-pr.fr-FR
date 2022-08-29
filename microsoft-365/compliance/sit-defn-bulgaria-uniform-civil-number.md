---
title: Définition uniforme de l’entité numéro civil en Bulgarie
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
description: Bulgarie Uniform civil number sensitive information type entity definition.
ms.openlocfilehash: f9e97c049cf20f3c804e0fbf0f12489e557ad9f1
ms.sourcegitcommit: 72d10d0bc29ecc8b19c395f1815dc48b549096d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2022
ms.locfileid: "67369668"
---
# <a name="bulgaria-uniform-civil-number"></a>Numéro civil uniforme de l’Espagne

## <a name="format"></a>Format

10 chiffres sans espaces et délimiteurs

## <a name="pattern"></a>Modèle

10 chiffres sans espaces et délimiteurs

- six chiffres qui correspondent à la date de naissance (AAAAMMD)
- deux chiffres qui correspondent à l’ordre de naissance
- un chiffre qui correspond au sexe : un chiffre pair pour un homme et un chiffre impair pour la femme
- un chiffre de vérification

## <a name="checksum"></a>Somme de contrôle

Oui

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_bulgaria_eu_national_id_card` trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keywords_bulgaria_eu_national_id_card` est trouvé.

Une stratégie DLP a une confiance moyenne ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_bulgaria_eu_national_id_card` trouve un contenu qui correspond au modèle.

```xml
      <!-- Bulgaria Uniform Civil Number -->
      <Entity id="100d58b1-0a35-4fb1-aa89-e4a86fb53fcc" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_bulgaria_eu_national_id_card" />
          <Match idRef="Keywords_bulgaria_eu_national_id_card" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_bulgaria_eu_national_id_card" />
          <Any minMatches="0" maxMatches="0">
            <Match idRef="Keywords_bulgaria_eu_telephone_number" />
            <Match idRef="Keywords_bulgaria_eu_mobile_number" />
          </Any>
        </Pattern>
      </Entity>
```

## <a name="keywords"></a>Mots-clés

### <a name="keywords_bulgaria_eu_national_id_card"></a>Keywords_bulgaria_eu_national_id_card

- bnn#
- bnn
- bucn #
- bucn
- edinen grazhdanski nomer
- egn #
- egn
- numéro d’identification
- id national
- numéro national
- #numéronational
- numéronational
- ID personnel
- personnel non
- numéro personnel
- #numéroidpersonnel
- numéro de sécurité sociale
- nss#
- nss
- ID civil uniforme
- non civil uniforme
- numéro civil uniforme
- uniformcivilno #
- uniformcivilno
- uniformcivilnumber #
- uniformcivilnumber
- numéro de citoyenneté unique
- егн #
- егн
- единен граждански номер
- идентификационен номер
- личен номер
- лична идентификация
- лично не
- национален номер
- номер на гражданството
- униформ id
- униформ граждански id
- униформ граждански не
- униформ граждански номер
- униформгражданскиid #
- униформгражданскине. #