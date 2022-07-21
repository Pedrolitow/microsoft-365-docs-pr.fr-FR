---
title: Définition d’entité de numéro BSN (Citizens Service) aux Pays-Bas
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
description: Définition d’entité de type d’information sensible du numéro BSN (Citizen’s Service) des Pays-Bas.
ms.openlocfilehash: 4a5ca70bbbffe2d89b2dd05bd51e3dcda525e6a3
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2022
ms.locfileid: "66950817"
---
# <a name="netherlands-citizens-service-bsn-number"></a>Numéro de service des citoyens néerlandais (BSN)

## <a name="format"></a>Format

huit ou neuf chiffres contenant des espaces facultatifs

## <a name="pattern"></a>Modèle

huit-neuf chiffres :

- trois chiffres
- un espace (facultatif)
- trois chiffres
- un espace (facultatif)
- deux-trois chiffres

## <a name="checksum"></a>Somme de contrôle

Oui

## <a name="definition"></a>Définition

Une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- Contenu de la fonction `Func_netherlands_bsn finds` qui correspond au modèle.
- Un mot clé est `Keyword_netherlands_bsn` trouvé.
- La somme de contrôle est correcte.

```xml
      <!-- Netherlands Citizen's Service (BSN) Number -->
      <Entity id="c5f54253-ef7e-44f6-a578-440ed67e946d" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_netherlands_bsn" />
          <Match idRef="Keywords_netherlands_eu_national_id_card" />
        </Pattern>
      </Entity>
```

## <a name="keywords"></a>Mots-clés

### <a name="keywords_netherlands_eu_national_id_card"></a>Keywords_netherlands_eu_national_id_card

- Bsn #
- Bsn
- burgerservicenummer
- numéro de service citoyen
- numéro de personne
- numéro personnel
- code numérique personnel
- numéro lié à la personne
- persoonlijk nummer
- persoonlijke numerieke code
- persoonsgebonden
- persoonsnummer
- sociaal-fiscaal nummer
- numéro social-fiscal
- Sofi
- sofinummer
- uniek identificatienummer
- uniek identiteitsnummer
- numéro d’identification unique
- numéro d’identité unique
- uniqueidentityno #