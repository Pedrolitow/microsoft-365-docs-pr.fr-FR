---
title: Définition d’entité d’en-tête d’autorisation Http (préversion)
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
description: Définition d’entité de type d’entité de type d’informations sensibles d’en-tête d’autorisation Http.
ms.openlocfilehash: b72934a88f85c0245320baa4b774d3c69196eb47
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2022
ms.locfileid: "66997649"
---
# <a name="http-authorization-header-preview"></a>En-tête d’autorisation Http (préversion)

## <a name="format"></a>Format

En-tête d’autorisation utilisé dans la requête HTTP.

## <a name="pattern"></a>Modèle

Différents formats d’en-tête d’authentification, par exemple :
 
`authorization: basic ********` <br>
`authorization: bearer ********` <br>
`authorization: digest ********` <br>
`authorization: negotiate ********` <br>

## <a name="checksum"></a>Somme de contrôle

Non

## <a name="definition"></a>Définition

Ce SIT est conçu pour correspondre aux informations de sécurité utilisées dans l’en-tête d’une [requête HTTP pour l’authentification et l’autorisation.](/dotnet/api/system.net.http.headers.httprequestheaders.authorization?view=netframework-4.8) 

Il utilise plusieurs ressources principales :

- Modèles d’en-tête d’autorisation Http.
- Modèles de CredentialName, CredentialFeatures, ResourceType.
- Modèles de valeurs de maquette, de réactions et d’espaces réservés.

Les modèles sont conçus pour correspondre aux informations d’identification réelles avec une confiance raisonnable. Les modèles ne correspondent pas aux informations d’identification mises en forme en tant qu’exemples. Les valeurs de maquette, les valeurs redépliquées et les espaces réservés, tels que le type d’informations d’identification ou les descriptions d’utilisation, dans la position où une valeur secrète réelle doit être présente ne seront pas mises en correspondance.

## <a name="keywords"></a>Mots-clés

### <a name="keyword_httpauthorizationheader"></a>Keyword_HttpAuthorizationHeader :

- autorisation

