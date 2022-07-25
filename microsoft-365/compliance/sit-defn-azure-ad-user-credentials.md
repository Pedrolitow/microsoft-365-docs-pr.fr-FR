---
title: Définition d’entité des informations d’identification de l’utilisateur Azure AD (préversion)
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
description: Définition d’entité de type d’informations sensibles des informations d’identification de l’utilisateur Azure AD.
ms.openlocfilehash: 5b27f2a5c700770df65be74f0cebb23351de77bc
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2022
ms.locfileid: "66996120"
---
# <a name="azure-ad-user-credentials-preview"></a>Informations d’identification de l’utilisateur Azure AD (préversion)

## <a name="format"></a>Format

Nom d’utilisateur et mot de passe associés au domaine *.onmicrosoft.com.

ou

Mot de passe en texte brut utilisé dans les extraits de code.

ou

Mot de passe en texte brut utilisé dans la configuration XML.

## <a name="pattern"></a>Modèle

Différents formats de nom d’utilisateur et de mot de passe, par exemple :

`username=...password=********` <br>
`/user:.../pass:********` <br>
`SharePointOnlineAuthenticatedContext` <br>
`sign_in`<br>


ou

Différents formats de mot de passe dans des extraits de code, par exemple :

`new X509Certificates2( ...` <br>
`ConvertTo-SecureString -String ********...`<br>
`password = "********"...` <br>
`"password" : "********"...` <br>
`UserPasswordCredential( ...` <br>

ou

Différents formats de mot de passe en XML, par exemple :


```xml
... <secret>********</secret> ...
... <password>********</password> ...
... <setting name="password" value="********" > ... 
... <setting name="password">********</setting> ... 
... <setting name="password"><value>********</value></setting> ... 
```


## <a name="checksum"></a>Somme de contrôle

Non

## <a name="definition"></a>Définition

Ce SIT est conçu pour correspondre aux informations de sécurité utilisées en tant que mots de passe d’utilisateur individuels pour s’authentifier auprès [d’Azure Active Directory](/azure/active-directory/fundamentals/active-directory-users-reset-password-azure-portal). 

Il utilise plusieurs ressources principales :

- Modèles de nom d’utilisateur et de mot de passe en texte brut pour le locataire Azure AD.
- Modèles de contexte de mot de passe dans le code.
- Modèles de contexte de mot de passe en XML.
- Modèles de CredentialName, CredentialFeatures, AccountIdentityName, AccountIdentityValue, ResourceType, ResourceName.
- Modèles de valeurs de maquette, de réactions et d’espaces réservés.
- Dictionnaire de vocabulaire.

Les modèles sont conçus pour correspondre aux informations d’identification réelles avec une confiance raisonnable. Les modèles ne correspondent pas aux informations d’identification mises en forme en tant qu’exemples. Les valeurs de maquette, les valeurs expurgées et les espaces réservés, tels que le type d’informations d’identification ou les descriptions d’utilisation, dans la position où une valeur secrète réelle doit être présente ne seront pas mises en correspondance.


## <a name="keywords"></a>Mots-clés

### <a name="keyword_azureactivedirectorylogincredentials"></a>Keyword_AzureActiveDirectoryLoginCredentials :

- mot de passe
- Pw
- userpass
- Pouvoirs
- cmdkey
- Authenti
- sign_in

### <a name="keyword_passwordcontextincode"></a>Keyword_PasswordContextInCode :

- clé
- x509c
- Credential
- mot de passe
- Pw
- Securestring

### <a name="keyword_passwordcontextinxml"></a>Keyword_PasswordContextInXml :

- userpass
- mot de passe
- Pw
- Connectionstring
- clé
- Credential
- jeton
- Sas
- Secret

