---
title: Définition de l’entité numéro de permis de conduire portugal
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
description: Définition d’entité de type d’entité du numéro de permis de conduire du Portugal.
ms.openlocfilehash: 235e33c55531e1f5bbc2de28a33ed6bb2b74390b
ms.sourcegitcommit: 176bbd29c92e1c0812e8bcd1e1e4938a3e1d7331
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/05/2022
ms.locfileid: "68472758"
---
# <a name="portugal-drivers-license-number"></a>Numéro de permis de conduire portugais

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="format"></a>Format

deux modèles : deux lettres suivies de 5 à 8 chiffres avec des caractères spéciaux

## <a name="pattern"></a>Modèle

Modèle 1 : Deux lettres suivies de 5/6 avec des caractères spéciaux :

- Deux lettres (non sensibles à la casse)
- Un trait d’union 
- Cinq ou six chiffres
- Un espace
- Un chiffre

Modèle 2 : Une lettre suivie de 6/8 chiffres avec des caractères spéciaux :

- Une lettre (non sensible à la casse)
- Un trait d’union 
- Six ou huit chiffres
- Un espace
- Un chiffre

## <a name="checksum"></a>Somme de contrôle

Non

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- L’expression régulière `Regex_portugal_eu_driver's_license_number` trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keywords_eu_driver's_license_number`ou `Keywords_portugal_eu_driver's_license_number` est trouvé.

```xml
      <!-- Portugal Driver's License Number -->
      <Entity id="977f1e5a-2c33-4bcc-b516-95bb275cff23" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_portugal_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_portugal_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

## <a name="keywords"></a>Mots-clés

### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver s_license_number

- permisconduire
- permisconduire
- permisconduire
- permisconduire
- permisconduire
- permisconduire
- permis de conduire
- permis de conduire
- Permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- permisconduire
- permisconduire
- permisconduire
- permisconduire
- permisconduire
- permisconduire
- permisconduire
- permisconduire
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- permisconduire
- permisconduire
- permisconduire
- permis de conduire
- permis de conduire
- permis de conduire
- permis conduire
- permis conduire
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- permisconduire
- permisconduire
- permisconduire
- permisconduire
- permisconduire
- permisconduire
- permis de conduire
- permis de conduire
- permis de conduire
- Permis de conduire
- permis de conduire
- permis de conduire
- pc#
- pc#
- permis de conduire n°
- permis de conduire n°
- permis de conduire n°
- permis de conduire n°
- permis de conduire n°
- permis de conduire n°
- permis de conduire n°
- permis de conduire n°
- permis de conduire n°
- permis de conduire n°
- permis de conduire n°
- permisconduire #
- permisconduire #
- permisconduire #
- permisconduire #
- permisconduire #
- permisconduire #
- permisconduire #
- permisconduire #
- permisconduire #
- permisconduire #
- permisconduire #
- permisconduire #
- permisconduire #
- permisconduire #
- permisconduire #
- permis de conduire #
- permis de conduire #
- permis de conduire #
- permis de conduire n°
- permis de conduire n°
- permis de conduire n°
- permis de conduire n°
- permis de conduire n°
- permis de conduire n°
- permis de conduire n°
- permis de conduire n°
- permis de conduire n°
- permis de conduire n°
- permis de conduire n°
- permis de conduire n°
- permis de conduire n°
- permis de conduire n°
- permis de conduire n°
- permis de conduire n°
- permis de conduire n°
- permis de conduire n°
- permis de conduire
- permis de conduire
- pc #
- permis conduire
- permis conduire
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduire
- permis conduire
- permis conduire
- permis de conduire
- permis de conduire
- permis de conduire
- permis de conduite
- pc no
- pcno
- pc numéro

### <a name="keywords_portugal_eu_drivers_license_number"></a>Keywords_portugal_eu_driver s_license_number

- carteira de motorista
- carteira motorista
- carteira de habilitação
- carteira habilitação
- número de licença
- número licença
- permissão de condução
- permissão condução
- Licença condução Portugal
- carta de condução
