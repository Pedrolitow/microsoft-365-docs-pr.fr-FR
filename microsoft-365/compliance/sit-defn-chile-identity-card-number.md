---
title: Définition de l’entité numéro de carte d’identité chilienne
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
description: Définition d’entité du type d’entité du type d’informations sensibles du numéro de carte d’identité chilienne.
ms.openlocfilehash: 1ec3b90d52d5404bf49a343cba7fb2c7f5464870
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2022
ms.locfileid: "66996590"
---
# <a name="chile-identity-card-number"></a>Numéro de carte d’identité chilien

## <a name="format"></a>Format

sept à huit chiffres plus délimiteurs un chiffre ou une lettre de vérification

## <a name="pattern"></a>Modèle

sept à huit chiffres plus délimiteurs :

- un à deux chiffres
- une période facultative
- trois chiffres
- une période facultative
- trois chiffres
- un tiret
- un chiffre ou une lettre (non sensible à la casse) qui est un chiffre à cocher

## <a name="checksum"></a>Somme de contrôle

Oui

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_chile_id_card` trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keyword_chile_id_card` est trouvé.
- La somme de contrôle est correcte.

Une stratégie DLP a une confiance moyenne ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_chile_id_card` trouve un contenu qui correspond au modèle.
- La somme de contrôle est correcte.

```xml
<!-- Chile Identity Card Number -->
<Entity id="4e979794-49a0-407e-a0b9-2c536937b925" recommendedConfidence="85" patternsProximity="300">
  <Pattern confidenceLevel="85">
     <IdMatch idRef="Func_chile_id_card"/>
     <Match idRef="Keyword_chile_id_card"/>
  </Pattern>
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Func_chile_id_card"/>
  </Pattern>
</Entity>
```

## <a name="keywords"></a>Mots-clés

### <a name="keyword_chile_id_card"></a>Keyword_chile_id_card

- cédula de identidad
- identificación
- numéro d’identification nationale
- numéro d’identification nationale
- id national
- número de identificación nacional
- rol único nacional
- rol único tributario
- COURIR
- ORNIÈRE
- tarjeta de identificación
- Rol Unico Nacional
- Rol Unico Tributario
- COURIR #
- ORNIÈRE #
- nationaluniqueroleID #
- nacional identidad
- número identificación
- identidad número
- numero identificacion
- identidad nombreuses
- Identité chilienne non.
- Numéro d’identité chilien
- Identité chilienne #
- Registre fiscal unique
- Unique Tributary Role
- Rôle fiscal unique
- Numéro de tribut unique
- Numéro national unique
- Rôle national unique
- Rôle unique national
- Identité chilienne non.
- Numéro d’identité chilien
- Identité chilienne #
- R.U.T
- R.U.N