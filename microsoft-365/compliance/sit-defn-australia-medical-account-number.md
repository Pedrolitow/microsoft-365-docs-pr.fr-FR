---
title: Définition de l’entité numéro de compte médical en Australie
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
description: Définition d’entité de type d’entité de type d’informations sensibles de numéro de compte médical en Australie.
ms.openlocfilehash: c17de71ef0c16b5c14ba118c66ae0d9274ce4468
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2022
ms.locfileid: "66996159"
---
# <a name="australia-medical-account-number"></a>Numéro de dossier médical Australie

## <a name="format"></a>Format

10 à 11 chiffres

## <a name="pattern"></a>Modèle

10 à 11 chiffres :

- Le premier chiffre est compris entre 2 et 6
- Le neuvième chiffre est un chiffre de contrôle
- Le dixième chiffre est le chiffre d’émission
- 11e chiffre (facultatif) est le nombre individuel

## <a name="checksum"></a>Somme de contrôle

Oui

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction Func_australian_medical_account_number trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_Australia_Medical_Account_Number est trouvé.
- La somme de contrôle est correcte.

```xml
  <!-- Australia Medical Account Number -->
<Entity id="104a99a0-3d3b-4542-a40d-ab0b9e1efe63" recommendedConfidence="85" patternsProximity="300">
    <Pattern confidenceLevel="85">
     <IdMatch idRef="Func_australian_medical_account_number"/>
     <Match idRef="Keyword_Australia_Medical_Account_Number"/>
    </Pattern>
</Entity>
```

## <a name="keywords"></a>Mots-clés

### <a name="keyword_australia_medical_account_number"></a>Keyword_Australia_Medical_Account_Number

- informations sur le compte bancaire
- remboursements d’assurance maladie
- compte de prêts immobiliers
- paiements bancaires
- direction de l’information
- prêt sur carte de crédit
- département des services sociaux
- service local
- Medicare
