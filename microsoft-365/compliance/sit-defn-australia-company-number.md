---
title: Définition de l’entité numéro d’entreprise en Australie
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
description: Définition d’entité de type d’informations sensibles numéro d’entreprise en Australie.
ms.openlocfilehash: 86b9167340d4730f6c1726d57e94c16b3ef9993c
ms.sourcegitcommit: 72d10d0bc29ecc8b19c395f1815dc48b549096d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2022
ms.locfileid: "67368438"
---
# <a name="australia-company-number"></a>Numéro d’entreprise en Australie



## <a name="format"></a>Format

neuf chiffres avec délimiteurs

## <a name="pattern"></a>Modèle

neuf chiffres avec délimiteurs :

- trois chiffres
- un espace
- trois chiffres
- un espace
- trois chiffres

## <a name="checksum"></a>Somme de contrôle

Oui

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction Func_Australian_Company_Number recherche le contenu qui correspond au modèle.
- Un mot clé de Keyword_Australian_Company_Number est trouvé.

Une stratégie DLP a une confiance faible ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- La fonction Func_Australian_Company_Number recherche le contenu qui correspond au modèle.

```xml
      <!-- Australia Company Number -->
      <Entity id="b1fba4f7-7b3e-4bb9-8f9a-9366df604dbb" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_Australian_Company_Number" />
          <Match idRef="Keyword_Australian_Company_Number" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Func_Australian_Company_Number" />
        </Pattern>
      </Entity>
```
## <a name="keywords"></a>Mots-clés

### <a name="keyword_australia_company_number"></a>Keyword_australia_company_number

- Anc
- australia company no
- australia company no #
- numéro d’entreprise australie
- australian company no
- australian company no #
- numéro d’entreprise australien
