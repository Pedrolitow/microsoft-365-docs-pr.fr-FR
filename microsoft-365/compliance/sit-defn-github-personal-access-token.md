---
title: Définition d’entité de jeton d’accès personnel GitHub
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
description: Définition d’entité de type d’entité de type jeton d’accès personnel GitHub.
ms.openlocfilehash: 9a887ec28d5e90ffc61a16a2a1975aa2d6f8e366
ms.sourcegitcommit: 50da6f1f6ef2274c17ed9729e7ad84395b0a9be2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/08/2022
ms.locfileid: "68504037"
---
# <a name="github-personal-access-token"></a>Jeton d’accès personnel GitHub

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

Ce SIT est également inclus dans le sit [groupé Toutes les informations d’identification](sit-defn-all-creds.md) .

 ## <a name="format"></a>Format

Combinaison de 40 caractères composés de lettres, de chiffres et de caractères spéciaux.

ou

Nom d’utilisateur et mot de passe associés utilisés dans l’URL.

ou

Combinaison de 40 caractères composés de lettres et de chiffres.

## <a name="pattern"></a>Modèle

- Un préfixe de jeton (respectant la casse) « ghp_ », « gho_ », « ghu_ », « ghs_ » ou « ghr_ »
- Toute combinaison de 36 
- a-z (non sensible à la casse) ou 0-9

par exemple :

`ghp_abcdefghijklmnopqrstuvwxyzABCD012345`

or

Différents formats de nom d’utilisateur et de mot de passe d’URL, par exemple :
 
`https://username:********@contoso.com/` <br>

`ftp://username:********@contoso.com:20/`<br>


or

Combinaison de 40 caractères :

- a-f ou A-F (respect de la casse) ou 0-9

par exemple :

`abcdef0123456789abcdef0123456789abcdef01`

## <a name="credential-example"></a>Exemple d’informations d’identification 

`pat=ghp_abcdefghijklmnopqrstuvwxyzABCD012345`

## <a name="checksum"></a>Somme de contrôle

Oui

Les SIT qui ont des sommes de contrôle utilisent un calcul unique pour vérifier si les informations sont valides. Cela signifie que lorsque la valeur **de somme de contrôle** est **Oui**, le service peut effectuer une détection positive basée sur les données sensibles uniquement. Lorsque la valeur de somme de **contrôle** est Aucun élément (secondaire) supplémentaire **ne** doit également être détecté pour que le service effectue une détection positive.

## <a name="definition"></a>Définition

Ce SIT est conçu pour correspondre aux informations de sécurité utilisées comme mot de passe de remplacement pour l’authentification sur GitHub lors de l’utilisation de [l’API GitHub ou de la ligne de commande](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token). 

Il utilise plusieurs ressources principales :

- Modèles de pat GitHub identifiable.
- Modèles d’informations d’identification de connexion utilisateur dans l’URL.
- Modèles de clé symétrique de 160 bits encodées hexadécimales.
- Modèles de CredentialName, CredentialFeatures, AccountIdentityName, AccountIdentityValue, ResourceType, ResourceName.
- Modèles de valeurs de maquette, de réactions et d’espaces réservés.

Les modèles sont conçus pour correspondre aux informations d’identification réelles avec une confiance raisonnable. Les modèles ne correspondent pas aux informations d’identification mises en forme en tant qu’exemples. Les valeurs de maquette, les valeurs redépliquées et les espaces réservés, tels que le type d’informations d’identification ou les descriptions d’utilisation, dans la position où une valeur secrète réelle doit être présente ne seront pas mises en correspondance.

## <a name="keywords"></a>Mots-clés

### <a name="keyword_githubpatidentifiablesecret"></a>Keyword_GitHubPatIdentifiableSecret :

- Gh_

### <a name="keyword_logincredentialsinurl"></a>Keyword_LoginCredentialsInUrl :

- ://

### <a name="keyword_symmetrickey160hex"></a>Keyword_SymmetricKey160Hex :

- jeton
