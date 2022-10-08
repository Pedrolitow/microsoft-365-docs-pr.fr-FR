---
title: Définition de l’entité numéro d’enregistrement du résident sud-coréen
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
description: Définition d’entité de type d’entité de type d’informations sensibles du numéro d’enregistrement résident sud-coréen.
ms.openlocfilehash: d775cadefa4007b2770b42901530c8a78e7f0eb2
ms.sourcegitcommit: 176bbd29c92e1c0812e8bcd1e1e4938a3e1d7331
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/05/2022
ms.locfileid: "68472437"
---
# <a name="south-korea-resident-registration-number"></a>Matricule de résident Corée du Sud

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="format"></a>Format

13 chiffres contenant un trait d’union

## <a name="pattern"></a>Modèle

13 chiffres :

- six chiffres au format YYMMDD, qui sont la date de naissance
- un trait d’union
- un chiffre déterminé par le siècle et le sexe
- Code de région de naissance à quatre chiffres
- un chiffre utilisé pour différencier les personnes pour lesquelles les nombres précédents sont identiques
- un chiffre à cocher.

## <a name="checksum"></a>Somme de contrôle

Oui

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_south_korea_resident_number` trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keyword_south_korea_resident_number` est trouvé.
- La somme de contrôle est correcte.

Une stratégie DLP a une confiance moyenne ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_south_korea_resident_number` trouve un contenu qui correspond au modèle.
- La somme de contrôle est correcte.

```xml
<!-- South Korea Resident Registration Number -->
<Entity id="5b802e18-ba80-44c4-bc83-bf2ad36ae36a" recommendedConfidence="85" patternsProximity="300">
  <Pattern confidenceLevel="85">
     <IdMatch idRef="Func_south_korea_resident_number"/>
     <Match idRef="Keyword_south_korea_resident_number"/>
  </Pattern>
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Func_south_korea_resident_number"/>
  </Pattern>
</Entity>
```

## <a name="keywords"></a>Mots-clés

### <a name="keyword_south_korea_resident_number"></a>Keyword_south_korea_resident_number

- National ID card
- Citizen’s Registration Number
- Jumin deungnok beonho
- RRN
- 주민등록번호
