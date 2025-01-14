---
title: Définition d’entité de numéro d’identification unique en Inde (Aadhaar)
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
description: Définition d’entité de type d’informations sensibles d’identification unique en Inde (Aadhaar).
ms.openlocfilehash: 242a186bf229b9d5bf05db2a72cbd060906311c4
ms.sourcegitcommit: be2334dbcd4e1bf309349d981a68a30e06de0297
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2022
ms.locfileid: "68380467"
---
# <a name="india-unique-identification-aadhaar-number"></a>Numéro d’identification unique de l’Inde (Aadhaar)

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="format"></a>Format

12 chiffres contenant éventuellement des espaces ou des tirets

## <a name="pattern"></a>Modèle

12 chiffres :

- Chiffre qui n’est pas 0 ou 1
- Trois chiffres
- Éventuellement un tiret ou un espace 
- Quatre chiffres
- Éventuellement un tiret ou un espace 
- Chiffre final, qui est le chiffre de vérification

## <a name="checksum"></a>Somme de contrôle

Oui

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_india_aadhaar` trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keyword_india_aadhar` est trouvé.
- La somme de contrôle est correcte.

Une stratégie DLP a une confiance moyenne ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_india_aadhaar` trouve un contenu qui correspond au modèle.
- La somme de contrôle est correcte.

```xml
<!-- India Unique Identification (Aadhaar) number -->
<Entity id="1ca46b29-76f5-4f46-9383-cfa15e91048f" recommendedConfidence="85" patternsProximity="300">
  <Pattern confidenceLevel="85">
     <IdMatch idRef="Func_india_aadhaar"/>
     <Match idRef="Keyword_india_aadhar"/>
  </Pattern>
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Func_india_aadhaar"/>
  </Pattern>
</Entity>
```

## <a name="keywords"></a>Mots-clés

### <a name="keyword_india_aadhar"></a>Keyword_india_aadhar

- aadhaar
- aadhar
- aadhar #
- uid
- आधार
- uidai
