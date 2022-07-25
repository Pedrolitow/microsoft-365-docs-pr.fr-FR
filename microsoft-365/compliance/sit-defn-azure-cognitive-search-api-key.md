---
title: Définition d’entité clé de l’API Recherche cognitive Azure (préversion)
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
description: Définition d’entité de type d’entité de type clé sensible de l’API Recherche cognitive Azure.
ms.openlocfilehash: 8d4b5ca6c968468c5d084e6adb44eaf921553e21
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2022
ms.locfileid: "66996059"
---
# <a name="azure-cognitive-search-api-key-preview"></a>clé API Recherche cognitive Azure (préversion) 

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

Ce SIT est conçu pour correspondre aux informations de sécurité utilisées pour authentifier les requêtes entrantes à [Recherche cognitive Azure API.](/azure/search/search-security-api-keys) 

Il utilise plusieurs ressources principales :

Modèles de clé symétrique hexadécimée de 128 bits.
Modèles de CredentialName, CredentialFeatures, AccountIdentityName, AccountIdentityValue, ResourceType, ResourceName.
Modèles de valeurs de maquette, de réactions et d’espaces réservés.
Dictionnaire de vocabulaire.

Les modèles sont conçus pour correspondre aux informations d’identification réelles avec une confiance raisonnable. Les modèles ne correspondent pas aux informations d’identification mises en forme en tant qu’exemples. Les valeurs de maquette, les valeurs expurgées et les espaces réservés, tels que le type d’informations d’identification ou les descriptions d’utilisation, dans la position où une valeur secrète réelle doit être présente ne seront pas mises en correspondance.

## <a name="keywords"></a>Mots-clés

### <a name="keyword_symmetrickey128hex"></a>Keyword_SymmetricKey128Hex :

- Dapi
- clé
- Secret
- jeton
- mot de passe
- Pw
