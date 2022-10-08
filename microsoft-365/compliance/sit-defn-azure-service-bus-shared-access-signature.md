---
title: Définition d’entité de signature d’accès partagé Azure Service Bus (préversion)
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
description: Définition d’entité de type d’entité de type d’informations sensibles de signature d’accès partagé Azure Service Bus.
ms.openlocfilehash: e477900557087f5ed4383af8b7cc8d2c26d7bf2d
ms.sourcegitcommit: fa570d90b00ed1bb40e1ca27b11c66a84c4204e9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/05/2022
ms.locfileid: "68476646"
---
# <a name="azure-service-bus-shared-access-signature-preview"></a>Signature d’accès partagé Azure Service Bus (préversion)

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="format"></a>Format

Combinaison de 44 caractères composée de lettres, de chiffres et de caractères spéciaux se terminant par un signe égal (=) qui ne fait pas partie du modèle.

ou

Combinaison d’un maximum de 76 caractères composée de lettres, de chiffres et de caractères spéciaux se terminant par un signe égal (=) qui ne fait pas partie du modèle.

## <a name="pattern"></a>Modèle

Toute combinaison de 43 caractères comprenant :
 
- a-z (non sensible à la casse)
- 0-9
- barres obliques (/)
- ou signes plus (+)
- se termine par un signe égal (=) qui ne fait pas partie du modèle

par exemple :

`abcdefghijklmnopqrstuvwxyz0123456789/+ABCDE=`

or

Toute combinaison de 43 à 73 caractères composée de :

- a-z (non sensible à la casse)
- 0-9
- ou signes de pourcentage (%)
- se termine par un suffixe « %3d » (non sensible à la casse)

par exemple : 

`abcdefghijklmnopqrstuvwxyz0123456789%2F%2BABCDE%3D`

## <a name="checksum"></a>Somme de contrôle

Non

## <a name="definition"></a>Définition

Ce SIT est conçu pour correspondre aux informations de sécurité utilisées pour accorder à un utilisateur l’accès à [Azure Service Bus ressources](/azure/service-bus-messaging/service-bus-authentication-and-authorization) avec des droits spécifiques.

Il utilise plusieurs ressources principales :

- Modèles de clé symétrique 256 bits encodée en Base64.
- Modèles de clé symétrique 256 bits encodée par URL.
- Modèles de CredentialName, CredentialFeatures, AccountIdentityName, AccountIdentityValue, ResourceType, ResourceName, ID.
- Modèles de valeurs de maquette, de réactions et d’espaces réservés.
- Dictionnaire de vocabulaire.

Les modèles sont conçus pour correspondre aux informations d’identification réelles avec une confiance raisonnable. Les modèles ne correspondent pas aux informations d’identification mises en forme en tant qu’exemples. Les valeurs de maquette, les valeurs redépliquées et les espaces réservés, tels que le type d’informations d’identification ou les descriptions d’utilisation, dans la position où une valeur secrète réelle doit être présente ne seront pas mises en correspondance.

## <a name="keywords"></a>Mots-clés

### <a name="keyword_symmetrickey256"></a>Keyword_SymmetricKey256 :

- SharedAccessKey
- AccountKey

### <a name="keyword_symmetrickey256urlencoded"></a>Keyword_SymmetricKey256UrlEncoded :

- sig=
- clé
- jeton
- Secret
- mot de passe
