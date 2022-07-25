---
title: Azure SQL définition d’entité de chaîne de connexion (préversion)
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
description: Azure SQL définition d’entité de type d’entité de type d’informations sensibles de chaîne de connexion.
ms.openlocfilehash: 7091c50d96f22370358f5743a3992a10025ea29f
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2022
ms.locfileid: "66996300"
---
# <a name="azure-sql-connection-string-preview"></a>chaîne de connexion Azure SQL (préversion)

## <a name="format"></a>Format

Jusqu’à 20 000 caractères combinés de lettres, de chiffres et de caractères spéciaux.

ou

Paire de nom d’utilisateur et de mot de passe utilisée dans le processus d’authentification générale.


## <a name="pattern"></a>Modèle

Toute combinaison d’un maximum de 20 000 caractères comprenant :

- a-z (non sensible à la casse)
- 0-9
- barres obliques (/)
- ou signes plus (+)
- Jusqu’à 2
- signes égaux (=)

par exemple : 

`MIIKcQIBAzCCCi0GCSqGSIb3DQEHAaCCCh4EggoaMIIKFjCCBg8GCSqGSIb3DQEHAaCCBgAEggX8MIIF+DCCBfQGCyqGSIb3DQEM`

ou

Formats de nom d’utilisateur et de mot de passe variants, par exemple :

`username=...;password=********;` <br>
`user id=...;password=********;` <br>
`uid=...;pwd=********;` <br>
`DB_USER=...;DB_PASS=********;` <br>
`Service Account=...;Password=********;` <br>


## <a name="checksum"></a>Somme de contrôle

Oui

## <a name="definition"></a>Définition

Ce SIT est conçu pour correspondre aux informations de sécurité utilisées pour se connecter à [Azure SQL bases de données](/azure/sql-database/sql-database-aad-authentication-configure).

Il utilise plusieurs ressources principales :

- Modèles du littéral de chaîne encodé en Base64.
- Modèles de nom d’utilisateur et de mot de passe en texte brut.
- Modèles de CredentialName, CredentialFeatures, AccountIdentityName, AccountIdentityValue, ResourceType, ResourceName.
- Modèles de valeurs de maquette, de réactions et d’espaces réservés.

Les modèles sont conçus pour correspondre aux informations d’identification réelles avec une confiance raisonnable. Les modèles ne correspondent pas aux informations d’identification mises en forme en tant qu’exemples. Les valeurs de maquette, les valeurs redépliquées et les espaces réservés, tels que le type d’informations d’identification ou les descriptions d’utilisation, dans la position où une valeur secrète réelle doit être présente ne seront pas mises en correspondance.

## <a name="keywords"></a>Mots-clés

### <a name="keyword_base64encodedstringliteral"></a>Keyword_Base64EncodedStringLiteral :

- MII

### <a name="keyword_logincredentials"></a>Keyword_LoginCredentials :

- mot de passe
- Pw
- DB_
