---
title: Microsoft Bing mappe la définition d’entité clé (préversion)
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
description: Microsoft Bing mappe la définition d’entité de type d’informations sensibles clés.
ms.openlocfilehash: 6f25ec9716be33a0e2bbe404f12742dddad89250
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2022
ms.locfileid: "66950822"
---
# <a name="microsoft-bing-maps-key-preview"></a>Clé de cartes Microsoft Bing (préversion)

## <a name="format"></a>Format

Combinaison de 64 caractères composés de lettres, de chiffres et de caractères spéciaux.

## <a name="pattern"></a>Modèle

Combinaison de 64 caractères :

- a-z (non sensible à la casse)
- 0-9
- soulignements (_) ou traits d’union (-)

par exemple :

`abcdefghijklmnopqrstuvwxyz0123456789-_ABCDEabcdefghijklmnopqrstu`

## <a name="checksum"></a>Somme de contrôle

Non

## <a name="definition"></a>Définition

Ce SIT est conçu pour correspondre aux informations de sécurité utilisées pour appeler [Bing Cartes API.](/bingmaps/getting-started/bing-maps-dev-center-help/getting-a-bing-maps-key) 

Il utilise plusieurs ressources principales :

- Modèles de clé symétrique codée en 384 bits de l’URL Base64.
- Modèles de CredentialName, CredentialFeatures, AccountIdentityName, AccountIdentityValue, ResourceType, ResourceName.
- Modèles de valeurs de maquette, de réactions et d’espaces réservés.
- Dictionnaire de vocabulaire.

Les modèles sont conçus pour correspondre aux informations d’identification réelles avec une confiance raisonnable. Les modèles ne correspondent pas aux informations d’identification mises en forme en tant qu’exemples. Les valeurs de maquette, les valeurs redépliquées et les espaces réservés, tels que le type d’informations d’identification ou les descriptions d’utilisation, dans la position où une valeur secrète réelle doit être présente ne seront pas mises en correspondance.

## <a name="keywords"></a>Mots-clés

### <a name="keyword_symmetrickey384url"></a>Keyword_SymmetricKey384Url :

- virtualearth
- api/maps
- clé
