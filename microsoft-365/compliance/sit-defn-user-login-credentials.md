---
title: Définition d’entité des informations d’identification de connexion utilisateur (préversion)
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
description: Définition d’entité de type d’informations sensibles des informations d’identification de connexion utilisateur.
ms.openlocfilehash: d75fcb7069e8393b5b03ce08071057ff503a4bfb
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2022
ms.locfileid: "66995499"
---
# <a name="user-login-credentials-preview"></a>Informations d’identification de connexion utilisateur (préversion)

## <a name="format"></a>Format

Nom d’utilisateur et mot de passe associés utilisés dans le processus d’authentification générale.

ou

Nom d’utilisateur et mot de passe associés utilisés dans le gestionnaire de connexions PuTTY.

ou

Mot de passe en texte brut utilisé dans les extraits de code.

ou

Combinaison de 88 caractères composés de lettres, de chiffres et de caractères spéciaux.

## <a name="pattern"></a>Modèle

Différents formats de nom d’utilisateur et de mot de passe, par exemple :
 
`username=...;password=********;` <br>
`user id=...;password=********;` <br>
`uid=...;pwd=********;` <br>
`DB_USER=...;DB_PASS=********;` <br>
`Service Account=...;Password=********;` <br>

ou

```xml
An XML element <login>
An embeded XML element <login>
Inner XML content
An embeded XML element </login>
An embeded XML element <password>
Inner XML content
An embeded XML element </password>
An XML element </login>
```

par exemple

`<login> <login>ZYXWVU_1</login> <password>ZY…`

ou

Différents formats de mot de passe dans des extraits de code, par exemple :

`new X509Certificates2(` <br>
`ConvertTo-SecureString -String ********` <br>
`password = "********"` <br>
`"password" : "********"`<br>
`UserPasswordCredential(` <br>

ou

Combinaison de 86 caractères :

- a-z (non sensible à la casse)
- 0-9
- barres obliques (/)
- ou signes plus (+)
- se termine par deux signes égaux (=)

par exemple :

`abcdefghijklmnopqrstuvwxyz0123456789/+ABCDEabcdefghijklmnopqrstuvwxyz0123456789/+ABCDE==`

## <a name="checksum"></a>Somme de contrôle

Non

## <a name="definition"></a>Définition

Ce SIT est conçu pour correspondre aux informations de sécurité utilisées dans le [processus de connexion](/azure/key-vault/quick-create-portal) utilisateur général. 

Il utilise plusieurs ressources principales :

- Modèles de nom d’utilisateur et de mot de passe en texte brut.
- Modèles de nom d’utilisateur et de mot de passe en texte brut dans le fichier de base de données PuTTYcm.
- Modèles de contexte de mot de passe dans le code.
- Modèles de clé symétrique codée en Base64 de 512 bits.
- Modèles d’CredentialName, CredentialFeatures, AccountIdentityName, AccountIdentityValue, ResourceType, ResourceName, Id, AccountName.
- Modèles de valeurs de maquette, de réactions et d’espaces réservés.
- Dictionnaire de vocabulaire.

Les modèles sont conçus pour correspondre aux informations d’identification réelles avec une confiance raisonnable. Les modèles ne correspondent pas aux informations d’identification mises en forme en tant qu’exemples. Les valeurs de maquette, les valeurs redépliquées et les espaces réservés, tels que le type d’informations d’identification ou les descriptions d’utilisation, dans la position où une valeur secrète réelle doit être présente ne seront pas mises en correspondance.

## <a name="keywords"></a>Mots-clés

### <a name="keyword_logincredentials"></a>Keyword_LoginCredentials :

- mot de passe
- Pw
- DB_

### <a name="keyword_logincredentialsputty"></a>Keyword_LoginCredentialsPutty :

- connectez-vous

### <a name="keyword_passwordcontextincode"></a>Keyword_PasswordContextInCode :

- clé
- x509c
- Credential
- mot de passe
- Pw
- Securestring

### <a name="keyword_symmetrickey512"></a>Keyword_SymmetricKey512 :

- SharedAccessKey
- AccountKey
