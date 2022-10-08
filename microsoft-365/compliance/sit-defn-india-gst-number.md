---
title: Définition de l’entité Numéro de TPS de l’Inde
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
description: Définition d’entité de type d’entité de type d’informations sensibles de numéro de TPS de l’Inde.
ms.openlocfilehash: 6fc840d994311a88ddbb5cc86a26a9b36969213a
ms.sourcegitcommit: be2334dbcd4e1bf309349d981a68a30e06de0297
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2022
ms.locfileid: "68379649"
---
# <a name="india-gst-number"></a>Numéro de GST pour l’Inde

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="format"></a>Format

Modèle alphanumérique à 15 caractères

## <a name="pattern"></a>Modèle

15 lettres ou chiffres :

- deux chiffres représentant le code d’état valide
- un espace ou un tiret facultatif
- dix caractères représentant le numéro de compte permanent (PAN)
- une lettre ou un chiffre
- un espace ou un tiret facultatif
- une lettre 'z' ou 'Z'
- un espace ou un tiret facultatif
- un chiffre de vérification

## <a name="checksum"></a>Somme de contrôle

Oui

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_india_gst_number` trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keyword_india_gst_number` est trouvé.

Une stratégie DLP a une confiance moyenne ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_india_gst_number` trouve un contenu qui correspond au modèle.

```xml
    <!-- India GST number  -->
      <Entity id="9f5a721c-2fd2-446a-a27e-0c02fbe4630c" patternsProximity="300" recommendedConfidence="85" relaxProximity="true">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_india_gst_number" />
          <Match idRef="Keyword_india_gst_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_india_gst_number" />
        </Pattern>
      </Entity>
```

## <a name="keywords"></a>Mots-clés

### <a name="keyword_india_gst_number"></a>Keyword_india_gst_number

- Tps
- gstin
- taxe sur les biens et services
- biens et taxe de service
