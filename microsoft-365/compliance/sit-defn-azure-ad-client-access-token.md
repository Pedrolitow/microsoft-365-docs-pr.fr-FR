---
title: Définition d’entité de jeton d’accès client Azure AD
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
description: Définition d’entité de type d’entité du jeton d’accès client Azure AD.
ms.openlocfilehash: 99c60e5c6ff2f78b2bf4ecf610e860baea7f95d4
ms.sourcegitcommit: 50da6f1f6ef2274c17ed9729e7ad84395b0a9be2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/08/2022
ms.locfileid: "68503421"
---
# <a name="azure-ad-client-access-token"></a>Jeton d’accès client Azure AD

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

Ce SIT est également inclus dans le sit [groupé Toutes les informations d’identification](sit-defn-all-creds.md) .

 ## <a name="format"></a>Format

Combinaison d’un maximum de 10 000 caractères composés de lettres, de chiffres et de caractères spéciaux.

ou

Clé secrète client ou jeton d’actualisation utilisé dans le protocole OAuth2.0.

ou

Combinaison d’un maximum de 1 000 caractères composés de lettres, de chiffres et de caractères spéciaux.

## <a name="pattern"></a>Modèle

N’importe quelle combinaison de :
 
- jusqu’à 10 000 
- a-z (non sensible à la casse)
- 0-9
- barres obliques (/)
- ou signes plus (+)
- Jusqu’à 2
- signes égaux (=)

par exemple :

`"VersionProfile": null, "TokenCache": { "CacheData": 
"AgAAAAIAAACZAWh0dHBzOi8vbG9naW4ubWljcm9zb2`

or

Variante des formats de clé secrète client ou de jeton d’actualisation, par exemple. <br> 
`ClientSecret:********` <br>
`AppSecret=********` <br>
`ConsumerKey:=********` <br>
`Refresh_Token:********` <br>

or

3 lettres : eyJ (respect de la casse)

And

Combinaison d’un maximum de 1 000 caractères

- a-z (non sensible à la casse)
- 0-9
- tirets (-)
- soulignements (_)
- ou points (.)

par exemple :

`eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsIng1dCI6Ing0Nzh4eU9wbHNNMUg3TlhrN1N4MTd4MX...`



## <a name="credential-example"></a>Exemple d’informations d’identification 

`Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsIng1dCI6Ing0Nzh4eU9wbHNNMUg3TlhrN1N4MTd4MX...`

> [!IMPORTANT]
> Cet exemple a été tronqué. Il ne s’agit pas d’un exemple détectable de ce SIT.

## <a name="checksum"></a>Somme de contrôle

Oui

Les SIT qui ont des sommes de contrôle utilisent un calcul unique pour vérifier si les informations sont valides. Cela signifie que lorsque la valeur **de somme de contrôle** est **Oui**, le service peut effectuer une détection positive basée sur les données sensibles uniquement. Lorsque la valeur de somme de **contrôle** est Aucun élément (secondaire) supplémentaire **ne** doit également être détecté pour que le service effectue une détection positive.

## <a name="definition"></a>Définition

Ce SIT est conçu pour correspondre aux informations de sécurité qui contiennent des revendications que l’on peut utiliser dans [Azure Active Directory B2C](/azure/active-directory-b2c/active-directory-b2c-access-tokens) (Azure AD B2C) pour identifier les autorisations accordées aux ressources Azure. 

Il utilise plusieurs ressources principales :

- Modèles de cache de jetons Azure PowerShell
- Modèles du contexte de clé secrète client
- Modèles de jeton web Json
- Modèles de CredentialName, CredentialFeatures, AccountIdentityName, AccountIdentityValue, ResourceType, ResourceName
- Modèles de valeurs de maquette, de réactions et d’espaces réservés
- Dictionnaire de vocabulaire

Les modèles sont conçus pour correspondre aux informations d’identification réelles avec une confiance raisonnable. Les modèles ne correspondent pas aux informations d’identification mises en forme en tant qu’exemples. Les valeurs de maquette, les valeurs redépliquées et les espaces réservés, tels que le type d’informations d’identification ou les descriptions d’utilisation, dans la position où une valeur secrète réelle doit être présente ne seront pas mises en correspondance.



## <a name="keywords"></a>Mots-clés

### <a name="keyword_symmetrickeycontextinxml"></a>Keyword_SymmetricKeyContextInXml :

- tokencache

### <a name="keyword_clientsecretcontext"></a>Keyword_ClientSecretContext :

- Secret
- jeton
- auth
- Securestring
- clé

### <a name="keyword_jsonwebtoken"></a>Keyword_JsonWebToken :

- eyJ

