---
title: Définition d’entité de numéro de carte d’identité d’inscription nationale (NRIC) de Singapour
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
description: Définition d’entité de type d’information sensible de numéro de carte d’identité d’inscription nationale (NRIC) de Singapour.
ms.openlocfilehash: f77564f85444f3928a3ed6d3437d04e19774c411
ms.sourcegitcommit: 176bbd29c92e1c0812e8bcd1e1e4938a3e1d7331
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/05/2022
ms.locfileid: "68471755"
---
# <a name="singapore-national-registration-identity-card-nric-number"></a>Numéro de carte d'identité d'enregistrement national (NRIC) Singapour

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="format"></a>Format

neuf lettres et chiffres

## <a name="pattern"></a>Modèle

- neuf lettres et chiffres :

- la lettre « F », « G », « M », « S » ou « T » (non sensible à la casse)
- sept chiffres
- un chiffre à cocher alphabétique

## <a name="checksum"></a>Somme de contrôle

Oui

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- L’expression régulière `Regex_singapore_nric` trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keyword_singapore_nric` est trouvé.
- La somme de contrôle est correcte.

Une stratégie DLP a une confiance moyenne ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- L’expression régulière `Regex_singapore_nric` trouve un contenu qui correspond au modèle.
- La somme de contrôle est correcte.

```xml
<!-- Singapore National Registration Identity Card (NRIC) Number -->
<Entity id="cead390a-dd83-4856-9751-fb6dc98c34da" recommendedConfidence="75" patternsProximity="300">
  <Pattern confidenceLevel="85">
     <IdMatch idRef="Regex_singapore_nric"/>
     <Match idRef="Keyword_singapore_nric"/>
  </Pattern>
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Regex_singapore_nric"/>
  </Pattern>
</Entity>
```

## <a name="keywords"></a>Mots-clés

### <a name="keyword_singapore_nric"></a>Keyword_singapore_nric

- National Registration Identity Card
- Identity Card Number
- NRIC
- Ic
- Foreign Identification Number
- FIN
- 身份证
- 身份證
