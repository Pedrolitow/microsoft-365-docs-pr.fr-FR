---
title: Définition d’entité de clé d’authentification Azure DocumentDB
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
description: Définition d’entité de type d’entité de type d’informations sensibles de clé d’authentification Azure DocumentDB.
ms.openlocfilehash: e499d185b0a1752960f71f659a212aa0422154f4
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2022
ms.locfileid: "66995989"
---
# <a name="azure-documentdb-auth-key"></a>Clé d’authentification Azure DocumentDB

## <a name="format"></a>Format

`DocumentDb` Chaîne suivie des caractères et des chaînes décrits dans le modèle ci-dessous.

## <a name="pattern"></a>Modèle

- Chaîne `DocumentDb`
- Toute combinaison comprise entre 3 et 200 lettres minuscules ou majuscules, chiffres, symboles, caractères spéciaux ou espaces
- Symbole supérieur (>), signe égal (=), guillemet (« ) ou apostrophe (')
- Toute combinaison de 86 lettres minuscules ou majuscules, chiffres, barre oblique (/) ou signe plus (+)
- Deux signes égaux (=)

## <a name="checksum"></a>Somme de contrôle

Non

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- L’expression régulière `CEP_Regex_AzureDocumentDBAuthKey` trouve un contenu qui correspond au modèle.
- L’expression `CEP_CommonExampleKeywords` régulière ne trouve pas de contenu qui correspond au modèle.

```xml
<!-- Azure Document DB Auth Key -->
<Entity id="0f587d92-eb28-44a9-bd1c-90f2892b47aa" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="CEP_Regex_AzureDocumentDBAuthKey" />
        <Any minMatches="0" maxMatches="0">
            <Match idRef="CEP_CommonExampleKeywords" />
          </Any>
  </Pattern>
</Entity>
```

## <a name="keywords"></a>Mots-clés

### <a name="cep_commonexamplekeywords"></a>CEP_CommonExampleKeywords

Ce type d’informations sensibles identifie ces mots clés à l’aide d’une expression régulière, et non d’une liste de mots clés.

- Contoso
- Fabrikam
- Northwind
- Sandbox
- Onebox
- Localhost
- 127.0.0.1
- testacs.<!--no-hyperlink-->Com
- s-int.<!--no-hyperlink-->Net
