---
title: Définition générale de l’entité de mot de passe (préversion)
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
description: Définition générale d’entité de type d’informations sensibles de mot de passe.
ms.openlocfilehash: 39a789fed5d0cf1467da4be0e05324dea3d5a12d
ms.sourcegitcommit: fa570d90b00ed1bb40e1ca27b11c66a84c4204e9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/05/2022
ms.locfileid: "68476686"
---
# <a name="general-password-preview"></a>Mot de passe général (préversion)

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="format"></a>Format

Jusqu’à 20 000 caractères combinés de lettres, de chiffres et de caractères spéciaux.

ou

Informations d’identification de connexion utilisées dans les lignes de commande

ou

Mot de passe en texte brut utilisé dans les extraits de code

or

Mot de passe en texte brut utilisé dans le script

ou

Mot de passe en texte brut utilisé dans la configuration XML

or

Combinaison de 24 caractères composés de lettres, de chiffres et de caractères spéciaux.

or

Combinaison de 32 caractères composés de lettres et de chiffres.

or

Combinaison de 32 caractères composés de lettres, de chiffres et de caractères spéciaux.

ou

Combinaison de 44 caractères composés de lettres, de chiffres et de caractères spéciaux.

or

Combinaison de 88 caractères de lettres, de chiffres et de caractères spéciaux.

## <a name="pattern"></a>Modèle

Toute combinaison d’un maximum de 20 000 caractères comprenant :

- a-z (non sensible à la casse)
- 0-9
- barres obliques (/) ou signes plus (+)
- Jusqu’à deux signes égaux (=)

par exemple :

`MIIKcQIBAzCCCi0GCSqGSIb3DQEHAaCCCh4EggoaMIIKFjCCBg8GCSqGSIb3DQEHAaCCBgAEggX8MIIF+DCCBfQGCyqGSIb3DQEM`

or

Différents formats d’informations d’identification de connexion en ligne de commande, par exemple : 

`-u username:********`

ou

`-u username -p ********`

ou

`/f ... /p ********`

ou

`-Password ********`

ou

`-U username%********`

ou

`-secrets:********`

par exemple :

`zDbg.DataPuller.exe -secrets:eyJ`

or

Différents formats de mot de passe dans des extraits de code, par exemple :

`new X509Certificates2(`

ou

`ConvertTo-SecureString -String ********`

ou

`password = "********"`

ou

`"password" : "********"`

ou

`UserPasswordCredential(`

par exemple :

`password = "ZYXWVU_1";`

or

Différents formats de mot de passe dans le script, par exemple :

`password = ********`

par exemple :

`password=ZYXWVU_1`

or

Différents formats de mot de passe en XML, par exemple :

```xml
<secret>********</secret>
<password>********</password>
<setting name="password" value="********" >
<setting name="password">********</setting>
<setting name="password"><value>********</value></setting>
```

par exemple :

`<secret>ZYXWVU_1</secret>`

ou

Toute combinaison de 22 caractères composée de :

- a-z (non sensible à la casse)
- chiffres, barres obliques ou signes plus
- se termine par deux signes égaux (=)

par exemple :

`abcdefgh0123456789/+AB==`

ou

Toute combinaison de 32 caractères comprenant :

- a-f ou A-F (respect de la casse) ou 0-9

par exemple :

`abcdef0123456789abcdef0123456789`

ou

Toute combinaison de 32 caractères comprenant :

- a-z (non sensible à la casse)
- 0-9
- barres obliques (/) ou signes plus (+)

par exemple :

`abcdefghijklmnopqr0123456789/+AB`

ou

Toute combinaison de 43 caractères comprenant :

- a-z (non sensible à la casse)
- 0-9
- barres obliques (/) ou signes plus (+)
- se termine par un signe égal (=)

par exemple :

`abcdefghijklmnopqrstuvwxyz0123456789/+ABCDE=`

ou

Toute combinaison de 86 caractères composée de :

- a-z (non sensible à la casse)
- 0-9
- barres obliques (/) ou signes plus (+)
- se termine par deux signes égaux (=)

par exemple :

`abcdefghijklmnopqrstuvwxyz0123456789/+ABCDEabcdefghijklmnopqrstuvwxyz0123456789/+ABCDE==`

## <a name="checksum"></a>Somme de contrôle

Oui

## <a name="description"></a>Description

Ce SIT est conçu pour correspondre aux informations de sécurité telles que les noms d’utilisateur et les mots de passe utilisés dans le [processus de connexion](/azure/key-vault/quick-create-portal) utilisateur de processus de connexion général. Il utilise plusieurs ressources principales :

- Modèles du littéral de chaîne encodé en Base64.
- Modèles de contexte de mot de passe dans la ligne de commande.
- Modèles de contexte de mot de passe dans le code.
- Modèles de contexte de mot de passe dans le script.
- Modèles de contexte de mot de passe en XML.
- Modèles de clé symétrique 128 bits encodée en Base64.
- Modèles de clé symétrique Hex encodée 128 bits.
- Modèles de clé symétrique 192 bits encodée en Base64.
- Modèles de clé symétrique 256 bits encodée en Base64.
- Modèles de clé symétrique 512 bits encodée en Base64.
- Modèles de CredentialName, CredentialFeatures, AccountIdentityName, AccountIdentityValue, ResourceType, ResourceName, ID, AccountName.
- Modèles de valeurs de maquette, de réactions et d’espaces réservés.
- Dictionnaire de mots de vocabulaire.


Les modèles sont conçus pour correspondre aux informations d’identification réelles avec une confiance raisonnable. Les modèles ne correspondent pas aux informations d’identification mises en forme en tant qu’exemples. Les valeurs de maquette, les valeurs redépliquées et les espaces réservés, tels que le type d’informations d’identification ou les descriptions d’utilisation, dans la position où une valeur secrète réelle doit être présente ne seront pas mises en correspondance.

## <a name="keywords"></a>Mots-clés

### <a name="keyword_base64encodedstringliteral"></a>Keyword_Base64EncodedStringLiteral

- Mii

### <a name="keyword_passwordcontextincmdline"></a>Keyword_PasswordContextInCmdLine

- certutil
- zdbg
- Secret
- VSTS_TOKEN
- Curl
- PowerShell
- ps1
- -U
- Smc
- AutoLogon
- Ldifde
- Rclone
- --Env
- SignTool
- winexe
- Net

## <a name="keyword_passwordcontextincode"></a>Keyword_PasswordContextInCode

- clé
- x509c
- Credential
- mot de passe
- Pw
- Securestring

### <a name="keyword_passwordcontextinscript"></a>Keyword_PasswordContextInScript

- Secret
- mot de passe
- Pw

### <a name="keyword_passwordcontextinxml"></a>Keyword_PasswordContextInXml

- userpass
- mot de passe
- Pw
- Connectionstring
- clé
- Credential
- jeton
- Sas
- Secret

### <a name="keyword_symmetrickey128"></a>Keyword_SymmetricKey128

- Secret
- clé
- mot de passe
- Pw

### <a name="keyword_symmetrickey128hex"></a>Keyword_SymmetricKey128Hex

- Dapi
- clé
- Secret
- jeton
- mot de passe
- Pw

### <a name="keyword_symmetrickey192"></a>Keyword_SymmetricKey192

- mot de passe
- -P
- azurecr

### <a name="keyword_symmetrickey256"></a>Keyword_SymmetricKey256

- SharedAccessKey
- AccountKey

### <a name="keyword_symmetrickey512"></a>Keyword_SymmetricKey512

- SharedAccessKey
- AccountKey
