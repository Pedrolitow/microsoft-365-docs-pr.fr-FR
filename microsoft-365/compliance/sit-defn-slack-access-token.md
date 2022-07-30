---
title: Définition d’entité du jeton d’accès Slack (préversion)
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
description: Définition d’entité de type d’entité de type d’informations sensibles du jeton d’accès Slack.
ms.openlocfilehash: 18e6654abe83bcbde40a832a74ec451c24f744b0
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2022
ms.locfileid: "66996819"
---
# <a name="slack-access-token-preview"></a>Jeton d’accès Slack (préversion)

## <a name="format"></a>Format

Combinaison d’un maximum de 34 caractères composés de lettres, de chiffres et de caractères spéciaux.

## <a name="pattern"></a>Modèle

Un préfixe de jeton (respectant la casse) 'xoxp-', 'xoxb-', 'xoxa-', 'xoxr-', 'xoxo-', 'xoxs-' ou 'xoxe-'

Combinaison de 29 caractères maximum :

- 29 a-z (non sensible à la casse)
- 0-9 ou traits d’union (-)

par exemple :

`xoxp-abcdef-abcdef-abcdef-abcdef` 

## <a name="checksum"></a>Somme de contrôle

Non

## <a name="definition"></a>Définition

Ce SIT est conçu pour correspondre aux informations de sécurité utilisées pour accéder aux [fonctionnalités de la plateforme Slack](https://api.slack.com/docs/token-type) (par exemple, les jetons de bot, les jetons utilisateur et les jetons au niveau de l’application). 

Il utilise plusieurs ressources principales :

- Modèles de jeton d’utilisateur/bot/d’espace de travail Slack.
- Modèles de CredentialName, CredentialFeatures, AccountIdentityName, AccountIdentityValue, ResourceType, ResourceName.
- Modèles de valeurs de maquette, de réactions et d’espaces réservés.

Les modèles sont conçus pour correspondre aux informations d’identification réelles avec une confiance raisonnable. Les modèles ne correspondent pas aux informations d’identification mises en forme en tant qu’exemples. Les valeurs de maquette, les valeurs redépliquées et les espaces réservés, tels que le type d’informations d’identification ou les descriptions d’utilisation, dans la position où une valeur secrète réelle doit être présente ne seront pas mises en correspondance.

## <a name="keywords"></a>Mots-clés

### <a name="keyword_slacktokens"></a>Keyword_SlackTokens :

- Xox