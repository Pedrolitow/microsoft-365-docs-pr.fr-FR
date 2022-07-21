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
description: Définition d’entité de type d’information sensible de numéro national belge.
ms.openlocfilehash: 5fc644a8dcb275cba2986139dfdd16444e47c218
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2022
ms.locfileid: "66950809"
---
# <a name="belgium-national-number"></a>Numéro national belge

## <a name="format"></a>Format

11 chiffres plus délimiteurs facultatifs

## <a name="pattern"></a>Modèle

11 chiffres plus des délimiteurs :

- six chiffres et deux périodes facultatives au format YY. MM.DD pour la date de naissance
- Délimiteur facultatif à partir d’un point, d’un tiret, d’un espace
- trois chiffres séquentiels (impairs pour les mâles, même pour les femelles)
- Délimiteur facultatif à partir d’un point, d’un tiret, d’un espace
- deux chiffres de vérification

## <a name="checksum"></a>Somme de contrôle

Oui

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction `Func_belgium_national_number` recherche le contenu qui correspond au modèle.
- Un mot clé est `Keyword_belgium_national_number` trouvé.
- La somme de contrôle est correcte.

Une stratégie DLP a une faible confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- La fonction `Func_belgium_national_number` recherche le contenu qui correspond au modèle.
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
- Bnn #
- Bnn
- carte d’identité
- identifiant national
- identifiantnational #
- identificatie
- Identification
- identifikation
- identifikationsnummer
- identifizierung
- identité
- identiteit
- identiteitskaart
- Identité
- inscription
- numéro national
- registre national
- nationalnumber #
- nationalnumber
- Nif #
- Nif
- numéro d’assuré
- numéro de registre national
- numéro de sécurité
- numéro d’identification
- numéro d’immatriculation
- numéro national
- numéronational #
- numéro d’ID personnel
- personalausweis
- personalidnumber #
- registratie
- Enregistrement
- registrationsnumme
- registrierung
- numéro de sécurité sociale
- Ssn #
- Ssn
- steuernummer
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