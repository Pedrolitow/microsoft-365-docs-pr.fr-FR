---
title: Définition d’entité d’en-tête d’autorisation Http
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
description: Définition d’entité de type d’entité de type d’informations sensibles d’en-tête d’autorisation Http.
ms.openlocfilehash: 052323c22f75a2ff9e843ed34b0340e11726aafa
ms.sourcegitcommit: 50da6f1f6ef2274c17ed9729e7ad84395b0a9be2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/08/2022
ms.locfileid: "68503861"
---
# <a name="http-authorization-header"></a>En-tête d’autorisation HTTP

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

Ce SIT est également inclus dans le sit [groupé Toutes les informations d’identification](sit-defn-all-creds.md) .

 ## <a name="format"></a>Format

En-tête d’autorisation utilisé dans la requête HTTP.

## <a name="pattern"></a>Modèle

Différents formats d’en-tête d’authentification, par exemple :
 
`authorization: basic ********` <br>
`authorization: bearer ********` <br>
`authorization: digest ********` <br>
`authorization: negotiate ********` <br>

## <a name="credential-example"></a>Exemple d’informations d’identification 

`Authorization: Basic ABCDEFGHIJKLMNOPQRS0123456789;`

## <a name="checksum"></a>Somme de contrôle

Non

Les SIT qui ont des sommes de contrôle utilisent un calcul unique pour vérifier si les informations sont valides. Cela signifie que lorsque la valeur **de somme de contrôle** est **Oui**, le service peut effectuer une détection positive basée sur les données sensibles uniquement. Lorsque la valeur de somme de **contrôle** est Aucun élément (secondaire) supplémentaire **ne** doit également être détecté pour que le service effectue une détection positive.

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

