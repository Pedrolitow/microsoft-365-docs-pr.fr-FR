---
title: Définition de l’entité informations d’identification de connexion utilisateur
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
description: Définition d’entité de type d’informations sensibles des informations d’identification de connexion utilisateur.
ms.openlocfilehash: 379675f09fdc44a6e9298e778247242db79f03bc
ms.sourcegitcommit: 50da6f1f6ef2274c17ed9729e7ad84395b0a9be2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/08/2022
ms.locfileid: "68503817"
---
# <a name="user-login-credentials"></a>Informations d’identification de connexion utilisateur

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

Ce SIT est également inclus dans le sit [groupé Toutes les informations d’identification](sit-defn-all-creds.md) .

 ## <a name="format"></a>Format

Nom d’utilisateur et mot de passe associés utilisés dans le processus d’authentification générale.

ou

Nom d’utilisateur et mot de passe associés utilisés dans le gestionnaire de connexions PuTTY.

ou

Mot de passe en texte brut utilisé dans les extraits de code.

or

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

or

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

## <a name="credential-example"></a>Exemple d’informations d’identification 

`{ "user": "user_name", "password": "ZYXWVU_2" }`

## <a name="checksum"></a>Somme de contrôle

Non

Les SIT qui ont des sommes de contrôle utilisent un calcul unique pour vérifier si les informations sont valides. Cela signifie que lorsque la valeur **de somme de contrôle** est **Oui**, le service peut effectuer une détection positive basée sur les données sensibles uniquement. Lorsque la valeur de somme de **contrôle** est Aucun élément (secondaire) supplémentaire **ne** doit également être détecté pour que le service effectue une détection positive.

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
- Db_

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
