---
title: Définition d’entité de secret client Azure AD (préversion)
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
description: Définition d’entité de type d’entité de type secret client Azure AD.
ms.openlocfilehash: ea597fc5493db6b6f919d907dcb61af115299ea1
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2022
ms.locfileid: "66996130"
---
# <a name="azure-ad-client-secret-preview"></a>Clé secrète client Azure AD (préversion)

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

Ce SIT est conçu pour correspondre aux informations de sécurité [utilisées pour sécuriser les principaux de service Azure Active Directory](/azure/active-directory/fundamentals/service-accounts-principal). 

Il utilise plusieurs ressources principales :

- Modèles de clé secrète client avec un format spécifique.
- Modèles de CredentialName, CredentialFeatures, AccountIdentityName, AccountIdentityValue, ResourceType, ResourceName.
- Modèles de valeurs de maquette, de réactions et d’espaces réservés.
- Dictionnaire de vocabulaire.

Les modèles sont conçus pour correspondre aux informations d’identification réelles avec une confiance raisonnable. Les modèles ne correspondent pas aux informations d’identification mises en forme en tant qu’exemples. Les valeurs de maquette, les valeurs redépliquées et les espaces réservés, tels que le type d’informations d’identification ou les descriptions d’utilisation, dans la position où une valeur secrète réelle doit être présente ne seront pas mises en correspondance.

## <a name="keywords"></a>Mots-clés

### <a name="keyword_appsecret"></a>Keyword_AppSecret :

- Secret
- assword
- clé

