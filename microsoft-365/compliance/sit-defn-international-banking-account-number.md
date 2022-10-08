---
title: Définition d’entité IBAN (International Banking Account Number)
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
description: Définition d’entité de type d’information sensible IBAN (International Banking Account Number).
ms.openlocfilehash: 2bd3eeaec0bffb8b75180e60782ecb3aeedc32a5
ms.sourcegitcommit: be2334dbcd4e1bf309349d981a68a30e06de0297
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2022
ms.locfileid: "68378377"
---
# <a name="international-banking-account-number-iban"></a>Numéro de compte bancaire international (IBAN)

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="format"></a>Format

Code pays (à deux lettres) plus chiffres de contrôle (à deux chiffres) plus numéro BBAN (jusqu’à 30 chiffres)

## <a name="pattern"></a>Modèle

Le modèle doit inclure tous ces modèles :

- Code pays à deux lettres
- Deux chiffres de contrôle (suivis d’un espace facultatif) 
- 1 à 7 groupes de quatre lettres ou chiffres (séparés par des espaces facultatifs)
- 1 à 3 lettres ou chiffres

Le format pour chaque pays est légèrement différent. Le type d’informations sensibles IBAN couvre ces 68 pays :

- ad
- Ae
- Al
- À
- az
- Ba
- be
- bg
- Bh
- br
- Ch
- Cr
- cy
- Cz
- de
- Dk
- faire
- Ee
- es
- fi
- fo
- fr
- Go
- ge
- Gi
- gl
- Gr
- gt
- hr
- hu
- Ie
- il
- is
- it
- jo
- Kw
- Kz
- lb
- Li
- lt
- lu
- lv
- mc
- md
- me
- mk
- mr
- mt
- Mu
- nl
- Non
- Pk
- pl
- ps
- pt
- Qa
- ro
- rs
- sa
- se
- si
- sk
- Sm
- tl
- Amt
- tr
- Vg
- Xk


## <a name="checksum"></a>Somme de contrôle

Oui

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction `Func_iban` trouve un contenu qui correspond au modèle.
- La somme de contrôle est correcte.

```xml
<Entity id="e7dc4711-11b7-4cb0-b88b-2c394a771f0e" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_iban" />
  </Pattern>
</Entity>
```

## <a name="keywords"></a>Mots-clés

Aucun
