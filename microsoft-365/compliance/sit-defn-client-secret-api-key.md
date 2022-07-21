---
title: Clé secrète client / définition d’entité de clé API (préversion)
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
description: Définition d’entité du type d’entité clé secrète client/clé API.
ms.openlocfilehash: 25bd50de2193abaa926d09475cc9ff537432fc62
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2022
ms.locfileid: "66950614"
---
# <a name="client-secret--api-key-preview"></a>Clé secrète client/API (préversion)

## <a name="format"></a>Format

Clé secrète client ou jeton d’actualisation utilisé dans le protocole OAuth 2.0.

ou

Combinaison de 24 caractères composés de lettres, de chiffres et de caractères spéciaux.

ou

Combinaison de 32 caractères composés de lettres et de chiffres.

ou

Combinaison de 40 caractères composés de lettres et de chiffres.

ou

Combinaison de 44 caractères composés de lettres, de chiffres et de caractères spéciaux.

ou

Combinaison de 56 caractères composés de lettres, de chiffres et de caractères spéciaux

ou

Combinaison de 88 caractères composés de lettres, de chiffres et de caractères spéciaux.


## <a name="pattern"></a>Modèle

Différents formats de clé secrète client ou de jeton d’actualisation, par exemple :
 
`ClientSecret:********` <br>
`AppSecret=********` <br>
`ConsumerKey:=********` <br>
`Refresh_Token:********` <br>

ou

Combinaison de 22 caractères :
 
- a-z (non sensible à la casse)
- chiffres, barres obliques ou signes plus
- se termine par deux signes égaux (=)

par exemple :

`abcdefgh0123456789/+AB==`

ou

Combinaison de 32 caractères :

- a-f ou A-F (respect de la casse)
- ou 0-9

par exemple :

`abcdef0123456789abcdef0123456789`

ou

Combinaison de 40 caractères :

- a-f ou A-F (respect de la casse)

ou

- 0-9

par exemple :

`abcdef0123456789abcdef0123456789abcdef01`

ou

Combinaison de 43 caractères :
 
- a-z (non sensible à la casse)
- 0-9
- barres obliques (/)
- ou signes plus (+)
- se termine par un signe égal (=)

par exemple :

`abcdefghijklmnopqrstuvwxyz0123456789/+ABCDE=`

ou

Combinaison de 54 caractères :

- a-z (non sensible à la casse)
- 0-9
- barres obliques (/) ou signes plus (+)
- se termine par deux signes égaux (==)

par exemple :

`abcdefghijklmnopqrstuvwxyz0123456789/+ABCDEFGHIJKLMNOP==`

ou

Combinaison de 86 caractères :

- a-z (non sensible à la casse)
- 0-9
- barres obliques (/) ou signes plus (+)
- se termine par deux signes égaux (=)

par exemple :

`abcdefghijklmnopqrstuvwxyz0123456789/+ABCDEabcdefghijklmnopqrstuvwxyz0123456789/+ABCDE==`


## <a name="checksum"></a>Somme de contrôle

Non

## <a name="definition"></a>Définition

Ce SIT est conçu pour correspondre aux informations de sécurité connues uniquement de [l’application OAuth et du serveur d’autorisation pour échanger](/azure/active-directory/develop/active-directory-how-applications-are-added) un jeton d’accès au moment de l’exécution. 

Il utilise plusieurs ressources principales :

- Modèles du contexte de clé secrète client.
- Modèles de clé symétrique de 128 bits encodée en Base64.
- Modèles de clé symétrique hexadécimée de 128 bits.
- Modèles de clé symétrique de 160 bits encodées hexadécimales.
- Modèles de clé symétrique de 256 bits encodée en Base64.
- Modèles de clé symétrique de 320 bits encodée en Base64.
- Modèles de clé symétrique codée en Base64 de 512 bits.
- Modèles d’CredentialName, CredentialFeatures, AccountIdentityName, AccountIdentityValue, ResourceType, ResourceName, Id, AccountName.
- Modèles de valeurs de maquette, de réactions et d’espaces réservés.
- Dictionnaire de vocabulaire.

Les modèles sont conçus pour correspondre aux informations d’identification réelles avec une confiance raisonnable. Les modèles ne correspondent pas aux informations d’identification mises en forme en tant qu’exemples. Les valeurs de maquette, les valeurs redépliquées et les espaces réservés, tels que le type d’informations d’identification ou les descriptions d’utilisation, dans la position où une valeur secrète réelle doit être présente ne seront pas mises en correspondance.

## <a name="keywords"></a>Mots-clés

### <a name="keyword_clientsecretcontext"></a>Keyword_ClientSecretContext :

- Secret
- jeton
- auth
- Securestring
- clé

### <a name="keyword_symmetrickey128"></a>Keyword_SymmetricKey128 :

- Secret
- clé
- mot de passe
- Pw

### <a name="keyword_symmetrickey128hex"></a>Keyword_SymmetricKey128Hex :

- Dapi
- clé
- Secret
- jeton
- mot de passe
- Pw

### <a name="keyword_symmetrickey160hex"></a>Keyword_SymmetricKey160Hex :

- jeton

### <a name="keyword_symmetrickey256"></a>Keyword_SymmetricKey256 :

- SharedAccessKey
- AccountKey

### <a name="keyword_symmetrickey320"></a>Keyword_SymmetricKey320 :

- code=
- clé

### <a name="keyword_symmetrickey512"></a>Keyword_SymmetricKey512 :

- SharedAccessKey
- AccountKey
