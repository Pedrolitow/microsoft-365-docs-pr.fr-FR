---
title: Définition d’entité de clé api /Maître de fonction Azure (préversion)
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
description: Définition d’entité de type d’entité de type d’informations sensibles de clé API/maître de fonction Azure.
ms.openlocfilehash: 78a4af95c6390cc16f6a60bd3874be660e3cfa5c
ms.sourcegitcommit: fa570d90b00ed1bb40e1ca27b11c66a84c4204e9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/05/2022
ms.locfileid: "68476376"
---
# <a name="azure-function-master--api-key-preview"></a>Maître de fonction Azure / clé API (préversion)  

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="format"></a>Format

Combinaison de 56 caractères composés de lettres, de chiffres et de caractères spéciaux.

ou

Combinaison d’un maximum de 90 caractères composé de lettres, de chiffres et de caractères spéciaux.

## <a name="pattern"></a>Modèle

Toute combinaison de 54 caractères composée de :

- a-z (non sensible à la casse)
- 0-9
- barres obliques (/)
- ou signes plus (+)
- se termine par deux signes égaux (=)

par exemple :

`abcdefghijklmnopqrstuvwxyz0123456789/+ABCDEFGHIJKLMNOP==`

or

Combinaison de 54 à 84 caractères composée de :

- a-z (non sensible à la casse)
- 0-9
- ou signes de pourcentage (%)
- se termine par un suffixe « %3d%3d » (non sensible à la casse)

par exemple :

abcdefghijklmnopqrstuvwxyz0123456789%2F%2BABCDEF0123456789%3D%3D


## <a name="checksum"></a>Somme de contrôle

Non

## <a name="definition"></a>Définition

Ce SIT est conçu pour correspondre aux informations de sécurité utilisées pour demander [l’API de fonction Azure](/azure/azure-functions/functions-how-to-use-azure-function-app-settings?tabs=portal) lorsque son niveau d’autorisation est défini sur une valeur autre que anonyme. 

Il utilise plusieurs ressources principales :

- Modèles de clé symétrique 320 bits encodée en Base64.
- Modèles de clé symétrique 320 bits encodée par URL.
- Modèles de CredentialName, CredentialFeatures, AccountIdentityName, AccountIdentityValue, ResourceType, ResourceName.
- Modèles de valeurs de maquette, de réactions et d’espaces réservés.
- Dictionnaire de vocabulaire.

Les modèles sont conçus pour correspondre aux informations d’identification réelles avec une confiance raisonnable. Les modèles ne correspondent pas aux informations d’identification mises en forme en tant qu’exemples. Les valeurs de maquette, les valeurs redépliquées et les espaces réservés, tels que le type d’informations d’identification ou les descriptions d’utilisation, dans la position où une valeur secrète réelle doit être présente ne seront pas mises en correspondance.


## <a name="keywords"></a>Mots-clés

### <a name="keyword_symmetrickey320"></a>Keyword_SymmetricKey320 :

- code=
- clé

### <a name="keyword_symmetrickey320urlencoded"></a>Keyword_SymmetricKey320UrlEncoded :

- code=
- clé
