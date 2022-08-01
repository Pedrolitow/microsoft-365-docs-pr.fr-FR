---
title: Définition d’entité de jeton d’accès personnel Azure Databricks (préversion)
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
description: Définition d’entité de type d’entité du jeton d’accès personnel Azure Databricks.
ms.openlocfilehash: 9dfe6cb2616cc389cd122b4430c717bd099900f0
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2022
ms.locfileid: "66996019"
---
# <a name="azure-databricks-personal-access-token-preview"></a>Jeton d’accès personnel Azure Databricks (préversion) 

## <a name="format"></a>Format

Combinaison de 32 caractères composés de lettres et de chiffres.

## <a name="pattern"></a>Modèle

Combinaison de 32 caractères composée des éléments suivants :
 
- a-f ou A-F (respect de la casse)
- ou 0-9

par exemple :

`abcdef0123456789abcdef0123456789`

## <a name="checksum"></a>Somme de contrôle

Non

## <a name="definition"></a>Définition

Ce SIT est conçu pour correspondre aux informations de sécurité utilisées pour s’authentifier auprès de [l’API REST Azure Databricks](/azure/databricks/administration-guide/access-control/tokens). 

Il utilise plusieurs ressources principales :

- Modèles de clé symétrique hexadécimée de 128 bits.
- Modèles de CredentialName, CredentialFeatures, AccountIdentityName, AccountIdentityValue, ResourceType, ResourceName.
- Modèles de valeurs de maquette, de réactions et d’espaces réservés.
- Dictionnaire de vocabulaire.

Les modèles sont conçus pour correspondre aux informations d’identification réelles avec une confiance raisonnable. Les modèles ne correspondent pas aux informations d’identification mises en forme en tant qu’exemples. Les valeurs de maquette, les valeurs expurgées et les espaces réservés, tels que le type d’informations d’identification ou les descriptions d’utilisation, dans la position où une valeur secrète réelle doit être présente ne seront pas mises en correspondance.


## <a name="keywords"></a>Mots-clés

### <a name="keyword_symmetrickey128hex"></a>Keyword_SymmetricKey128Hex :

dapi key secret token password pw
