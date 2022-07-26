---
title: Définition d’entité de numéro national belge
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
description: Définition d’entité de type d’informations sensibles de numéro national belge.
ms.openlocfilehash: 5fc644a8dcb275cba2986139dfdd16444e47c218
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2022
ms.locfileid: "66950809"
---
# <a name="belgium-national-number"></a>Numéro national en Belgique

## <a name="format"></a>Format

11 chiffres plus des délimiteurs facultatifs

## <a name="pattern"></a>Modèle

11 chiffres plus des délimiteurs :

- six chiffres et deux points facultatifs au format AA.MM.JJ pour la date de naissance 
- Délimiteur facultatif à partir d’un point, d’un tiret, d’un espace
- trois chiffres séquentiels (impairs pour les hommes, pairs pour les femmes)
- Délimiteur facultatif à partir d’un point, d’un tiret, d’un espace
- deux chiffres de contrôle

## <a name="checksum"></a>Somme de contrôle

Oui

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_belgium_national_number` trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keyword_belgium_national_number` est trouvé.
- La somme de contrôle est correcte.

Une stratégie DLP a une confiance faible ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_belgium_national_number` trouve un contenu qui correspond au modèle.
- La somme de contrôle est correcte.

```xml
<!-- Belgium National Number -->
       <Entity id="fb969c9e-0fd1-4b18-8091-a2123c5e6a54" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_belgium_national_number" />
          <Match idRef="Keyword_belgium_national_number" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Func_belgium_national_number" />
        </Pattern>
      </Entity>
```

## <a name="keywords"></a>Mots-clés

### <a name="keyword_belgium_national_number"></a>Keyword_belgium_national_number

- belasting aantal
- bnn#
- bnn
- Carte d’identité
- identifiant national
- #identifiantnational
- identificatie
- identification
- identifikation
- identifikationsnummer
- identifizierung
- identité
- identiteit
- identiteitskaart
- identité
- inscription
- numéro national
- registre national
- #numéronational
- numéronational
- n#if
- nif
- numéro d’assuré
- numéro de registre national
- numéro de sécurité
- numéro d’identification
- numéro d’immatriculation
- numéro national
- #numéronational
- numéro d’ID personnel
- personalausweis
- #numéroidpersonnel
- registratie
- inscription
- registrationsnumme
- registrierung
- numéro de sécurité sociale
- nss#
- nss
- steuernummer
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