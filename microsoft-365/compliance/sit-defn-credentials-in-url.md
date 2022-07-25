---
title: Crednetial dans l’URL
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
description: Informations d’identification dans la définition d’entité de type d’informations sensibles d’URL.
ms.openlocfilehash: f7a363539ec9bdd7fa0ddaab30ac7e2d20afb69b
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2022
ms.locfileid: "66996499"
---
# <a name="credentials-in-url"></a>Informations d’identification dans l’URL

## <a name="format"></a>Format

Nom d’utilisateur et mot de passe associés utilisés dans l’URL

ou

Mot de passe en texte brut utilisé dans le script

## <a name="pattern"></a>Modèle

Différents formats de nom d’utilisateur et de mot de passe d’URL, par exemple : 

`https://username:********@contoso.com/...`
`ftp://username:********@contoso.com:20/...`

par exemple : `https://myuser:mypassword@localhost`

ou

Différents formats de mot de passe dans le script, par exemple : 

`password = ********...`

par exemple :

`password=ZYXWVU_1`

## <a name="checksum"></a>Somme de contrôle

Non

## <a name="description"></a>Description

Ce SIT est conçu pour correspondre aux informations de sécurité utilisées comme jeton dans l’URL pour effectuer le processus de validation ou d’identification des [utilisateurs](/azure/key-vault/quick-create-portal) du client. Il utilise plusieurs ressources principales :

- Modèles d’informations d’identification de connexion utilisateur dans l’URL.
- Modèles de contexte de mot de passe dans le script.
- Modèles de CredentialName, CredentialFeatures, AccountIdentityName, AccountIdentityValue, ResourceType, ResourceName.
- Modèles de valeurs de maquette, de réactions et d’espaces réservés.

Les modèles sont conçus pour correspondre aux informations d’identification réelles avec une confiance raisonnable. Les modèles ne correspondent pas aux informations d’identification mises en forme en tant qu’exemples. Les valeurs de maquette, les valeurs redépliquées et les espaces réservés, tels que le type d’informations d’identification ou les descriptions d’utilisation, dans la position où une valeur secrète réelle doit être présente ne seront pas mises en correspondance.

## <a name="keywords"></a>Mots-clés

### <a name="keyword_logincredentialsinurl"></a>Keyword_LoginCredentialsInUrl

- ://

### <a name="keyword_passwordcontextinscript"></a>Keyword_PasswordContextInScript

- Secret
- mot de passe
- Pw
