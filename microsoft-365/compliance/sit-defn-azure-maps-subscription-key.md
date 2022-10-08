---
title: Azure Maps définition d’entité de clé d’abonnement (préversion)
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
description: Azure Maps définition d’entité de type d’entité de type d’informations sensibles de clé d’abonnement.
ms.openlocfilehash: d8729175d86ecd37c9bb27f5ee8b1985eabed318
ms.sourcegitcommit: fa570d90b00ed1bb40e1ca27b11c66a84c4204e9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/05/2022
ms.locfileid: "68476834"
---
# <a name="azure-maps-subscription-key-preview"></a>Azure Maps clé d’abonnement (préversion)

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="format"></a>Format

Combinaison de 43 caractères composés de lettres, de chiffres et de caractères spéciaux.

## <a name="pattern"></a>Modèle

Toute combinaison de 43 caractères comprenant :
 
- a-z (non sensible à la casse)
- 0-9
- tirets (-)
- ou soulignements (_)

par exemple :

`abcdefghijklmnopqrstuvwxyz0123456789-_ABCDE`

## <a name="checksum"></a>Somme de contrôle

Non

## <a name="definition"></a>Définition

Ce SIT est conçu pour correspondre aux informations de sécurité utilisées pour accéder aux ressources dans [Azure Maps comptes](/azure/azure-maps/how-to-manage-authentication). 

Il utilise plusieurs ressources principales :

- Modèles de clé symétrique codée en 256 bits de l’URL Base64.
- Modèles de CredentialName, CredentialFeatures, AccountIdentityName, AccountIdentityValue, ResourceType, ResourceName.
- Modèles de valeurs de maquette, de réactions et d’espaces réservés.
- Dictionnaire de vocabulaire.

Les modèles sont conçus pour correspondre aux informations d’identification réelles avec une confiance raisonnable. Les modèles ne correspondent pas aux informations d’identification mises en forme en tant qu’exemples. Les valeurs de maquette, les valeurs redépliquées et les espaces réservés, tels que le type d’informations d’identification ou les descriptions d’utilisation, dans la position où une valeur secrète réelle doit être présente ne seront pas mises en correspondance.

## <a name="keywords"></a>Mots-clés

### <a name="keyword_symmetrickey256url"></a>Keyword_SymmetricKey256Url :

- clé
- microsoft.maps
