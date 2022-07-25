---
title: Définition de l’entité Carte d’identité de l’électeur de l’Inde
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
description: Définition d’entité de type d’entité de type d’information sensible de carte d’électeur de l’Inde.
ms.openlocfilehash: 4556824999f44f6407e996fbca7c82e79fe2cafc
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2022
ms.locfileid: "66996239"
---
# <a name="india-voter-id-card"></a>Carte d’ID d’vote pour l’Inde

## <a name="format"></a>Format

Modèle alphanumérique de 10 caractères

## <a name="pattern"></a>Modèle

10 lettres ou chiffres :

- trois lettres
- sept chiffres

## <a name="checksum"></a>Somme de contrôle

Non

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- L’expression régulière `Regex_india_voter_id_card` trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keyword_india_voter_id_card` est trouvé.

Une stratégie DLP a une confiance faible ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- L’expression régulière `Regex_india_voter_id_card` trouve un contenu qui correspond au modèle.

```xml
      <!-- India Voter Id Card  -->
        <Entity id="646d643f-5228-4408-acc8-f2e81a6df897" patternsProximity="300" recommendedConfidence="75" relaxProximity="true">
           <Pattern confidenceLevel="75">
             <IdMatch idRef="Regex_india_voter_id_card" />
             <Match idRef="Keyword_india_voter_id_card" />
            </Pattern>
           <Pattern confidenceLevel="65">
              <IdMatch idRef="Regex_india_voter_id_card" />
            </Pattern>
        </Entity>
```

## <a name="keywords"></a>Mots-clés

### <a name="keyword_india_voter_id_card"></a>Keyword_india_voter_id_card

- Électeur
- voterid
- votercard
- voteridcard
- carte d’identité de photo électorale
- ÉPIQUE
- ECI
- élection commmision