---
title: Définition de l’entité du code fiscal de l’Italie
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
description: Définition d’entité de type d’entité de type d’informations sensibles du code fiscal italien.
ms.openlocfilehash: 1a27af7f33aba799a37c64c37e53eef01555ec3c
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2022
ms.locfileid: "66997590"
---
# <a name="italy-fiscal-code"></a>Code fiscal italien

Ce type d’informations sensibles est uniquement disponible pour une utilisation dans :

- stratégies de protection contre la perte de données
- stratégies de conformité des communications
- gestion du cycle de vie des données
- gestion des enregistrements
- Microsoft Defender for Cloud Apps

## <a name="format"></a>Format

combinaison de 16 caractères de lettres et de chiffres dans le modèle spécifié

## <a name="pattern"></a>Modèle

Combinaison de 16 caractères de lettres et de chiffres :

- trois lettres qui correspondent aux trois premières consonnes dans le nom de famille
- trois lettres qui correspondent aux première, troisième et quatrième consonnes dans le prénom
- deux chiffres qui correspondent aux derniers chiffres de l’année de naissance
- une lettre qui correspond à la lettre pour le mois de naissance : les lettres sont utilisées par ordre alphabétique, mais seules les lettres A à E, H, L, M, P, R à T sont utilisées (donc, Janvier est A et Octobre est R)
- deux chiffres qui correspondent au jour du mois de naissance afin de différencier les sexes, 40 sont ajoutés au jour de naissance pour les femmes
- quatre chiffres qui correspondent à l’indicatif régional spécifique à la municipalité où la personne est née (les codes nationaux sont utilisés pour les pays étrangers)
- un chiffre de parité

## <a name="checksum"></a>Somme de contrôle

Oui

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_italy_eu_national_id_card` trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keywords_italy_eu_national_id_card` est trouvé.

Une stratégie DLP a une confiance moyenne ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_italy_eu_national_id_card` trouve un contenu qui correspond au modèle.

```xml
      <!-- Italy Fiscal Code -->
      <Entity id="4cd79172-8da9-4ff5-9188-98b1e7e2eca6" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_italy_eu_national_id_card" />
          <Match idRef="Keywords_italy_eu_national_id_card" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_italy_eu_national_id_card" />
        </Pattern>
      </Entity>
```

## <a name="keywords"></a>Mots-clés

### <a name="keywords_italy_eu_national_id_card"></a>Keywords_italy_eu_national_id_card

- codice fiscal
- codice fiscale
- codice id personale
- codice personale
- code fiscal
- numero certificato personale
- numero di identificazione fiscale
- numero id personale
- nombreuses informations personnelles
- numéro de certificat personnel
- code personnel
- code d’ID personnel
- numéro d’ID personnel
- personalcodeno #
- code fiscal
- id fiscal
- numéro d’identification fiscal
- numéro d’identification fiscal
- numéro d’identité fiscale
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