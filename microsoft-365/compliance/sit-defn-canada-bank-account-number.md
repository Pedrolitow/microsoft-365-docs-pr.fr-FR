---
title: Définition de l’entité numéro de compte bancaire du Canada
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
description: Définition d’entité de type d’entité de type d’information sensible de numéro de compte bancaire du Canada.
ms.openlocfilehash: c7008b17ff532a55dfefc079a07fc8e95f789b04
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2022
ms.locfileid: "66996670"
---
# <a name="canada-bank-account-number"></a>Numéro de compte bancaire du Canada

## <a name="format"></a>Format

7 ou 12 chiffres

## <a name="pattern"></a>Modèle

Un numéro de compte bancaire du Canada est de 7 ou 12 chiffres.

Un numéro de transit de compte bancaire du Canada est indiqué au format suivant :

- cinq chiffres
- un trait d’union
- trois chiffres OU
- un zéro « 0 »
- huit chiffres

## <a name="checksum"></a>Somme de contrôle

Non

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- L’expression régulière `Regex_canada_bank_account_number` trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keyword_canada_bank_account_number` est trouvé.
- L’expression régulière `Regex_canada_bank_account_transit_number` trouve un contenu qui correspond au modèle.

Une stratégie DLP a une confiance élevée ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- L’expression régulière `Regex_canada_bank_account_number` trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keyword_canada_bank_account_number` est trouvé.

```xml
<!-- Canada Bank Account Number -->
<Entity id="552e814c-cb50-4d94-bbaa-bb1d1ffb34de" patternsProximity="300" recommendedConfidence="75">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="Regex_canada_bank_account_number" />
        <Match idRef="Keyword_canada_bank_account_number" />
        <Match idRef="Regex_canada_bank_account_transit_number" />
   </Pattern>
   <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_canada_bank_account_number" />
        <Match idRef="Keyword_canada_bank_account_number" />
   </Pattern>
</Entity>
```

## <a name="keywords"></a>Mots-clés

### <a name="keyword_canada_bank_account_number"></a>Keyword_canada_bank_account_number

- obligations d’épargne du Canada
- agence du revenu du Canada
- institution financière du Canada
- formulaire de dépôt direct
- citoyen canadien
- représentant légal
- notaire
- commissaire à l’assermentation
- prestation pour la garde d’enfants
- prestation universelle pour la garde d’enfants
- prestation fiscale canadienne pour enfants
- prestation fiscale pour le revenu gagné
- taxe de vente harmonisée
- numéro d’assurance sociale
- remboursement d’impôt
- prestation fiscale pour enfants
- paiements aux territoires
- numéro d’institution
- demande de dépôt
- informations bancaires
- dépôt direct