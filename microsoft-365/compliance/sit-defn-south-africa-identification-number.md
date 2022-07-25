---
title: Définition de l’entité numéro d’identification en Afrique du Sud
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
description: Définition d’entité de type d’information sensible du numéro d’identification en Afrique du Sud.
ms.openlocfilehash: 95fbf2baa8842f1654881d0435a0328b5593242a
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2022
ms.locfileid: "66996629"
---
# <a name="south-africa-identification-number"></a>Numéro d'identification Afrique du Sud

### <a name="format"></a>Format

13 chiffres pouvant contenir des espaces

## <a name="pattern"></a>Modèle

13 chiffres :

- six chiffres au format YYMMDD, qui sont la date de naissance
- quatre chiffres
- un indicateur de citoyenneté à un chiffre
- le chiffre « 8 » ou « 9 »
- un chiffre, qui est un chiffre de somme de contrôle

## <a name="checksum"></a>Somme de contrôle

Oui

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_south_africa_identification_number` trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keyword_south_africa_identification_number` est trouvé.
- La somme de contrôle est correcte.

```xml
<!-- South Africa Identification Number -->
<Entity id="e2adf7cb-8ea6-4048-a2ed-d89eb65f2780" recommendedConfidence="85" patternsProximity="300">
  <Pattern confidenceLevel="85">
     <IdMatch idRef="Func_south_africa_identification_number"/>
     <Match idRef="Keyword_south_africa_identification_number"/>
  </Pattern>
</Entity>
```

## <a name="keywords"></a>Mots-clés

### <a name="keyword_south_africa_identification_number"></a>Keyword_south_africa_identification_number

- Identity card
- ID
- Identification