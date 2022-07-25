---
title: Définition d’entité de clé secrète Azure Bot Framework (préversion)
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
description: Définition d’entité de type d’entité de type clé secrète Azure Bot Framework.
ms.openlocfilehash: c436436b00dda8a5273939665920ef709ff164c5
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2022
ms.locfileid: "66996070"
---
# <a name="azure-bot-framework-secret-key-preview"></a>Clé secrète Azure Bot Framework (préversion)

## <a name="format"></a>Format

Combinaison de 55 caractères composés de lettres, de chiffres et de caractères spéciaux.

ou

Combinaison de 63 caractères composés de lettres, de chiffres et de caractères spéciaux.

## <a name="pattern"></a>Modèle

Combinaison de 55 caractères :

- a-z (non sensible à la casse)
- 0-9
- soulignements (_)
- ou points (.)


`abcdefghijklmnopqrstuvwxyz.0123456789_ABCDEabcdefghijkl`

ou pour les 63 caractères

Combinaison de 11 caractères :

- a-z (non sensible à la casse)
- 0-9
- tirets (-)
- ou soulignements (_)
- un point

Combinaison de 3 caractères :

- a-z (non sensible à la casse)
- 0-9
- tirets (-)
- ou soulignements (_)
- un point

Combinaison de 3 caractères :

- a-z (non sensible à la casse)
- 0-9
- tirets (-)
- ou soulignements (_)
- un point

Combinaison de 43 caractères

- a-z (non sensible à la casse)
- 0-9
- tirets (-)
- ou soulignements (_)

par exemple :

`abcdefghijk.lmn.opq.rstuvwxyz0123456789-_ABCDEFGHIJKLMNOPQRSTUV`


## <a name="checksum"></a>Somme de contrôle

Non

## <a name="definition"></a>Définition

Ce SIT est conçu pour correspondre aux informations de sécurité utilisées pour se connecter aux [canaux WebChat à partir des services Azure Bot.](/azure/bot-service/bot-service-channel-connect-webchat?view=azure-bot-service-4.0) 

Il utilise plusieurs ressources principales :

- Modèles de clé symétrique codée en 328 bits de l’URL Base64.
- Modèles de clé symétrique codée en 360 bits d’URL base64.
- Modèles de CredentialName, CredentialFeatures, AccountIdentityName, AccountIdentityValue, ResourceType, ResourceName.
- Modèles de valeurs de maquette, de réactions et d’espaces réservés.
- Dictionnaire de vocabulaire.

Les modèles sont conçus pour correspondre aux informations d’identification réelles avec une confiance raisonnable. Les modèles ne correspondent pas aux informations d’identification mises en forme en tant qu’exemples. Les valeurs de maquette, les valeurs expurgées et les espaces réservés, tels que le type d’informations d’identification ou les descriptions d’utilisation, dans la position où une valeur secrète réelle doit être présente ne seront pas mises en correspondance.

## <a name="keywords"></a>Mots-clés

### <a name="keyword_symmetrickey328url"></a>Keyword_SymmetricKey328Url :

- botframework
- clé

### <a name="keyword_symmetrickey360url"></a>Keyword_SymmetricKey360Url :

- botframework
- clé
