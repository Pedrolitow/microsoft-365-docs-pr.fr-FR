---
title: Définition d’entité secrète de l’application Azure Bot Service (préversion)
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
description: Définition d’entité de type d’entité de type secret d’application Azure Bot Service.
ms.openlocfilehash: 67afea4534b81abc6dd58e459e014035a40d8d03
ms.sourcegitcommit: fa570d90b00ed1bb40e1ca27b11c66a84c4204e9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/05/2022
ms.locfileid: "68476108"
---
# <a name="azure-bot-service-app-secret-preview"></a>Secret d’application Azure Bot Service (préversion)

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="format"></a>Format

Combinaison d’un maximum de 40 caractères composés de lettres, de chiffres et de caractères spéciaux.

## <a name="pattern"></a>Modèle

Combinaison d’un maximum de 40 caractères comprenant :

- a-z (non sensible à la casse)
- 0-9
- tirets (-)
- soulignements (_)
- points (.) 
- ou des accents tilde (~)

par exemple :

`abc7Q~defghijklmnopqrs0t123456789-_.~`

## <a name="checksum"></a>Somme de contrôle

Oui

## <a name="definition"></a>Définition

Ce SIT est conçu pour correspondre aux informations de sécurité utilisées pour établir une communication sécurisée entre un [bot Azure, des canaux WebChat et des applications clientes](/azure/bot-service/bot-builder-concept-authentication-types?view=azure-bot-service-4.0).  

Il utilise plusieurs ressources principales :

- Modèles de clé secrète client avec un format spécifique.
- Modèles de CredentialName, CredentialFeatures, AccountIdentityName, AccountIdentityValue, ResourceType, ResourceName.
- Modèles de valeurs de maquette, de réactions et d’espaces réservés.
- Dictionnaire de vocabulaire.

Les modèles sont conçus pour correspondre aux informations d’identification réelles avec une confiance raisonnable. Les modèles ne correspondent pas aux informations d’identification mises en forme en tant qu’exemples. Les valeurs de maquette, les valeurs redépliquées et les espaces réservés, tels que le type d’informations d’identification ou les descriptions d’utilisation, dans la position où une valeur secrète réelle doit être présente ne seront pas mises en correspondance.


## <a name="keywords"></a>Mots-clés

### <a name="keyword_appsecret"></a>Keyword_AppSecret :

- Secret
- mot de passe
- clé
