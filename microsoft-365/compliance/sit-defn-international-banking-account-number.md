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
- M365-security-compliance
hideEdit: true
feedback_system: None
recommendations: false
description: Définition d’entité de type d’information sensible IBAN (International Banking Account Number).
ms.openlocfilehash: 739c0a1fd90da1da817f46019cd1023be8ab27a3
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2022
ms.locfileid: "66996700"
---
# <a name="international-banking-account-number-iban"></a>Numéro de compte bancaire international (IBAN)

## <a name="format"></a>Format

Code pays (à deux lettres) plus chiffres de contrôle (à deux chiffres) plus numéro BBAN (jusqu’à 30 chiffres)

## <a name="pattern"></a>Modèle

Le modèle doit inclure tous les éléments suivants :

- Code pays à deux lettres
- Deux chiffres de contrôle (suivis d’un espace facultatif) 
- 1 à 7 groupes de quatre lettres ou chiffres (séparés par des espaces facultatifs)
- 1 à 3 lettres ou chiffres

Le format pour chaque pays est légèrement différent. Le type d’informations sensibles IBAN recouvre ces 60 pays :

- ad
- Ae
- Al
- À
- az
- Ba
- be
- bg
- Bh
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
- hr
- hu
- Ie
- il
- is
- it
- Kw
- Kz
- lb
- Li
- lt
- lu
- lv
- Mc
- md
- me
- mk
- mr
- mt
- Mu
- nl
- Non
- pl
- pt
- ro
- rs
- sa
- se
- si
- sk
- Sm
- Amt
- tr
- Vg

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