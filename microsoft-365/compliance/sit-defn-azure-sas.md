---
title: Définition d’entité Azure SAS
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
description: Définition d’entité de type d’informations sensibles Azure SAS.
ms.openlocfilehash: c7d63497a94204b77f83c5b357700311bf332e8c
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2022
ms.locfileid: "66996759"
---
# <a name="azure-sas"></a>Azure SAS

## <a name="format"></a>Format

`sig` Chaîne suivie des caractères et des chaînes décrits dans le modèle ci-dessous.

## <a name="pattern"></a>Modèle

- la chaîne `sig`
- de zéro à deux espaces blancs
- un signe égal (=)
- de zéro à deux espaces blancs
- toute combinaison comprise entre 43 et 53 caractères qui sont des lettres minuscules ou majuscules, des chiffres ou le signe de pourcentage (%)
- la chaîne `%3d`
- tout caractère qui n’est pas une lettre minuscule ou majuscule, un chiffre ou un signe de pourcentage (%)

## <a name="checksum"></a>Somme de contrôle

Non

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- L’expression régulière `CEP_Regex_AzureSAS` trouve un contenu qui correspond au modèle.

```xml
<!--Azure SAS-->
<Entity id="4d235014-e564-47f4-a6fb-6ebb4a826834" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="CEP_Regex_AzureSAS" />
  </Pattern>
</Entity>
```
